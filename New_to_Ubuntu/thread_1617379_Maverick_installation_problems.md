---
title: "Maverick installation problems"
date: 2010-11-09
forum: New to Ubuntu
---

### Post by Roger49 on 2010-11-09
Hi, an absolute beginner here. I am attempting to install Maverick 10.10 as a dual-boot on my Lenovo 300 C200. I have the distro which was in Linux magazine. On my first attempt, I clicked on "Install Ubuntu" on boot-up. The system showed me that I was not connected to the Internet. My dongle was in the machine. Everything went smoothly until everything stopped (except the timer symbol), on installing system.
After waiting 30 minutes, I shut the machine down.
Second attempt, I started the live CD, connected to the internet and clicked on the icon. I had to use GParted to sort out some partitions, and mark one of them for root.
Again, the installer stopped on "installing system".
Again, I waited 30 minutes, and switched the machine off.
The machine dual-boots, but I get a "no-entry" symbol at the top of the screen.
There is a prompt in package manager to open a window and run "sudo dpkg -- configure -a".
I've done this. Nothing seems to happen, except that it seems to offer me a choice of options which seem to be unrelated to the problem.
Help Please.
Roger49

---

### Post by mastablasta on 2010-11-09
2 things to check:
 
1. if CD is OK and if everything is on
2. if the stop is actually Ubuntu trying to update before finishing the instalation and it can't because the net is not configured 
 
might be good to know when exaclty everything stops.  because otherwise instalation shoul dbe quite fast.
 
if you have an option you could try and download a new CD (either via torrent or direct download)

---

### Post by oldfred on 2010-11-09
Is the issue that you are not getting on the internet? Did you try using the CD as a liveCD and see if that got on the internet?

Dongles often have extra issues. Is this an older computer that does not have a Ethernet connection? I did have an older computer and a couple of years ago only certain distributions worked with a usb-ethernet dongle. Ubuntu's two year ago version was one that worked but I had so little memory (128MB) that it did not run well.

---

### Post by TBABill on 2010-11-09
If you can plug in to an ethernet port on a router instead of relying on your adapter you may be able to get the machine up and running, then configure the dongle post-install. Many do not automatically become enabled without a proprietary driver being installed so it is easier to plug in first and let the machine complete the installation and run updates. It may then prompt you to install the proprietary driver, if required, or you can take additional steps to get it going. 
 
Posting as much detail as possible here will help identify some issues. I agree with others, this sounds like a bad burn or corrupted iso, which results in a corrupted burn.
 
Booting from the CD to a full (live) desktop is probably best if you are new to Ubuntu so you can try to connect and see how well it works with your hardware. If it will not connect from the liveCD then you likely just need a driver installed after installing the OS. Not a big deal and you can post back here to get help with that.

---

### Post by Roger49 on 2010-11-09
Hi all,
Thanks for the replies.
The internet connection works fine, and I chose the "update while installing?" option.
Country and keyboard selections went well, various files were written from the DVD and downloaded. I was confidently expecting the installation to finish. The progress bar was close to the end, and then no more movement. The internet was still connected, and the little spinning icon was still going - for 30 minutes.
Maybe the image on the DVD was duff.
How would I go about removing all the files and partitions before having another go with a different disc? - I wouldn't want to screw things up even more than they are at the moment!
Regards,
Roger49

---

### Post by candtalan on 2010-11-09
> **mastablasta said:**
> 2 things to check:
1. if CD is OK and if everything is on

+1
and also in this situation, run the CD as a live CD but when initially booting the live cd, hit a key early on when you see some symbols at the bottom of the screen. This will reveal a menu which includes the option to
'check the cd for defects'
This is a cd self check, and one important aspect of this is, it does its work in the *target drive*. So that even if the CD itself is perfect, but the cd drive is a bit sticky, you are likely to see errors listed.
Good luck

---

### Post by Roger49 on 2010-11-10
Evening all,
I think this one can be marked "Solved" now.
I'm using the machine in question, with the Huawei dongle, and the "unmet dependencies" message has gone. Although the original installation stalled, I was able to fix the broken packages and the error message has disappeared. There must have been a syntax error on the first few times I ran "sudo dpkg --configure -a". Once I was able to open Package Manager, and choose "Fix - All - Apply??", many packages were installed, and everything is now rosy.
Many thanks for all your suggestions.
Roger49

---

### Post by Roger49 on 2011-06-11
An update to this thread.
As a result of installing Ubuntu on another machine, it would seem that some DVDs are better than others.
When attempting to install from the *2-sided*  disc I used originally on this second machine, I got absolutely nowhere. It was only when I used a *single-sided* disc that my CD/DVD combo drive operated correctly.
TTFN,
Roger.

---

