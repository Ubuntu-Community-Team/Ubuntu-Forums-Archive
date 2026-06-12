---
title: "Can't enable wireless on HP6710b with Intel PRO/Wireless 3945ABG card"
date: 2008-08-16
forum: Networking &amp; Wireless
---

### Post by gtxizang on 2008-08-16
Hi,

First post and a recent convert to Ubuntu 8.04 from OS X.  

I can't get wireless working on my HP6710b laptop.  The wired connection is fine.  I've looked at the solutions listed here and on other sites and either they don't work for me, or I'm doing it wrong (high probability).

Any help would be greatly appreciated.  I've seen lots of references to iwl3945 and when I type 'lshw -C network', I get:

description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=iwl3945 latency=0 module=iwl3945

which suggested to me that it is using the correct driver.

Like I said, I have looked at the solutions detailed here, but am still stuck in the corner beside the router with the Ethernet cable plugged in.

Thanks,

Gtxizang

---

### Post by cpetercarter on 2008-08-16
This is a really troublesome wireless card. My son has a Dell Inspiron 1525 (which also uses the 3945) running Hardy. Sometimes the computer finds a wireless connection without problems. Other times it hangs out a "gone to lunch" sign. The only things I can suggest from experience are:

if your computer has a switch for the wireless card, make sure that it is set to "on" before you boot up;

try disabling and re-enabling "wireless" and "networking" on the menu which you get when you right click on the wireless icon. Sometimes doing this seems to prod the system into action.

There is a need for a good "how to" for this card. There have been several posts in the past few days from people who cannot get it to work.

Edit : also, if you have not done so already, have a look at [http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/]("http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/")

---

### Post by gtxizang on 2008-08-16
Thanks for your prompt response
> **cpetercarter said:**
> 

if your computer has a switch for the wireless card, make sure that it is set to "on" before you boot up;
No hardware switch, just a button (disabled since Ubuntu installation)
> **cpetercarter said:**
> 
try disabling and re-enabling "wireless" and "networking" on the menu which you get when you right click on the wireless icon. Sometimes doing this seems to prod the system into action.
I don't have a wireless icon:confused: I have the two overlapping monitors icon in beside my logon name in the top panel.  But no wireless icon per se.  If I go System-> Admin-> Network, there's no reference to wireless connections
> **cpetercarter said:**
> 
There is a need for a good "how to" for this card. There have been several posts in the past few days from people who cannot get it to work.
Indeed.

All help appreciated.

Gtxizang

---

### Post by cpetercarter on 2008-08-16
Sorry, when I said the "wireless icon" I meant the two overlapping monitors. It is, in fact, the network icon.

Have you installed the linux-backports-modules-hardy-generic package? The link in my previous posting explains how to do this.

---

### Post by gtxizang on 2008-08-16
> **cpetercarter said:**
> 
Have you installed the linux-backports-modules-hardy-generic package? The link in my previous posting explains how to do this.

That worked.  Thanks, much appreciated.  It was strange though. I installed the backports and rebooted and immediately had working LEDs, but still the same problem (no wireless access).  I 'tinkered' about with System-> Admin-> Network and another reboot and it worked.  I don't think I ultimately changed anything under Network, so maybe it was just the additional reboot required.

Regardless, much appreciated.  

Thanks,

Gtxizang

---

