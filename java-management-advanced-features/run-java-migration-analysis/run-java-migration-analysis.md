# Run Java Migration Analysis

## Introduction

This lab walks you through the steps to run Java Migration Analysis on any Java application on your Fleet.

Estimated Time: 30 mins

### Objectives

In this lab, you will:

* Create a Java Migration Analysis Work Request using the Java Management Service console interface.
* View and monitor the status of Work Requests created using the Java Management Service console interface.
* View/download the generated Java Migration Analysis report.

### Prerequisites

* You have signed up for an account with Oracle Cloud Infrastructure and have received your sign-in credentials.
* You are using an Oracle Linux image or Windows OS on your Managed Instance for this workshop.
* Access to the cloud environment and resources configured in [Lab 1](?lab=set-up-and-enable-advanced-features-on-java-management-service).
* Java migration analysis is enabled on the fleet.
* Have a Java application compiled and run at least once with JDK 8 on your instance.

## Task 1: Submit Java Migration Analysis Work Request

1. First, open the navigation menu, click **Observability & Management**, and then click **Fleets** under **Java Management**. Select the fleet that you have configured in [Lab 1](?lab=set-up-and-enable-advanced-features-on-java-management-service).

    ![image of console navigation to java management service](images/console-navigation-jms.png)

2. Under the **Resources** tab, select **Managed instances**.

   You should see a list of Managed instances that are currently in your Fleet. Select the Managed instance you are interested in.

   ![image of fleet details page](images/fleet-managed-instances.png)

3. Under the **Resources** tab, select **Applications**. You should see a list of Java applications running in this managed instance.

   You could toggle the show/hide Java runtime installation paths to view or hide the Java runtime associated with each application.

   ![image of java applications in managed instance](images/java-migration-analysis-mi-applications.png)

4. Select the Java application or applications you want to run with Java migration analysis. Click on **Actions** and select **Start Java migration analysis**.

   ![image of java migration analysis run settings](images/java-migration-analysis-panel-open.png)

5. In the **Java migration analysis** panel, the source JDK is auto-populated, which is used for compiling and running this java application.

   Under the **Target JDK for migration analysis**, click the dropdown menu and select **JDK 21**. Leave package prefixes to filter as blank for now.

   ![image of Java migration analysis configuration](images/java-migration-analysis-configuration.png)

   Once the changes are made, select **Submit request** and click **Submit**.

   ![image of Java migration analysis submit now](images/java-migration-analysis-submit-now.png)

   > **Note:** You can also schedule Java migration analysis by selecting the **Schedule for later** and setting the schedule preference. Once submitted, you should see a new Scheduled task been created. To view/manage the scheduled task, refer to [Lab 12](?lab=view-and-manage-scheduled-tasks)
   > ![image of Java migration analysis schedule later](images/java-migration-analysis-schedule-later.png)

6. On the same **Managed Instance** page, select **Work requests** under the resources tab. You should see a list of work requests created in your fleet.

    ![image of work request](images/managed-instance-work-requests.png)

7. Wait for the work request to be processed. If the work request has been completed successfully, the status will change to **Completed without Errors**.

    >**Note:** It will take approximately 15 minutes for the request to be completed.

8. Once the work request status shows **Completed without Errors**, Select **Migration analysis reports** under the **Resources** tab.

   You should see a list of Java migration analysis reports that have been conducted in your Fleet. The latest **Java migration analysis** that has been completed should be displayed at the top of the list.

    The entire report can be downloaded for offline viewing by clicking **...** and **Download report**. More information about the downloaded report will be covered under Task 2.

    ![image of java migration analysis report](images/java-migration-analysis-result-final.png)

9. Click on the **Name** of the **Java Migration Analysis report** to view the report. You should see the Report Summary Page indicating an assessment outcome of the migration effort.

   If there are no changes required, the assessment outcome should be **None**. Otherwise, it will be Minor or Major, depending on the percentage of mandatory changes required.

   ![image of java migration analysis report](images/java-migration-analysis-result-final-details.png)

10. Select **Detailed Summary** under **Resources** tab to view the detailed breakdown of the type of the change, category, class count and diagnostic counts in the report.

   ![image of java migration analysis report](images/java-migration-analysis-result-final-1.png)

