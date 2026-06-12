---
title: "Hang on Ndiswrapper command (Modprobe)"
date: 2007-12-04
forum: Networking &amp; Wireless
---

### Post by FlyinRedneck on 2007-12-04
This is not the fatal error. 
What happens is after i plug in the command

sudo modprobe ndiswrapper

it sorta hangs and never loads.

This NEVER happened to me before, it worked well in feisty.

Someone tell me what is wrong.

---

### Post by raul_ on 2007-12-04
did you run "sudo depmod -a" first?

to be honest I have no idea what it does, but in the wiki page it says that if this step fails, you can't load the module

---

### Post by FlyinRedneck on 2007-12-04
i have already done that and it returned no errors... as i said i have done this many times before.. untill i started using gutsy.

---

### Post by raul_ on 2007-12-04
[http://ubuntuforums.org/showthread.php?t=28017]("http://ubuntuforums.org/showthread.php?t=28017")

A long shot, but i'm no expert. Sorry :(

---

### Post by FlyinRedneck on 2007-12-04
I am not using a notebook computer. I am using an old 2001 custom built desktop. My wireless device is a netgear WPN111 usb dongle. So this aproach is completely useless to me though. Thanx for trying to help though. I wish i would get some more suggestions from other people.

---

### Post by kevdog on 2007-12-04
What does ndiswrapper -l show?!

---

### Post by FlyinRedneck on 2007-12-04
I did that as well, It said that the two drivers were installed (I am not posting code because i dont feel like booting just to see it) and the device was present.

---

### Post by kevdog on 2007-12-05
Cant have two devices installed -- by the way -- thanks for the attitude, it was much appreciated.

---

### Post by rustybronco on 2007-12-05
> **FlyinRedneck said:**
> I did that as well, It said that the two drivers were installed (I am not posting code because i dont feel like booting just to see it) and the device was present. Of the handful of people that are truly capable of helping you on this forum, Kevdog is one of them. sounds like you may have shot your self in the foot.

---

### Post by HokeyFry on 2007-12-05
I am having this exact same problem on a friend of mine's laptop. I'm going to uninstall ndiswrapper and then install from source since he and I have the same laptop and the only difference is that I did a source install. I will post whether or not this works, but it will have to wait until tomorrow.

But did you blacklist the native linux driver?

---

### Post by HokeyFry on 2007-12-05
also, dont add "ndiswrapper" to your "/etc/modules" file if anyone tells you too, because if it is the same problem I am having (and it sounds like it) it will be a pain in the [butt] to change your modules file back.

---

### Post by kevdog on 2007-12-05
???

gksu gedit /etc/modules


Delete the line that states ndiswrapper
Done!

Is this hard?

---

### Post by HokeyFry on 2007-12-05
no, but the kernel panic that hangs my friend's system when it loads makes it a tad tricky to access the file.

---

### Post by Erwin Criddle on 2008-03-05
This is a common problem within the Ubuntu repositories. The ndiswrapper package is broken. The only solution is to compile ndiswrapper by hand.
Remove ndiswrapper and then follow this tutorial: [http://ubuntuforums.org/showthread.php?t=652910]("http://ubuntuforums.org/showthread.php?t=652910")

---

