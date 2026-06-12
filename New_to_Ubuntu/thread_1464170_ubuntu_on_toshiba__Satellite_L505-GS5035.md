---
title: "ubuntu on toshiba  Satellite L505-GS5035"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by marianarqm on 2010-04-27
I want my laptop have two operative system windows 7 and ubuntu 9.04 my laptop is Satellite L505-GS5035, is it possible?, I can't install ubuntu. I wrote to toshiba and they said: 
From what I understand the iCore chipset isn't supported by any of the older versions of the 'Buntu's due to the kernel they use.  Only 10.4 has built in support for them.  If you can get through the install process with 9.04 or 9.10 some people have been able to keep it running long enough to update the kernal to 2.6.33 or later which is the earliest kernel that supports the iCores. 
Have i try with the ubuntu 10.4?

---

### Post by cariboo on 2010-04-29
Lucid Lynx (10.04) will be released April 29th, why not download the Live CD and boot from it to see if everything works.

There are several people running Lucid on the iCore chipset, which uses kernel version 2.6.32-21-generic #32-Ubuntu, which is a custom built kernel by the Ubuntu devs.

---

### Post by marianarqm on 2010-05-03
Hi! I download the Lucid Lynx (10.04) Live CD and boot from it, but the computer always hangs at the same place 

[<c0104087>] kernel_thread_helper+0x7/0x10

What can i do?

---

### Post by Chainring on 2010-05-05
I just bought a new Toshiba laptop (L505-ES5034) and am having the same problem.

Install hangs in the exact manner you describe (kernel dump?) using 32-bit Ubuntu.  I also tried the 64-bit version and got similar results (with different screen info at fail).  Also tried Mint 8 and install hung on blank screen.

Searching forums seems to indicate that the problem is recent and epidemic for newer Toshibas.  Here's hoping a solution comes soon, 'cause I'm not finding one.

---

### Post by Alver on 2010-05-08
I just purchased a Toshiba Satellite L505-10M with 6 GB RAM and Windows 7 64 bit preinstalled. I tried a live CD with Sabayon 5.1 (which I had lying around). Everything worked out of the box. I will try Ubuntu 10.04 soon and report on it.

Greetings

Alver

---

### Post by frillybob on 2010-05-08
I had the same exact probelm. Now I am dualbooting. What you need to do is press f6 as soon as it loads then press f6 again and acpi=off then it will load... After you install you will see several things if you want to boot Ubuntu you must press c for cammand line then say acpi and windows should boot fine!

---

### Post by Alver on 2010-05-08
> **Alver said:**
> I just purchased a Toshiba Satellite L505-10M with 6 GB RAM and Windows 7 64 bit preinstalled. I tried a live CD with Sabayon 5.1 (which I had lying around). Everything worked out of the box. I will try Ubuntu 10.04 soon and report on it.

Greetings

Alver
I downloaded the live Ubuntu 10.04 64 bit dvd iso image. I ran the live dvd for some time and everything worked out of the box, including my wireless internet connection. There is one small exception, while the printer part of my all-in-one Epson Stylus SX 410 was recognized at once, the scanner part did not function. I have the same printer-scanner working on Ubuntu 9.10 on another pc but there it took some fiddling around to get the scanner going. I'm confident I will get this going on 10.04 also. Sound and video worked also as expected. All in all, 10.04 seems to work well on this Toshiba with the added proviso that I did not install the proprietary ATI graphics card driver for this small test, but even with the basic Ubuntu driver a had an excellent screen image. 
As soon as I have some spare time I will go for a dual boot 10.04 vs. Win 7. Keep your fingers crossed.

Greetings

---

### Post by Alver on 2010-07-06
> **Alver said:**
> I downloaded the live Ubuntu 10.04 64 bit dvd iso image. I ran the live dvd for some time and everything worked out of the box, including my wireless internet connection. There is one small exception, while the printer part of my all-in-one Epson Stylus SX 410 was recognized at once, the scanner part did not function. I have the same printer-scanner working on Ubuntu 9.10 on another pc but there it took some fiddling around to get the scanner going. I'm confident I will get this going on 10.04 also. Sound and video worked also as expected. All in all, 10.04 seems to work well on this Toshiba with the added proviso that I did not install the proprietary ATI graphics card driver for this small test, but even with the basic Ubuntu driver a had an excellent screen image. 
As soon as I have some spare time I will go for a dual boot 10.04 vs. Win 7. Keep your fingers crossed.

Greetings

As announced in the previous message I finally installed a dual boot W7 64b/10.04 64b. To start with I freed 115 GB on my D (data ) partition using Partition Wizard Home Ed. (freeware). I left these 115 GB as UNALLOCATED space. I then booted from my dvd ticked install, picked the option "Use the largest available free space" and let the electronics do their way. Some 52 minutes later, I had 10.04 up and running. Everything went flawlessly and without error reporting. I hit the first snag when I tried to use my wireless internet connection. After bringing in my password and the AES encryption (the same as I use in W7) the icon is seen to be beaming and very soon the black applet tells me I have now internet connection. BUT: I cannot load any page or e-mail. The wireless applet tells me I have the rtl819xSE driver loaded for my NIC. This is the correct one I have a Realtek RTL 8191 SE card! Very strange. I then reverted to an ethernet cable connection and that worked like lightning, much faster than in W7. I then updated the system, installed the proprietary ATI drivers and all that went extremely well. Sound & video seem to work also (I did some limited testing). Printer recognition worked out of the box, I still have to install the Avasys driver for the scanner but I'm confident it will work. 
Conclusions sofar: A rather painless operation except for the wireless connection which is a complete mystery for me (please bear with me I'm not much of a Linux specialist).

If any of the learned members of this community can offer some clue on the wireless problem, I will be very gratefull because ten I will have the near perfect setup.

---

### Post by Alver on 2010-07-06
I have done some additional reading in several fora and one correspondent stated an almost identical problem with the wireless NIC, apparent connection but no possibility to download web pages or mail messages. Further to this person he (or she) found a solution by installing & using Wcid. I installed this programme and after a restart of Ubuntu I had one more icon (see print screen), two black screens and a vertical green beam. What is more important, I now have wireless connection! I can surf and read my mails. Who does understand this?

---

