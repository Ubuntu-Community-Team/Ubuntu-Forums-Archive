---
title: "Wireless Connection cuts in and out, how do I make it stop?"
date: 2007-05-28
forum: Networking &amp; Wireless
---

### Post by Medesthai on 2007-05-28
Hi, I'm pretty much completely new to this. New as in, first heard of Ubuntu maybe a month ago. I installed Ubuntu on my machine about 4 days ago, and I love it, its been going great.  There have been a few issues, but the forums have helped me figure them all out, except one.

My wireless connection works fine, for the most part, but once every few minutes it notifies me that I was disconnected from the network, and about three seconds later, announces that its connected to the network again.  I've looked under System - Administration - Network and it says that roaming mode is enabled.  I have a sneaking suspicion that that is the source of my problems, but turning it off disables my connection entirely, even after entering the ESSID and the WEP key, setting Automatic Configuration (DHCP).

I'm currently running Ubuntu 7.04 on a machine with an atheros card.  

I'd really appreciate any help with this.  It isn't a huge deal, more of an inconvenience, kinda like the Keyring. ;) pages may or may not load, Instant messages may or may not get sent or received, based on if the network is "connected" or not.  

Anyways, Thanks again in advance!

---

### Post by wrycatcher on 2007-06-12
Same issue here pretty much since upgrading to Feisty from Edgy on my notebook machine.  Very frustrating.  Basically, eth1 (wireless) will go into "disconnected" state and not reconnect.  Sometimes rebooting will solve, but not always.  Haven't found any rhyme or reason to why it stays up sometimes and other times not.  Connecting to a Linksys "B" wireless router from an Acer notebook.

---

### Post by dardack on 2007-06-12
I too have the same chipset i think, bestbuy brandname PCI card.

This is what i had to do or found out.  Network-manager seems to have this issue, at least with this chipset (and with my USB linksys also same issue, not sure about my PCMCIA belkin card because wife uses and you know probably dones't notice).  So i had to diable/uninstall NM.  Than in a terminal (i use WEP) i have to type:

sudo iwconfig ath0 key 1234abcd (my key)
sudo dhclient ath0

and since i manually connect i haven't had this issue.  I do have to do this every time i log in but since i keep it up all the time no big deal.

Now i did put them in a bash script, and added it to my session start up, but it doesn't seem to run, maybe because it needs the sudo password to run.  Can anyone tell me how to automate these commands and keep it encrypted so my key just isn't sitting on my desktop in unecrytped form.

---