11. Select **Mandatory changes** under **Resources** tab to view the classes associated with this change type and the specific counts for removed API(s) as well as unsupported internal API(s).

   ![image of java migration analysis report](images/java-migration-analysis-result-final-2.png)

12. Click on any of the hyperlinks displaying the **Removed API(s)** or **Unsupported internal API(s)** count to view the details of all the selected APIs under the specific class such as location, line number and description with a link for more information.

   ![image of java migration analysis report](images/java-migration-analysis-result-final-3.png)

13. Click on the **back button** at the top of the page to navigate back to the migration report.

    ![image of java migration analysis report](images/migration-report-navigation.png)

14. Select **Recommended changes** under **Resources** tab to view the classes associated with this change type and the specific counts for terminally deprecated as well as deprecated API(s).

   You may click any of the hyperlinks displaying the **Terminally deprecated API(s)** or **Deprecated API(s)** count to view more details.

    ![image of java migration analysis report](images/java-migration-analysis-result-final-4.png)

15. Navigate back to the migration report. Select **Archive summary** under **Resources** tab to view the details of each analyzed archive that contains at least one diagnostic count of changes.

    ![image of java migration analysis report](images/java-migration-analysis-result-final-5.png)

16. Select **API view** under **Resources** tab to view the details of the changes. Click on any of the hyperlinks displaying the **Removed API(s)** or **Unsupported internal API(s)** or **Terminally deprecated API(s)** or **Deprecated API(s)** diagnostics count to view the API occurrence details.

    ![image of java migration analysis report](images/java-migration-analysis-result-final-6.png)

    ![image of java migration analysis report](images/java-migration-analysis-result-final-7.png)

17. Click on any of the hyperlinks displaying the **Occurrence count** to view all references for a specific API.

   ![image of java migration analysis report](images/java-migration-analysis-result-final-8.png)

## Task 2: (Optional) Download Java Migration Analysis Report

1. To access the consolidated report and the raw results in multiple json files, navigate to the **Fleet** details page and scroll down till you see **Object storage**. Click the **View bucket details** name under **Object storage**.

   ![image of java migration analysis bucket object](images/fleet-bucket-link.png)

2. The **Java Migration Analysis** HTML report for the application is stored in the zip file: **JMS** > **JAVA_MIGRATION** > **fleet-ocid** > **managed-instance-ocid** > **workrequest-ocid** > **unique-id** > **application-name.zip**.

   The raw results that make up the zip file are available in json file format.

    ![image of java migration analysis bucket object](images/java-migration-analysis-download.png)

3. You can view the HTML report by opening the index.html file located in the folder, extracted from the zip file. A sample view of the report is shown below.

   ![image of java migration analysis html report](images/java-migration-analysis-html-report-1.png)

4. The report is divided into various sections.  You can go to a section by hovering on the **Go To Section** at the top right of the page and select a specific section.

   The information displayed in each section is similar to what is shown on the Oracle Cloud user console.

   ![image of java migration analysis html report](images/java-migration-analysis-html-report-2.png)

You may now **proceed to the next lab.**

## Learn More

* Refer to the [Advanced Features](https://docs.oracle.com/en-us/iaas/jms/doc/advanced-features.html), [Work Requests](https://docs.oracle.com/en-us/iaas/jms/doc/using-java-management-service.html#GUID-77AEEBC0-93A5-4E99-96D6-BEE0FEE4539F) sections of the JMS documentation for more details.

* Use the [Troubleshooting](https://docs.oracle.com/en-us/iaas/jms/doc/troubleshooting.html#GUID-2D613C72-10F3-4905-A306-4F2673FB1CD3) chapter for explanations on how to diagnose and resolve common problems encountered when installing or using Java Management Service.

* If the problem still persists or it is not listed, then refer to the [Getting Help and Contacting Support](https://docs.oracle.com/en-us/iaas/Content/GSG/Tasks/contactingsupport.htm) section. You can also open a support service request using the **Help** menu in the OCI console.

## Acknowledgements

* **Author** - Sherlin Yeo, Java Management Service
* **Last Updated By** - Satish Sarakanam, Sep 2025
