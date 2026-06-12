---
title: "Q: Wifi trouble"
date: 2010-11-28
forum: New to Ubuntu
---

### Post by Trandre on 2010-11-28
I have had my WiFi disabled three times on two different laptops. I cannot fix it and all that helps is a fresh install. The modification I have done in all instances is to change the language to norwegian. Is this a known bug in the system, or is it just a coinidence?

---

### Post by Trandre on 2010-11-28
The language wasn't it. The wifi was disbled again after for restart. any ideas?

---

### Post by anewguy on 2010-11-28
Does the syslog (in /var/log) show any error messages for your wireless trying to start?  Also, if you left click on the network manager icon, do you see the "Enable Wireless" option or is it missing or grayed out?  If it's there, is it enabled?

Since I don't know any other languages, I've never been in the position you are, but I do have a question:

- since this happens after you change the language, what happens if you just install and select Norwegian on the install?

Dave ;)

---

### Post by Trandre on 2010-11-28
I have this paralell issue. It cannot lovk this file. Does that make any sense to the same issue?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=176847&stc=1&thumb=1&d=1290977960[/IMG]

---

### Post by anewguy on 2010-11-28
> **Trandre said:**
> I have this paralell issue. It cannot lovk this file. Does that make any sense to the same issue?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=176847&stc=1&thumb=1&d=1290977960[/IMG]

Unfortunately the image there is too small to read.  Can you post a large image or even the text?

thanks
Dave ;)

BTW - you may want to try this in a terminal window and see if it helps or not:

rfkill unblock all

---

### Post by zipteye on 2010-11-28
Doesnt grub clober some user modified files occasionally?
Could it be something like that?
 
Or maybe... update-grub
Reboot

---

### Post by anewguy on 2010-11-28
grub shouldn't clober any file that deal with anything other than booting, in particular just the grub menu files.  It used to be you edited just one file to make changes for grub, but with enhanced grub, grub2, whatever it's called, came a big change in the structure of things.  However, nothing dealing with grub should do anything to wifi.

Dave ;)

---

### Post by Trandre on 2010-11-30
Thank you for the responses. I am sure its not about the language now. Because the WIFI failed after the first reboot after the fresh install. That means that I was in and able to input my code and surf on the web. 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=177007&stc=1&d=1291139141[/IMG]

When I click on the WIFI symbol I now see WiFi disabled, without having the option to enable the WiFi

---

### Post by Trandre on 2010-11-30
Hooked up to a wired network and performed an update. solved another issue. Then i was suddenly able to log on the WiFi

---

### Post by anewguy on 2010-12-01
Glad to hear it - the update probably downloaded a driver for you or at least some portion that was needed.

Dave ;)

---

### Post by Trandre on 2010-12-01
It happend again, the Wifi got disabled and i wasnt able to activate it. After some investigation I found out the default user priveliges out of the pack, did not include handleling WiFi. So I enabled this. No Change. Then I hooked up to a wired connection, did a sudo apt-get update and an update through update manager. Still no access to wifi. 

Then i turned the WIFI hardware switch off, restarted and then turned it on and presto. The WiFi was enabled
:D:popcorn:

---

### Post by Trandre on 2010-12-01
I have to start with the wifi hardware switch off everytime and then on after stratup, to enable the wifi. weird. What can cause this?

---

### Post by NCLI on 2010-12-01
> **Trandre said:**
> I have to start with the wifi hardware switch off everytime and then on after stratup, to enable the wifi. weird. What can cause this?

I don't know, but it sounds like a bug to me.

Press alt+F2, then enter(without the quotes): "ubuntu-bug network-manager".

That should start the bug reporting process.

BTW: The error in your terminal has nothing to do with your Wifi, it's just saying that something is already trying to update your system, which is why apt-get update won't work. It's probably trying to check for updates in the background.

---

### Post by Trandre on 2010-12-02
Done :-)


[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/684315](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/684315)

---

