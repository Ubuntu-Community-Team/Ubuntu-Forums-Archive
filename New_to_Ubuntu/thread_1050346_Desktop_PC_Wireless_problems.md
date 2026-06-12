---
title: "Desktop PC Wireless problems"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by iLeet on 2009-01-25
Hi all, Im really new to ubuntu and I just installed it on my desktop pc I opened the terminal and scanned my pci ports

It said [0280]Boardcom coperation(sumthing like that :p) blah b;ah [14e4:blah] 

I installed ndigtk or sumthing like that and under administration I got Windows wireless drivers but now im stuck I dont know where to get the drivers or anything and Iv searched and searched and no results.

Please help,
iLeet

---

### Post by pi.boy.travis on 2009-01-25
Try looking in System>Administration>Hardware Drivers.

---

### Post by ugm6hr on 2009-01-25
Help us help you...

First - read the "Getting help here" link in my signature (for future reference).

Then, give us more detail than "blah" - copy and paste the exact entries and results from the following commands:

```
lspci
lshw -class network
```

And let us know which version of Ubuntu you use, in addition to whether you could use a wired connection temporarily to download drivers / firmware.

---

### Post by iLeet on 2009-02-05
Yeah i got nDiswrapper working

But now I CANNOT find the drivers for:

> 01:05.0 Network controller [0280]: Broadcom Corporation BCM43xG 802.11b/g [14e4:4325] (rev 02) 

I'v searched everywere

P.S
Ubuntu 8.10

---

### Post by abyssius on 2009-02-05
> **iLeet said:**
> Yeah i got nDiswrapper working

But now I CANNOT find the drivers for:



I'v searched everywere

P.S
Ubuntu 8.10

If you're using ndiswrapper, then you'll need the windows driver for your wireless card. Don't you have the Windows Install disk for your adapter? That is where you'll find the appropriate ndiswrapper driver. It's the same driver used by Windows. You can use the Windows driver to get on the Internet, where I'm pretty sure you'll find a native Linux solution for your card.

---

### Post by iLeet on 2009-02-05
Unfornatly I dont have the disk

---

### Post by abyssius on 2009-02-05
> **iLeet said:**
> Unfornatly I dont have the disk

Actually, if it was installed on Windows you can find the driver by searching in the Windows/System32 folder. You'll only need two files. One will be a .sys file and the other will be a .inf file, probably sharing the same name. If you can correctly identify these files, all you'll have to do is copy them to a place where ubuntu ndiswrapper can locate them. Then you're done. I'm surprised that 8.10 doesn't natively support that adapter. Anyway, I'll see if I can find the actual filenames. You could use the Windows search feature to find them.

---

### Post by iLeet on 2009-02-05
Where to find the wndows folder though? My whole pc is Ubuntu 100%

---

### Post by abyssius on 2009-02-05
> **iLeet said:**
> Where to find the wndows folder though? My whole pc is Ubuntu 100%

Search the Internet for a windows driver download for your adapter. Many different vendors use that chipset. The best place is go to the vendor's website. Download the .exe file to your desktop. It is really a compressed (zip) file, which Ubuntu can uncompress. Just double-click on the file. When, you've uncompressed it, locate the .sys and .inf files. These are what you need to get ndiswrapper working.

---

### Post by abyssius on 2009-02-05
> **iLeet said:**
> Where to find the wndows folder though? My whole pc is Ubuntu 100%

You might want to look this over..

[http://linuxwireless.org/en/users/Drivers/b43#FAQ-Frequentlyaskedquestions]("http://linuxwireless.org/en/users/Drivers/b43#FAQ-Frequentlyaskedquestions")

---

### Post by iLeet on 2009-02-06
Erm, On that site i found:
 
 > Microsoft MN-720 PC Card 43XG 0x4325 0x1414 0x0003 
Microsoft MN-730 PCI Card 43XG 0x4325 0x1414 0x0004 


Where is the download though?

---

### Post by abyssius on 2009-02-06
> **iLeet said:**
> Erm, On that site i found:
 
 

Where is the download though?

You've posted the card identifier as it appears in Linux. If you want to use the Windows driver, you have to go to your wireless card manufacturer's website. The recommended way to get your card working in Ubuntu is posted on this link:

[http://ubuntuforums.org/showthread.php?t=185174&highlight=broadcom]("http://ubuntuforums.org/showthread.php?t=185174&highlight=broadcom")

You have to VERY carefully follow each instruction. I will tell you in advance, this is not an easy task for a novice, but if you take it one step at a time, you'll be successful.

---

