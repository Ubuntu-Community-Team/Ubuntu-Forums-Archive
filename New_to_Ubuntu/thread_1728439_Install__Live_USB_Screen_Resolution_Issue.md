---
title: "Install / Live USB Screen Resolution Issue"
date: 2011-04-13
forum: New to Ubuntu
---

### Post by grants on 2011-04-13
I have a Sony KDL-55HX800 1080p TV. It is compatible with 1024x768 60 hz resolution along with many others. Graphics is a Sapphire Readon HD  5870 2GB Eyefinity Edition. 

During boot I get my BIOS and normal boot selection. I can select my USB to boot from. I can select different options like Install Ubuntu or Try, typical grub options. But when It starts to load my TV gives me an error saying its an unsupported resolution. I've tried all options. I've even set vga mode by trying to boot advanced off Live version. I've tried vga=792 and vga=796 and lastly vga=771. I've tried setting all these options for the live boot and when it failed I also tried for the Install only options. 

The odd thing is that Back Track 4 will boot just fine. Graphics and command line. 

Ubuntu Versions I've Tried. 

10.10 Server ( Command line works just fine, install and all)
   - sudo apt-get install ubuntu-desktop breaks everything. 
   - I first suspected a driver issue so I'd escape to the command line and try to install the driver, Driver doesn't seem to want to install. 10.8 or 11.3.

10.10 Desktop ( Can only see boot Screen )
10.08 Server ( Command line works just fine, install and all)
   - tried same things as above with 10.10 server, same results.
10.08 Desktop ( Can only see the boot screen )

I've tried both 32 bit and 64 bit versions of 10.10 server, both act the same. 


Back Track works just fine drivers install but fglrxinfo doesn't work so I suspect that the driver never really installed correctly.

I don't remember the command I used but I was able to verify that my pci device was correct. One command shows that it was a Readon HD 5870 another I used shows that it was a 5800 series. 


Any help would be great!

---

### Post by grants on 2011-04-14
bump

---

### Post by KegHead on 2011-04-14
Hi!

I had a few problems like yours w/viewsonic.

I was upgrading my kernel in 11.04.

It took one -two kernel upgrades for my monitor to act correctly.

Are you up to date?

KegHead

---

### Post by grants on 2011-04-14
It's a fresh download, I can't even get the console up to install. You would have to install before you can do updates. 

If I use the live boot option I get the screen resolution error. When I hit CTRL - ALT - F1 my screen says no input signal so I can't even pull up the terminal. Although typing sudo reboot now blindly still restarts the system.

---

### Post by K_45 on 2011-04-14
Are you connected via HDMI? And if so, is this a direct link between PC and TV or is there a receiver in-between?

---

### Post by KegHead on 2011-04-14
Hi!

If I were to guess it's:  Sapphire Readon HD 5870 2GB Eyefinity Edition. 

KegHead

---

### Post by grants on 2011-04-14
Direct with HDMI,

I've tried the DVI - HDMI adapter, I've tried all ports on the video card, I've tried a different input on the TV and also a different HDMI cable. 

No Luck. 

There has to be a way to specify the resolution within a file on my install USB. Setting advanced boot options with vga= doesn't work though so maybe I'm wrong. But Back Track works just fine and server worked before I added ubuntu-desktop. Only reason why I tried switching away from ubuntu-server is because I couldn't get the driver to work. I kept getting an error saying my desktop environment was wrong and my OS wasn't supported by the AMD driver.

---

### Post by K_45 on 2011-04-14
I'd try a Live CD of 11.04 beta, which has an updated kernel.

---

### Post by KegHead on 2011-04-14
Hi!

system..preferences...monitor.

KegHead

---

### Post by grants on 2011-04-14
> **KegHead said:**
> Hi!

system..preferences...monitor.

KegHead



How can I get to this if I can't see the desktop?

I'm trying to do an initial clean install.

---

### Post by grants on 2011-04-14
> **KegHead said:**
> Hi!

