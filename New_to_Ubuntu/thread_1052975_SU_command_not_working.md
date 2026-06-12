---
title: "SU command not working"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by shizumasa14 on 2009-01-28
I am trying to install Java from here: [http://java.com/en/download/help/5000010500.xml#rpm](http://java.com/en/download/help/5000010500.xml#rpm)   It says in terminal to type SU and enter the password.  I type SU and it asks me for my password.  When I type my password I get the authentication failed message.  I am using the only password I have ever set for ubuntu.  I just got it 2 days ago and I wrote it down....  Why isn't it working?

---

### Post by handydan918 on 2009-01-28
First, the file you are trying to install is an rpm and is not designed for debian based systems like Ubu.

Second, before attempting to install any software, always check the Ubu repos (Synaptic) to see if the package is available there. 

Third, the su command doesn't work in Ubu. You can obtain root power temporarily by using sudo instead.

---

### Post by jespdj on 2009-01-28
To install Sun Java 6 from the Ubuntu repository:
```
sudo apt-get install sun-java6-jre
```
If you want to be able to run Java applets in your browser, install the browser plug-in (this is for Ubuntu 8.10):
```
sudo apt-get install sun-java6-plugin
```

---

### Post by binbash on 2009-01-28
you can use sudo or sudo su - command also

---

### Post by Nepherte on 2009-01-28
The command su works in Ubuntu, but by default it switches to the root account which is disabled. Try sudo -i instead.

---

### Post by SeanHodges on 2009-01-28
> **shizumasa14 said:**
> I am trying to install Java

Documentation on how to install Java in Ubuntu:

[https://help.ubuntu.com/community/JavaInstallation](https://help.ubuntu.com/community/JavaInstallation)

---

