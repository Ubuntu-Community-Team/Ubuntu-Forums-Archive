---
title: "jre-linux.bin on desktop - now what??"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by trachys on 2009-02-20
Er,

I just figured out how to give myself root privileges. I tried to follow the install instructions at java.com but am lost.

Someone, please tell me how to install jre-6u12-linux-i586.bin .. I'll buy the beer the next time you're in Busan.

Thanks in advance!

ON EDIT: I just found via synaptic package manager that the java plugin hadn't been installed .. installed it, this may soothe the sores ..

EDITED AGAIN: Sores remain unsoothed.

FINAL EDIT: Thanks for your help, taurus and oldos2er

---

### Post by taurus on 2009-02-20
Why not use the version from the repos?  It's easier to install.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```
When you see the java licensing screen, press the Tab key to highlight the <OK> and Return to accept it.

---

### Post by trachys on 2009-02-20
> **taurus said:**
> Why not use the version from the repos?  It's easier to install.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```
When you see the java licensing screen, press the Tab key to highlight the <OK> and Return to accept it.

Thanks for the prompt help!

I did as you recommend, and was told that everything is already up-to-date.

Yet when I go here: [http://www.java.com/en/download/installed.jsp?jre_version=1.6.0_0&vendor=Sun+Microsystems+Inc.&os=Linux&os_version=2.6.27-11-generic](http://www.java.com/en/download/installed.jsp?jre_version=1.6.0_0&vendor=Sun+Microsystems+Inc.&os=Linux&os_version=2.6.27-11-generic)

I'm told I'm using 1.6.0_0 ..

Shall I ignore Java.com's verifier?

(on edit: I don't get a licensing screen??)

---

### Post by taurus on 2009-02-20
Bet you are running version 6.11 while that link is looking for 6.12!  What's the output of this command from a terminal?

```
java -version
```

---

### Post by oldos2er on 2009-02-20
This worked for me: [http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/](http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/)

---

### Post by trachys on 2009-02-20
"version 1.6.0_10" etc.

java.com is right, synaptic is wrong?

---

### Post by trachys on 2009-02-20
> **oldos2er said:**
> This worked for me: [http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/](http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/)

Thanks for the link. I did as instructed and all went well until the install:

333: cannot create install.sfx.etc. permission denied

??

---

### Post by oldos2er on 2009-02-20
> **trachys said:**
> Thanks for the link. I did as instructed and all went well until the install:

333: cannot create install.sfx.etc. permission denied

??

 Which command had you run when you got that error?

---

### Post by trachys on 2009-02-20
sudo ./jre-6u12-linux-i586.bin 

.. I believe. I'd created the directories and tried to execute. Permission issue?

---

### Post by trachys on 2009-02-20
I did what I could to follow java.com's installation instructions, creating the symbolic link etc. about:plugins tells me I'm still at 1.6.0_10.

I think I can live with my old unreliable jre ..

---

### Post by oldos2er on 2009-02-20
> **trachys said:**
> sudo ./jre-6u12-linux-i586.bin 

.. I believe. I'd created the directories and tried to execute. Permission issue?

 "sudo" should take care of permissions. I don't know what could be wrong, sorry.

---

### Post by Robster2 on 2009-02-20
Try having a look at this

[http://amitech.50webs.com/installing/index.php.html](http://amitech.50webs.com/installing/index.php.html)

How to install anything in Ubuntu.

---

