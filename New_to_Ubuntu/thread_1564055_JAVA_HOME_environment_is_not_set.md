---
title: "JAVA_HOME environment is not set"
date: 2010-08-30
forum: New to Ubuntu
---

### Post by mail2vs.dvg on 2010-08-30
Hi,

I have install java-6-sun and java-6-openjdk on my system and
As for ubuntu forum i have  set 
JAVA_HOME path as /usr/lib/jvm/java-6-openjdk in /etc/profile.
but whenever i am going to install ChainBuilder CONNECT on system.
chainbuilder ask for license agreement and i accept that immediately i will display

JAVA_HOME environment is not set.
The JDK(JRE) 1.5 or up is required to run the program

So what i have to do to resolve this problem?

Thanks,
mail2vs.dvg

---

### Post by akoskm on 2010-08-30
> **mail2vs.dvg said:**
> Hi,

I have install java-6-sun and java-6-openjdk on my system and
As for ubuntu forum i have  set 
JAVA_HOME path as /usr/lib/jvm/java-6-openjdk in /etc/profile.
but whenever i am going to install ChainBuilder CONNECT on system.
chainbuilder ask for license agreement and i accept that immediately i will display

JAVA_HOME environment is not set.
The JDK(JRE) 1.5 or up is required to run the program

So what i have to do to resolve this problem?

Thanks,
mail2vs.dvg

Hi!
Add the following lines to your ~/.bashrc file:
```

PATH=/usr/lib/jvm/java-6-openjdk:$PATH
export PATH

```.
If it doesn't exist or it's empty just create one.
Hope this help.

---

### Post by mail2vs.dvg on 2010-09-01
Hi [akoskm]("http://ubuntu-ky.ubuntuforums.org/member.php?u=825896"),

I wrote that code in ~/.bashrc file still i facing same problem. 

JAVA_HOME environment is not set.
The JDK(JRE) 1.5 or up is required to run the program.

Thanks,
vijay

---

### Post by jtarin on 2010-09-01
If you installed Suns Jave there should be a Java control panel in System>Preferences>Java 6 Control panel.Then Run it.The tab Java will have two environmental listings. "User" and "System"....sometimes it is enought to set the path there and check enable. 

OR
[Set JAVA_HOME / PATH variables]("http://www.cyberciti.biz/faq/linux-unix-set-java_home-path-variable/")

---

### Post by mail2vs.dvg on 2010-09-01
Hi,

I tried in both way (means Sun Java6 Plugin Control and ~/.bashrc file), but still facing same problem and also i got other error sometimes like below whenever i am trying to install Chainbuilder CONNECT ESB.


Do you agree to the above license terms? [yes or no] 
yes
Unpacking...
Checking integrity of install file...
Extracting...
./cbesb-2.1.1_092209_install.bin: 109: /usr/lib/jvm/java-6-sun-1.6.0.20/jre/bin/java/bin/jar: not found
cd: 115: can't cd to cbesb-2.1.1/config/errordb
mv: cannot stat `derbyserver.properties': No such file or directory
sed: can't read derbyserver.properties_orig: No such file or directory
mv: cannot stat `*.xml': No such file or directory
sed: can't read *.xml_orig: No such file or directory
cd: 125: can't cd to ../runtimedb
chmod: cannot access `bin/fixshell.sh': No such file or directory
./cbesb-2.1.1_092209_install.bin: 137: bin/fixshell.sh: not found
chmod: cannot access `eclipse/eclipse': No such file or directory
chmod: cannot access `wrapper/bin/wrapper-*': No such file or directory
./cbesb-2.1.1_092209_install.bin: 143: /usr/lib/jvm/java-6-sun-1.6.0.20/jre/bin/java/bin/java: not found

JVM vendor is SUN
./cbesb-2.1.1_092209_install.bin: 158: cannot create eclipse/configuration/.settings/org.eclipse.ui.ide.prefs: Directory nonexistent
./cbesb-2.1.1_092209_install.bin: 159: cannot create eclipse/configuration/.settings/org.eclipse.ui.ide.prefs: Directory nonexistent
./cbesb-2.1.1_092209_install.bin: 160: cannot create eclipse/configuration/.settings/org.eclipse.ui.ide.prefs: Directory nonexistent
./cbesb-2.1.1_092209_install.bin: 161: cannot create eclipse/configuration/.settings/org.eclipse.ui.ide.prefs: Directory nonexistent
./cbesb-2.1.1_092209_install.bin: 162: cannot create eclipse/configuration/.settings/org.eclipse.ui.ide.prefs: Directory nonexistent

Done.

Source /usr/set_cbesb.sh to setup your environment variables.
Put these settings in your .profile or .rc script to make them automatic.
root@sun:/usr/local/Chain_Builder# 





**Please provide me steps to install Chainbuilder CONNECT ESB on Ubuntu 10.04**


Thanks,
mail2vs.dvg

---

### Post by akoskm on 2010-09-01
You can see in the error message above that the installer is searching for sun-java and not for the openjdk one.
Please replace the line in your .bashrc
```

PATH=/usr/lib/jvm/java-6-openjdk:$PATH

```
with
```

PATH=/usr/lib/jvm/java-6-sun-1.6.0.20:$PATH

```
and start the installation.

---

### Post by freak42 on 2010-09-01
take a command line and issue:
> 
update-java-alternatives -l

on my system I get a list: 
```
ia32-java-6-sun 63 /usr/lib/jvm/ia32
java-6-openjdk 1061 /usr/lib/jvm/jav
java-6-sun 63 /usr/lib/jvm/java-6-su
java-gcj 1042 /usr/lib/jvm/java-gcj

```

pick the one you want and set it like this:

```
sudo update-java-alternatives -s #nameHere#

```
like

```
sudo update-java-alternatives -s java-6-sun

```

---

### Post by jtarin on 2010-09-01
If it were me and I faced this situation....which I have before concerning Java. I would backup and start over by removing all Java incarnations from my install. Then I would only install the basic implementation of sun-java that was necessary to set up my java environment. I have more thanone java application on my computer and have always found sun-java to be the foremost implementation of Java available. I'm all for Open Source as long as it does what "I" need it to do. When it doesn't I go to the boys that do. Sun! One of the first things I did with my Ubuntu install was to remove all java associated software using the Synaptic Package Manager. Then I installed sun-java...using Synaptic and downloaded:
```
sun-java6-bin
sun-java6-jre
java-common
sun-java6-plugin (for browsers)
sun-java6-fonts
```
Once that was done it was effortless to run as I followed these directions which sets everything.
[Documentation]("https://help.ubuntu.com/community/Java")

---

### Post by jtarin on 2010-09-01
I don't know if you have this info but here is a "[Getting Started Guide]("www.chainforge.net/chainbuilder/GettingStarted.pdf")" for your application in .pdf

---

### Post by mail2vs.dvg on 2010-09-02
Hi,

Thanks for all

sudo update-java-alternatives -s java-6-sun

This code is worked out to set JAVA_HOME path

And i also got another problem. Chainbuilder ebs is installed on my system (ubuntu 10.04) but 
when i was startup eclipse IDE. It will display only Chainbuilder CONNECT loading. After this it 
will  not load Eclipse IDE.
What i have to do for this problem.

Thanks,
mail2vs.dvg

---

