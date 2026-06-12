---
title: "Fresh Feisty: Intel pro/wireless 2200BG sees network, cannot connect"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by Phyrexicaid on 2007-04-22
Hi,

I convinced my girlfriend to ditch XP and install Kubuntu 7.04, she already uses OpenOffice and Firefox, so there won't be too much of a change.

Problem is, she uses a wireless network at home, and in order for her to print etc she *needs* to be able to connect.  As you can tell from the title, she has an intel pro/wireless 2200BG.

knetwork-manager sees the network just fine (gives signal strength etc), when she clicks connect it prompts for a WEP passphrase.  When she enters the passphrase it says 
"Activation stage: Configuring device" and just sits there at 28%

The passphrase she is entering is correct as a reboot back into Windows verifies.

What are my options?  I'd *really* like her to switch from windows to Linux, but if I can't get wireless working, it's not going to happen. 

Thanks.

EDIT
It seems similar to the following bug:

[https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/96097](https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/96097)

---

### Post by Phyrexicaid on 2007-04-22
My apologies.  It seems the network uses WPA-PSK security with TKIP encryption

I've edited my /etc/network/interfaces file and added in the information provided in the following thread:
[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

I'll send the laptop home with the girlfriend and see if she can connect to her network.

Bit of a complicated way of going about things!

EDIT:
Oh, will there be anything special she'll have to do on her side when she boots into Linux, or will the settings in /etc/network/interfaces provide all the information straight to knetworkmanager?

---

### Post by Phyrexicaid on 2007-04-23
> **Phyrexicaid said:**
> My apologies.  It seems the network uses WPA-PSK security with TKIP encryption

I've edited my /etc/network/interfaces file and added in the information provided in the following thread:
[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

I'll send the laptop home with the girlfriend and see if she can connect to her network.

Bit of a complicated way of going about things!

EDIT:
Oh, will there be anything special she'll have to do on her side when she boots into Linux, or will the settings in /etc/network/interfaces provide all the information straight to knetworkmanager?

Just to finish the story, in case anyone searches and comes up with my post.

I uninstalled network-manager and knetworkmanager (before I did that I made sure that all the dependencies for wicd were installed, notably python-glade2)
I then installed wicd and showed her what she needed to do when she got home.

She put in her network key and was able to connect to her WPA secured network, no hassles.  She also added a network printer on her own, she's catching on fast! (although the printer section in System Settings [Kubuntu] crashed a few times... not the impression I was hoping Linux would make)

But, she's on her way to becoming a fully fledged linux user.

---

### Post by wersdaluv on 2007-04-27
Thanks for posting the solution. 

I have a very similar problem.

I'll try your solution. :)

---

