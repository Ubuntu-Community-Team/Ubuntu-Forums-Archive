---
title: "Please Help! Belkin F5D7000uk"
date: 2006-10-24
forum: Networking &amp; Wireless
---

### Post by mrsirrus on 2006-10-24
OK, after installing Ubuntu I think I've actually lost all of my hair since I've been to PC World about 4 times this week, noone wants to help me and Linux seems to deny me at the last post every sodding time.

Just plugged in a new Belkin F5D7000 wireless-G PCI card. Boot up, Ubuntu recognises it. I select it to "active", it picks up my wireless router, I select my network. Restart, and it hangs when at "Configuring Network Connections". How come it worked fine before, but once I'm one second away from configuring it my system won't boot up?

I was just using it Plug and Play style. From the last wireless connection I had I got used to using Ndiswrapper, and will be able to use it if I have to. This is the third wireless connection I've had problems with. Please someone help before I kill someone in cold blood.

---

### Post by mrsirrus on 2006-10-24
Oh, and on the chipset it says "ver.6000uk". I've noticed that everyone who actually owns one of these seems to have it working pretty much instantly, but I did spot that people were using the 3000 version.

---

### Post by mrsirrus on 2006-10-24
Furthur information:

The drivers included with the card are the RA61 chipset and not the drivers for the 25XX. As stated before, the computer hangs when trying to boot up Ubuntu Dapper. I have just booted from a live CD of Dapper and it has loaded up fine, with the Wireless being recognised. It seems to have installed the RA61 chipset drivers automatically.

Once again, could someone please help me with this. I'm starting to ask myself why I got into computing in the first place!

---

### Post by mrsirrus on 2006-10-24
Furthur information.

Reinstalled Ubuntu, it booted first time. Activated my Wireless card, which showed up with no problems. Rebooted Ubuntu, system hanged again at "Configuring Network".

I am now running a Live DVD of Kubuntu. Kubuntu seems fine, it has even connected my wireless card to the network and is running as we speak without the machine being hard-wired to the router.

I will try and install Kubuntu, but I am guessing that once it is installed it will hang at the same point.

---

### Post by alsuren on 2008-07-24
From what I have gathered, F5D7000uk is not the same as F5D7000.

Some revisions of F5D7000 seem to be supported by madwifi, but you have to use ndiswrapper for this card. I have updated the belkin wiki page.

---

