---
title: "Wifi card randomly turns off"
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by AlanD on 2007-05-04
I am running Fiesty (32 bit) using a Broadcom 4311 wifi card built into my Lenovo 3000 C100 laptop (0761-2BU model number), and used this guide to get my wifi working:

[http://ubuntuforums.org/showthread.php?t=185174&highlight=broadcom](http://ubuntuforums.org/showthread.php?t=185174&highlight=broadcom)

However, at seemingly random times, my wifi card will turn off without me hitting the switch to do so - the light turns off, I lose all internet, but the wifi switch is in the on position. I use the Firestarter ip tables GUI with default settings for a firewall. Any idea what can cause this?

---

### Post by ZombiekE on 2007-05-09
I have a broadcom 4318 and I also have this problem from time to time, and there is no way to switch it on. So I have to reboot. It happens randomly. Especially if it has not been able to connect to any of the networks available (I don't know why) or if you try to select a certain network when it has not been able to connect. I find this annoying because you never know if next time you turn on your laptop it will work from the beginning or you'll have to reboot again.

I hope this gets fixed.

---

### Post by tgalati4 on 2007-05-09
Make sure you close all of your applications.  Pull the card (assuming it's a pcmcia) and feel how warm it is.  Some cards will shut down due to heat--leaving the system in an indeterminate state.  Try putting in another slot (if you have 2).  Do a google search of this card and see if others are have similar issues with other distros or Windows.

I have an Airlink 101 card that has similar symptoms on a Dell Inspiron 7500.  It normally happens after a couple hours of use on a warm day.

Usually I have no choice but do a hard reboot, since the pcmcia is directly tied to the system, when it locks up it normally takes your system with it.

---

### Post by AlanD on 2007-05-12
It is not a PCMCIA card, it is an onboard card inside the laptop. There is no way to remove it. So either I need to buy a new wifi card to use Feisty or stick with Windows if I want to use wireless internet :/

---

