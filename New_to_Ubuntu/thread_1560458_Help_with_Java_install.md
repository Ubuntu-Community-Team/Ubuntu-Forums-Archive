---
title: "Help with Java install"
date: 2010-08-24
forum: New to Ubuntu
---

### Post by Sleven7 on 2010-08-24
I'm trying to install the Java plug-in for Firefox 3.6.8

Java gave me 2 choices for 32bit.

self extracting  or
self extracting RPM

I Googled RPM and Ubuntu was not on the list so I downloaded the other one.

The first instruction was

**Change the permission of the file you downloaded to be executable.** Type:
  chmod a+x jre-6u<version>-linux-i586.bin

returns this error message

chmod: cannot access `jre-6u21-linux-i586.bin': No such file or directory

I changed to the correct directory and the command did not return an error, just another prompt.

The next instruction was

**Change to the directory in which you want to install.** Type:
    cd <directory path name>
    For example, to install the software in the /usr/java/ directory, Type:
    cd /usr/java/

That directory does not exist and I'm not sure how to create it, this is where I'm stuck, can someone tell me how to create this directory.

---

### Post by LiquidMeson on 2010-08-24
[http://tinyurl.com/3yq3p93](http://tinyurl.com/3yq3p93)

:D might need to add a sudo in there.

---

### Post by WhatAreHackers on 2010-08-24
> **Sleven7 said:**
> I'm trying to install the Java plug-in for Firefox 3.6.8

Java gave me 2 choices for 32bit.

self extracting  or
self extracting RPM

I Googled RPM and Ubuntu was not on the list so I downloaded the other one.

The first instruction was

**Change the permission of the file you downloaded to be executable.** Type:
  chmod a+x jre-6u<version>-linux-i586.bin

returns this error message

chmod: cannot access `jre-6u21-linux-i586.bin': No such file or directory

I changed to the correct directory and the command did not return an error, just another prompt.

The next instruction was

**Change to the directory in which you want to install.** Type:
    cd <directory path name>
    For example, to install the software in the /usr/java/ directory, Type:
    cd /usr/java/

That directory does not exist and I'm not sure how to create it, this is where I'm stuck, can someone tell me how to create this directory.

 Just go to this site [http://java.com/en/download/help/linux_install.xml#selfextracting](http://java.com/en/download/help/linux_install.xml#selfextracting) ... you might need to be root to change that file to be executable ... mkdir /usr/java and i think you need for that also ... and i'm pretty sure, you should use self-extracting and not RPM

---

### Post by oldos2er on 2010-08-24
Enable the partner repository (System, Administration, Software Sources, Other Software tab), then in a terminal run ```
sudo apt-get install sun-java6-plugin
```

---

### Post by WhatAreHackers on 2010-08-24
> **oldos2er said:**
> Enable the partner repository (System, Administration, Software Sources, Other Software tab), then in a terminal run ```
sudo apt-get install sun-java6-plugin
```

 woh lol, i didn't know you didn't need the jre?? you learn something everyday now :P

---

### Post by Sleven7 on 2010-08-24
oldos2er,  when I try to add a partner repository it says

Enter the complete APT line of the repository

How do I find the APT line for a particular repository?  In this instance Java's

---

### Post by Sleven7 on 2010-08-24
oldos2er, I went back and looked and found the partners enable, thank you.  Sorry for the misunderstanding you to start with.

---

### Post by Sleven7 on 2010-08-24
Your command seem to work fine, it started the install and then a user agreement popped up with this

<ok>

under the agreement.  I hit enter, the space bar, typed in "yes" then hit enter... nothing, it just sat there.  When
I tried to x out of terminal it said I would kill a process that was still running.  I found no way to agree with the install
to allow it to continue.  Any idea?

---

### Post by jtarin on 2010-08-24
The spacebar and the Enter key are not the same thing....re-run the command. Save yourself some trouble next time.If your going to install something or change any configuration ask here first if your uncertain whether you should do it or not.

---

### Post by Miljet on 2010-08-24
Hit the "tab" key on your keyboard. That will enable you to select the EULA.

---

### Post by Miljet on 2010-08-24
> i didn't know you didn't need the jre

Selecting the plugin will automatically pull in any required dependencies, in this case the jre.

---

