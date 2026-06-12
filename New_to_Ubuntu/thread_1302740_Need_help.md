---
title: "Need help"
date: 2009-10-27
forum: New to Ubuntu
---

### Post by sunrex on 2009-10-27
Since the subforum for remix appears to be useless (day old thread no help) ill ask here.

EEE_PC 1000HD

1: Flickering screen. Only occurs if something changes, so I'm guessing its the graphic driver/compiz.

2: Audio crackles. Probably current driver, I would like to know what to set it to and how to get skype configured correctly for microphone support.

3: Need a underclocking tool for the CPU and the ability to shutdown wifi.

4: How do you disable the standby that happens when you close the screen?.

Thank you!.

---

### Post by martrn on 2009-10-27
> **sunrex said:**
> EEE_PC 1000HD..1: Flickering screen. Only occurs if something changes, so I'm guessing its the graphic driver/compiz..2: Audio crackles. Probably current driver, I would like to know what to set it to and how to get skype configured correctly for microphone support..3: Need a underclocking tool for the CPU and the ability to shutdown wifi..4: How do you disable the standby that happens when you close the screen?.

[https://help.ubuntu.com/community/EeePC]("https://help.ubuntu.com/community/EeePC")
(Techdocs for your machine - Subnotebook)

1. Don't install compiz on a subnotebook, not really designed for it.
```
sudo apt-get remove --purge compiz
```
should do the trick.

2. See : [https://help.ubuntu.com/community/EeePC]("https://help.ubuntu.com/community/EeePC").
Audio shouldn't be a problem unless headphones are plugged in but there is a fix on the website. See URL above.

3.  Underclocking a < 1GHZ CPU. Err yerr ok, some people want to overclock some underclock, hmmm.  Apparently there is a website if you see the above site for a kernel for eeepc which offers support for tweeks you suggest.

4.  If you don't want standby when you close the screen, then don't close the screen.

---

### Post by sunrex on 2009-10-27
> **martrn said:**
> [https://help.ubuntu.com/community/EeePC]("https://help.ubuntu.com/community/EeePC")
(Techdocs for your machine - Subnotebook)

1. Don't install compiz on a subnotebook, not really designed for it.
```
sudo apt-get remove --purge compiz
```
should do the trick.

2. See : [https://help.ubuntu.com/community/EeePC]("https://help.ubuntu.com/community/EeePC").
Audio shouldn't be a problem unless headphones are plugged in but there is a fix on the website. See URL above.

3.  Underclocking a < 1GHZ CPU. Err yerr ok, some people want to overclock some underclock, hmmm.  Apparently there is a website if you see the above site for a kernel for eeepc which offers support for tweeks you suggest.

4.  If you don't want standby when you close the screen, then don't close the screen.

Compiz came with the install, its not like I went around searching for it, nor was there a option to not install it.

Does it matter if the CPU is less then 1Ghz?. I saved over a hour of power when I used windows XP and underclocked it. For simple web browsing, I did not notice a difference.

Um, if I don't close the screen then the backlight stays on. If I do close it then the netbook goes on standby - it did not do this on windows, so there must be a option to change it.

Thank you for your help.

---

### Post by semitone36 on 2009-10-27
To keep your computer from going into standby when closing the lid go to System -> Preferences -> Power Management (or something to that effect).  There should be an option somewhere that says "When lid closed:" and then it gives you several options, "Do nothing" or "turn off screen" should be among the options you can choose from that will keep your computer on.

---

### Post by martrn on 2009-10-28
> Compiz came with the install, its not like I went around searching for it, nor was there a option to not install it.
To need a large amount of memory and a good 3d graphics card for compiz to work as it should. It comes for desktops, just uninstall it.

> Does it matter if the CPU is less then 1Ghz?. I saved over a hour of power when I used windows XP and underclocked it. For simple web browsing, I did not notice a difference..
No of course not, as long as as long as you have > 256MB memory it desn't matter too much what speed your cpu runs at.  If you goto [https://help.ubuntu.com/community/EeePC]("https://help.ubuntu.com/community/EeePC") you will find a link there for custom distributions that has a link to the eepc-array site.  If you follow this link through, you will find some custom kernels and some of these include a custom eeepc enhanced eeee power module for manipulating the fsb/eeepower/temp/...., you will need to download the custom kernel.

> Um, if I don't close the screen then the backlight stays on. If I do close it then the netbook goes on standby - it did not do this on windows, so there must be a option to change it.
This is documented at eeepc--acpi enhancments see above.
[https://help.ubuntu.com/community/EeePC]("https://help.ubuntu.com/community/EeePC") +Follow +Read notes.

---

### Post by sunrex on 2009-10-28
> **martrn said:**
> To need a large amount of memory and a good 3d graphics card for compiz to work as it should. It comes for desktops, just uninstall it.

It comes preinstalled on the mobile distro...

---

### Post by martrn on 2009-10-28
> **sunrex said:**
> It comes preinstalled on the mobile distro...

Intel gma mobile chipset support on Linux is not optimal. The driver is closed source limited 3d accelerated drivers, with instability and lack of support.and the graphic core is not an optimal one.  Intel gma mobile chipset support in ubuntu has supporting hardware accelerated video decoding.

Compiz is heavely dependent on 3D hardware which was supported by Xgl and your computer in this circumstance will be working flat out just to draw a desktop.  I wouldn't think it a good idear to use (compiz) here.

But each to their own.

---