If I were to guess it's:  Sapphire Readon HD 5870 2GB Eyefinity Edition. 

KegHead


That is correct!

How did you know?

---

### Post by grants on 2011-04-14
> **K_45 said:**
> I'd try a Live CD of 11.04 beta, which has an updated kernel.

Will ATI / AMD drivers that list 10.04 as the supported platform install in this environment?

Also on my install list is . . .
libboost
Python-dev
libssl-dev
libpcap-dev
scapy
calapp / cal++
ATI Stream SDK or AMD APP stream SDK 

If all these work I'll jump right to 11.04

---

### Post by K_45 on 2011-04-14
There will be updated AMD drivers that support 11.04, but the idea now is to see if your TV works out of the box.

---

### Post by grants on 2011-04-14
> **K_45 said:**
> There will be updated AMD drivers that support 11.04, but the idea now is to see if your TV works out of the box.

TV works just fine. TV works. Blue Ray works. Xbox works. Even BackTrack works via HDMI. Old video card works too but the max resolution it can support is much smaller. I'm thinking that Ubuntu tries to set a resolution by default during the load of either the Live Boot or during the GUI for install and it somehow displays a resolution that isn't supported. I'd like to know how to override this.

---

### Post by KegHead on 2011-04-14
Hi!

It was an educated guess.

Based on learning from all of the folks on the forum!

KegHead

---

### Post by K_45 on 2011-04-14
Try disabling KMS - boot up a live cd, then open up a terminal and enter

```
gksu gedit /etc/default/grub
```Then add [COLOR=Black]nomodeset to the [/COLOR]GRUB_CMDLINE_LINUX_DEFAULT entry so it looks like [COLOR=Black]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [/COLOR][COLOR=Black]nomodeset[/COLOR]*"*. Save the file then run sudo update grub and restart.

---

### Post by KegHead on 2011-04-14
Hi!

I hope everything works out!

If you're satisfied please mark your post as "solved".

KegHead

---

### Post by grants on 2011-04-14
> **K_45 said:**
> Try disabling KMS - boot up a live cd, then open up a terminal and enter

```
gksu gedit /etc/default/grub
```Then add [COLOR=Black]nomodeset to the [/COLOR]GRUB_CMDLINE_LINUX_DEFAULT entry so it looks like [COLOR=Black]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [/COLOR][COLOR=Black]nomodeset[/COLOR]*"*. Save the file then run sudo update grub and restart.

Is this on the boot USB?

I don't have the system installed yet.

---

### Post by grants on 2011-04-14
I'm using UNetBootin so if you know where I can edit this on the boot USB it would be a great help!

---

### Post by K_45 on 2011-04-14
Here:  [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)  Try the safe graphics mode, and then adjust the rest post-install (if this works).

---

### Post by grants on 2011-04-14
> **K_45 said:**
> Try the safe graphics mode

Not an option with UNetBootin unfortunately from what I can see anyway.

---

### Post by grants on 2011-04-14
Tried 10.04 from CD and boots to an unsupported signal. Doesn't even pull up the main menu where I can select different boot options. 

I'll try 11.04 as I just finished that download but still, I'd like to know how to specify the resolution some where on the CD / USB itself.

---

### Post by grants on 2011-04-14
> **grants said:**
> I'll try 11.04 

OMG,
It Actually worked!

Any idea how I can replicate the settings from this into a 10.04 boot where all my drivers will install correctly?

---

### Post by K_45 on 2011-04-14
> **grants said:**
> OMG,
It Actually worked!

Any idea how I can replicate the settings from this into a 10.04 boot where all my drivers will install correctly?

 Possibly, but we should have done 11.04 from the start . . . anyway there is an updated kernel in 11.04 so I'd wait until its released and install that.

---

### Post by grants on 2011-04-14
Everything but the ATI driver installed. 

This package is a must. Perhaps theres a way to roll my version back from 11.04 to 10.10? Or would that be a bad idea?

---

### Post by K_45 on 2011-04-15
If the graphics works, you don't need the proprietary driver.

---

