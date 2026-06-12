---
title: "vuze problems"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by Uruk-hai on 2010-10-26
So I installed vuze through the ubuntu software program. It launches okay, looks completely normal but when I try and search stuff It doesn't work. There's this error message showing a bunch of Java stuff. What do I do?

---

### Post by TeoBigusGeekus on 2010-10-26
Could you post us the message?

---

### Post by john77eipe on 2010-10-26
Some applications would require JRE. Please post the error message.

---

### Post by Uruk-hai on 2010-10-26
this is what came up. 

Error loading plugin aefeatam_v/com.aelitits.azureus.plugins.featman.featmanplugin'org/gudy/azureus2/plugins/utuls/featuremanager$featureenabler

more. 

java.lang.NoClassDefFoundError: org/gudy/azureus2/plugins/utils/FeatureManager$FeatureEnabler
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:634)
	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:142)
	at java.net.URLClassLoader.defineClass(URLClassLoader.java:277)
	at java.net.URLClassLoader.access$000(URLClassLoader.java:73)
	at java.net.URLClassLoader$1.run(URLClassLoader.java:212)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
	at org.gudy.azureus2.pluginsimpl.local.PluginInitializer.loadPluginFromDir(PluginInitializer.java:1117)
	at org.gudy.azureus2.pluginsimpl.local.PluginInitializer.loadPluginsFromDir(PluginInitializer.java:767)
	at org.gudy.azureus2.pluginsimpl.local.PluginInitializer.loadPlugins(PluginInitializer.java:561)
	at com.aelitis.azureus.core.impl.AzureusCoreImpl$5.run(AzureusCoreImpl.java:777)
	at org.gudy.azureus2.core3.util.AEThread2$threadWrapper.run(AEThread2.java:287)
Caused by: java.lang.ClassNotFoundException: org.gudy.azureus2.plugins.utils.FeatureManager$FeatureEnabler
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
	... 15 more

---

### Post by DirtyPC on 2010-10-26
It's worth un-installing Vuze, then go to Synaptic Package Manager, then Mark All Upgrades, apply (if applicable) then reinstall Vuze, worked for me. But in the end, I switched from Vuze to Transmission, I find it much better

---

### Post by Uruk-hai on 2010-10-26
> **harrylucas1 said:**
> It's worth un-installing Vuze, then go to Synaptic Package Manager, then Mark All Upgrades, apply (if applicable) then reinstall Vuze, worked for me. But in the end, I switched from Vuze to Transmission, I find it much better

Hmm. Ok. I will try that.
Its interesting that you find transmission easier...It gives me a ton of problems. Plus Its super slow.

---

### Post by DirtyPC on 2010-10-27
> **Uruk-hai said:**
> Hmm. Ok. I will try that.
Its interesting that you find transmission easier...It gives me a ton of problems. Plus Its super slow.
I find transmission to be less hassle and simpler. And I admit Transmission does stay Idle for a while before downloading, but then it stays steady at speeds compareable to Bittorrent (ie 2mbps +)
Also, i'm curious, are you Running Ubuntu 10.04?

---

### Post by Uruk-hai on 2010-10-27
> **harrylucas1 said:**
> I find transmission to be less hassle and simpler. And I admit Transmission does stay Idle for a while before downloading, but then it stays steady at speeds compareable to Bittorrent (ie 2mbps +)
Also, i'm curious, are you Running Ubuntu 10.04?


Indeed I am. 10.04

---

### Post by mister_playboy on 2010-10-27
I would not recommend using the old version of Vuze in the repos.  We are not getting newer versions there because of some political issue between the Vuze devs and Ubuntu.

Try downloading Vuze from [here](http://azureus.sourceforge.net/download.php) (because the 64bit version is not offered by the Vuze website for some reason) and installing using the instructions [here](ttp://forlong.blogage.de/en/entries/2008/12/2/How-to-install-and-update-Vuze-formerly-Azureus-4-on-Ubuntu).

---

### Post by GabrielYYZ on 2010-10-27
if you don't like transmission and vuze keeps giving you problems, you can try deluge, i found it to be pretty decent.

---

### Post by DirtyPC on 2010-10-28
Vuze with 10.04 has loads of problems, the search didnt work for me on 10.04 either....

---

### Post by Uruk-hai on 2010-10-28
> **mister_playboy said:**
> I would not recommend using the old version of Vuze in the repos.  We are not getting newer versions there because of some political issue between the Vuze devs and Ubuntu.

Try downloading Vuze from [here](http://azureus.sourceforge.net/download.php) (because the 64bit version is not offered by the Vuze website for some reason) and installing using the instructions [here](ttp://forlong.blogage.de/en/entries/2008/12/2/How-to-install-and-update-Vuze-formerly-Azureus-4-on-Ubuntu).

Okay. I downloaded it but the instruction link doesn't work...It says to launch some kind of application. I am very new at this so is there any really easy way to install vuze? If not could you help me install it the way your telling me?

---

### Post by mister_playboy on 2010-10-28
> **Uruk-hai said:**
> I downloaded it but the instruction link doesn't work...It says to launch some kind of application.I am very new at this so is there any really easy way to install vuze? If not could you help me install it the way your telling me?

I inadvertently cut off the "h" in "http". :P  Try this:
[http://forlong.blogage.de/en/entries/2008/12/2/How-to-install-and-update-Vuze-formerly-Azureus-4-on-Ubuntu](http://forlong.blogage.de/en/entries/2008/12/2/How-to-install-and-update-Vuze-formerly-Azureus-4-on-Ubuntu)

You can skip this step: ```
sudo apt-get install default-jre
``` since Vuze works fine with already-present OpenJDK on newer *buntus.

You might ask well become familiar with running commands from the terminal, because that's the format we use to help each other on the forums, instead of trying to explain things via the GUI: "click here, scroll down there, blah blah."

---

