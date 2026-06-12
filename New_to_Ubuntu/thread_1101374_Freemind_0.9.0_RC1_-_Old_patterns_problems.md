---
title: "Freemind 0.9.0 RC1 - Old patterns problems"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by Torgeir on 2009-03-20
Good afternoon! 
After updating Freemind to 0.9.0 RC1, the program does not start. Please see attached files for more info. Have tried to delete the patterns.xml files, but is getting the same error when try to launch the program. Freemind version 0.8.0 is work super!

Any help?:P

Best regards

Torgeir

---

### Post by tieuvinhlong on 2009-06-05
Me too. I using freemind but not start because have error with file patterns..


Help me.... how fix it?

---

### Post by Helge on 2009-07-06
Me too, with Freemind 0.9.0 RC4.

When I start Freemind from the command line, I get plenty of error messages. Maybe it's related. See below.




helge@helge-laptop:~$ freemind 
Checking Java Version...
java.io.FileNotFoundException: /home/helge/.freemind/auto.properties (No such file or directory)
	at java.io.FileInputStream.open(Native Method)
	at java.io.FileInputStream.<init>(FileInputStream.java:106)
	at freemind.main.FreeMindStarter.readUsersPreferences(FreeMindStarter.java:136)
	at freemind.main.FreeMindStarter.main(FreeMindStarter.java:56)
Panic! Error while loading default properties.
2009-jul-06 21:47:29 freemind.main.Resources logException
ALLVARLIG: An exception occured: 
org.jibx.runtime.JiBXException: Binding information for class freemind.controller.actions.generated.instance.XmlAction must be recompiled with current binding compiler (compiled with jibx_1_0_2, runtime is jibx_1_1_6a)
	at org.jibx.runtime.BindingDirectory.getFactoryFromName(Unknown Source)
	at org.jibx.runtime.BindingDirectory.getFactory(Unknown Source)
	at freemind.common.XmlBindingTools.getInstance(XmlBindingTools.java:64)
	at freemind.modes.StylePatternFactory.loadPatterns(StylePatternFactory.java:66)
	at freemind.modes.mindmapmode.MindMapController.loadPatterns(MindMapController.java:597)
	at freemind.modes.mindmapmode.MindMapController.loadPatternActions(MindMapController.java:520)
	at freemind.modes.mindmapmode.MindMapController.createStandardActions(MindMapController.java:466)
	at freemind.modes.mindmapmode.MindMapController.<init>(MindMapController.java:388)
	at freemind.modes.mindmapmode.MindMapMode.createModeController(MindMapMode.java:61)
	at freemind.modes.mindmapmode.MindMapMode.init(MindMapMode.java:56)
	at freemind.modes.ModesCreator.getMode(ModesCreator.java:93)
	at freemind.controller.Controller.createNewMode(Controller.java:574)
	at freemind.main.FreeMind.init(FreeMind.java:275)
	at freemind.main.FreeMind.main(FreeMind.java:716)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at freemind.main.FreeMindStarter.main(FreeMindStarter.java:63)

STDERR: Patterns not loaded:java.lang.NullPointerException2009-jul-06 21:47:33 freemind.modes.ModesCreator getMode
ALLVARLIG: Mode freemind.modes.mindmapmode.MindMapMode could not be loaded.
2009-jul-06 21:47:33 freemind.main.Resources logException
ALLVARLIG: An exception occured: 
java.lang.NullPointerException
	at freemind.common.XmlBindingTools.createUnmarshaller(XmlBindingTools.java:85)
	at freemind.modes.mindmapmode.hooks.MindMapHookFactory.actualizePlugins(MindMapHookFactory.java:161)
	at freemind.modes.mindmapmode.hooks.MindMapHookFactory.searchFor(MindMapHookFactory.java:118)
	at freemind.modes.mindmapmode.hooks.MindMapHookFactory.getPossibleNodeHooks(MindMapHookFactory.java:104)
	at freemind.modes.mindmapmode.MindMapController.createNodeHookActions(MindMapController.java:715)
	at freemind.modes.mindmapmode.MindMapController.<init>(MindMapController.java:393)
	at freemind.modes.mindmapmode.MindMapMode.createModeController(MindMapMode.java:61)
	at freemind.modes.mindmapmode.MindMapMode.init(MindMapMode.java:56)
	at freemind.modes.ModesCreator.getMode(ModesCreator.java:93)
	at freemind.controller.Controller.createNewMode(Controller.java:574)
	at freemind.main.FreeMind.init(FreeMind.java:275)
	at freemind.main.FreeMind.main(FreeMind.java:716)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at freemind.main.FreeMindStarter.main(FreeMindStarter.java:63)

