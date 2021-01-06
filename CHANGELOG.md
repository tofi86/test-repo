# Changelog


## v3.0.6
_2020-03-19_

* Fixed an issue related to Java 4-8 version number detection (PR #81, Thanks to @thatChadM for his contribution)

## v3.0.5
_2019-12-15_

* If java is missing, offer a choice between Oracle and AdoptOpenJDK download buttons (#78)
* Support Array style `Java:Arguments` for Apple Plist style (#76)
* Bugfix: do not crash if `CFBundleIconFile` is provided without ".icns" extension (#75)
* Minor French translation fix (PR #73, Thanks to @ebourg for his contribution)

## v3.0.4
_2018-08-24_

* Bugfix: Variables `$APP_PACKAGE`, `$JAVAROOT`, `$USER_HOME` in `JVMOptions` key (Oracle) or `Java:Properties` key (Apple) were not expanded (#69)

## v3.0.3
_2018-07-29_

* Bugfix: changes for the new Java 10 `java -version` formatting (#66)

## v3.0.2
_2018-04-12_

* Bugfix: fix typo in JVMOptions expansion on java exec call (PR #63, Thanks to @michaelweiser for his contribution)
* Added a basic Travis CI build pipeline running a `shellcheck` test for errors and executing the basic testsuite

## v3.0.1
_2018-03-10_

* Bugfix: remove build number from JVM version number when creating comparable version number or extracting major version (fixes #61)

## v3.0.0
_2018-02-25_

* Completeley overhauled algorithm for JVM detection (JRE and JDK)
  * JDK has no longer precedence over JRE
  * All Java Virtual Machines on the system are taken into account
  * See Readme section 'How the script works' for more details
* NEW special syntax in Plist key `JVMVersion` to specify a maximum JVM version requirement in addition to the minimum requirement.
  * See issue #51 for examples
* Support `JVMVersion` also in Oracle PList style (#59)
* Implemented logging to `syslog` facility which can be viewed via `Console.app` (#49)
* Translation of messages to Chinese (PR #55, Thanks to @acely for his contribution)
* Added a table with 'Supported PList keys' to the Readme file
* Refactoring of functions, bash syntax, etc... (#46, #50, #56)
* Bugfix: pass JVM options with spaces correctly to the java exec call (#14)
* Bugfixes: better handling of MainClass arguments with spaces (#57, #58)
* Bugfixes: issues #47, #48, #52

## v2.1.0
_2017-07-28_

* Support for Java 9 which introduces a new version number schema (fixes #43)

## v2.0.2
_2017-04-23_

* Bugfix: do NOT expand/evaluate the default Oracle Classpath (`App.app/Contents/Java/*`) (PR #42, Thanks to @mguessan for his contribution)

## v2.0.1
_2016-11-27_

* Bugfix for regression in argument passthru introduced in 2.0.0 (fixes #39)

## v2.0.0
_2016-11-20_

* Localization of messages (English, German, French) (fixes #27 / PR #30, Thanks to @ebourg for his contribution)
* Improve the version of Java reported in the error messages (fixes #28)
* Send to java.com when the version of Java installed is too old (fixes #29)
* Bugfix for parsing 3-digit java release/build numbers (e.g. for 1.8.0_101) (fixes #36)
* Better search algorithm for specific Java version (fixes #35)
* Use highest available Java version for execution if `JVMversion` is NOT specified (fixes #37)
  * matches the new behaviour for when `JVMversion` IS specified (#35)
* Switch to `/bin/bash` with changes in #35
* Add support for arrays of VMOptions in Apple style Info.plists (PR #25, Thanks to @spectre683 for his contribution)
* Pass command line arguments through to the application (PR #31, Thanks to @dbankieris for his contribution)
* Allow specifying `$JAVA_HOME` relative to `$AppPackageFolder` (fixes #7 / PR #26, Thanks to @toonetown for his contribution)
  * This allows you to set a relative `$JAVA_HOME` via the `<LSEnvironment>` Plist key
  * Which means you can bundle a custom version of Java inside your app!

## v1.0.1
_2015-11-02_

* Improved display error message with applescript (PR #22, Thanks to @ygesnel for his initial contribution)
* Reorder search for Java VM locations when specific JVM version is required (PR #22, Thanks to @yoe for his contribution)

## v1.0.0
_2015-10-08_

* Support for a splash file (PR #19)
  * For details see https://github.com/tofi86/universalJavaApplicationStub/pull/19
* Also search for JRE's (not only for JDK's) when a specific JVMversion is required (fixes #15)
* Expand variables like $APP_ROOT or $JAVAROOT in Apple formatted Plist files so as to match the Oracle format  (PR #17, Thanks to @cxbrooks for his contribution)
* support for `JVMClasspath` in Oracle formatted Plist files (PR #16, Thanks to @pedrofvteixeira for his contribution)
* Mark script as executable (PR #18, Thanks to @yoe for his contribution)
* bugfix: fix JVMDefaultOptions when retrieved from array
* bugfix: hide the retrieved java home path in stdout

## v0.9.0
_2015-05-15_

* added support for `JavaX` Plist key (fixes #9)

## v0.8.1
_2015-03-26_

* Bugfix for `JVMVersion` key present but no JVMs in `/usr/libexec/java_home`

## v0.8.0
_2015-02-22_

* support for `JVMVersion` key (fixes #13, Thanks to @Dylan-M for his contribution)
* use `$HOME` instead of `~` to set the users home directory (fixes #11)
* WorkingDirectory: improved substitution of variables ($JAVAROOT, $APP_PACKAGE, $USER_HOME) (fixes #12)
* use different non-zero exit codes

## v0.7.0
_2014-10-12_

* read ClassPath from ApplePlist in either Array or String style (PR #5, Thanks to Philipp Holzschneider for his contribution)
* read StartOnMainThread (issue #4, Thanks to @wrstlbrnft for his contribution)

## v0.6.3
_2014-07-31_

* check Info.plist for Apple style Java keys. Better indicator to distinguish between Apple or Oracle parsing...

## v0.6.2
_2014-07-28_

* minor code refactoring and bugfixes

## v0.6.1
_2014-07-27_

* Standard Working Directory for Apple PList apparently is the AppRoot directory

## v0.6
_2014-07-12_

* also catch fixed paths for Plist key `JVMWorkDir` *(thanks @dpolivaev)*

## v0.5
_2014-06-30_

* bugfix for pathes / App bundles containing spaces (#2)

## v0.4
_2014-06-30_

* read and set WorkingDirectory based on the key in `Info.plist` (#1)
 * interpret the 3 different values $JAVAROOT, $APP_PACKAGE, $USER_HOME
 * fallback to root / as standard

## v0.3
_2014-03-16_

* enable drag&drop to the dock icon

## v0.2
_2014-03-16_

* trim whitespace from variables and commandline
* don't show errors in output for Info.plist querying

## v0.1
_2014-03-09_

* initial release of 'universalJavaApplicationStub'
