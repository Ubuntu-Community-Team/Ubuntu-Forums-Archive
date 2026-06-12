---
title: "Boot Problem Please Help"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by rippedcb on 2009-04-24
I'm absolutely new to Linux and Ubuntu. After doing some research and hearing great things about Ubuntu i decided to finally take the plunge into this world. 

I had Win XP on my 1TB SATA drive and i wanted to dual boot and wanted to keep XP till i can get used to ubuntu so i got another hd 500GB SATA as well and wanted to install ubuntu on it. I installed Ubuntu Ultimate Edition 2 and it seemed like everything went well. However, now when i boot up, GRUB gives me options and shows me Win XP as an option but it won't let me pick it. I am not able to move up/down and select win XP (or anything else for that matter) i get automatically logged into Ubuntu after the time expires.

I know that Win XP is still there as when i go to the partition manager i can see my first hard drive and the partitions on it and everything seems right. I've googled and googled but haven't been able to find out whats going on.

Anyone able to help.. pls help :confused:

---

### Post by rippedcb on 2009-04-24
i forgot to mention that even if i disconnect my second hard drive (one with ubuntu on it) and i try to boot up.. GRUB gives me an error (obviously) and won't let me boot up anything. Is there any way i can uninstall GRUB and format my second hard drive and try to do a new install??
thanks,
CB

---

### Post by LinuxGuy1234 on 2009-04-24
What kind of keyboard do you have? If you have a USB keyboard, you're out of luck unless you get a non-USB keyboard.

---

### Post by PukingPenguin on 2009-04-24
> **rippedcb said:**
>  I am not able to move up/down and select win XP (or anything else for that matter) i get automatically logged into Ubuntu after the time expires.

I assume that you are using the arrow keys to try to navigate up and down the grub menu? 
If so, you may need to try a p/s2 keyboard. (Although this really shouldn't be an issue anymore....)

---

### Post by qwertyuiop96 on 2009-04-24
A REALLY cheap quikie would be to open the computer and disconnect the Ubuntu drive.  BTW, I have a wireless USB keyboard and I can manuever in GRUB fine.

---

### Post by SirNuke on 2009-04-24
Assuming you have a usb keyboard, there should be an option in your system's bios to enable legacy usb support.  [See this page for more details]("http://www.intel.com/support/peripherals/sb/cs-011939.htm").

The reason why GRUB fails to work when you remove your second hard is because it stores files inside your Ubuntu installation.  Reverting entirely to Windows XP will require reinstalling the Windows XP master boot record.   [See this page for instructions]("http://pcsupport.about.com/od/fixtheproblem/ht/repairmbr.htm").

A quick overview of how grub works: when booting your computer executes code residing in the beginning of the hard drive, known as the master boot record.  This code then starts the operating system.  Before, Windows XP had a bootloader installed that starts itself, Ubuntu replaced this with GRUB which allows you to select which operating system to start.  Since the space available inside the master boot record is fairly small (on top of the boot strapping code, it stores other information), GRUB stores most of the files it needs inside the Ubuntu partition.

---

### Post by rippedcb on 2009-04-24
Thanks guys, got it working. Thanks SirNuke. I had to go into bios and enable usb keyboard and mouse option (as SirNuke had said) and it all worked. Had me worried for a minute as my motherboard doesn't even have PS2 connectors on the back.

Thanks again for taking the time to help me.
Regards,
CB

---

