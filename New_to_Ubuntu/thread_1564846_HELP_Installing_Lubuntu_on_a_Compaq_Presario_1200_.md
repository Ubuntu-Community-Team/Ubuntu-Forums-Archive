---
title: "HELP: Installing Lubuntu on a Compaq Presario 1200 (model number 12XL410)"
date: 2010-08-31
forum: New to Ubuntu
---

### Post by Mbnbmbv0 on 2010-08-31
I have an old Compaq Presario 1200 from 1999-2000. It has an 800MHZ Intel Celeron processor and 312MB or ram. It was running extremely slow with Windows XP installed on it, so I thought I would give Linux a try. I read that Lubuntu was a good OS for old computers so I downloaded it and burned it to a CD. I put it in the computer and selected the boot from live CD option. I got an error message saying something like ERROR: UPGRADE BIOS, then the screen blacked out and the laptop became unresponsive before it even loaded the desktop. I'm sure this laptop has more than enough power to handle lubuntu. Can anyone help me here?:confused:

---

### Post by juil on 2010-08-31
Um, I don't think your supposed to boot from the live cd. Just run the live cd within windows. Go to youtube and it'll give you a good instruction on how to install ubuntu.

---

### Post by mastablasta on 2010-08-31
it could be that it's not compatible with your processor.
 
try normal Ubuntu it will be slower but just try to see if it works. (Lubuntu is missing some things...). Also you could try and upgrade your BIOS (back up any important data first).
 
edit: try to get the complete message instead of "something like"
 
Edit2:
> 
Um, I don't think your supposed to boot from the live cd. Just run the live cd within windows. Go to youtube and it'll give you a good instruction on how to install ubuntu.

 
This is not true. you can boot from LiveCD that's why it is called "Live"

---

### Post by Mbnbmbv0 on 2010-08-31
I tried every Ubuntu variation (Kubuntu, Lubuntu, Xubuntu, etc.) and they all give me the same message. I could however install Xubuntu 6.06, but then the update wouldn't work. I am a noob to Linux and to computers built for Windows so I have no idea what bios are and how to upgrade them. I will try to capture the full error message and post it.

---

### Post by Mbnbmbv0 on 2010-08-31
The error message is "[   17.728988] vt596_smbus 888:88:87.4:  SMBUS:  Error:  Host SMBus controller not enabled! - upgrade BIOS or use force=1". Then the screen blanks out. There was another error above it, but the screen was moving too fast for me to catch it. If I can, I will post it later on.

---

### Post by Mbnbmbv0 on 2010-08-31
The error message above that one says "waiting for the /dev to be fully populated.....[   17.556953] via606a 888.88.87.4 base address not set - upgrade BIOS or use force_addr=0xaddr

---

### Post by juil on 2010-08-31
Well, I've never tried booting straight from the cd but 'live' means that you can run linux Ubuntu 'live' within windows as if your using another operating system. Why don't you just try my suggestion?

---

### Post by mastablasta on 2010-09-01
> **juil said:**
> Well, I've never tried booting straight from the cd but 'live' means that you can run linux Ubuntu 'live' within windows as if your using another operating system. Why don't you just try my suggestion?
 
 
Live uses CD to boot from and basically loads everyhting into RAM or reads from CD that's why it is much slower. However on the plus side it doesn't touch or messes arorund with your current system in any way since it doesn't write any files. i think...
 
-------
 
@Mbnbmbv0
 
Now hoepfully someone will know what this message means. give them some time. there is probably a solution to this and is solved with a command.
 
But here is an older post form people wiht same problem:
[http://ubuntuforums.org/showthread.php?t=337474&page=3](http://ubuntuforums.org/showthread.php?t=337474&page=3)
 
it seems using alternate CD workedfor the guy.
 
in the mean time BIOS is basically what loads before the OS. it sort of control the devices. Each computer has different way of accessing it. more here: [http://en.wikipedia.org/wiki/BIOS](http://en.wikipedia.org/wiki/BIOS)
 
updating it usually requiores carefully reading the manual for upgrade and then runnning a file or something... forgot exactly how it's done since it's been a while. but nothing too hard as i remember. most is done for you by the upgrade programme.

---

