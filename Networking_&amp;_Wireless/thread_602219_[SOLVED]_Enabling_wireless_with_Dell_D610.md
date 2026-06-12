---
title: "[SOLVED] Enabling wireless with Dell D610"
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by amphibem on 2007-11-04
Hey I (like many others) am trying to get my wireless working in 7.04. I have a Dell D610 w/ Intell 2200 card.

When i go into network setting I can see mine and my neighbors networks; I select mine, set WEP and type in the pass phrase. All good. But fn+f2 doesn't enable my wireless, or at least it doesn't turn the LED on.

Go into Firefox, or Update Manager and nothing can connect. I tried wired and that worked.

Tried various suggestions from other threads:

'iwlist eth1 scanning' brings my network FLAT, looks good

'iwconfig' brings up the same network under eth1, got ESSID "FLAT", 54MB/s, looks good

But when I go into my router setup it cannot see the laptop as an attached device. Access control is turned off on the router and this laptop found the network, and the internet, perfectly under XP.

So even though various tools can see the network, I cannot connect to the internet. Is something wrong with a security setting somewhere? I'm hoping someone will find this and have an idea.

Cheers

Edit: Also tried 'sudo sudo lsmod | grep ipw2200' and gave some lines in return so it seems the driver is loaded. But the wifi LED light is off and fn+f2 does not switch it on

---

### Post by DellCA on 2007-11-12
I'm not sure if you've gotten this fixed yet or not, but I thought I'd post some useful info on troubleshooting wireless connectivity problems.  This is not Linux specific, but general info that might help you figure out what is happening.  Unfortunately I have not had the opportunity to play with wireless networking under Linux, but I have quite a bit of experience with it in Windows.

With any kind of networking you should always start with the simple stuff and work from there to the more complicated, as most of the time the problem is something simple like a bad or lose cable, misconfigured DNS, etc.  For wireless it is best to tackle a problem as two parts: association with the AP/router and network connectivity.  You can not have connectivity when you are not associated, but you can be associated without connectivity.

If I'm reading things correctly the hardware is known to be good (since it worked in XP) and you have verified the wireless card is seeing your network in Ubuntu.  I believe the problem is that it is not associated with (actually talking to) the router, even though it can see the router.  If you have not already done so I would recommend setting your router to no encryption and verify the SSID (aka Network Name, up to 32 alpha-numeric characters of your choice) that it is using.  The SSID is case sensitive and is often the problem when a person can't connect (usually because they see an SSID they think is theirs, but is actually just something similar).

Unfortunately, this is where my information starts to get vague, since I don't know the specifics of setting up wireless under Ubuntu.  If the information above does not fix the problem my recommendation, what I usually have Windows users try, is to blow away any current configuration for the wireless card on the computer and start over from scratch on configuring the wireless network connection.  19 times out of 20 this has fixed any wireless problem I've helped with before.

If you have any specific questions for me about the system itself I'll be more than happy to answer them.  I will also be able to help with any general wireless questions, since that is the same no matter what OS you are using.  Hopefully this helps.

Larry
Dell Customer Advocate

---

### Post by amphibem on 2007-11-12
Thanks Larry, I have tried re-doing the settings but still the strange combination of a apparently working adapter, with the correct key, and no internet. Given this is all that stops me from using Ubuntu permanently it's really annoying!

---

### Post by DellCA on 2007-11-13
Since I decided to take this as an excuse to learn more about wireless under linux I did some checking. :)

Have you already read through the [Ubuntu WiFi HowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)?

From everything you've posted it sounds like the card is not being told what network to try and connect to.  Try the Command Line section of the HowTo (about halfway down the page) and see if that works for you.  It gives the CLI commands for setting the channel, SSID and (if you are using it) encryption settings.  The next section of the HowTo is adding those commands to /etc/network/interfaces, which is needed to have the system automatically use those settings.

Near the bottom is also a link to a troubleshooting page.  I'd recommend trying that next if the CLI section doesn't help.

Larry
Dell Customer Advocate

---

