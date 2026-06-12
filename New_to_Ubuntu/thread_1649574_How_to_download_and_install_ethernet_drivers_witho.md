---
title: "How to download and install ethernet drivers without internet&gt;"
date: 2010-12-20
forum: New to Ubuntu
---

### Post by sjkregs on 2010-12-20
&#65279;I need to know how I can download onto my laptop (running Xubuntu 10.10) and install on my desktop computer ( with no Internet access) nvidia drivers for the on-board wired Ethernet card. I removed the non working 320G hard drive ( originally containing Windows Vista ) and put in a used 40G hard drive ( originally containing Windows XP) and installed Xubuntu onto it. Xubuntu detects the LAN Card but it will not connect to the Internet.
    
    
    Original Specifications:
    &#65279;
    HP Pavilion a1710n Desktop
    Processor Speed 2.2GHz
 Cache (L2) 512KB+512KB L2 Cache
 Bus Speed 2000MHz System Bus
 
Operating System Windows Vista Home Premium
Chip set Ge Force 6150 LE/n Force 430 Chip set
 Memory 1024MB PC2-4200 DDR2 SDRAM memory(2x512MB for ultimate performance)(expandable performance)(expandable to 4GB)
 Hard Drive 320GB 7200RPM Serial ATA hard drive
 Optical Drive(s) Super Multi DVD Burner with Light Scribe Technology: 16x DVDR, 8x DVD+RW, DVD+RW, 6x DVD-RW, 8x DVD+R DL, 4x DVD-R DL, 5x DVD-RAM, 16x DVD-ROM, DVD-ROM, 40x CDR, 32x CDRW, 40x CD-ROM* 
Video Graphics NVIDIA Ge Force 6150 LE Graphics with 128MB dedicated graphics memory. Up Up to 319MB Total Available Graphics Memory as allocated by Windows Vista 
    
    Please Help !!!!

---

### Post by coffeecat on 2010-12-20
> **sjkregs said:**
> &#65279;I need to know how I can download onto my laptop (running Xubuntu 10.10) and install on my desktop computer ( with no Internet access) nvidia drivers for the on-board wired Ethernet card.

Drivers for nvidia ethernet devices come in the kernel for all versions of Ubuntu. I doubt whether there is a nvidia ethernet chipset that isn't supported. Your connection problem is probably down to something else. Tell us more about your setup and perhaps we can find out what has gone wrong.

For the record, post the terminal output of:

```
lspci | grep -i ethernet
```

---

### Post by ctm54 on 2012-07-08
Bumping this thread because I am having the exact same problem except with the following chipset: NVIDIA GeForce 7025 / nForce 630a

Terminal output of the command you suggested is:

```
00:07.0 Bridge: nVidia Corporation MCP61            (rev a2)
```

Please help! Thanks!

---

### Post by wildmanne39 on 2012-07-08
Hi, this is an old thread so it has been closed please start a new thread of your own with a descriptive title. 
Thanks

---

