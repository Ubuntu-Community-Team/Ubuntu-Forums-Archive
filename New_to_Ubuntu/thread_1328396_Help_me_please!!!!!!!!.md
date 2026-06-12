---
title: "Help me please!!!!!!!!"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by Sheed3036 on 2009-11-16
hey i have M3A78Pro motherboard with ati chipset, i was trying to udate the the drives for the chipset and some how it doesnt work anymore, when you go to type your username in it comes up with the ubuntu logo with pink and purple lines through it, i tried pressing Alt F1 and Ctrl Alt F3 but nothing happens so i was wondering if there was any way of updateing the drivers through the live cd PS im new to ubuntu but know a few commands thanks for ur help

---

### Post by ukripper on 2009-11-16
can you post output of the follwing command 
```
lspci
```

---

### Post by Paqman on 2009-11-16
> **Sheed3036 said:**
> i was trying to udate the the drives for the chipset

Which chipset? Graphics? Wifi? Something else? And how exactly were you updating them?

---

### Post by Sheed3036 on 2009-11-16
> **ukripper said:**
> can you post output of the follwing command 
```
lspci
```

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

---

### Post by NullHead on 2009-11-16
> 01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics

That's your graphics card right there. I'm guessing you tried upgrading the **graphics card** driver with the "Hardware Drivers" program.

---

### Post by Sheed3036 on 2009-11-16
> **NullHead said:**
> That's your graphics card right there. I'm guessing you tried upgrading the **graphics card** driver with the "Hardware Drivers" program.

a couple of days ago i was trying to update the sound driver through command line and now i when i get to the log in screen i get the ubuntu logo with pin and purple lines through it and cant log in

---

### Post by NullHead on 2009-11-16
If you could, please link to the tutorial you were following, if you were following one at all. Please link to the driver(s) you were using as well. 

Any information about what you were doing would be useful.

---

### Post by khelben1979 on 2009-11-16
If you choose the drivers from the ATi homepage, it's very important that you get the right one for your hardware, which one did you choose?

I found your motherboard by looking at [this page]("http://www.silentpcreview.com/article855-page1.html") b.t.w, I guess you recognize it?

---

### Post by Sheed3036 on 2009-11-16
> **NullHead said:**
> If you could, please link to the tutorial you were following, if you were following one at all. Please link to the driver(s) you were using as well. 

Any information about what you were doing would be useful.


Sorry I cant i was using way to many sites , is there any way to install the drivers through a live cd

---

### Post by khelben1979 on 2009-11-16
As a first step you can use the slow open source ati video drivers and if the problem with colours disappears, you know it's not a hardware problem and you will be able to surf the web again where you can download the drivers from the ATi homepage, [here]("http://support.amd.com/us/gpudownload/Pages/index.aspx").

I would like to recommend you do some reading over at: [Binary Driver HowTo ATi]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") to better understand how it works.

---

### Post by Sheed3036 on 2009-11-16
> **khelben1979 said:**
> As a first step you can use the slow open source ati video drivers and if the problem with colours disappears, you know it's not a hardware problem and you will be able to surf the web again where you can download the drivers from the ATi homepage, [here]("http://support.amd.com/us/gpudownload/Pages/index.aspx").
 
I would like to recommend you do some reading over at: [Binary Driver HowTo ATi]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") to better understand how it works.
 
 
where would i enter this command i cant get to the terminal and i tried to get to terminal through recovery mode but cant

---

### Post by khelben1979 on 2009-11-16
> **Sheed3036 said:**
> where would i enter this command i cant get to the terminal and i tried to get to terminal through recovery mode but cant

You might be better off by just going for a reinstallation of Ubuntu then, then you try to do it the right way from the beginning instead.

---

### Post by Sheed3036 on 2009-11-16
> **khelben1979 said:**
> You might be better off by just going for a reinstallation of Ubuntu then, then you try to do it the right way from the beginning instead.
 
 
i was trying to avoid that method

---

### Post by Sheed3036 on 2009-11-16
any other possible solutions

---

### Post by halitech on 2009-11-16
let it boot up and then press CTRL+ALT+F1 which should take you to the terminal. Log in with your username and password and then run this

```
sudo apt-get remove --purge xorg-driver-fglrx
```
reboot and see what happens

---

### Post by Sheed3036 on 2009-11-16
> **halitech said:**
> let it boot up and then press CTRL+ALT+F1 which should take you to the terminal. Log in with your username and password and then run this
 
