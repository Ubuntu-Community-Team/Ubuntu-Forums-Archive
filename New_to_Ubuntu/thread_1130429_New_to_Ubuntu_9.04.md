---
title: "New to Ubuntu 9.04"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by Irish1 on 2009-04-19
I'm new to Ubuntu.  I use it at work and decided that I would start using it at home.  I recently bought a new computer with a blank HD figuring I would install Ubuntu and forget about Windows.  The computer I bought has an ASUS M3A78-EM motherboard.  I'm trying to run the disks that came with it to install some software, but I keep getting an Autorun error message.  I've tried to open the ASUS setup file manually, but then I get an Archive Manager error message.  What steps do I need to take to run this software setup disk?  It is a .exe file type which I think is for Windows.  Is that the problem, that Ubuntu cannot read the file types meant for Windows?  

Also, I currently do not have my new computer hooked up to the internet, is that going to be a problem?  I do have access in my building to another comuter with an internet connection.

Please help me, I really don't want to have to resort to using Vista, I haven't heard one good thing about it.

---

### Post by Tibuda on 2009-04-19
> **Irish1 said:**
> I'm new to Ubuntu.  I use it at work and decided that I would start using it at home.  I recently bought a new computer with a blank HD figuring I would install Ubuntu and forget about Windows.  The computer I bought has an ASUS M3A78-EM motherboard.  I'm trying to run the disks that came with it to install some software, but I keep getting an Autorun error message.  I've tried to open the ASUS setup file manually, but then I get an Archive Manager error message.  What steps do I need to take to run this software setup disk?  It is a .exe file type which I think is for Windows.  Is that the problem, that Ubuntu cannot read the file types meant for Windows?
Those software you are trying to install are probably made for Windows, and won't work in Ubuntu. Can you tell what are you trying to install? If they are drivers, don't worry. You almost don't have to install them in Linux if your hardware is well supported.

> Also, I currently do not have my new computer hooked up to the internet, is that going to be a problem?  I do have access in my building to another comuter with an internet connection.
I think that would be a problem. Ubuntu relies too much in the Internet to install software. I would connect it to the Internet using your other computer connection, install everything you want, and then disconnect it.

---

### Post by nandemonai on 2009-04-19
> **Irish1 said:**
> I'm new to Ubuntu.  I use it at work and decided that I would start using it at home.  I recently bought a new computer with a blank HD figuring I would install Ubuntu and forget about Windows.  The computer I bought has an ASUS M3A78-EM motherboard.  I'm trying to run the disks that came with it to install some software, but I keep getting an Autorun error message.  I've tried to open the ASUS setup file manually, but then I get an Archive Manager error message.  What steps do I need to take to run this software setup disk?  It is a .exe file type which I think is for Windows.  Is that the problem, that Ubuntu cannot read the file types meant for Windows?  

Also, I currently do not have my new computer hooked up to the internet, is that going to be a problem?  I do have access in my building to another comuter with an internet connection.

Please help me, I really don't want to have to resort to using Vista, I haven't heard one good thing about it.

Windows drivers are not needed for Linux, nor can they be used. (Unless you're talking about getting networking to work IF your adapter is not recognized which is a whole different issue).

As far as Internet access goes, no it's not needed but it's probably a bad idea to install a beta version of Ubuntu without the ability to update it. Expect breakage and or bugs.

---

### Post by bartcramer on 2009-04-19
Hi! 

Great that you're trying Ubuntu, welcome! 

From your post, it wasn't entirely clear what you were trying to do, so I might be a tad off here. Were the disks you were trying from your computer's manufacturer? In that case, the programs on those discs will not work, as these programs are Windows-only. If you can say which programs you were trying to install, we can help you to find Ubuntu-counterparts. 

As to your second question: having an Internet connection is handy. The installation of new programs is done with Synaptic, a central piece of software that lets you install all kinds of new programs. It works via the Internet mostly, so if you want to experiment with new software, having an internet connection is indispensable (although there are some workarounds). 

HTH,

Bart.

---

### Post by Irish1 on 2009-04-19
The software I'm trying to run from the disk is "The support DVD that came with the motherboard package contains the drivers, software applications and utilities that you can install to avail all mother board features."  There are AMD Chipset Driver, Realtek Audio Driver, ATI HDMI Driver, AMDVGA Driver, a LAN Driver.  Do I absolutly need to install this disk?  It sounds important.  There are also anti-virus application downloads.  What's a guy to do?  I can hook up to the internet, but then what am I looking for?

---

### Post by Tibuda on 2009-04-19
> **Irish1 said:**
> The software I'm trying to run from the disk is "The support DVD that came with the motherboard package contains the drivers, software applications and utilities that you can install to avail all mother board features."  There are AMD Chipset Driver, Realtek Audio Driver, ATI HDMI Driver, AMDVGA Driver, a LAN Driver.  Do I absolutly need to install this disk?  It sounds important.
No, you don't have to install them. Most hardware drivers are already on the Linux kernel. But don't throw this DVD away. You'll need it later if you want to install Windows in your computer.

> There are also anti-virus application downloads.  What's a guy to do?  I can hook up to the internet, but then what am I looking for?
Installing an anti-virus in Ubuntu would only check for Windows virus in your files. It is used for those mail servers. Hey, why are you worried if your computer won't have an Internet connection?

---

### Post by nandemonai on 2009-04-19
> **Irish1 said:**
> The software I'm trying to run from the disk is "The support DVD that came with the motherboard package contains the drivers, software applications and utilities that you can install to avail all mother board features."  There are AMD Chipset Driver, Realtek Audio Driver, ATI HDMI Driver, AMDVGA Driver, a LAN Driver.  Do I absolutly need to install this disk?  It sounds important.  There are also anti-virus application downloads.  What's a guy to do?  I can hook up to the internet, but then what am I looking for?

No you do not need to install any of that stuff. As stated before that is Windows software.

Drivers on Linux are handled by the kernel and kernel modules. Rarely these days do you need extra drivers.

Anti-virus is also a non issue due to the fact Linux systems are a lot more secure and no real viruses exist as yet for Linux. (Debatable I know but pretty valid in this context).

Here are some links you may find helpful:

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)
[https://help.ubuntu.com/](https://help.ubuntu.com/)
[http://ubuntuguide.org/](http://ubuntuguide.org/)
[http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

Again I'd like to state that you have installed a Beta version of Ubuntu (9.04) and doing so without the ability to update it (ala Internet access) is not a wise thing to do.

All that aside, welcome to the community :)

---

### Post by presence1960 on 2009-04-19
> **Irish1 said:**
> The software I'm trying to run from the disk is "The support DVD that came with the motherboard package contains the drivers, software applications and utilities that you can install to avail all mother board features."  There are AMD Chipset Driver, Realtek Audio Driver, ATI HDMI Driver, AMDVGA Driver, a LAN Driver.  Do I absolutly need to install this disk?  It sounds important.  There are also anti-virus application downloads.  What's a guy to do?  I can hook up to the internet, but then what am I looking for?

Those mobo drivers & software are for windows. They not only will not run in Linux, but aren't needed. The kernel will take care of those things for you so your hardware works. Welcome to the world of Linux. I have a whole bunch of CDs with drivers and software that are useless now. It feels good to be free of all that as well as the other issues that led me to switch to Linux. I like freedom, it is great!

---

### Post by steve101101 on 2009-04-19
dont install a beta b/c it gets updated a lot which requires an Internet connection.

---

