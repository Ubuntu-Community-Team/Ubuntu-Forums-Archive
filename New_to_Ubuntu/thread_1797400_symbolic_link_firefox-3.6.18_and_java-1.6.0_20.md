---
title: "symbolic link firefox-3.6.18 and java-1.6.0_20"
date: 2011-07-05
forum: New to Ubuntu
---

### Post by nomani77 on 2011-07-05
Hi i am newbie at linux, having issue and will try to give you as much information as possible for your better understanding.
 
we are planning to implement Linux on all desktops in our company. We need to have an oracle application working, so that we may migrate our desktops from XP to Linux.
 
For testing purpose we installed the followings.
 
Operating System: Ubuntu 10.10.
Java version : java-1.6.0_20
Explorer : Mozilla Firefox version 3.6.18
 
As i said earlier, we need Java to be linked with Firefox to open the Oracle Forms. To do this, downloaded and installed JRE 5.0 Update 10 on client machine. How i did it all, is mentioned below.
 
1- Went to [[COLOR=#22229c]http://java.sun.com/products/archive..._10/index.html[/COLOR]]("http://java.sun.com/products/archive/j2se/5.0_10/index.html").
2- Downloaded jre-1_5_0_10-linux-i586.bin (Linux self-extracting file).
3- Changed the persmission using ”chmod 755 jre-1_5_0_10-linux-i586.bin”
4- On execution of this file, it created a directory "jre1.5.0_10" and installed the package successfully.
5- Changed my present working directory and went into the Mozilla Firefox plug-in directory, which is /usr/lib/firefox-3.6.18/plugins.
6- Created the softlink using the below commands
ln -s /home/ali/Downloads/java/jre1.5.0_10/plugin/i386/ns7/libjavaplugin_oji.so ./libjavaplugin_oji.so
7- Restarted th Firefox and tried accessing the page, but it still says.
"In order to access this application, you must install the J2SE Plugin version 1.5.0_10 on your client and NPX_PLUGIN_PATH environment variable is set before starting Netscape. To install this plugin, click here to download the oaj2se.exe executable. Once the download is complete, double-click the oaj2se.exe file to install the plugin. You will be prompted to restart your browser when the installation is complete."
 
I dont know what i am missing, i have a little doubt if i successfully created the symbolic link between Java and Firefox.
 
Now when i again try to run the command of creating the symbolic link, it says "ln: creating symbolic link `./libjavaplugin_oji.so': File exists"
 
I will appreciate if anyone could help me, to run the Java Forms [IMG]http://static.linuxquestions.org/questions/images/smilies/smile.gif[/IMG]
 
Regards,

---

### Post by beew on 2011-07-05
This really sounds complicated. You can simply install sun java from Synaptic (go to Settings > Repositories and make sure that Canonical's Partner is activated. Then install sun-java6-plugin (it will pull in sun-java6-bin and sun-java6-jre) and sun-java6-jdk

After that you have to make sun-java the default or Ubuntu would use openjdk even if sun-java is installed. Run this in the terminal
```

sudo update-java-alternatives -s java-6-sun
```

---

### Post by nomani77 on 2011-07-05
> **beew said:**
> This really sounds complicated. You can simply install sun java from Synaptic (go to Settings > Repositories and make sure that Canonical's Partner is activated. Then install sun-java6-plugin (it will pull in sun-java6-bin and sun-java6-jre) and sun-java6-jdk

After that you have to make sun-java the default or Ubuntu would use openjdk even if sun-java is installed. Run this in the terminal
```

sudo update-java-alternatives -s java-6-sun
```
i found from web that i have to have jre1.5.0_10 installed on client end, just to make the oracle form functional. Basically server configuration tells us, which java version should be used at client end using CONTEXT_FILE. I checked and found out that i need to use jre1.5.0_10 at client end. But as you said, i should go and get Java6-plugin installed, i did it and my about:plugins shows that i have Java 1.6.0_24 as shown below.
Java(TM) Plug-in 1.6.0_24
    File: libnpjp2.so
    Version: 
    The next generation Java plug-in for Mozilla browsers.
 
It was neither working with 1.5.0_10 nor with this 1.6.0_24.

---