```
sudo apt-get remove --purge xorg-driver-fglrx
```
reboot and see what happens
 
when i press that nothing happens

---

### Post by halitech on 2009-11-16
pressing CTRL + ALT +F1 does nothing at all? are you hitting all 3 keys together?

---

### Post by Cope57 on 2009-11-16
[Use meaningful, specific subject headers]("http://catb.org/~esr/faqs/smart-questions.html#bespecific")

Thank you.

[How To Ask Questions The Smart Way]("http://catb.org/~esr/faqs/smart-questions.html")
*~ Eric Steven Raymond*

---

### Post by Paqman on 2009-11-17
> **Sheed3036 said:**
> any other possible solutions

Without actually knowing what you've done it's almost impossible for anyone to tell you how to fix it. We'd just be guessing really. I'm afraid a full reinstall is probably the easiest option. Once you've got it installed, start a new thread and someone will be happy to help you get your video drivers installed properly.

---

### Post by NullHead on 2009-11-17
> **Sheed3036 said:**
> a couple of days ago i was trying to update the sound driver through command line and now i when i get to the log in screen i get the ubuntu logo with pin and purple lines through it and cant log in

Is this sound be any chance coming from an HDMI port on your computer?

---

### Post by Sheed3036 on 2009-11-17
> **NullHead said:**
> Is this sound be any chance coming from an HDMI port on your computer?

There no sound coming from my HDMI cable when my computer was working and to halitech i was pressing all three keys together

---

### Post by Sheed3036 on 2009-11-17
> **halitech said:**
> pressing CTRL + ALT +F1 does nothing at all? are you hitting all 3 keys together?
 
yes im hitting all three keys together

---

### Post by halitech on 2009-11-17
try holding down the CTRL and ALT keys and then hit F3, it should give you a terminal screen and if its not then I'm not sure why

---

### Post by Sheed3036 on 2009-11-17
> **halitech said:**
> try holding down the CTRL and ALT keys and then hit F3, it should give you a terminal screen and if its not then I'm not sure why
 
 
kk i pressed CTRL and ALT and F3 then CTRL and ALT and F1 then it goes to terminal

---

### Post by halitech on 2009-11-17
ok, now try my command from post 15

```
sudo apt-get remove --purge xorg-driver-fglrx
```

---

### Post by Sheed3036 on 2009-11-17
> **halitech said:**
> ok, now try my command from post 15
 
```
sudo apt-get remove --purge xorg-driver-fglrx
```
 
 
when  i press the CTRl ALT F3/F1 it only shows the boot up in terminal i can trype any thing in

---

### Post by halitech on 2009-11-17
so you don't get the log in screen?

---

### Post by Sheed3036 on 2009-11-17
> **halitech said:**
> so you don't get the log in screen?
 
the logo comes up with pink and purple lines through it and i cant eneter a usrname or psswrd

---

### Post by Sheed3036 on 2009-11-18
> **Sheed3036 said:**
> the logo comes up with pink and purple lines through it and i cant eneter a usrname or psswrd

what should i do next?

---

### Post by NullHead on 2009-11-18
> **Sheed3036 said:**
> what should i do next?

I'm only guessing here, but try running this command in the terminal that you got to earlier with ctrl+alt+F3

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Sheed3036 on 2009-11-18
> **NullHead said:**
> I'm only guessing here, but try running this command in the terminal that you got to earlier with ctrl+alt+F3

```
sudo dpkg-reconfigure -phigh xserver-xorg
```


i cant, its only showing the boot up in ternimal form, i dont have a chance to enter anything

---

### Post by NullHead on 2009-11-18
> **Sheed3036 said:**
> i cant, its only showing the boot up in ternimal form, i dont have a chance to enter anything

That's okay, you want to enter that command into the terminal. What you should do is write it down in a piece of paper, and login on that terminal, CRTL + ALT + F3, and type it in.

All you need to do is wait until you see the corrupted ubuntu logo and /then/ press CTRL + ALT + F3. When you see the corrupted Ubuntu logo, that means that your system is fully loaded.

---

### Post by Sheed3036 on 2009-11-19
> **NullHead said:**
> That's okay, you want to enter that command into the terminal. What you should do is write it down in a piece of paper, and login on that terminal, CRTL + ALT + F3, and type it in.
 
All you need to do is wait until you see the corrupted ubuntu logo and /then/ press CTRL + ALT + F3. When you see the corrupted Ubuntu logo, that means that your system is fully loaded.
 
