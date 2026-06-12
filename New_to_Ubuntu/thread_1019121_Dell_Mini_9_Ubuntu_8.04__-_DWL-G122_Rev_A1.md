---
title: "Dell Mini 9 Ubuntu 8.04  - DWL-G122 Rev A1"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by mini.nine on 2008-12-22
My problems and questions are several-fold.  I have an old D-Link Wireless USB Adapter (DWL-G122 Rev A1) that no longer works under Windows XP Service Pack 3 due to Microsoft removing several key APIs and D-Link being dumb and not fixing the problems on their end as a result of using undocumented APIs in their drivers.  Basically, for Windows, the device is a brick.

I recently bought a Dell Mini 9 (sitting right next to me) and would like to give some new life to this old USB Wireless adapter.  I've searched and the only things I come across are Rev B/C "guides" and lots of handwaving.  Basically, I need some serious hand holding.  I can use a terminal and know how to sudo and run apt-get, but none of the guides are geared for the Mini 9, nobody appears to have tried Rev A1 before, and, more importantly, no one seems to have very specific instructions that work with both.

The Dell is running Ubuntu 8.04 (shipping version).  The guides I've found that seemed the most promising are the ndiswrapper-related ones.  I've read plenty on ndiswrapper having "issues".  My problem is I can't get 'ndiswrapper-utils' nor 'ndisgtk' installed as the ndiswrapper guides I've read say needs to be done.  Attempting to use the GUI-based Add/Remove... tool shows the "Windows Wireless Drivers" greyed out and says, "Windows Wireless Drivers cannot be installed on your computer type (lpia).  Either the application requires special hardware features or the vendor decided to not support your computer type."  After a bit of searching, I've discovered that LPIA means "Low Power Intel Architecture" and is some type of mutilated x86 processor.

I should mention that I do have a wired connection for the Mini 9 that works fine.  So, I can install, update/upgrade, and other apt-get oriented things (if necessary).  I'd prefer to use GUI-based tools, if at all possible, to get this working.  I hate fiddling around with the Linux command-line.

So, after that background, my question is:

What steps, precisely, do I need to take to get this device to work?

I would prefer NOT upgrading to 8.10 as the computer will become a gift to someone who really needs it more than me and I don't want to mess up whatever support Dell might offer.  Getting wireless access working with this computer is a bonus - the wireless adapter is useless to me.  I only want to make minimal changes to the computer to add wireless support.

---

### Post by anjilslaire on 2008-12-22
I'm confused. The built-in wireless should work out of the box on a dell install...

---

### Post by james_xxx on 2008-12-22
I don't know anything about the wireless USB adapter that you have, but I am a little bit confused as to why you are not using the built-in wireless adapter that comes with the Mini 9.

The Mini 9's come with mini-PCI Broadcom adapters (with the BCM4312 chipset), which can be a bit of a pain sometimes, but should have worked for you out of the box. 

If for some reason the built-in wireless is not working for you, you might try connecting it to a wired network, and running 'sudo apt-get update && sudo apt-get upgrade'. Within a few minutes, you should see a pop-up asking you about proprietary drivers/firmware for your hardware. Click on that, and allow it to install firmware for the wireless adapter.

I recently bought 3 Mini 9's, one for myself, and 2 that I sold to friends, and wireless has been working just fine on them.

---

### Post by mini.nine on 2008-12-22
> **james_xxx said:**
> I don't know anything about the wireless USB adapter that you have, but I am a little bit confused as to why you are not using the built-in wireless adapter that comes with the Mini 9.

The Mini 9's come with mini-PCI Broadcom adapters (with the BCM4312 chipset), which can be a bit of a pain sometimes, but should have worked for you out of the box. 

If for some reason the built-in wireless is not working for you, you might try connecting it to a wired network, and running 'sudo apt-get update && sudo apt-get upgrade'. Within a few minutes, you should see a pop-up asking you about proprietary drivers/firmware for your hardware. Click on that, and allow it to install firmware for the wireless adapter.

I recently bought 3 Mini 9's, one for myself, and 2 that I sold to friends, and wireless has been working just fine on them.

Hmm...I didn't realize that.  I thought it didn't have wireless access for some reason.

