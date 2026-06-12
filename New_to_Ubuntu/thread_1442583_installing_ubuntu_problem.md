---
title: "installing ubuntu problem"
date: 2010-03-30
forum: New to Ubuntu
---

### Post by Vallista on 2010-03-30
I'm new to ubuntu. I understand how to install ubuntu. That is not my problem, my real problem, how do I install my drivers for my ATI mobility Radeon HD 5470? I looked on ATI support forums couldn't find anything. Also I having a real problem over all installing 64 bit verison of ubuntu, but the 32 bit verison i do fine. Is there anyone here with a similar system like my that can help me? my computer specs:
 
Asus K42J
intel core i5
ATI Mobility Radeon HD 5470
4gig of ram
500 HDD
 
if anyone have similar system to me please let me know. I'm struggling to understand what i need to do to install this OS properly. 
 
Intel® Core&#8482; i5 Processor 520M/430M : 2.4 GHz - 2.26 GHz, with Turbo Boost up to 2.93/2.53 GHz;
 
 
Operating System[Genuine]("http://ubuntuforums.org/#") Windows® 7 Ultimate
ChipsetMobile Intel® HM55 Express Chipset 
Main MemoryDDR3 1066 MHz SDRAM, 2 x SODIMM socket for expansion up to 8GB SDRAM 
 
Display14" HD (1366x768) LED backlight
Video Graphics & MemoryATI Mobility&#8482; Radeon® HD 5470 1G DDR3 VRAM 
Hard Drive 500GB 7200rpm
 
Optical DriveDVD Super Multi

---

### Post by coffeecat on 2010-03-30
You'll be running on the open source ATI driver at the moment, which should be OK (ish). If you want the proprietary driver, have a look in System > Administration > Hardware Drivers. If nothing is showing there, refresh your package metadata by Update Manager > Check, or Synaptic > Reload. (Both these apps are in System > Administration.)

That being said, you may or may not find the proprietary fglrx driver a happy experience.

Good luck!

**Edit:** sorry, missed the 64/32 bit question. Can you give more details of the problems you have installing the 64-bit version? That system should be OK with 64-bit.

---

### Post by 3rdalbum on 2010-03-30
Ubuntu 9.10's ATI driver from Hardware Drivers will work, but you'll get an "Unsupported Hardware" watermark in the bottom-right corner of the screen.

If the watermark annoys you (I'm sure it would me), then download the latest 64-bit ATI driver from [www.ati.com](www.ati.com), and the following packages from Synaptic:

```
sudo apt-get install linux-headers-generic build-essential
```

Then make the ATI driver installer executable:

```
sudo chmod a+x <whatever_the_filename_is>
```

And run it as root:

```
sudo ./<whatever_the_filename_is>
```

In place of <whatever_the_filename_is> you can just drag the file to the terminal and it will fill it in for you.

---

### Post by Vallista on 2010-03-30
ok,  let me try that.  thanks for the advice thanks guys.

---

### Post by jaycee23 on 2010-03-30
I have a similar system - check out my signature!
I tried the open source driver for my graphics card but got that dirty watermark so I installed the ATI driver version 10.3 - works like a dream
Installation instructions are on the ATI website

---

### Post by quadproc on 2010-03-30
> **Vallista said:**
> I'm new to ubuntu. I understand how to install ubuntu. That is not my problem, my real problem, how do I install my drivers for my ATI mobility Radeon HD 5470? I looked on ATI support forums couldn't find anything. Also I having a real problem over all installing 64 bit verison of ubuntu, but the 32 bit verison i do fine. Is there anyone here with a similar system like my that can help me? my computer specs:
 ...

I am running a somewhat similar system so hopefully some of the things that I have learned will be useful to you.

Other posters have pretty much answered the installation question but I would like to offer a couple of additional tidbits:

The ATI driver is a big package, over 80 MB.  It can take a while to download so don't be discouraged if things seem to go to sleep.  If you run the System Monitor then you can see the network activity.

The ATI driver file is a .run file; it is a self extracting file.  The first part of the file is a shell script which uncompresses, organizes, and locates all of the various files and directories used for the installation. Most editors will choke on the binary portions of the file so if you want to look at the script, try something like ```
head -n 305 <the_ati_file_name.run>
``` Adjust the 305 to just include all of the script portion.

If you download the file yourself from the ATI site (rather than letting Hardware Drivers get it) then you can put it in a directory for later inspection.  If you add --keep to the command line then the installer will leave behind all of the files that it temporarily used.  You can examine these, or you can remove them later if you have no interest in them.  Without the --keep option, the script will clean up all of this when it is done.

The System > Administration > Hardware Drivers utility is actually named jockey-gtk and** it does not necessarily correctly report** the status of your driver(s).  In the system that I am using right now, that utility reports that the fglrx driver is not in use, even though it is.

quadproc

---

