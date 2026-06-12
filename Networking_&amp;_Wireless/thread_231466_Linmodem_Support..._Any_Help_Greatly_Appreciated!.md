---
title: "Linmodem Support... Any Help Greatly Appreciated!"
date: 2006-08-07
forum: Networking &amp; Wireless
---

### Post by BantryBayFarm on 2006-08-07
I have been attempting to get my Conexant HSF 56k Data/Fax Modem working, but to no avail. ](*,) 

I used linuxant's scanmodem utility to find my modem, and it found the connexant hsf.

I am running ubuntu 6.06 amd64 generic so i downloaded hsfmodem-7.47.00.01x86_64full.tar.gz from [http://www.linuxant.com/drivers/hsf/full/downloads.php]("http://www.linuxant.com/drivers/hsf/full/downloads.php")

I got gcc, make, and kernel headers. I made the install. Ran hsfconfig. And this is what was at the end of it.

[I]Warning: no device detected by hsf driver - HDA modems may require reboot

Note: kernel module snd-via82xx-modem overridden by hsfmc97via
Note: kernel module snd-intel8x0m overridden by hsfmc97ich hsfmc97sis
Note: kernel module snd-atiixp-modem overridden by hsfmc97ati
[/I]

If anyone has any clue, what my problem is or how i could fix it i would be very thankful. The sooner i have internet working in ubuntu the sooner i can leave windows behind.

full text for hsfconfig is [here]("http://www.bantrybayfarm.ca/otherdocs/hsfconfig.txt")

full text for hsfdiag (#hsfconfig --dumpdiag) is [here]("http://www.bantrybayfarm.ca/otherdocs/hsfdiag.txt")

---

### Post by BantryBayFarm on 2006-08-08
Got an email from linuxant, seems hsfdrivers don't work in the x86_64 version very well, sooo disapointing. Switched to 32-bit version worked fine. I guess i will have to wait for an update.

---