New problem:  Won't connect to the network.  WPA-PSK.  Meh.  Actually, this might be why I tried to use my DWL-G122 in the first place.  (I've had it sitting in a corner for a few months - had planned on using it for something and then that idea sort of fell through).

---

### Post by mini.nine on 2008-12-22
Never mind.  Just figured out what was wrong.  Forgot about the MAC address filter on the access point.  No wonder it didn't work.

---

### Post by james_xxx on 2008-12-22
Hmmm, I would still recommend updating/upgrading and then allowing the restricted drivers manager to install the most current firmware from Dell's repositories.

As far as I had been aware, WPA wireless should be working fine in the default Hardy install, but WPA is an issue if you upgrade to (the non-Dell) Ubuntu Intrepid.

The first thing I did when I got my Mini 9, was wipe the drive, and install Intrepid. To get the wireless adapter to work with WPA/WPA2, I finally had to resort to using ndiswrapper. I wish I hadn't had to go that route, but all is working well at the moment.

---

### Post by mini.nine on 2008-12-22
Erk.  New problem.  The whole computer froze shortly after connecting to the access point.  And by frozen, I mean the "mouse cursor refuses to budge" and "keyboard hosed" (i.e. completely unresponsive to even terminal switching keystrokes) frozen.  Had to hold down the power button to get it to shut off.

---

### Post by mini.nine on 2008-12-22
I ran the Update Manager back when I first got this and re-ran it now.  It says that the system is up to date.  I haven't changed any of the sources (some of the guides for the DWL-G122 recommended doing that but I was a bit nervous about doing that).

---

### Post by james_xxx on 2008-12-22
Yeah, I would recommend leaving the sources as they are. In fact, I don't believe you will be able to use any non-Dell sources on this system, as long as you are using Dell's version of Ubuntu.

I am sad to hear about it locking up on you. That is the issue I encountered in Intrepid when trying to connect to a WPA2 network. That is what prompted me to switch to using ndiswrapper with a Windows driver.

However, since you plan to give this Mini 9 away, do you know what kind of encryption the person receiving this machine uses at home? I don't think that unencrypted or WEP encrypted networks will cause any problems at all.

---

### Post by mini.nine on 2008-12-22
I'm pretty sure it is WPA, but if WPA is going to be a problem, I can switch it to WEP.

I just ran around with it for about a half hour with no problems.  Could be a weird fluke from connecting with the network the first time.  Could also be a weird fluke that happens randomly and I got lucky running into it (so I know how to deal with it).

Thanks for your quick response.

---

### Post by cozmicharlie on 2008-12-22
> **james_xxx said:**
> Hmmm, I would still recommend updating/upgrading and then allowing the restricted drivers manager to install the most current firmware from Dell's repositories.

As far as I had been aware, WPA wireless should be working fine in the default Hardy install, but WPA is an issue if you upgrade to (the non-Dell) Ubuntu Intrepid.

The first thing I did when I got my Mini 9, was wipe the drive, and install Intrepid. To get the wireless adapter to work with WPA/WPA2, I finally had to resort to using ndiswrapper. I wish I hadn't had to go that route, but all is working well at the moment.

Just got my Dell and so far I love it.  I would normally agree with mini.nine and install Intrepid but I like Dell's interface and I am giving this as a gift to a non-linux user so I want it to be easy and work for her.

My wireless worked out of the box also (gotta watch those mac addresses) but for those that want to upgrade to the newer version of Network Manager without having to install Intrepid you can install the latest NM from the maintainers repository. The main advantage is for mobile broadband.  NM 0.7 svn has much better support for mobile broadband.

To install simply follow this How to:
[http://ubuntuforums.org/showpost.php?p=5305278&postcount=82](http://ubuntuforums.org/showpost.php?p=5305278&postcount=82)
Don't worry about adding a non-Dell repository it works fine.  

If you get an error that the "applet cannot start since some resources are not available" enter the following command from a terminal:
```
sudo update-icon-caches
```

---

### Post by anjilslaire on 2008-12-23
So, does nm 0.7 in Intrepid support WPA then? Can users install vanilla 8.10 anf have easy access to WPA APs now? If so, that would be great. I'm getting my mini 9 in the next few days.

---

### Post by Tyche on 2008-12-23
> **anjilslaire said:**
> So, does nm 0.7 in Intrepid support WPA then? Can users install vanilla 8.10 anf have easy access to WPA APs now? If so, that would be great. I'm getting my mini 9 in the next few days.

I installed Intrepid Ibex on a Mini 9 using a LiveUSB key.  I had no problem with it.  It even found my wireless connection and I was shortly downloading gobs of updates :-)

