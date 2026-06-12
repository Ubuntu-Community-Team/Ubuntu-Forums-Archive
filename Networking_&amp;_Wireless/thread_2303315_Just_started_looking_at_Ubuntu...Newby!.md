---
title: "Just started looking at Ubuntu...Newby!"
date: 2015-11-17
forum: Networking &amp; Wireless
---

### Post by Phil_Brantley on 2015-11-17
I have an old Dell 1501 Inspiron with XP. I wanted to install Ubuntu and get to know the OS. I plan to convert all my laptops to it once I get use to it. An old friend, that is no longer with us, introduced me to Redhat years ago. It was wonderful. Before installing, I have been booting it from USB to see if the computer can handle it(32bit). Everything seems to be OK except the wireless routing. I have read many suggestions that a simple dropdown from wireless icon for available networks, click and go. I am not getting that info. So I downloaded the driver for the wireless mini card in Firefox using LAN line. Now what do I do to get into the program? Does Ubuntu work better once you install it? I plan on giving it this laptop. Thanks for the help....NEWBY

---

### Post by grahammechanical on 2015-11-17
> introduced me to Redhat years ago. It was wonderful. Before installing, I  have been booting _**it**_ from USB to see if the computer can handle  it(32bit).

It? RedHat? Or do you mean that you have been running Ubuntu from a live session?

If it is Ubuntu in a live session and you are connected to a router by an ethernet cable, then you should see an Network Manager icon in the top panel on the right. It will be 2 arrows pointing in opposite directions. What do you see in the drop down menu?

Is Enable WiFi ticked? Do you see a list of available wireless access points? You may need to install a driver. You can go to System Settings>Software and Updates>Additional Drivers tab. If you are connected to the internet and allow time for the utility for do its work you may get offered a driver for that wireless adapter.

Is Windows XP still installed on that machine? Is Wireless turned off in Windows? That may be stopping Ubuntu from detecting the wireless adapter.

Regards.

---

### Post by Bucky Ball on 2015-11-17
*Thread moved to **Networking & Wireless**.*

Welcome. Here for now, but as above: Are you using Ubuntu or Redhat??? :-k

---

### Post by mörgæs on 2015-11-18
A 1501 is from around 2006 and might not be strong enough for Ubuntu. Lubuntu is probably a better choice.

---

### Post by Bucky Ball on 2015-11-18
PS: Getting wireless up on a live session (running from install media) can be problematic and any drivers you install will be lost on reboot. Open a terminal and copy this command:

```
sudo lshw -C network
```

Wrap the output of that in code tags (see last link in my signature) here, thanks. 

When you're booted into the live session, what do you see in Additional Drivers?

PPS: When you do install to hard drive, don't start installing wireless drivers without being sure they are what you are looking for (or close). That can cause a lot of confusion and waste time. Ask for help here first, but the output of that command should confirm how easy/difficult your wireless is going to be. :)

---

### Post by Hadaka on 2015-11-18
Hi, you should have no problem running ubuntu on a Dell 1501,providing you have
atleast 1.5 gig of ram and you loaded something other than ubuntu 15.10

since you are in the "Try Me" mode. these changes will be gone on first boot,
From a working wired connection to the internet
please open a terminal...ctrl/alt/t...then COPYand paste.
*Ignore any file not found..
```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer
sudo modprobe b43
```
remove wired connection,test wireless

*You would be wise to dual boot and keep your xp/windows access as there are some things
due to vendors that will not run on ubuntu.

---

