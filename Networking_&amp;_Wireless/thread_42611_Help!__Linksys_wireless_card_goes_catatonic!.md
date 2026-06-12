---
title: "Help!  Linksys wireless card goes catatonic!"
date: 2005-06-18
forum: Networking &amp; Wireless
---

### Post by meldroc on 2005-06-18
I've been having this problem periodically.  I have a Linksys 801.11g PCI wireless card in my desktop machine, which works nicely using ndiswrapper.  The problem I have is that periodically, the connection dies.  The LED on the back of the card goes out, the network stops responding, and nothing I do short of rebooting can get the damn thing back to life.

Actually skip that, I got frustrated and started tinkering around, and found using some of the wireless utilities, like iwscan gets the card to come back to life, and I was able to reestablish the connection.

Any ways to deal with this?  I'm getting tired of having to constantly fiddle with the connection.  I like connections that Just Work.

---

### Post by meldroc on 2005-06-19
Update: I was able to bring the card back to life once using iwlist, but since then, I keep being forced to reboot.  Why is my card continuing to drop my connection like this?  Is the card itself going bad?  Help me!

---

### Post by meldroc on 2005-06-22
Bump:  Using iwlist to ping the card has only worked once.  My card still likes to go catatonic periodically, and the only way to force the system to get wireless back up is to reboot.

HELP ME!!!  I HATE REBOOTING!!!  REBOOTING IS FOR WINDOWS USERS!!!  Sigh.  This is what I get for using ndiswrapper to contaminate my system with a Windows driver...

---

### Post by compboy1 on 2005-06-23
I myself am having the same problem. I hav found a few things:
1. Going to System>Administration>Networking>Selecting Wlan0>Properties, and switching from Static IP Address to DHCP and back (or vice-versa) brings the card back to life, though the Networking applet starts acting up (usually have to force-close).
2. When the card dies, the Signal Strength meter goes to 100%, regardless of actual strength (For example, mine is usually 95%, if it hits 100%, then the card dies)
3. Once the card activates, you have to keep using the connection, or it dies again.

I'm thinking it has to do with a bad driver. E.g. NDISWRAPPER is misreading somthing, and its ccausing the card to doe, or loop back, or SOMTHING (it would explain he 100% signal strength)

I'm going to try an older version of the driver, maybe that'll do it...

---

### Post by meldroc on 2005-06-24
After probing around a bit, I looked at the Windows drivers files for my wlan card, and found they were named rt2500.cat, Rt2500.INF and rt2500.sys.  Googling around, I found that someone has made a [Linux driver module for the Ralink RT2400 and RT2500 wireless chipsets](http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page).  Looks like it's implemented as a Linux kernel module.  What's the most painless way to compile and use this module and make it work within (K)Ubuntu?

I'm sorely tempted to try this.  Ndiswrapper works, but is annoyingly flaky.

---

### Post by kleeman on 2005-06-24
Believe it or not  :)  :)  :) there is a Ubuntu howto for this, check it out here, sounds fairly easy (unless your a newbie):

[https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/](https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/)

---

### Post by meldroc on 2005-06-25
[QUOTE=kleeman]Believe it or not  :)  :)  :) there is a Ubuntu howto for this, check it out here, sounds fairly easy (unless your a newbie):

[https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/](https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/)[/QUOTE]
 Sweet!!!  I'll play with this when I have time.

---

