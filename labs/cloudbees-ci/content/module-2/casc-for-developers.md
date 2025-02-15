---
title: "CloudBees CI Configuration as Code for Developers"
chapter: false
weight: 3
---

As a developer you typically (and shouldn't) have access to makes configuration changes to your team's CloudBees CI ***managed controller*** (Jenkins instance). However, developers can take advantage of the GitOps approach to managing the configuration of a CloudBees CI *managed controller* by requesting configuration changes via a GitHub pull requests.

In this lab you will act as developer and CloudBees CI admin, where you will review and merge a pull request to your `cloudbees-ci-config-bundle` repository in your workshop GitHub Organization and then the CasC bundle will be updated and automatically reloaded by the **config-bundle-ops** job on your managed controller.

>NOTE: Please ensure that you have signed up for the [CloudBees Workshops Slack workspace](https://app.slack.com/client/T010A455W77/) as instructed in the *[Pre-Workshop Setup](https://cloudbees-ci.labs.cb-sa.io/getting-started/pre-workshop-setup/#slack)* before continuing with this lab.

1. Navigate to your `cloudbees-ci-config-bundle` repository in GitHub and click on the **Pull requests** link. ![PR link](pr-link.png?width=50pc) 
2. On the next screen, click on the **CasC for Devs lab updates** pull request and then click on the **Files changed** tab to review the requested configuration changes. As you can see, we are adding the `cloudbees-slack` plugin and `cloudbees-slack-integration` configuration for your CloudBees CI user. ![PR Files Changed](dev-casc-changes.png?width=50pc)
3. On the **Files changed** screen click on the 3 dots to the right of the `jenkins.yaml` file name to edit the file. ![Update jenkins.yaml](update-jenkins-yaml.png?width=50pc) 
4. Update the value of the `slack` parameter to match the email you used to sign up to the [CloudBees Workshops Slack workspace](https://app.slack.com/client/T010A455W77) in the *[Pre-Workshop Setup](https://cloudbees-ci.labs.cb-sa.io/getting-started/pre-workshop-setup/#slack)*, then scroll down to **Commit changes**, ensure that **"Commit directly to the `dev-casc-lab` branch"** is selected and click the **Commit changes** button. ![Update Slack email](slack-email.png?width=50pc)
5. Once you have reviewed the change, click on the **Conversation** tab, scroll down and click the green **Merge pull request** button and then the **Confirm merge** button.
6. On the next screen click the **Delete branch** button.
7. Navigate to the **config-bundle-ops** job under the **template-jobs** folder on your CloudBees CI *managed controller*. Shortly after the **master** branch job completes successfully, navigate to the top-level of your managed controller, click on the **Manage Jenkins** link in the left navigation menu.
9. The updated CasC bundle for your CloudBees CI *managed controller* will install the `cloudbees-slack` plugin and update the configuration to match what is in the `master` branch of you `cloudbees-ci-config-bundle` repository and you will see the **CloudBees Slack Integration** added to the  **Managed Jenkins** screen.
10. Next we will check the CloudBees Slack integration for your user by sending a test message. Click your CloudBees CI user name at the top of the screen and then click on the **Slack Integration** link in the contextual menu. ![Slack Integration link](slack-integration-link.png?width=50pc)
12. On the **User Settings** screen for the CloudBees Slack Integration, click on the **Send Test Message** button and you should see the message ***"Message sent successfully, please check Slack"***. If the test message is not sent successfully then make sure your **Slack email** is entered correctly. Finally, click on the **Save** button. ![Slack Send Test Message](slack-send-test-msg.png?width=50pc)
13. Navigate to the [CloudBees Workshops Slack workspace](https://app.slack.com/client/T010A455W77/) and you should see a direct message from the **Slackbot**. ![Slack Test Message](slack-test-msg.png?width=50pc)

**For instructor led workshops please <a href="https://cloudbees-days.github.io/cloudbees-field-workshops/cloudbees-ci/#contextual-feedback-title">return to the workshop slides</a>**
