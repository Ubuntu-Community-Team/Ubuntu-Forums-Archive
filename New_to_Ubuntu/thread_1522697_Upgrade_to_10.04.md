---
title: "Upgrade to 10.04"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by Obso1337 on 2010-07-02
Hi, I'm trying to upgrade from Heron to Lynx. I initially tried burning a disk as it is how I've always done it in the past, but something is up with the disk drive of my laptop and it won't work, so I pursued other options. I read you could upgrade from the Update Manager by clicking "Check" after all updates are loaded, but this did not work. I then came across some archived threads with instructions to input the command "sudo apt-get dist-upgrade" but this did nothing. 
I would really appreciate it if someone could help me upgrade to 10.04 through command line somehow!

---

### Post by PotcFdk on 2010-07-02
Uhm one question: Why do you reinstall Ubuntu to upgrade it? Don't you can download the update and apply it on-the-fly?
Edit: Whoopsie, I didn't read a part of your post. Don't you have gnome/Kde/whatever? This seems easier for me than applying a distro update via command line.

---

### Post by Obso1337 on 2010-07-02
Sorry, I believe I used the incorrect term. I meant by using a Terminal in Gnome.

---

### Post by lkjoel on 2010-07-02
First back up all of your documents that you want to keep.
Then, the plan is to erase the whole hard drive and reinstall the new version.
I would suggest you should install 9.10 instead of 10.04, unless you have a lot of time to spare.

So download a live CD of 10.04 or 9.10, then boot to Boot selection pop-up.
Select your CD drive, then once there is a title, I would suggest that you should try it out first.
Then if you are happy with the system, install it.

---

### Post by sandyd on 2010-07-02
```
update-manager -d
```> **Obso1337 said:**
> Sorry, I believe I used the incorrect term. I meant by using a Terminal in Gnome.

---

### Post by 3rdalbum on 2010-07-02
Go to System > Administration > Software Sources (or Software Properties, possibly) and under the Updates tab you can choose to be notified for Long Term Service releases.

Then Update Manager should tell you that there's a new release 10.04 LTS and you can click a special button at the top of the window to upgrade. You might need to update your Hardy first (to the latest Hardy packages) before the button will appear.

---

### Post by Obso1337 on 2010-07-15
> **3rdalbum said:**
> Go to System > Administration > Software Sources (or Software Properties, possibly) and under the Updates tab you can choose to be notified for Long Term Service releases.

Then Update Manager should tell you that there's a new release 10.04 LTS and you can click a special button at the top of the window to upgrade. You might need to update your Hardy first (to the latest Hardy packages) before the button will appear.
Eventually I was able to do this, but for some reason I was only able to upgrade one release at a time and had to go through every one from 8.10-10.04. Very aggrivating and time consuming.

---

### Post by oldsoundguy on 2010-07-15
LTS to LTS can be upgraded without the step upgrades.  (Did so with 8.04 to 10.04)

BUT if you  were running 8.10 .. you had to go to 9.04, then 9.10 before you could get to 10.04.

Have NO idea why you can't skip releases IF you are doing an upgrade, but found out (the hard way) a couple of years back, that you can't.  And no notifications of a change in policy, so suspect that it remains that way.

HOWEVER .. if you copy your ~/home folder to either a separate partition, cd or USB thumb drive, you can do a FRESH install from the CD and just bring that folder back into your install and all your settings and added programs and data will be right there.

---

