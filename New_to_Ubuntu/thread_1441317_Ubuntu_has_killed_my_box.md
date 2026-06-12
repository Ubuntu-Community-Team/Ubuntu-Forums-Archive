---
title: "Ubuntu has killed my box"
date: 2010-03-28
forum: New to Ubuntu
---

### Post by fly_boy on 2010-03-28
Hi, 

The unthinkable has happened, and I don't know what...

Whenever I boot my box hosting Ubuntu 9.1 Karmic OS, the Ubuntu logo shows and then disappears to a blank, black screen...

I popped the CD back in and selected IDE CD DRIVE form boot selector, and did a memory check which passed OK, I also checked the integrity of the CD and that was OK...

What could be the problem??????

Should I try to install it again? or is my box a total write off?

Entering setup on the bios appears to be OK etc etc...

What am I to do?????:???::???:

---

### Post by roger_1960 on 2010-03-28
Hi

Have you previously installed ubuntu to the hard drive (if so did it ever run?)

OR 

are you trying to run the "Live" CD?

What are your machine specs ie RAM & processor

---

### Post by fly_boy on 2010-03-28
It was installed a complete install, on the hard drive!

Running it form the CD doesn't work either....

I really don't know what to do, 

Is there some way of formatting my hard drive, and restarting????

Alan

---

### Post by fly_boy on 2010-03-28
I will try and find out the spec,, 

I know it has 1GB of RAM, 250 GB hard drive, 2 Mhz Clock Speed etc etc...

---

### Post by new_tolinux on 2010-03-28
Try deleting all partitions with a gparted live disc.
Maybe a Windows CD/DVD also will do the trick.

---

### Post by fly_boy on 2010-03-28
> **new_tolinux said:**
> Try deleting all partitions with a gparted live disc.
Maybe a Windows CD/DVD also will do the trick.

Brilliant, 

How can I do that gparted thing??

Alan

---

### Post by fly_boy on 2010-03-28
Ah right, I am downloading gparted form cnet...

---

### Post by jflaker on 2010-03-28
> **fly_boy said:**
> Brilliant, 

How can I do that gparted thing??

Alan

actually...running the install again and choosing use entire hard disk will do the same thing....removes ALL partitions and creates the necessary partitions for the install....

---

### Post by new_tolinux on 2010-03-28
[http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php) -> Gparted at sourceforge, including a download-page.

I guess after you burned that one and started it, it speaks for itself.

---

### Post by Chronon on 2010-03-28
> **fly_boy said:**
> It was installed a complete install, on the hard drive!

Running it form the CD doesn't work either....


That is a bit troubling.  I wonder if this signifies some hardware failure.

---

### Post by Chronon on 2010-03-28
> **jflaker said:**
> actually...running the install again and choosing use entire hard disk will do the same thing....removes ALL partitions and creates the necessary partitions for the install....

But the troubling thing is that the LiveCD will no longer boot.

---

### Post by halitech on 2010-03-28
at what point does the boot fail? ie. what is the last thing you see on the screen?

---

### Post by fly_boy on 2010-03-28
I see the Ubuntu logo, and then some text appears but just for a moment... Then the black screen of death...

---

### Post by halitech on 2010-03-28
when the machine first boots, there should be an option to enter grub. Hit ESC and select safe mode/recovery mode (not sure on the exact name right now) and see if you can boot to a command line. If that works then the issue is more then likely video drivers. what video card are you using?

---

### Post by a.walker on 2010-03-28
I don't think anything is physically broken on your computer. The first step I would take is to boot from an ubuntu live cd and then select "try ubuntu without installing it". Does everything work from a live session?

If so, connect some external media (an external hard drive or USB thumb disk) to your computer and copy your files off of it. 

You can access your internal hard drive by clicking on "Places" and then "Computer". Your HD should be listed.

If this works, then the next step is to try to enter recovery mode. It could be that there is some problem related to the specific hardware in your computer that was in the version of ubuntu on your CD that has been fixed since its release. What you will want to do is hit the "shift" key during boot. Then select to enter recovery mode.

Once you are in the recovery console, you can run type in the following commands:

```
sudo apt-get update
```and
```
sudo apt-get upgrade
```If this doesn't work, give a detailed account of what happened and we will try to get Ubuntu working for you. Once again, there is probably nothing wrong with the hardware on your computer.

---

### Post by Chronon on 2010-03-28
> **fly_boy said:**
> 
Running it form the CD doesn't work either....


I thought this meant that he couldn't get into a live session.

---

### Post by rory526 on 2010-03-28
Hi,

when you boot up your live CD, press F4 at the screen that asks you if you want to "try Ubuntu without changing your computer" and "Install to computer" etc. This will give you the option of running the live cd in safe-graphics mode.

See does that work.

---

### Post by rory526 on 2010-03-28
also, at the black screen, try pressing CTRL + ALT + F1. This should bring up a terminal.

---

### Post by buckyaustin on 2010-03-28
I had the same problem on my computer your problem is a graphics problem, your drivers aren't actually working.I tried everything too but the graphics driver for me wouldn't work. Use the live cd to back up everything and reinstall Ubuntu, reinstall with the non-live cd for best use.

Good luck.

---

### Post by anewguy on 2010-03-28
Follow halitech's advice.   Also, when you try to boot and the screen goes black, hold down ctrl and alt and press the F1 key.  This should also open a terminal window.  If this works, then as halitech mentioned it is most likely a video driver problem.  At the prompt when the terminal window opens, type:

lspci <press enter>

copy and paste the output back here.

That way we can see what type of video adapter you have and hopefully point you to the correct driver.

Dave ;)

---

### Post by jflaker on 2010-03-28
> **Chronon said:**
> But the troubling thing is that the LiveCD will no longer boot.

Try burning the cd at a lower speed....The cd may be rated for a speed, but not necessarily be integral at the maximum burn speed...I've always burned CDs at much lower speeds and never had issues reading/booting them

---

### Post by a.walker on 2010-03-28
You wrote that you tried various BIOS settings, you might also want to verify that your CD-ROM is listed before your Hard Drive in your boot order in the BIOS. That might be the reason why the CD stopped working.

---

### Post by fly_boy on 2010-03-29
Thanks for all the great responses, I have tried the Ctrl Alt F1 sequence at the black screen to no effect...
 
I will try these suggestions...
 
Thanks
 
A

---

### Post by fly_boy on 2010-03-29
When I boot, i hit f12 and this brings up boot select, the CD Drive is 4th in the list, I select the CD option and press enter..
 
I then get a language selection screen, I choose english and press enter.

---

### Post by k3lt01 on 2010-03-29
> **fly_boy said:**
> When I boot, i hit f12 and this brings up boot select, the CD Drive is 4th in the list, I select the CD option and press enter..Make it 1st

---

### Post by halitech on 2010-03-29
as long as the OP is selecting the cd during boot then it doesn't matter what the order is. The cd is booting and they can select the language and then they get a black screen so the boot order is not an issue.

---

