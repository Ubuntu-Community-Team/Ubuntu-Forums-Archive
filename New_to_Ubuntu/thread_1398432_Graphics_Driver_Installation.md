---
title: "Graphics Driver Installation"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by Afiorentino on 2010-02-04
Hi, I am relatively new to Linux and have some light computer background (I can work my way around Ubuntu with a guide). I have been trying to install the driver for my video card so that I can play games through WINE and watch movies on my tv through with the s-video cable, but I've ran in to a few problems. 

The video card I currently have installed is a Radeon X1950XTX. I've tried going through ati's website to install the legacy driver, but when I try to use the .run file in terminal, I get an shell error saying that it can't be opened.

I've also tried using the synaptic file, but I find it too confusing. Any suggestions?

---

### Post by dondiego2 on 2010-02-04
Did you go to System->Hardware Drivers and run that?  That will look for compatible drivers for your system.  That's how I got my graphic card to work.

---

### Post by mesuhas_sit on 2010-02-04
First of all I am also new to Linux... But I also have a ATI graphics card which was not working when I first installed Ubuntu. What I did was to enable 3rd EXTRA option in Appearance preferences. First it gave me an error automatically switched back to NONE which is the first default option. I tried it once more it automatically downloaded some packages and now I have the extra features turned on like COmpiz. 

Hope this will help you as well

---

### Post by verachion on 2010-02-04
> **mesuhas_sit said:**
> First of all I am also new to Linux... But I also have a ATI graphics card which was not working when I first installed Ubuntu. What I did was to enable 3rd EXTRA option in Appearance preferences. First it gave me an error automatically switched back to NONE which is the first default option. I tried it once more it automatically downloaded some packages and now I have the extra features turned on like COmpiz. 

Hope this will help you as well

Hey there, I too am new to ubuntu, I have been playing around with it all day. I too have an ATI card what I did was search in either add and remove programmes or ubuntu software in one of those is the ATI 3rd party control centre, then I installed it, rebooted the o/s and then got cracking on the 3d effects. Hope this helps

---

### Post by Afiorentino on 2010-02-09
Sorry guys, had a busy couple of days so I haven't had the chance to get back to this until now. Here's what I did: uninstalled ubuntu and did a fresh install of xubuntu 9.10. The very first thing I did after install was complete and my  computer seemed stable was I went to synaptic package manager and downloaded fglrx-amdcccle and xorg-driver-fglrx. 

The catalyst control center is installed, but when I double click on the program, it gives me an error message saying "No ATI graphics driver is installed, or the ATI driver is not functioning properly. Please install the ATI driver appropriate for you {sic} ATI hardware, or configure using aticonfig."

In terminal the command aticonfig gives me "aticonfig: No supported adapters detected".

Hardware Drivers comes up with nothing.

---

### Post by Mark Phelps on 2010-02-11
> **Afiorentino said:**
> Hardware Drivers comes up with nothing.

That's because there are NO ATI drivers that will work with Ubunto 9.10 versions and your video card.  ATI dropped Linux support for your card last May.  Doesn't matter where you get the drivers from or how you try to install them -- they simply won't work.

Read the directions in the link below about removing the fglrx drivers and replacing them with the open source drivers:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

