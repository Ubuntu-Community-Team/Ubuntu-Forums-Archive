---
title: "yoga 2 pro 14.04 lts wifi trouble"
date: 2014-09-13
forum: Networking &amp; Wireless
---

### Post by clorbag on 2014-09-13
just intsalled ubuntu 14 on my yoga 2 pro and tryig to get wifi working, ive attached the wifi info . 
ive completly erased windows by accident but probly for the best lol. any help will be greatly appreciated.

---

### Post by chili555 on 2014-09-13
Wow! Just WOW!! You have been a busy little tinkerer there! First, it appears that you have tried a few USB wireless devices in order to get going. None of them worked, I'll bet. That's because the underlying problem is not the device and driver combination at all! It is this:> 0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	[COLOR="#FF0000"]Hard blocked: yes[/COLOR]That means the key combination, Fn+F2 or some such, has the wireless switched off. The laptop thinks you are on an airplane and can't use wireless....even USB wireless! Now I am certain you have manipulated the keys a dozen times and nothing ever changes. Why am I sure? Because this is a well known issue with the Yoga 2 Pro! I solved just such a case a few days ago and we're going to solve yours now.

First, remove all those USB wireless devices and stick them in a drawer; we probably won't need them again. Second, open a terminal and do:```
gksudo gedit /etc/rc.local
```Use nano or kate or leafpad if you don't have the text editor gedit. 
Right above exit 0 add:
```
modprobe -r ideapad-laptop
sleep 2s
rfkill unblock all
```
Proofread carefully, save and close the text editor. Detach the ethernet, reboot and run and post:
```
rfkill list all
lsmod | grep idea
```
Thanks.

---

### Post by clorbag on 2014-09-13
Yeah I tried the fn button combos as well as a few USB devices. I like to do as much as I can before asking but being a Linux noob it was too much. I will try these methods within then next hour and repost results thanks for your response

---

### Post by clorbag on 2014-09-13
thank you this works great maybe a sticky should be made out of this, many yoga 2 pro owners havinng this problem. attached is new wifi info

---

### Post by chili555 on 2014-09-13
> **clorbag said:**
> thank you this works great maybe a sticky should be made out of this, many yoga 2 pro owners havinng this problem. attached is new wifi infoLooks awesome! The searchers will find it if you use thread tools at the top to mark Solved.

---

### Post by buzzzz on 2014-11-22
Will not that disable the webcam also?

---

### Post by chili555 on 2014-11-22
This is the first I've heard of it. As I haven't a Yoga 2 Pro, I have no way to test. I assume you can:```
sudo modprobe -r ideapad-laptop
cheese  [COLOR="#FF0000"]<--or any application that uses the webcam[/COLOR]
```Does it report that the device is not found?

---

