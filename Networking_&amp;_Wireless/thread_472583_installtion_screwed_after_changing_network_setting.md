---
title: "installtion screwed after changing network settings"
date: 2007-06-13
forum: Networking &amp; Wireless
---

### Post by sokar2 on 2007-06-13
Hi all,

Firstly I'll apologise for my ignorance... I'm *completely* new to this (Linux) and have been a Windows advocate for the last 10 years, but hey, I'm trying to do the right thing now :)

My problem is this:

A clean install of Ubuntu 7.04 to a Dell Latitude D600 hard drive from the Live CD. All looks good from what I can see. Recognises the wireless and wired nics.

I don't use DHCP though on my network so I change all details to static IP in the wired nic and stick the IP of my router in for DNS entrry and reboot. It sticks about quarter of the way through the boot up and goes through an endless list of microcode failures and moaning about SDA1 :(

It's fine and can be rebooted several times **until** I change the network settings.

I'd really appreciate any help on this folks as I'm very eager to embrace the world of Ubuntu and Linux (and let's face it, Beryl) but I need the laptop up and working again within a couple of days for work, otherwise I'll have to go back to the dreaded dark side of XP... <sob>

Thanks

---

### Post by dfreer on 2007-06-14
> **sokar2 said:**
> 
I don't use DHCP though on my network so I change all details to static IP in the wired nic and stick the IP of my router in for DNS entrry and reboot. It sticks about quarter of the way through the boot up and goes through an endless list of microcode failures and moaning about SDA1 :(

It's fine and can be rebooted several times **until** I change the network settings.


Can you post the relevant sections (the part where it complains about SDA1) of /var/log/dmesg for us? Also, How are you setting the static IP? Are you using the Network Manager applet or are you editing the /etc/network/interfaces file?

EDIT: BTW, welcome to Ubuntu! Hopefully we can get this fixed for you!

---

