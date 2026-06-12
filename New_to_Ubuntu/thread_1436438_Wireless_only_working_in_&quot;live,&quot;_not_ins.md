---
title: "Wireless only working in &quot;live,&quot; not installed version"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by chris_b_shanks on 2010-03-22
I've got something that's really confusing me.  I'm a total noob, but I read a fair bit about Ubuntu before I overwrote my windows.  To make sure it worked, I used the Live run option, and it worked fine on my system.  Everything worked, it notified me, however, to use the internet I'd have to download proprietary drivers (Broadcom B43 wireless driver and Broadcom STA wireless driver).  I did it and my internet started working.  So everything was fine and I rebooted and actually installed the OS.  Once installed, it would not get internet, nor prompt for drivers being required.  So I checked my manual and tried to do it manually: System / Administration / Hardware Drivers.  It searched, and said there were no proprietary drivers.  I thought that this was weird, so I rebooted my system "Live" again (even though it was already installed): and the Drivers were there again!  They only show up in live, I can't get internet in the installed version. What's going on?  How do I get these two drivers to show up on my actual installed copy, not my lie copy?  Help would be greatly appreciated!

thanks for your time and consideration, chris

---

### Post by TBABill on 2010-03-22
I just went through this with my Broadcom wireless. When you run from the CD, it contains that driver you need and works fine. However, when you install it does not automatically install the driver. So when you are installed and not running from the CD, the driver is not available to install. You'd either need to set synaptic to grab it off the CD or just plug into the router and do an update. It'll then prompt (it did for me) you for a proprietary driver and go through the install/activate process. Then you'll need to reboot. Once rebooted, you're all set.

Seems silly to not have a method of grabbing it off the CD during the install process, but at least it's on the CD if you need it.

---

### Post by chris_b_shanks on 2010-03-22
Stupid question: How do I do that?  I'm assuming synaptic is "Ubuntu Software Center", but how do I get it to pull it from the install disk?  (Real noob here...)

---

### Post by chris_b_shanks on 2010-03-22
Nevermind, I found Synaptic Package Manager, and it's giving me an error when I try and mount the disk...

---

### Post by chris_b_shanks on 2010-03-22
Okay.  I've downloaded 3 things from the disk, "Broadcom 802.11 Linus STA wireless driver source" "modailiases for the broadcom 802.11" and "Utility for extracting broadcom 43xx firmware"  What do I do with them:confused::confused:

---

### Post by TBABill on 2010-03-22
Can you just plug directly into your router? That's the easiest way. It'll update and ask you to install the driver so you won't be fighting the CD. Otherwise I think you need to add the CD drive to the repositories listed? I'm not certain on that part because I haven't had to do it. Maybe someone can advise how to add the LiveCD as a source for Synaptic?

---

### Post by chris_b_shanks on 2010-03-22
Thanks so much!  After noodling around a bit with help from someone else i figured out to do what you said but use "software sources" instead of "synaptic"  Thanks for your time!

---

### Post by TBABill on 2010-03-22
Anytime!! Best of luck and welcome to Ubuntu!

---

