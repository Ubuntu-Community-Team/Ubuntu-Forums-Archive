---
title: "Disk Utility app window issue and using sdb drive"
date: 2010-06-30
forum: New to Ubuntu
---

### Post by Guttermouth on 2010-06-30
ASUS eee 901 netbook with built in 4GB & 8GB solid state drives. I dumped Windows XP and last night loaded Ubuntu (reformatting 4GB drive) as a linux only netbook. I have never used linux before (although I have had a tiny bit of unix experience and have poked around the terminal on my Mac.

Installed Netbook version but after updates it now seems to be LTS. Not sure if that makes a difference or not. So...

Two problems/questions...

1) Most windows and applications come up properly sized for my eee 901's screen. However in Disk Utility when I try to look at the properties of the 8GB drive, the window extends beyond the bottom of the screen with no apparent way to scroll down or resize the window, so that I can not see a couple of the options for manipulating the drive. Am I missing something? And if there is nothing I ca do with Disk Utility is there an equivalent app I can replace it with that won't give me this window issue?

2) With this installation I have roughly 900+kB free on the 4GB boot drive, which is more than I had with XP and sees to work fine. However I want to keep it that way so how do I configure the system to install any further applications I download onto the 8GB SSD? Or for that matter any other downloads such as temp files, updates, etc.

Thanks,
Patrick

---

### Post by mikewhatever on 2010-06-30
> **Guttermouth said:**
> ASUS eee 901 netbook with built in 4GB & 8GB solid state drives. I dumped Windows XP and last night loaded Ubuntu (reformatting 4GB drive) as a linux only netbook. I have never used linux before (although I have had a tiny bit of unix experience and have poked around the terminal on my Mac.
Hi there and welcome.
I'll try to answer your question one by one. Here it comes.

> Installed Netbook version but after updates it now seems to be LTS. Not sure if that makes a difference or not. So...
The netbook edition has a modified interface to better suit small netbooks screens. LTS simply is Long Term Support. 10.04 is an LTS, it's supported for 3 years on desktops and 5 on servers, as opposed to 18 months support for non-LTS.



> 1) Most windows and applications come up properly sized for my eee 901's screen. However in Disk Utility when I try to look at the properties of the 8GB drive, the window extends beyond the bottom of the screen with no apparent way to scroll down or resize the window, so that I can not see a couple of the options for manipulating the drive. Am I missing something? And if there is nothing I ca do with Disk Utility is there an equivalent app I can replace it with that won't give me this window issue?[quote]
Some interface windows are still not optimized for small screens, there is a workaround, however. Press ALT key and and drag the window to see the hidden part.

[quote]2) With this installation I have roughly 900+kB free on the 4GB boot drive, which is more than I had with XP and sees to work fine. However I want to keep it that way so how do I configure the system to install any further applications I download onto the 8GB SSD? Or for that matter any other downloads such as temp files, updates, etc.

Thanks,
Patrick
That could have been done at the partitioning stage during the installation, and I am not sure you can do it afterwards. I'd probably have opted to put /home to a separate partition.

---

### Post by Guttermouth on 2010-06-30
> **mikewhatever said:**
> The netbook edition has a modified interface to better suit small netbooks screens. LTS simply is Long Term Support. 10.04 is an LTS, it's supported for 3 years on desktops and 5 on servers, as opposed to 18 months support for non-LTS.

Ah I see. So it sounds like I hvae LTS with the netbook interface, so kind of the best of both worlds (as the netbook interface works for me).


> **mikewhatever said:**
> Some interface windows are still not optimized for small screens, there is a workaround, however. Press ALT key and and drag the window to see the hidden part.

Brilliant! Worked great so solved that issue.


> **mikewhatever said:**
>  That could have been done at the partitioning stage during the installation, and I am not sure you can do it afterwards. I'd probably have opted to put /home to a separate partition.

The system is brand new so not a whole lot of customization, apps downloaded, or personal stuff yet, so I have no problem booting off the USB thumb drive again and reinstalling to fix the partitioning. But it is late now and I am going to bed so tomorrow night I will give it a try. So still time if anyone else has suggestions.

Thanks !!!
Patrick

---

