---
title: "Cannot install openjdk-6-jre"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by mn_voyageur on 2011-05-08
In my attempt to install openjdk-6-jre, I get the following.

Any help would be appreciated.

MarkN

openjdk-6-jre:
 Depends: openjdk-6-jre-headless but it is not going to be installed
 Depends: libaccess-bridge-java-jni but it is not going to be installed

CLI returns:

$ sudo apt-get install openjdk-6-jdk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 openjdk-6-jdk : Depends: openjdk-6-jre (>= 6b20-1.9.7-0ubuntu1) but it is not going to be installed
E: Broken packages
$

---

### Post by mn_voyageur on 2011-05-08
Bump.

---

### Post by munky99999 on 2011-05-10
I just discovered this problem as well. Are you still at maverick?

I believe it might have been something that removed the update repos.

Synaptic -> Settings -> Repos -> Updates

or for cli guys

```
deb http://security.ubuntu.com/ubuntu/ maverick-security universe main multiverse restricted
deb http://mirror.csclub.uwaterloo.ca/ubuntu/ maverick-updates universe main multiverse restricted
deb http://mirror.csclub.uwaterloo.ca/ubuntu/ maverick-backports universe main multiverse restricted
```

should fix your problem.

---

### Post by wildmanne39 on 2011-05-10
> **mn_voyageur said:**
> In my attempt to install openjdk-6-jre, I get the following.

Any help would be appreciated.

MarkN

openjdk-6-jre:
 Depends: openjdk-6-jre-headless but it is not going to be installed
 Depends: libaccess-bridge-java-jni but it is not going to be installed

CLI returns:

$ sudo apt-get install openjdk-6-jdk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 openjdk-6-jdk : Depends: openjdk-6-jre (>= 6b20-1.9.7-0ubuntu1) but it is not going to be installed
E: Broken packages
$

Hi you can try these commands one at a time and then try to install that package again. Aslo make sure that your repositories have the main,universe,restricted and multiverse enabled in synaptic package manager.

sudo rm /var/lib/apt/lists/partial/*

sudo apt-get update

---

### Post by mn_voyageur on 2011-05-13
I have been unsuccessful.

Repos look good.

CLI ```
sudo apt-get update
``` did not help.

Any other suggestions?

MarkN

---

### Post by wildmanne39 on 2011-05-13
> **mn_voyageur said:**
> I have been unsuccessful.

Repos look good.

CLI ```
sudo apt-get update
``` did not help.

Any other suggestions?

MarkN

Hi, let make sure the partial download is completely gone. Type
 
sudo apt-get --purge remove --force sun-java6-jre 
Then
sudo apt-get autoclean
Then
sudo apt-get autoremove
Then try to install the package again.:)

---

### Post by Amp1776 on 2011-05-15
Did anybody solve this? 

 I get: openjdk-6-jre:
 Depends: openjdk-6-jre-headless but it is not going to be installed

in synaptics. headless will respond: openjdk-6-jre-headless:
 Depends: openjdk-6-jre-lib but it is not going to be installed
 Depends: tzdata-java but it is not going to be installed
 Recommends: icedtea-6-jre-cacao but it is not going to be installed

Then backwards to tzdata-java...tzdata-java:
  Depends: tzdata (=2010l-1) but 2011d-0ubuntu0.10.10 is to be installed

which it is. I have apt-get updates and fixed. im at a loss at this point, been on ubuntu several months. Im trying to run android from ubuntu. :confused:

---

### Post by munky99999 on 2011-05-15
Amp1776 have you tried my fix? It worked for me.

---

### Post by Amp1776 on 2011-05-15
thanks dude! been on that for hours, somehow missed yours! :guitar:

---

### Post by itsmekrazzy4 on 2011-08-07
I have been tryin to install scilab...even my problem boils down to
tzdata-java:
  Depends: tzdata (=2011g-0ubuntu0.10.10) but 2011g-0ubuntu0.11.04 is to be installed

I tried the repositories suggested by munky but it still doesn't work!!

---

### Post by sindhughanti on 2012-04-19
> **munky99999 said:**
> I just discovered this problem as well. Are you still at maverick?

I believe it might have been something that removed the update repos.

Synaptic -> Settings -> Repos -> Updates

or for cli guys

```
deb http://security.ubuntu.com/ubuntu/ maverick-security universe main multiverse restricted
deb http://mirror.csclub.uwaterloo.ca/ubuntu/ maverick-updates universe main multiverse restricted
deb http://mirror.csclub.uwaterloo.ca/ubuntu/ maverick-backports universe main multiverse restricted
```should fix your problem.

thank you so much! i am on natty, so i changed the 'maverick' to 'natty'.
many other applications which were dependent on java had stopped working for me and i could not work at all. this helped. i can finally install java now! :P:KS

---

