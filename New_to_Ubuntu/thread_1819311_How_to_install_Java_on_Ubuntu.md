---
title: "How to install Java on Ubuntu?"
date: 2011-08-05
forum: New to Ubuntu
---

### Post by WubiAR on 2011-08-05
Hi,

I wanted to know what is the fastest way of installing Java JRE, and JDK onto the Ubuntu machine. I've been trying to download straight off the website, but I am having trouble with the .bin files. When, I try to follow the instructions, I get stuck because the terminal is not co-operating :KS.

I am trying to download Java from here: [http://www.java.com/en/download/linux_manual.jsp?locale=en](http://www.java.com/en/download/linux_manual.jsp?locale=en)
I downloaded the bin. file (the 2nd option). I am trying to follow the instructions, but when I try to "chmod" the file, the terminal keeps on giving me an error message that there is no such file or directory. 

Example of what I entered. When the first one didn't work, I tried the second. Both commands had same response of no such file or directory, when the file was in fact, placed on my desktop.
> 
chmod a+x jre-6u26-linux-i586.bin

chmod a+x myusername/Desktop/jre-6u26-linux-i586.bin

I've been trying to correctly install the Java set for a couple of days now and failed. It has prevented me from downloading applications like OpenOffice, and hasn't allowed me to run Eclipse yet.

**I am unsure as to whether or not downloading the packages from this tutorial [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java) will get me the latest versions of Java. That's why I didn't follow it.**

---

### Post by raja.genupula on 2011-08-05
are you sure that the file is in correct location at where your trying for chmod.
check it out 

one more thing is file name , be sure about the file name . other wise press first one or two letters and then press tab to get entire file name .

---

### Post by WubiAR on 2011-08-05
Yes I checked and it is still failing.

---

### Post by Metaxa on 2011-08-05
Have you tried doing this?


sudo apt-get install sun-java6-jre sun-java6-plugin equivs


From there you can run:

sudo apt-get update && apt-get upgrade


Easiest way I can think of for Java support


Metaxa

---

### Post by WubiAR on 2011-08-05
> **Metaxa said:**
> Have you tried doing this?


sudo apt-get install sun-java6-jre sun-java6-plugin equivs


From there you can run:

sudo apt-get update && apt-get upgrade


Easiest way I can think of for Java support


Metaxa

For the second command, at the end I get this error:
> 
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


My OpenOffice.org setup keeps failing. It keeps saying that it failed to extract the Java Runtime Environment (JRE) files. (exit code 7)

I downloaded the ,tar.gz package and extracted it. Then clicked "Execute" for the setup and this is what happened.

---

### Post by JRV on 2011-08-05
```
sudo apt-get install ubuntu-restricted-extras
```

will install Java, Flash, and most audio/video codecs in one shot.

---

### Post by beew on 2011-08-06
> **JRV said:**
> ```
sudo apt-get install ubuntu-restricted-extras
```will install Java, Flash, and most audio/video codecs in one shot.

No, with the restricted-extras you get OpenJdk. If you want to install sun java you have to install the packages from Canonical Partners repo.

@op,

First open Synaptic, go to Settings > Repositories > Other Software and make sure that the box for  Canonical Partners is checked. If not, check it and reload.

Now install the packages sun-java6-plugin (it will pull in sun-java6-bin and sun-java6-jre as dependencies) and sun-java6-jdk

Since Ubuntu uses Openjdk as default you still have to tell Ubuntu to use Sun java as default instead. To do that open the terminal and type
```

sudo update-java-alternatives -s java-6-sun 
```

---

### Post by dcsoldschool53 on 2011-08-06
> **WubiAR said:**
> Hi,

I wanted to know what is the fastest way of installing Java JRE, and JDK onto the Ubuntu machine. I've been trying to download straight off the website, but I am having trouble with the .bin files. When, I try to follow the instructions, I get stuck because the terminal is not co-operating :KS.

I am trying to download Java from here: [http://www.java.com/en/download/linux_manual.jsp?locale=en](http://www.java.com/en/download/linux_manual.jsp?locale=en)
I downloaded the bin. file (the 2nd option). I am trying to follow the instructions, but when I try to "chmod" the file, the terminal keeps on giving me an error message that there is no such file or directory. 

Example of what I entered. When the first one didn't work, I tried the second. Both commands had same response of no such file or directory, when the file was in fact, placed on my desktop.
I've been trying to correctly install the Java set for a couple of days now and failed. It has prevented me from downloading applications like OpenOffice, and hasn't allowed me to run Eclipse yet.

**I am unsure as to whether or not downloading the packages from this tutorial [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java) will get me the latest versions of Java. That's why I didn't follow it.**

I hope one of these sites will help you to understand, how to install your java:

```
[http://www.java.com/en/download/help/linux_install.xml](http://www.java.com/en/download/help/linux_install.xml)
``````
[http://www.java.com/en/download/help/linux_x64_install.xml](http://www.java.com/en/download/help/linux_x64_install.xml)
```

---

### Post by Praveen30 on 2011-08-06
well, i have very simple steps to install java and run java programmes on my Ubuntu..it worked for me..

[http://www.tricksfind.in/2011/07/how-to-run-java-programmes-in-ubuntu.html](http://www.tricksfind.in/2011/07/how-to-run-java-programmes-in-ubuntu.html):D

---

### Post by spy_1134 on 2011-08-06
The reason the command didn't work is because the second part of the command you entered didn't have sudo on it, so apt-get couldn't do anything.

Try this:
```
sudo apt-get update; sudo apt-get upgrade
```

---

### Post by frogo on 2011-08-06
> **beew said:**
> No, with the restricted-extras you get OpenJdk. If you want to install sun java you have to install the packages from Canonical Partners repo.

@op,

First open Synaptic, go to Settings > Repositories > Other Software and make sure that the box for  Canonical Partners is checked. If not, check it and reload.

Now install the packages sun-java6-plugin (it will pull in sun-java6-bin and sun-java6-jre as dependencies) and sun-java6-jdk

Since Ubuntu uses Openjdk as default you still have to tell Ubuntu to use Sun java as default instead. To do that open the terminal and type
```

sudo update-java-alternatives -s java-6-sun 
```

I have seen that strategy (have alternative javas) advised but I had troubles understanding what I was doing :( 

For all it's worth, my current strategy is two steps and works as follows:

1. Remove all OpenJDK and IcedTea packages (from ubuntu software center or directly in synaptic package manager)
 
2. Install Sun Java (I'm afraid I drop everything in the basket, ignoring dependencies):

sudo apt-get -y install sun-java6-bin sun-java6-fonts sun-java6-jdk sun-java6-jre sun-java6-plugin

---

### Post by maxar6 on 2011-08-06
Try using openjdk it will run all java virtual machine files.

---

### Post by Miljet on 2011-08-06
> Try using openjdk it will run all java virtual machine files.
I beg to differ. Just ask anybody who plays games on [www.pogo.com](www.pogo.com).

---

### Post by Soul-Sing on 2011-08-07
installing sun/oracle java from their site?: [https://sites.google.com/site/easylinuxtipsproject/java](https://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by RichKatz on 2011-08-12
> **Metaxa said:**
> 


From there you can run:

sudo apt-get update && apt-get upgrade





Metaxa


Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'sun-java6-jre' has no installation candidate
E: Package 'sun-java6-plugin' has no installation candidate

================
I was able to get it using Oracle's .bin file.  However I'm not sure how you plug this in so that you can select it in 
update-alternatives --config java 

Does it have to have a particular name?  Exist in a particular directory?  Or howyou add it to or specify it in the alternatives list.

---

### Post by flyfishingphil on 2011-08-16
> **beew said:**
> No, with the restricted-extras you get OpenJdk. If you want to install sun java you have to install the packages from Canonical Partners repo.

@op,

First open Synaptic, go to Settings > Repositories > Other Software and make sure that the box for  Canonical Partners is checked. If not, check it and reload.

Now install the packages sun-java6-plugin (it will pull in sun-java6-bin and sun-java6-jre as dependencies) and sun-java6-jdk

Since Ubuntu uses Openjdk as default you still have to tell Ubuntu to use Sun java as default instead. To do that open the terminal and type
```

sudo update-java-alternatives -s java-6-sun 
```

beew, Thanks for the info in this thread. Was having problems with Pogo but followed your steps and it works fine now. Let's just hope it doesn't mess up anything else in 11.04. 

Thanks again.

---

### Post by robmcangus on 2011-08-31
I know this is an older thread...but I ran the following command:

chmod a+x jre-6u27-linux-x64.bin

then ran ./jre-6u27-linux-x64.bin

I'm logged in as root but get the following error message:


Unpacking...
Checksumming...
Extracting...
./install.sfx.5752: 1:  ELF    : not found
./install.sfx.5752: 2: Syntax error: ")" unexpected
Failed to extract the files.  Please refer to the Troubleshooting
section of
the Installation Instructions on the download page for more
information.

What am I doing incorrectly?

thanks,
Rob

---

