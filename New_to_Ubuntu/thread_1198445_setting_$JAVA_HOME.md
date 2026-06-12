---
title: "setting $JAVA_HOME"
date: 2009-06-27
forum: New to Ubuntu
---

### Post by BeardedLinuxGeek on 2009-06-27
```

colin@torrentfreak:~/confluence/confluence-3.0.0_01-std/bin$ sudo ./startup.sh 
If you encounter issues starting up Confluence Standalone, please see the Installation guide at http://confluence.atlassian.com/display/DOC/Confluence+Installation+Guide
Neither the JAVA_HOME nor the JRE_HOME environment variable is defined
At least one of these environment variable is needed to run this program

```I'm trying to set JAVA_HOME to the location where I have installed JDK

I know that I have to put the information in ~/.bash_profile
What I need to know is where JDK is located

to install java all I did was
sudo apt-get install sun-java6

I think java is installed here:
```

colin@torrentfreak:/usr/lib/jvm/java-6-sun$ ls
bin  COPYRIGHT  ext  include  jre  lib  LICENSE  man  README.html  THIRDPARTYLICENSEREADME.txt

```But all I see is JRE not JDK

However, I'm fairly certain JDK is installed because
```

colin@torrentfreak:~$ dpkg --get-selections | grep java
java-common                    install
sun-java5-bin                    deinstall
sun-java5-demo                    deinstall
sun-java5-jdk                    deinstall
sun-java5-jre                    deinstall
sun-java6-bin                    install
**sun-java6-jdk                    install**
sun-java6-jre                    install

``````

colin@torrentfreak:~$ whereis sun-java6-jdk
sun-java6-jdk:
colin@torrentfreak:~$ 

```

EDIT:
The reason I need to set it to JDK and not JRE is because on the website of the program I'm trying to run they say:
> 
Confluence needs JDK 1.5 or newer to be installed on your computer.
 
[LIST]
[*]A JRE (Java Runtime Environment) is not enough
[/LIST]

---

### Post by QIII on 2009-06-27
Looks to me like you are being told you have the option to install java6.

Try sudo java -version 

(can't remember if you need to have root privileges to call that...)

If you get an error, or you don't get 6:


sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-bin sun-java6-fonts
    sudo update-java-alternatives -s java-6-sun

---

