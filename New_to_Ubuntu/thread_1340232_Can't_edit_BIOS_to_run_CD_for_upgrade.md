---
title: "Can't edit BIOS to run CD for upgrade"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by JauntyJack on 2009-11-28
OK, stupid question. I have installed Ubuntu on a few older machines. The CD wouldn't run automatically on reboot but that wasn't a problem: I hit escape during boot-up to get to the BIOS menu and had it boot from the CD.  One of these machines is my Mom's. I am trying to upgrade her from Jaunty to Karmic. The CD doesn't run on a restart. Also, trying to get into BIOS just gets me to a screen where I only have options to choose which kernel to boot. No other options or menus.   I tried looking at the readme files on the disk for boot manager (KBM, maybe?), but I can't figure out the instructions there.   Anyone know a page with a simple step by step for this situation? I would normally do the research, but I only have a few hours to spend on this.  Thanks in advance.

---

### Post by oldos2er on 2009-11-28
"Also, trying to get into BIOS just gets me to a screen where I only have options to choose which kernel to boot."

 That's grub; by the time grub's menu comes up, it's too late to get into the BIOS. You need to hit F2, or Del, or F12 (it varies) when the computer is just starting.

---

### Post by Captain_tux on 2009-11-28
How's Jaunty running? 

If all is good, why is there a need to jump to Karmic??

---

### Post by ptn107 on 2009-11-28
You can just upgrade from within a running installation via the internet or an alternate cd.  Given that you have more than one pc to upgrade the best (and fastest) thing would be to download and burn an 'upgrade' disk.  Download the Ubuntu 9.10 Alternate Disk[1,2], burn it, and stick it in while Ubuntu 9.04 is running.  You'll get a dialog box asking if you would like to upgrade.

[1-iso] [http://releases.ubuntu.com/karmic/ubuntu-9.10-alternate-i386.iso]("http://releases.ubuntu.com/karmic/ubuntu-9.10-alternate-i386.iso")
[2-torrent] [http://releases.ubuntu.com/karmic/ubuntu-9.10-alternate-i386.iso.torrent]("http://releases.ubuntu.com/karmic/ubuntu-9.10-alternate-i386.iso.torrent")

---

### Post by oldsoundguy on 2009-11-28
[http://michaelstevenstech.com/bios_manufacturer.htm](http://michaelstevenstech.com/bios_manufacturer.htm)

You need to change the boot order sequence in order to be able to boot from a cd/dvd.

---

### Post by JauntyJack on 2009-11-28
Thanks for the replies. Good to know in future.   No issues with Jaunty - I upgraded to Karmic because I understood it would allow a certain amount of free cloud storage, and on the assumption that the latest version would be the likeliest to have new solutions developed for it (drivers for hardware, etc). Not sure if those are good assumptions.  In the event, I opened the upgrade manager to just let it download the upgrade over the internet - and after a step or two it asked me to insert the disk, so presumably it used the disk's files rather than download. Confusing process.  At any rate, it's now installed.   Thanks!

---

