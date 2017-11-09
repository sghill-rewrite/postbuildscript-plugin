# PostBuildScript Jenkins plugin

[![Build Status](https://ci.jenkins.io/job/Plugins/job/postbuildscript-plugin/job/master/badge/icon)](https://ci.jenkins.io/job/Plugins/job/postbuildscript-plugin/job/master/)

This plugin allows you to run the following actions after a build:

* Batch or shell scripts
* Groovy scripts
* Build steps

You can configure these actions depending on the build status (i.e., only run when build is successful).

Please refer to the [plugin description](https://wiki.jenkins.io/display/JENKINS/PostBuildScript+Plugin) for further
information.

## Issue Tracking

Please use the
[official Jenkins Jira project and issue tracking software](https://issues.jenkins-ci.org/issues/?jql=component%20%3D%20postbuildscript-plugin)
to report new bugs or request features.

## Contributing

### Pull Requests

For bug fixes and enhancements to existing features, first make sure an issue is filed by checking

[this Jira filter](https://issues.jenkins-ci.org/issues/?jql=status%20not%20in%20(Resolved%2C%20Closed%2C%20Done)%20AND%20component%20%3D%20postbuildscript-plugin)


After that please create a pull request on GitHub with your change and link to the JIRA issue in the PR, and link to
the PR from the JIRA issue.

### Plugin Installation

Run

	mvn clean package

Then copy the resulting ./target/postbuildscript.hpi file to the $JENKINS_HOME/plugins directory.
Don't forget to restart Jenkins afterwards.

Alternatively use the plugin management console (http://example.com:8080/pluginManager/advanced)
to upload the hpi file. You have to restart Jenkins in order to find the plugin in the installed plugins list.

### Running in development mode

If you want to try running recent development changes, rather than released binaries, you have two options.
You can run directly from the root of the plugin repository:

    mvn hpi:run

Then visit http://localhost:8080/jenkins/ to play with the plugin.

If your IDE supports compile-on-save mode this is especially convenient since each `hpi:run` will pick up compiled
changes without needing to run to `package` phase.

## Changelog

### Version 1.0.0
* JENKINS-30011 - Allow multiple instances of Post Build Scripts as a post build action
* Fix JENKINS-28825 - Confusing error message when leaving script path empty
* Major refactoring, but still trying to be downwards compatible
* Added help files and translations
* JENKINS-24308 - Expost build variable, the AbstractBuild

### Version 0.18
* Fix JENKINS-43637 - Arbitrary code execution vulnerability:
https://github.com/jenkinsci/postbuildscript-plugin/pull/15
* Fix JENKINS-19873 - Batch or a shell script files to execute doesn't run with arguments

### Version 0.17
* Added an option to set the build to unstable instead of failed

### Version 0.16
* Fix JENKINS-16789 - Concurrent builds using postbuildscript plugin will wait for all the instances to finish

### Version 0.15
* Fix JENKINS-19954 - PostBuildScript runs for each matrix configuration rather than after they are all completed when
set to MATRIX

### Version 0.14
* Fix JENKINS-19326 - Groovy script should execute with workspace dir as working directory.
* Fix JENKINS-19072 - No Such Field: 'executeOnMatrixNodes'
* Fix JENKINS-18936 - checkbox is not staying checked
* Fix JENKINS-19033 - execution is always last, rather than where placed in the post-build actions list
* Fix JENKINS-18530 - Postbuild script plugin not respecting order in Post-build Action

### Version 0.13
* Fix JENKINS-11219 - execution is always last, rather than where placed in the post-build actions list

### Version 0.12
* Let user configure script to be executed either on matrix head or axes nodes. Hidden for non-matrix projects

### Version 0.11
* Fix JENKINS-15395 - Add checkbox to run script when build fails (as well as when it passes)

### Version 0.10
* Fix JENKINS-14668 - failure to load without ivy plugin installed

### Version 0.9
* Merge pull request - Make dependency to Ivy plugin optional

### Version 0.8
* Fixed JENKINS-13418 - PostBuildScript plugin does not load its configuration properly
* Change default value for condition to run scripts if the build is not on success.

### Version 0.7
* Fixed a bug where this plugin breaks Promoted Builds Plugin

### Version 0.6
* Added support of Ivy job type

### Version 0.5
* Built for 1.409 (LTS series)
* Added an option to run this build scripts only on success (merge pull request)

### Version 0.4
* Fixed JENKINS-11219 - Add the option to run the script after all the sub elements of a matrix project build have
finished

### Version 0.3
* Added job build steps to post-build actions

### Version 0.2
* Fixed JENKINS-10889 - PostBuildScript plugin fails with Maven2 jobs

### Version 0.1
* Initial Version