STDERR: java.lang.reflect.InvocationTargetException
STDERR: 	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
STDERR: 	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
STDERR: 	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
STDERR: 	at java.lang.reflect.Method.invoke(Method.java:597)
STDERR: 	at freemind.main.FreeMindStarter.main(FreeMindStarter.java:63)
STDERR: Caused by: java.lang.NullPointerException
STDERR: 	at freemind.controller.Controller.getModeController(Controller.java:320)
STDERR: 	at freemind.main.FreeMind.createModeController(FreeMind.java:920)
STDERR: 	at freemind.main.FreeMind.main(FreeMind.java:720)
STDERR: 	... 5 morehelge@helge-laptop:~$

---

### Post by poikiloid on 2009-07-19
If you are using the exerimental version of freemind for ubuntu (ie, the 0.9 release candidate(s) in eric lavar's ubuntu repository...instructions: [http://freemind.sourceforge.net/wiki/index.php/FreeMind_on_Linux#Install_FreeMind_Manually](http://freemind.sourceforge.net/wiki/index.php/FreeMind_on_Linux#Install_FreeMind_Manually))

then beware that this version of FreeMind relies on version 1.0.x of libjibx-java, whereas Jaunty contains a later version, which is (slightly) not backwards compatible. until these packages are updated to the latest libjibx-java, you should downgrade libjibx-java to version 1.0 using synaptic:
find it in synaptic, highlight it, then in Package menu, choose Force Version, then select the one that says eric.lavar.de

voila. no more "patterns.xml" error message.

---

### Post by Helge on 2009-08-31
poikiloid's solution works for me. But when I start freemind from the command line, there are still plenty of error messages and warnings. About the same amount as I reported before.

---

### Post by Helge on 2009-08-31
Follow up question:
When you have downgraded a package, how do you keep it that way? The update manager nags me about upgrading.

On the other hand, I don't want to keep the package downgraded for longer than needed by freemind.

---

### Post by Rosa Walker on 2009-09-03
Hi, I have a related problem with freemind. I am a new Ubuntu (Hardy Heron, 8.1) user. I am still on bottom of learning curve with using Ubuntu, so please explain as simply as possible. I have installed Freemind by going to Administration/Synpatic Package Manager. However, no matter what commands I use in the terminal, I cannot get it to run. Here is an example of an error message: 

~$ export JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.03/;export PATH=$PATH:/usr/lib/jvm/java-6-sun-1.6.0.03/bin/;freemind
Command 'freemind' is available in '/usr/bin/freemind'[I]
The command could not be located because '/usr/bin' is not included in the PATH environment variable.[/I]

Any help would be so appreciated!

Cheers, Rosa M.

---

### Post by falkaholic on 2009-09-16
Adding the other repos and downgrading libjibx-java worked for me.

---

### Post by poikiloid on 2009-09-24
> **Helge said:**
> Follow up question:
When you have downgraded a package, how do you keep it that way? The update manager nags me about upgrading.

On the other hand, I don't want to keep the package downgraded for longer than needed by freemind.

[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-pin]("http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-pin")

to keep the version

edit the file: /etc/apt/preferences
add:
```
Package: libjibx-java
Pin: version 1.0*
Pin-Priority: 1001
```


you can remove that someday. who knows when. maybe after v. 1.0 of freemind comes out as official release...

---

