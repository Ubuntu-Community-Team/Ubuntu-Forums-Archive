---
title: "[SOLVED] Where does alien install .rpm to"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by ufis on 2008-12-12
I have downloaded ibm-java-i386-sdk-6.0-3.0.i386.rpm from ibm.com (I have been struggling too long to get a client interface working on sun java so I'll be using ibm java for this)

I installed alien (sudo apt-get install alien)
and then installed the rpm (sudo alien -i ibm-java-i386-sdk-6.0-3.0.i386.rpm)

It runs through the install without any errors.

But I cannot find the installed files anywhere (possibly because I do not know where to look for it). All kinds of combinations using the locate command revealed nothing.

sudo update-java-alternatives -l lists only the sun java installation.

Any ideas where I can find the ibm java installed? And maybe some hints on where to look for any other alien installed software. 

Alternatively: I could download ibm-java-sdk-6.0-3.0-linux-i386**.tgz** which I guess is a snapshot of the installed files/directory structure.
How would I then go about to install/implement it to be able to use it with update-java-alternatives?

---

### Post by Michael.Godawski on 2008-12-12
Installing .rpm packages is the last resort in Ubuntu. 

However alien can also convert a rpm package into a deb package, which is easier to handle and to find.

This should convert the file.
```
sudo alien package_file.rpm
```

---

### Post by ufis on 2008-12-12
As I understand it the command
```
sudo alien -i package_file.rpm
```
converts it to .deb anyway and then installs it.

Though even if I just convert it and then install the .deb file, it still leaves me clueless as to where it is installed or how to access it though update-java-alternatives.

---

### Post by spiderbatdad on 2008-12-12
```
java -version
```

```
update-java-alternatives -l
sudo update-java-alternatives -s JRE_Version #where JRE_Version is a variable
```

To locate files:
```
sudo updatedb
locate file
```

---

### Post by ufis on 2008-12-12
Is my questions not clear enough? *read OP again*

Let me try again.

I have: ```
ibm-java-i386-sdk-6.0-3.0.i386.rpm
```

So I navigate to the directory where the file is located. ```
cd ~/downloads/ibmjava
```

Then I install it using alien ```
sudo alien -i -c ibm-java-i386-sdk-6.0-3.0.i386.rpm
```
I get the following output: >         dpkg --no-force-overwrite -i ibm-java-i386-sdk_6.0-4_i386.deb
(Reading database ... 170257 files and directories currently installed.)
Preparing to replace ibm-java-i386-sdk 6.0-4 (using ibm-java-i386-sdk_6.0-4_i386.deb) ...
Unpacking replacement ibm-java-i386-sdk ...
Setting up ibm-java-i386-sdk (6.0-4) ...


So I assume that the rpm was converted to deb and installed.
Yet when I do ```
update-java-alternatives -l
```
All I get is > java-6-sun 63 /usr/lib/jvm/java-6-sun which is my sun java installation.

So my question again:
Where is my ibm java installation? How do I access it or set it as the default java on my box?

---

### Post by spiderbatdad on 2008-12-12
sorry for your frustration. I was hoping the "sudo updatedb" and "locate java" commands might help you. Don't know much about redhat, but I believe it uses /opt often, where gnu/linux/debian-based/ubuntu uses /usr. I'm thinking you may need to set environment variable with something like:```
export PATH=/opt/ibm/java2-s390-50/jre/bin:$PATH
```
 If that is successful, you may need to write that into your .bashrc, rather than set it each time. Of course the package name may be wrong...this is from an earlier version, as discussed here: [http://publib.boulder.ibm.com/infocenter/tivihelp/v2r1/topic/com.ibm.itame.doc/am61_install242.htm](http://publib.boulder.ibm.com/infocenter/tivihelp/v2r1/topic/com.ibm.itame.doc/am61_install242.htm)

---

### Post by ufis on 2008-12-12
Thank you, that helped. found it under /opt

but even if I export the path I still only get my sun java listed when I do ```
update-java-alternatives -l
```
although ```
java -version
``` now shows ibm java

I will see if everything works fine and come back if it does not.

Thanks for your time.

---

### Post by markthecarp on 2008-12-12
Did you remove the open-jdk java packages before installing java-ibm?

I'm very curious as I could not get sound working with the open-jdk java packages in the RH virtual training environment.

If today wasn't the last day of class I'd try the ibm-java packages you link to...

---

### Post by ufis on 2008-12-12
> **markthecarp said:**
> Did you remove the open-jdk java packages before installing java-ibm?

I did not have open-jdk installed, only sun. And I did not remove it before installing ibm java.

> **markthecarp said:**
> If today wasn't the last day of class I'd try the ibm-java packages you link to...

Save yourself the world of trouble and stay away from ibm-java.

Use sun java. It works best.


PS. Everything works fine now.

---