i when i press CTRL + ALT + F3 when the logo is corrupted nothing happens, im pressing CTRL + ALT + F3 before the corrupted logo comes up

---

### Post by NullHead on 2009-11-19
Okay, lets try something else. 

Reboot the PC and wait for grub to show up. It will say something like: 

> Grub loading stage1.5. 

GRUB Loading, please wait...
Press 'ESC' to enter menu... 

When you see that, press escape and select the second option. From what I can tell, you're running ubuntu 9.04, so the menu option that you want to select will look like this: 

> Ubuntu 9.04, kerne. 2.6.28-16-generic (recovery mode)

After you select that, press enter and wait for it to finish booting. You'll be prompted with a "Recovery Menu" that lists several options. You need to select "xfix" all the way at the bottom. The screen will change, then go back to the "recovery menu". When that is done, go back up to the top of the menu, and select "resume". 

Let me know what the results are.

---

### Post by Sheed3036 on 2009-11-19
> **NullHead said:**
> Okay, lets try something else. 
 
Reboot the PC and wait for grub to show up. It will say something like: 
 
 
 
When you see that, press escape and select the second option. From what I can tell, you're running ubuntu 9.04, so the menu option that you want to select will look like this: 
 
 
 
After you select that, press enter and wait for it to finish booting. You'll be prompted with a "Recovery Menu" that lists several options. You need to select "xfix" all the way at the bottom. The screen will change, then go back to the "recovery menu". When that is done, go back up to the top of the menu, and select "resume". 
 
Let me know what the results are.
 
when i press esc i got Ubuntu 9.04, kerne. 2.6.28-15-generic (recovery mode) and not Ubuntu 9.04, kerne. 2.6.28-16-generic (recovery mode) but i went to the 15 one and xfix and pressed resume and it came up with a disorted image of my motherboard name at the top

---

### Post by Sheed3036 on 2009-11-19
> **Sheed3036 said:**
> when i press esc i got Ubuntu 9.04, kerne. 2.6.28-15-generic (recovery mode) and not Ubuntu 9.04, kerne. 2.6.28-16-generic (recovery mode) but i went to the 15 one and xfix and pressed resume and it came up with a disorted image of my motherboard name at the top
 
 
What should I do next?

---

### Post by NullHead on 2009-11-19
I'm at a loss here ... It's hard to tell what's wrong with your PC without knowing exactly what was done to break it.

---

### Post by Sheed3036 on 2009-11-19
> **NullHead said:**
> I'm at a loss here ... It's hard to tell what's wrong with your PC without knowing exactly what was done to break it.
 
 
if i posted a video of what is happening would that be more helpful?

---

### Post by Sheed3036 on 2009-11-21
> **NullHead said:**
> I'm at a loss here ... It's hard to tell what's wrong with your PC without knowing exactly what was done to break it.

would a video help out?

---

### Post by NullHead on 2009-11-21
It's worth a shot.

---

### Post by Sheed3036 on 2009-11-26
> **NullHead said:**
> I'm at a loss here ... It's hard to tell what's wrong with your PC without knowing exactly what was done to break it.
 
 
Is there any way i could use a live cd to update the system?

---

### Post by Don1500 on 2009-11-26
Do you have anything on the drive you wish to keep (besides your  preferences)?

Since you are coming on here can I ask if you are dual booting with windows, and windows works?

If the above is ture, save any data you need on the Ubuntu drive to some place safe, and reinstall Ubuntu.

---

### Post by Sheed3036 on 2009-11-26
> **Don1500 said:**
> Do you have anything on the drive you wish to keep (besides your preferences)?
 
Since you are coming on here can I ask if you are dual booting with windows, and windows works?
 
If the above is ture, save any data you need on the Ubuntu drive to some place safe, and reinstall Ubuntu.
 
 
I'm not sure if i have anything on it, but i wanted to avoid formatting, and i dont have windows or another os

---

### Post by Don1500 on 2009-11-27
Why would you avoid re-formatting? It's an easy process and will get rid of your problems.
Do a fresh install with the live CD and your problems will be over. 20 to 40 minutes.

---

### Post by Sheed3036 on 2009-11-27
> **Don1500 said:**
> Why would you avoid re-formatting? It's an easy process and will get rid of your problems.
Do a fresh install with the live CD and your problems will be over. 20 to 40 minutes.
 
but theres no way to update through the live cd?

---

### Post by halitech on 2009-11-27
no you can not use the live cd to update the system. The file system the cd uses to allow you to run the system from the cd without installing prevents it from being used to update the system.

---

