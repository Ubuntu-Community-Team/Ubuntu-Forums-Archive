---
title: "upgrading to new Ubuntu release"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by thraxsa on 2009-04-20
Only a few days away to the next release ... how easy is it to upgrade ??

I take it that it will be pretty straight fwd ??

---

### Post by Bakon Jarser on 2009-04-20
Easiest way is to open a terminal and type this:

```
sudo apt-get dist-upgrade
```

Be sure to back up any important data first.  Upgrades don't always go smoothly.

---

### Post by anjilslaire on 2009-04-20
yup:
[http://www.ubuntu.com/getubuntu/releasenotes/904overview]("http://www.ubuntu.com/getubuntu/releasenotes/904overview")
> 
Upgrading from Ubuntu 8.10

To upgrade from Ubuntu 8.10 on a desktop system, press Alt+F2 and type in "update-manager -d" (without the quotes) into the command box. Update Manager should open up and tell you: New distribution release '9.04' is available. Click Upgrade and follow the on-screen instructions.

To upgrade from Ubuntu 8.10 on a server system: install the update-manager-core package if it is not already installed; edit /etc/update-manager/release-upgrades and set Prompt=normal; launch the upgrade tool with the command sudo do-release-upgrade; and follow the on-screen instructions. 


---

### Post by ptn107 on 2009-04-20
[http://www.ubuntu.com/getubuntu/releasenotes/904overview#Upgrading%20from%20Ubuntu%208.10](http://www.ubuntu.com/getubuntu/releasenotes/904overview#Upgrading%20from%20Ubuntu%208.10)

> **Bakon Jarser said:**
> ```
sudo apt-get dist-upgrade
```
This won't upgrade 8.10 to 9.04 unless /etc/apt/source.list is edited replacing all occurrences of intrepid with jaunty (this is not a nice way to upgrade, especially with 3rd party repositories enabled).  Let update-manager handle it.

---

### Post by cariboo on 2009-04-20
Before doing an update, make sure you disable any ppa's, then make sure your current version is fully up-to-date, then press Alt-F2 and type:

```
sudo update-manager -d
```

Jim

---

### Post by nandemonai on 2009-04-20
Changing sources and doing a apt-get dist-upgrade tends to breaks things bad these days. Trust me ;)

Use cariboo907's suggestion.

---

### Post by thraxsa on 2009-04-20
> **cariboo907 said:**
> Before doing an update, make sure you disable any ppa's, then make sure your current version is fully up-to-date, then press Alt-F2 and type:

```
sudo update-manager -d
```

Jim


ppa's ???  sorry for sounding a little silly, but what do you mean ??

---

### Post by ptn107 on 2009-04-20
1. Open System -> Administration -> Software Sources.
2. Click on the Third-Party Software tab and uncheck everything on that list (those are unofficial repositories that may screw up your upgrade).  
3. Click close and then open update manager (update-manager -d).  Click 'Check' and install any remaining upgrades before clicking 'Upgrade' above.

---

### Post by Ben Crisford on 2009-04-20
I posted on my blog about this :D.

[http://www.freeyourpc.tk](http://www.freeyourpc.tk)

Lots of info to be found there!

---

### Post by orlox on 2009-04-20
Arent the ppas automatically disabled???

I even remember a dialog mentioning that thir party repositories were being disabled when I used "sudo update-manager -d" to update

---

### Post by Kirk M on 2009-04-20
> **orlox said:**
> Arent the ppas automatically disabled???

I even remember a dialog mentioning that third party repositories were being disabled when I used "sudo update-manager -d" to update

I just updated from 8.10 to 9.04 using the update manager and third party repositories were indeed disabled during the upgrade. After the upgrade was completed, I re-enabled only those third party sources that listed Jaunty among the supported versions. I believe that's the correct way of doing it?

---

### Post by thraxsa on 2009-04-21
> **ptn107 said:**
> 1. Open System -> Administration -> Software Sources.
2. Click on the Third-Party Software tab and uncheck everything on that list (those are unofficial repositories that may screw up your upgrade).  
3. Click close and then open update manager (update-manager -d).  Click 'Check' and install any remaining upgrades before clicking 'Upgrade' above.

Excellent - thanks for that : )

---

### Post by thraxsa on 2009-04-21
I have standard broadband .. I take it that upgrading i something I am better of running overnight due to being a lengthy process ??

anyone have any idea how long the upgrade takes ??

---

### Post by anjilslaire on 2009-04-21
"Standard" broadband doesn't really exist. Is it DSL? Cable? Satellite? Aso, the speeds available in each type vary wildly. I know some people with 3mb DSL, and others with 512kb cable. I have 100mb fiber on my house.

That being said, it shouldn't take overnight to do an upgrade, but it will be quite a while most likely, especially in the 1st week after Jaunty is released, due to Canonical's servers being hammered by everyone.

---

### Post by dcory on 2009-04-21
I upgraded to Jaunty, and now want to re-enable some of the 3rd party repos.  Problem is, I can't access the "software sources" interface.  It just closes every time after I type my pssw.  Anyone else having this problem?

---

### Post by steve101101 on 2009-04-21
no my jaunty works great.

---

### Post by Kirk M on 2009-04-21
> **thraxsa said:**
> I have standard broadband .. I take it that upgrading i something I am better of running overnight due to being a lengthy process ??

anyone have any idea how long the upgrade takes ??

To give you an idea, I have a low end 768k DSL connection. Download speeds are a bit less than 768k but close to it. The upgrade to Jaunty on a fairly new install of Intrepid took about 2 hours and 45 minutes. That includes download, the upgrade process and restarting.

After many years of working with computers (other OS's) it's always good if you monitor the upgrade because on the off-chance that something might go wrong you might catch something useful for troubleshooting later. I didn't stick around for the downloading part of it myself but I definitely monitored the actual upgrade process (about 1/2 hour give or take depending on the hardware).

Of course the best way to upgrade is to back up all your data and do a clean install but I wanted to see how well the upgrade process went. For me, the process went flawlessly. Very impressed.

---

### Post by thraxsa on 2009-04-21
> **Kirk M said:**
> To give you an idea, I have a low end 768k DSL connection. Download speeds are a bit less than 768k but close to it. The upgrade to Jaunty on a fairly new install of Intrepid took about 2 hours and 45 minutes. That includes download, the upgrade process and restarting.

After many years of working with computers (other OS's) it's always good if you monitor the upgrade because on the off-chance that something might go wrong you might catch something useful for troubleshooting later. I didn't stick around for the downloading part of it myself but I definitely monitored the actual upgrade process (about 1/2 hour give or take depending on the hardware).

Of course the best way to upgrade is to back up all your data and do a clean install but I wanted to see how well the upgrade process went. For me, the process went flawlessly. Very impressed.


Excellent - thanks for that, I will back up what i need and then upgrade.  Appears that it should go through without any major issues ( fingers crossed ).  I also have installed kde as well as gnome.  Not too sure how to update that one ...

---

### Post by ugriffin on 2009-04-21
I suggest you try the distro upgrade offered on ubuntu.com. I upgraded to Kubuntu RC 1 with no problem at all.

> 
To upgrade from Ubuntu 8.10 on a desktop system, press Alt+F2 and type in "update-manager -d" (without the quotes) into the command box. Update Manager should open up and tell you: New distribution release '9.04' is available. Click Upgrade and follow the on-screen instructions.


This is most probably how the final upgrade will be handled, but I can't be sure at all. Only 2 days to find out, anyways.

---

### Post by thraxsa on 2009-04-21
hmmm ... my mate is going to do a fresh install .. now I am probably wondering into nothing more than delusional paranoia but at the end of the day, I am better of doing a fresh install or attempt to upgrade ??

Just that I have installed additional programs and setup config files for things like fetchmail ....

Potentially it could be a pain in the backside to go from scratch again ....

---

### Post by ugriffin on 2009-04-23
Today's launch day. And to avoid yourself any bothers, just upgrade. It is simpler in the end. I also suggest that you upgrade using the notification Ubuntu will generate for you, or with my first post. This is how most end-users will upgrade anyways.

---

### Post by thraxsa on 2009-04-23
> **ugriffin said:**
> Today's launch day. And to avoid yourself any bothers, just upgrade. It is simpler in the end. I also suggest that you upgrade using the notification Ubuntu will generate for you, or with my first post. This is how most end-users will upgrade anyways.


Cool - I just ran the update mgr this morning and it said the new distro is available, so I am upgrading at home while I am at work.

---