I am running a larger system than the "stock" ubuntu machine, though, as I upgraded the memory, SSD and added the webcam.  I've been having heads turning ever since I got it, anyplace I take it, partly because it acts like a full-sized computer.  To see some of my experiences, see [http://tycheent.wordpress.com/2008/10/14/mini-mine/](http://tycheent.wordpress.com/2008/10/14/mini-mine/) and its followup, [http://tycheent.wordpress.com/2008/10/17/update-on-mini-mine/](http://tycheent.wordpress.com/2008/10/17/update-on-mini-mine/)

---

### Post by cozmicharlie on 2008-12-23
> **anjilslaire said:**
> So, does nm 0.7 in Intrepid support WPA then? Can users install vanilla 8.10 anf have easy access to WPA APs now? If so, that would be great. I'm getting my mini 9 in the next few days.

Yes, nm 0.7 has much better support for wpa.  As tyche states a vanilla intrepid should work fine for you.  I have installed Intrpeid on eeepc's and Acer Aspire Ones and it has worked great.  They alo have an Intrepid version specifically optimized for umpc (netbooks).  It is very hard to find (I think) on the Ubuntu web site but the download and instructions for installing are here:
[https://wiki.ubuntu.com/MobileTeam/Mobile/HowTo/TurnUMPCDesktopIntoNetbook](https://wiki.ubuntu.com/MobileTeam/Mobile/HowTo/TurnUMPCDesktopIntoNetbook)

---

### Post by Tyche on 2008-12-23
> **cozmicharlie said:**
> Yes, nm 0.7 has much better support for wpa.  As tyche states a vanilla intrepid should work fine for you.  I have installed Intrpeid on eeepc's and Acer Aspire Ones and it has worked great.  They alo have an Intrepid version specifically optimized for umpc (netbooks).  It is very hard to find (I think) on the Ubuntu web site but the download and instructions for installing are here:
[https://wiki.ubuntu.com/MobileTeam/Mobile/HowTo/TurnUMPCDesktopIntoNetbook](https://wiki.ubuntu.com/MobileTeam/Mobile/HowTo/TurnUMPCDesktopIntoNetbook)

I'll add this to cozmicharlie's post:  There is a way to get the Ubuntu Intrepid Ibex Remix.  I've played with it a little (a very little) and it works fine.  But I'm so used to the standard screen that I may drop it out again.  You can get instructions for installing it at [http://www.ubuntumini.com/2008/10/installing-ubuntu-netbook-remix.html](http://www.ubuntumini.com/2008/10/installing-ubuntu-netbook-remix.html)

---

### Post by anjilslaire on 2008-12-28
OK, guys.

My mini 9 arrived finally and I've installed Intrepid, with all updates, and the proprietary Restricted drivers for the broadcom wireless. I've also got nm v0.7 as well.

No WPA. I can see it, but nothing connects. Unsecured works fine. Can you give details on what I may be missing? I've confirmed the SSID, key, etc. Nothing.

Help?

---

### Post by cozmicharlie on 2008-12-29
What do you mean "I can see it"?

---

### Post by anjilslaire on 2008-12-29
meaning, the mini can find the AP and tries to connect, but the WPA key is never accepted and connection fails. I've tried disabling WPA, connecting is prompt and network access is strong. Enable WPA again and no-go. Keeps prompting for a key. I've even tried setting the WPA key to something simple like 12345678, to rule out fat-fingering the key, but it fails every time. I see there are several bugs logged and various suggestions as to a solution, but they're not working for me.

Unless I get this worked out, I guess not broadcasting the SSID and using MAC Filtering will have to be sufficient, but WPA would be nice.

---

### Post by cozmicharlie on 2008-12-29
> **anjilslaire said:**
> meaning, the mini can find the AP and tries to connect, but the WPA key is never accepted and connection fails. I've tried disabling WPA, connecting is prompt and network access is strong. Enable WPA again and no-go. Keeps prompting for a key. I've even tried setting the WPA key to something simple like 12345678, to rule out fat-fingering the key, but it fails every time. I see there are several bugs logged and various suggestions as to a solution, but they're not working for me.

Unless I get this worked out, I guess not broadcasting the SSID and using MAC Filtering will have to be sufficient, but WPA would be nice.

Don't take this wrong but sometimes it is something minor so start with simple things and rule them out.  WPA should work for you so something is not right.  Double check the following:
[LIST=1]
[*]Is wpa supplicant installed (check via synaptic)?
[*]Do you have mac address security either turned off (in the router) or set to allow the mac address for the computer (I once had my mac address set to "prevent" rather than "permit").
[*]Is your wireless security set to "wpa & wpa personal" (right click on the nm applet in the panel and go to edit connections>wireless>wireless security).
[*]Don't know if this matters but my encryption is set as "AES".
[*]Did you cut and paste the password from the router interface or are you typing it?  I find some of the letters hard to read and on mine, I am not always sure what they are.  It works better if I cut and paste the password from the router interface to the wireless set up in Network Manager.
[/LIST]

Hopefully it is just something minor and you will figure it out.  Worse comes to worse - WEP, don't broadcast your ssid and mac address filtering aren't as good as wpa but they still give you some protection at least.

---

### Post by anjilslaire on 2008-12-31
No go.

1. yup, wpasupplicant 0.6.4-2, network-manager 0.7-0ubuntu1~nm1~intrepid1
2. MAC fIltering is correct, I have it enabled with WPA off & connection is fine
3. wpa personal, yes
4. tried tkip and AES, no difference
5. Confirmed the password is correct.

Whats maddening is I have an Inspiron 1429 with Kubuntu 8.04 that can connect to my AP flawlessly with WPA on.

BTW, my wireless driver is the latest Broadcom STA wireless driver offered by the Hardware Drivers applet, and my kernel is 2.6.27-9-generic, running on vanilla Ubuntu 8.10 i386

UPDATE:
Dunno why, but switching my router to WPA2 Personal, AES has fixed it. Same Key, Mac filtering etc. Doesn't make any sense, but hey..
Thanks for making me run through all the common stuff again with a clear head. And, teh configuration is staying through a full reboot as well. Mark this another Mini WPA solved :)

---

### Post by cozmicharlie on 2008-12-31
> **anjilslaire said:**
> No go.

1. yup, wpasupplicant 0.6.4-2, network-manager 0.7-0ubuntu1~nm1~intrepid1
2. MAC fIltering is correct, I have it enabled with WPA off & connection is fine
3. wpa personal, yes
4. tried tkip and AES, no difference
5. Confirmed the password is correct.

Whats maddening is I have an Inspiron 1429 with Kubuntu 8.04 that can connect to my AP flawlessly with WPA on.

BTW, my wireless driver is the latest Broadcom STA wireless driver offered by the Hardware Drivers applet, and my kernel is 2.6.27-9-generic, running on vanilla Ubuntu 8.10 i386

UPDATE:
Dunno why, but switching my router to WPA2 Personal, AES has fixed it. Same Key, Mac filtering etc. Doesn't make any sense, but hey..
Thanks for making me run through all the common stuff again with a clear head. And, teh configuration is staying through a full reboot as well. Mark this another Mini WPA solved :)

Excellent - enjoy

---

### Post by anjilslaire on 2008-12-31
I'd also like to throw out the following now that I"m sorted:

Don't edit your connections in Network Manager, delete & recreate them, and do a reboot after each attempt. I found as I was editing and stopping the connection & restarting, the wireless would "see" weird APs, like my AP 2x with & without encryption at the same time, when I had only 1 instance created...

Wipe your wireless connections clean and start each attempt fresh.

---

### Post by vdoki on 2009-01-09
> **anjilslaire said:**
> switching my router to WPA2 Personal, AES has fixed it.

What kind of router do you have? I have the same problem, WPA2 works fine, but WPA is not. But I need WPA, because there are other devices, that don't know about WPA2 (a sonyericsson phone). This is an SMC router.

Anyone solved something like this? This is a Broadcom Corporation BCM4312 card, and I'm using an up to date ubuntu 8.10.

---

### Post by anjilslaire on 2009-01-10
I"ve got a Linksys WRT54G, bought cheap from a brick & mortal store, nothing special.

---

