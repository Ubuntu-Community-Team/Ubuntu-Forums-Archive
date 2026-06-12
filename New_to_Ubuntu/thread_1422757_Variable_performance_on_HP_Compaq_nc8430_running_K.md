---
title: "Variable performance on HP Compaq nc8430 running Karmic 9.10"
date: 2010-03-05
forum: New to Ubuntu
---

### Post by bardsey on 2010-03-05
Hi, am new to Linux, switched from Windows XP a couple of days ago. I think I'm experiencing a problem with my graphics card driver.

The first day the system was running very slowly, with the GRUB screen taking a while to paint, which didn't seem right. Then I did a kernel update and everything suddenly was blazing FAST.

However, for some reason, it's running slowly again now. I've tried using the Synaptic Package Manager to get more drivers (by searching for ATI) and marking some likely looking ones for install, but this hasn't helped, and possibly was a backwards step.

Can anyone help show me how to diagnose and fix this problem?

Here's some info on my system:
Hardware: HP Compaq nc8430
Distribution: Ubuntu 9.10
Kernel: 2.6.31-20-generic
Graphics Card: ATI Technologies Inc M56P [Radeon Mobility X1600]


Thank you very much!

---

### Post by bardsey on 2010-03-05
If it's going to help, is there some way I can find a record of what drivers are called during the boot?

Getting really frustrated because I know the system can be very fast, but right now it's crawling.

---

### Post by Kingster on 2010-03-09
I had much the same issue.

In my opinion, so far, the proprietary drivers don't hold a candle to the OSS ones, and the OSS ones are only going to get better from here on out.

I had much the same problem as you, it seems, when I tried to run the proprietary drivers.

Have a look here: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Hope that helps.

---

### Post by bardsey on 2010-03-09
Thank you Kingster. I had to revert to XP because I needed my machine to get some work done. But I will be back. Appreciate the Radeon page link, I will check it out.

Because I had wiped the drive completely on my HP when going to Ubuntu, I couldn't use the Windows Recovery partition to reinstall, but luckily I had an extra XP Pro CD.

In going back to Windows temporarily, I may have stumbled upon a couple of issues. Since I'd wiped the drive completely when I put Ubuntu on, I had to resort to using an old Win XP Pro install disk that I had lying around (which is evidently not the recommended Windows recovery method for this machine - HP intends for you to use their own special recovery partition, installed as standard on new nc8430s).

Anyway, that didn't work at first - it kept throwing errors within the first few mins of Win install. Ran memtest to check RAM. Took forever. RAM seemed fine. Then finally, after seeing some advice on the HP forums, I found this [http://tinyurl.com/yz3qrpv](http://tinyurl.com/yz3qrpv)and made some changes to the BIOS. Then Windows installed OK.

Now that I do finally have the machine back on XP SP3 (takes hours from SP1A disk), I intend to go get the latest BIOS update from the [HP's nc8430 driver page]("http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareIndex.jsp?lang=en&cc=us&prodNameId=1839197&prodTypeId=321957&prodSeriesId=1839150&swLang=8&taskId=135&swEnvOID=1093"), flash the BIOS, reinstall Ubuntu, and hope for the best.

Cheers for the corroboration. I was beginning to wonder if I was on my own with this problem!

As you say, OS drivers are getting better all the time. Here's hoping Lucid Lynx will = problem solved

---

### Post by bardsey on 2010-04-23
FYI am no longer having problems, this machine runs 9.10 perfectly.

I think the initial problem was that I was using a Targus universal laptop power adapter in place of the OEM power adapter from HP.

Once I replaced the Targus adapter with the original adapter from HP, it all worked.

---

### Post by paulrhansen on 2011-08-08
> **bardsey said:**
> Thank you Kingster. I had to revert to XP because I needed my machine to get some work done. But I will be back. Appreciate the Radeon page link, I will check it out.

Because I had wiped the drive completely on my HP when going to Ubuntu, I couldn't use the Windows Recovery partition to reinstall, but luckily I had an extra XP Pro CD.

In going back to Windows temporarily, I may have stumbled upon a couple of issues. Since I'd wiped the drive completely when I put Ubuntu on, I had to resort to using an old Win XP Pro install disk that I had lying around (which is evidently not the recommended Windows recovery method for this machine - HP intends for you to use their own special recovery partition, installed as standard on new nc8430s).

Anyway, that didn't work at first - it kept throwing errors within the first few mins of Win install. Ran memtest to check RAM. Took forever. RAM seemed fine. Then finally, after seeing some advice on the HP forums, I found this [http://tinyurl.com/yz3qrpv](http://tinyurl.com/yz3qrpv)and made some changes to the BIOS. Then Windows installed OK.

Now that I do finally have the machine back on XP SP3 (takes hours from SP1A disk), I intend to go get the latest BIOS update from the [HP's nc8430 driver page]("http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareIndex.jsp?lang=en&cc=us&prodNameId=1839197&prodTypeId=321957&prodSeriesId=1839150&swLang=8&taskId=135&swEnvOID=1093"), flash the BIOS, reinstall Ubuntu, and hope for the best.

Cheers for the corroboration. I was beginning to wonder if I was on my own with this problem!

As you say, OS drivers are getting better all the time. Here's hoping Lucid Lynx will = problem solved

--------------------------------
You need to be aware the hp/compaq nc8430 models all have sata hard drives installed in them (no eide hard drives) and need  the Intel Serial ATA (SATA) Advanced Host Controller Interface (AHCI) Controller Driver (the mobile one). This drive in most cases can only be installed from a floppy disk and can be downloaded from the 
[1. hp/compaq nc8430 driver page, ]("http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareIndex.jsp?lang=en&cc=us&prodNameId=1839197&prodTypeId=321957&prodSeriesId=1839150&swLang=8&taskId=135&swEnvOID=1093#113100")
[**2. Operating System - Enhancements and QFEs, **]("http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareIndex.jsp?lang=en&cc=us&prodNameId=1839197&prodTypeId=321957&prodSeriesId=1839150&swLang=8&taskId=135&swEnvOID=1093#113100")
[**3. Intel SATA AHCI Controller driver**]("http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareIndex.jsp?lang=en&cc=us&prodNameId=1839197&prodTypeId=321957&prodSeriesId=1839150&swLang=8&taskId=135&swEnvOID=1093#113100")[B]
4. Read the Installation Instructions step 5 tells which one to use.

Windows XP Pro installs just as easy as it does on any other desktop/laptop.
[/B]

---

