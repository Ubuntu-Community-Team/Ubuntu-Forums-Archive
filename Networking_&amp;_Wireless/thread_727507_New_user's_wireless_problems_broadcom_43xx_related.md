---
title: "New user's wireless problems broadcom 43xx related?"
date: 2008-03-17
forum: Networking &amp; Wireless
---

### Post by A Dardeau on 2008-03-17
I am considering switching my os to ubuntu, being thoroughly angered at windows in my short time using it again.  I am completely impressed by the boot disk version, however I can not get my wireless card to work.  As I do not have a wired connection getting tech support requires shutting down my computer, returning to windows, and then re booting ubuntu.  The problem seems to be related to what I gather to be a common problem related to the broadcom 43xx firmware.  Every time I try to go through the secure drivers manager and enable the firmware I am met with an error message.  After reviewing all of the fixes I could find for the broadcom 43xx problems, they all seem to require a wired connection.  Are there any solutions that I could use without having a wired connection?  Or is this even a broadcom 43xx issue?  i am a completely new linux user, and fairly new to windows, having spent most of my computer use time in osx and os9.  I am running ubuntu ver. 7.10 from a boot disk on an HP Pavillion dv5000.  I would really like to make ubuntu my new os but wireless breaking down is a dealbreaker.

---

### Post by Th3Professor on 2008-03-18
I initially had similar problems with wireless, similar card too.

The difference though was my work was done on a full install, it sounds like you're using the livecd. I'm not sure how much luck you'll have with the proprietary driver installation in that case.

Could you provide the specific steps that you are taking? (The attempts at getting wireless to work.)

It sounds like you've looked into the "restricted" drivers, though providing specific steps you've taken will clarify that.

Have you done the following:

Select System menu --> Administration --> "Restricted Drivers Manager"

Two very common components that show up in the next window are the accelerated graphics driver and the firmware for network cards by chipset.

In that window do you see firmware for Broadcom 43xx (chipset family)?

When you check-mark "Enabled" (and go through the following steps that turn up from enabling it) do you get any positive results?

If not, see if you can include the details of any errors or failed installs/etc. in here so other individuals may better assist you.

---

### Post by A Dardeau on 2008-03-18
I have gone through the steps Select System menu --> Administration --> "Restricted Drivers Manager"

The options on the restricted drivers  menu was "ATI accelerated graphics driver", "software modem driver", and "firmware for broadcom 43xx chipset family".  When I attempt to enable the firmware bor broadcom... I am met with the message "The software source for the package bcm43xx-fwcutter is not enabled."  I'm sure this would be much easier on a full install, however I do not want to run a full install until I have this problem figured out, if I was to run a full install and was not immediately able to fix my wireless then I would be cut off from internet access, including tech support.  I would really like to switch to ubuntu but just cannot until this issue is resolved.

---

### Post by Th3Professor on 2008-03-20
> **A Dardeau said:**
> I have gone through the steps Select System menu --> Administration --> "Restricted Drivers Manager"

The options on the restricted drivers  menu was "ATI accelerated graphics driver", "software modem driver", and "firmware for broadcom 43xx chipset family".  When I attempt to enable the firmware bor broadcom... I am met with the message "The software source for the package bcm43xx-fwcutter is not enabled."  I'm sure this would be much easier on a full install, however I do not want to run a full install until I have this problem figured out, if I was to run a full install and was not immediately able to fix my wireless then I would be cut off from internet access, including tech support.  I would really like to switch to ubuntu but just cannot until this issue is resolved.

Search these forums for threads with the keyword:
fwcutter

There are fixes available in some of the fwcutter-related threads. Hopefully one of them will work for you.

---

### Post by jlauts on 2008-03-20
I had this problem as well with my Hp Pavilion which has the broadcom $#*!-set. If the restricted drivers part doesn't automatically download it for you, you need to go into System, Admin, then the Synaptics Package Manager thing. Once you are in there search for "broadcom". Check off the bradcom-fwcutter for installation then hit apply on the top of that window. Allow everything to download and install. After this is done, go back and try to the restricted drivers menu and try your original part.

Hope that helped.

---

### Post by seps1816 on 2008-05-22
any chance u can get the firmware from another computer then transfer it over cause im having the same problem and i have no internet connection except for the wifi from my neighborhood

---

### Post by Gonzalo_VC on 2008-07-24
[COLOR="Navy"]Unfortunately wireless connection, specially with Broadcom devices, looks pretty complicated and unsatisfactory...   got some clues here (but not so easy, at first look):

[http://bcm43xx.berlios.de/?go=devices](http://bcm43xx.berlios.de/?go=devices)

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

Good luck! [/COLOR]

---

