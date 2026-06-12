---
title: "Lenovo 3000 N200, wireless network help"
date: 2007-08-23
forum: Networking &amp; Wireless
---

### Post by Butcher00 on 2007-08-23
Recently installed Ubuntu on my Lenovo N200.

Found out on the Lenovo homepage that it has a Intel wireless card.

Searched around this forum 100 times, and tried all good guides for getting the wireless network to work, but nothing ever comes up.
Up in the right corner i never get a "Wireless connection", only Wired connection and modem connection.. (wireless works ofcourse perfect in Vista)

Tried a broadcom installer, both version 0.2.1 and 0.2.2, rebooted, crossed my fingers, but nothing, the network card are nowhere to be seen.

Also tried a bcmwl5 thing, and a wl_apsta thing.. 

Please give me some advice or even a complete guide, from a to z, cause
this i driving me crazy! 

Thanks in advance! :)

---

### Post by scrooge_74 on 2007-08-23
Is your card Intel or Broadcom.

If you have Vista on the same PC or the specs you should check which card exactly you have.

It will depend on that information which is the best way to get it working: either ndsiwrapper using (M$ drivers), Linux drivers or some HOWTO.

Post the info..

---

### Post by Butcher00 on 2007-08-23
It is a Intel Wireless WiFi link 4965AGN according to Vista.

---

### Post by scrooge_74 on 2007-08-23
A Quick search in [http://google/linux](http://google/linux) says this 

[http://intellinuxwireless.org/?p=iwlwifi&n=HOWTO-iwlwifi](http://intellinuxwireless.org/?p=iwlwifi&n=HOWTO-iwlwifi)
[http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/)

From what I read that chipset is  supported...is buggy with Ubuntu and you may have to recompile your kernell or use ndiswrapper

[https://answers.launchpad.net/ubuntu/+question/8861](https://answers.launchpad.net/ubuntu/+question/8861)

---

### Post by Butcher00 on 2007-08-23
cant get anything to work :(

---

### Post by Butcher00 on 2007-08-24
Bump.. Really need your help guys, sorry for my incompetence regarding linux and commands, but i have tried so much now that maybe some drivers are laying in the background and messing when i try to install over again..

I couldn`t remove the ndiswrapper for example, it said that it was stored on more then 1 place on my harddrive, so e tried the remove command over and over, but it continued to say the exact same thing..

I never got the message i was supposed to according to the guide, that "no more files to remove" ore something like that..

Please help, really stuch with this one =/

---

### Post by tfarinella on 2007-09-16
same exact problem i havent tried any of those links but if he had no success then whos to say i will on the exact same laptop

---

### Post by DannyW on 2007-10-10
I just got my N200 today.

Most things seem to work out of the box with Kubuntu **Gutsy** beta, and so probably with Ubuntu Gutsy beta too.

KNetworkManager shows a wireless network in my range, but it's protected by some encryption. I won't have access to a wireless network until I go to Uni tomorrow, but it seems very promising.

The bluetooth icon shows up in the panel tray when I switch it on with the switch on the laptop case. It picks up my PocketPC.

I haven't tried the webcam yet, don't have a program to test it with.

Do not know about the fingerprint reader either, Have you had any luck with it?

Edit: Wireless just worked. Didn't try it with an secure wireless network though. Also, sound appears not to be working, I'll have a search around the forums about that.

---

