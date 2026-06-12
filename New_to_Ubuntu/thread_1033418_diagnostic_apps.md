---
title: "diagnostic apps"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by sanubie on 2009-01-07
A friend of mine is having problems with his computer. From what I discern, he is using Windows XP. Besides telling him to open DOS and type *Format C* I thought: *Hey maybe Ubuntu can help him somehow.*

_Before I go into everything, does anybody know of any free XP diagnostic tools I can download to bring with me when I go look at his computer? _

Okay, here are my ideas. Let me know if you guys have any others. He tells me he keeps getting errors, and he cannot access the internet. Things keep crashing, etc. You guys have all heard these common problems from Windows users before. Chances are he has viruses, there might be some funky drivers causing chaos, or maybe there is some kind of registry issues. 

Now obviously XP can do a restore, but I'm trying to save his data if possible. That will be one of my last suggestions for him. I could always offer to install Ubuntu as a dual partition. But I have a question about those Live USB drives. Since I've never made a LIVE USB, can anyone tell me a little about it. Do you just need an ISO image? Ubuntu 8.10 even has a utility to make it easy. I'm just curious how to make it work. Is there a place in the BIOS to configure a system to boot from USB before the hard drive? I don't think I've ever seen such an option except for maybe my mini 9series Dell. Will Live USB work in this scenario; for an older PC? I heard Live USB is faster than Live CD. Any help would be greatly appreciated.

---

### Post by cozmicharlie on 2009-01-07
Of course you are on a Ubuntu forum so my advice (and I am sure many will agree) is to save all the important data, wipe XP and install Ubuntu.  However, if you do not want to go to that extreme you can try the following:

It sounds like he has a virus, malware or even a root kit installed.  You will probably need to scan using a good spyware/malware program.  This is "the best" site for free programs available for Windows ([http://www.techsupportalert.com/](http://www.techsupportalert.com/)).  Go to the section on "Security" and also the How To's for instructions on how to clean an infected computer.  Remember though - no matter what you do, _backup first_ (at least the important files he wants to keep).  If it is a root kit, you may be in for a long day/night.  The site I referenced above has info on how to get rid of them but in the end you may have to just save all the important files and reinstall.  Also, a good time to teach your friend about the importance of routine backups.

You can also look at Portable Apps ([http://portableapps.com/)for](http://portableapps.com/)for) programs that will launch from a usb stick.

You can make a live usb drive very easy now in Ubuntu.  you have many options including a package called Unetbootin" ([http://www.ubuntu-eee.com/wiki/index.php5?title=How_to:_Using_Unetbootin](http://www.ubuntu-eee.com/wiki/index.php5?title=How_to:_Using_Unetbootin)).  very easy - yes you will need to download the 8:10 live CD iso (or whatever flavor of Linux you want to use).  

To make it work you hit F2 (or F10 or F12 depending on your computer) right when you turn on the computer and it starts to boot.  It should say on the screen which Fx to use to get to the boot manager or if not go into the bios.  The Bios will have a section on boot devices to use and it will allow you to choose the device to boot from.  It should give you a list of available devices and you should be able to change the order.  In most computers though you should not have to go into bios - you should have an option at start-up to go into a boot manager and choose which device to boot from.  You do have to be sure that the usb device is bootable - most newer usb sticks with at least 1 gb are.

Post back if you have any problems.

good luck!

---

