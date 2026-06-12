---
title: "Problems Installing Ubuntu"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by Oodi on 2009-05-15
Recently I decided to try installing Ubuntu on my laptop. I no longer had any use for any of the files on it, and I did not want to use the Xp platform anymore, so I downloaded a program called killdisk that I used to eliminate everything from my harddrive. Next I burned the .iso file to a CD and started installing it onto my laptop, which went well for quite a bit (There weren't any defects shown when I followed the steps at [https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck)). It was installing and up to 60% if I remember correctly, then it suddenly stopped, and an odd discolored pattern appeared on the screen. I restarted the laptop, tried to redo the process, but the only thing that appeared was the blinking underscore that appears on start up. I tried to redo the killdisk process, but this didn't work either. If someone could point me in the direction of a program which could delete the incomplete Ubuntu version so that I can retry installing it in full, that would be appreciated. If any more information is needed I will do my best to provide it.

---

### Post by albinootje on 2009-05-15
> **Oodi said:**
> It was installing and up to 60% if I remember correctly, then it suddenly stopped, and an odd discolored pattern appeared on the screen. 

Which Ubuntu release did you try to install ? Jaunty or Hardy ?
Can you perform a RAM memory test ?
Is the hard disk really old ? Could it have bad blocks ?

Can you still start the "live session" ? If so, can you post the output of the following (in a terminal) :
```

sudo fdisk -l
lspci
sudo apt-get install smartmontools
smartctl -s on --all /dev/sda

```

---

### Post by Oodi on 2009-05-15
> **albinootje said:**
> Which Ubuntu release did you try to install ? Jaunty or Hardy ?
Can you perform a RAM memory test ?
Is the hard disk really old ? Could it have bad blocks ?

Can you still start the "live session" ? If so, can you post the output of the following (in a terminal) :
```

sudo fdisk -l
lspci
sudo apt-get install smartmontools
smartctl -s on --all /dev/sda

```
Jaunty.
The system memory is 512MB if that answers your question, if not explain it to me like I'm dumb.
The hard disk is about 5 years old.
I don't know what a bad block is.
I don't know how to start the live session. I can't type anything when there's a blinking underscore, I can however get it to a screen titled "PhoenixBIOS Setup Utility" when I press f10 on startup.

---

### Post by albinootje on 2009-05-15
> **Oodi said:**
> I can't type anything when there's a blinking underscore, I can however get it to a screen titled "PhoenixBIOS Setup Utility" when I press f10 on startup.

Thanks for the information. 

Are you saying that you cannot boot from any cdrom anymore ?
Can you check in the BIOS whether the cdrom drive is still the first device to boot from ?

Is it possible that you left an usb stick in the machine, and the machine tries to boot from that ?

---

### Post by Oodi on 2009-05-15
Yes, I guess the implication is that I can't boot from CD's at the moment. My boot order currently goes in the order "+Hard Drive, ATAPI CD-ROM Drive, Floppy Diskeete Drive, Network Adaptor". All of the USB ports are empty.

Edit: Cool, I disabled the +Hard Drive in the boot order and it's allowing me to reinstall Ubuntu, hopefully this will work.

---

### Post by arapa on 2009-05-15
I believe what albinootje is asking you to do is boot off of the installation disk. You will be presented an option to 'Try Ubuntu without installing" or something to that effect. This will boot your computer - not off the hard drive but off the CD drive (provided the version of the installation disk you have is a "Live CD").

I have had a couple of installation disks behave like this. I found that by re-burning the disk at a slow speed and selecting the 'disk at once' option (rather than track/session-at-once) yielded better results. 

Personally I would suspect the installation media before hardware in your case. It could be a bad hard drive but I think it may be more likely that it is your CD-R.

Do you have access to a computer where you can try burning a new install disk?

---

### Post by Oodi on 2009-05-15
Yes, I am using a desktop to burn everything/ask questions on here. I'll try burning a new CD with the method you suggested, thanks.

---

### Post by NHArticleTen on 2009-05-15
> **Oodi said:**
> Yes, I am using a desktop to burn everything/ask questions on here. I'll try burning a new CD with the method you suggested, thanks.

when you burn the new one, use the slowest burn speed on your machine.  you are not the first to have that issue.

---

