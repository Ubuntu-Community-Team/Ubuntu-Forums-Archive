---
title: "Toshiba Portege M200 Ubuntu USB Install"
date: 2011-07-21
forum: New to Ubuntu
---

### Post by Erykwidday on 2011-07-21
I have a Toshiba Portege M200 its a tablet without a CD/DVD drive. When  it boots the HDD it comes up with the UNMOUNTABLE_BOOT-VOLUME error, i  dont care about the stuff on my HD so i just want to install a new OS.  But without the disc drive its kinda difficult.
Well, I've managed to install Ubuntu 11.04 onto a 4gb usb stick, apparently i made it bootable using Unetbootin. 
I  checked it on my other laptop and it boots, but when i plug it into the  Toshiba and set it up to read the FDD an error message comes up saying  PXE-E61 : Media Test failure, check cable
PXE-M0F Exiting Boot Intel Agent.

I have no idea what to do, I've spent the whole day Googling forums and stuff but nothing worked, so Please Guys HELP!
I  know that there is a way of doing it by LAN but i havent found a good  detailed thread about it. Once again Please Guys help me out with this!!.

---

### Post by davegaunt on 2011-07-28
I'm in the same boat; no CD drive, new empty HD. One thing I DO know (from searching the Toshiba site) is that you can't boot from ANY USB device except a Toshiba floppy or CD. No booting from flash drives or USB HDs. The PXE error you're seeing is a network boot error.

Supposedly you can boot from a SD card but the Toshiba utilities I downloaded can't find my SD card reader - I can only assume it's because it's not the SD card reader in my M200 which I can't boot. Very frustrating.

One thing I haven't tried is taking out the HD and putting it in another computer and installing to it there, then taking it out and putting it back in the M200. Anyone know if that will work? Or a way to install from a network?

---

### Post by relik0fages on 2011-09-01
This is how I installed Ubuntu on my current Portege M200.
Prerequisites: 2.5" HDD USB enclosure, a PC currently running Ubuntu.

1) Hook the hard drive up to the USB port on your PC. And launch the "Startup Disk Creator"(you should see your Hard Drive listed in there)
2) Only make a max 4GB partition for it. Anymore is a waste of space.
3) Use the .iso version you want and click on "Make..." button(Make sure you have selected the 4GB partition.
4) After it's done making install, remove from enclosure and put it in Portege M200.
5) Startup your laptop and the Ubuntu launch should begin.
Hopefully this works for you. It was a Pain in the A$$ for me.

---

### Post by rldreams on 2011-09-07
The bios on the m200 does not allow booting from anything but a toshiba cd rom, The problem is that these are rare, but can be found. I did get one one Ebay for <$30 US . The option I found easiest was put your HDD in another laptop that will boot from USB or a cdrom ( I used an old IBM T20 ), install Ubuntu on that laptop as I normally would ( don't just copy the iso ). Once it is fully installed and running, I took the HDD out of the T20 and installed it in the M200 and updated it with all the drivers for the M200. 
 Now I am working on figuring out how to get the tablet features working,but the install worked fine. Once I upgraded to 11.04 the stylus works fine with the exception of the buttons and the quick launches on the tablet.

---

### Post by tpinkfloyd on 2012-01-20
I am trying to get a Portege m200 working the problem with not having a Optical drive is that I had to install Ubuntu some how. I installed 10.10 on the HDD in another computer but my issue right now is no that it is in the m200 it is running super slow (20 minutes from power on to desktop). If anyone could help me with this it would be greatly appreciated. Also all the files that ran the clock and so on in the top right corner had to be uninstalled no clue why.

[Edit]
Solved the Slowing issue. Apparently the CPU has an issue with if the memory is removed/replaced it clears the settings in the bios for the CPU turning off the L2 cache. Went in and turned it back on and it boosted speed greatly.

---

### Post by tpinkfloyd on 2012-01-20
> **rldreams said:**
> The bios on the m200 does not allow booting from anything but a toshiba cd rom, The problem is that these are rare, but can be found. I did get one one Ebay for <$30 US . The option I found easiest was put your HDD in another laptop that will boot from USB or a cdrom ( I used an old IBM T20 ), install Ubuntu on that laptop as I normally would ( don't just copy the iso ). Once it is fully installed and running, I took the HDD out of the T20 and installed it in the M200 and updated it with all the drivers for the M200. 
 Now I am working on figuring out how to get the tablet features working,but the install worked fine. Once I upgraded to 11.04 the stylus works fine with the exception of the buttons and the quick launches on the tablet.

Could you tell me where to find said drivers.

---

### Post by mörgæs on 2012-01-20
Please don't post the same problem multiple times. Moved. 

Also, some punctuation would help the one reading your posts.

---

### Post by tpinkfloyd on 2012-01-20
Sorry about the punctuation thing. I was really tired last night and had been working on this laptop for 4 days straight trying to get windows working. Same goes for the double post, I edited them accordingly.

---

