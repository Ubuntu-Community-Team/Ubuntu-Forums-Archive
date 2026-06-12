---
title: "Ubutnu 10.10 will not boot from CD"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by Mamacia on 2011-02-15
):P Hello.  Absolute beginner here.  

I downloaded Ubutnu (32 bit), burned the image, checked the hashes, and have tried numerous times to get this thing to boot from the CD.  I have yet to get to the first page.  

It looks like it is starting, with the purple screen, then **everything goes black with the flashing white thing in the upper left corner**.  I have let it sit there for 10 minutes or so, but it does nothing.  I have to unplug the computer and restart the stupid thing to get back into Windows.  

On the last try, I held the space bar while booting, chose English, got to the start page (?) and asked to check disk integrity.  Got the **black screen** once again.

](*,)  Aarg!  I forgot.  When trying Wubi install, I got a "Permission Denied" message, which is in a huge log file which I can attach if needed.  The last install attempt was made directly from the CD without Wubi.

How do I get Ubutnu to even come up on the screen?

And what all do you need to know about my machine?

Toshiba A665D  414 GB free space
AMD quad core processor  1.6 GHz    64 bit
Windows 7 Home Premium

I'd really like to dump Microsoft completely. I've been using OpenOffice for years (loving it) and just threw away that WindowsLive thing in favor of SeaMonkey browser/email client.  Beginning to think Bill Gates is out to get me 8-[

Thanks in advance for any helpful advice.  You have been very brave to have read this to the very end :)
[I]
Oh where have I gone wrong!?  It began many years ago in a land far, far away.
[/I]

---

### Post by grahammechanical on 2011-02-15
When everything goes black except for a flashing white thing in the upper left corner, then you know that you have been dumped at a command line prompt (a DOS box in Windows speak). This is because the CD installer program was unable to determine the optimum setting for your monitor due to issues with your video card. In my opinion.

here is a link that might help

[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

What is the make of your video card?

Regards.

---

### Post by Mamacia on 2011-02-15
Thank you, graham.  It is an ATI, so I'll check the workaround and see if that doesn't fix things for me.

---

### Post by kitsuneclem on 2011-02-15
that happened to me when reinstalling the Buntu
what i did to get the live cd working is typed run disk
loaded up then 
If that doesn't work then im sorry i wasn't able to help

(from one beginner to another)

---

### Post by kitsuneclem on 2011-02-15
also It may be theres an error on your Live cd when running the live cd do a check for cd flaws

also press f6 and enable the stuff in there seems to work for me when I cant get the darn disk to load for me

---

### Post by quadproc on 2011-02-15
> **Mamacia said:**
>  
I downloaded Ubutnu (32 bit), burned the image, checked the hashes, and have tried numerous times to get this thing to boot from the CD.  I have yet to get to the first page.  

It looks like it is starting, with the purple screen, then **everything goes black with the flashing white thing in the upper left corner**.  I have let it sit there for 10 minutes or so, but it does nothing.  I have to unplug the computer and restart the stupid thing to get back into Windows.  

First, a couple of points which are not directly related to the problem: It is hard on a system to power it off to regain control.  It sounds like the system was probably running but was unable to produce video output so you may have been able to use ctrl-alt-bksp to restart the graphics system, or you may have been able to use ctrl-alt-del to reboot.  Alternatively, using the reset button is somewhat kinder than the power switch.

Just out of curiousity, why are using the 32 bit OS when your system is 64 bit?  It should run OK but will be less efficient.

Are you installing Ubuntu directly and not through wubi?  I will assume that you are.

Did you get a short drumroll from the speakers roughly half a minute after the purple screen came up?  If so, this is an indicator that the system wants you to log in.  That brings me to my next question - did you choose to log in normally as opposed to automatic login?  I will assume a normal login.

Did you get a chance to see the grub menu?  This should have appeared shortly after the BIOS finished its standard startup displays.  If you did, then you might succeed by changing the kernel options to be nomodeset.  To make this change, move the grub cursor to another line, then move it to the Ubuntu selection.  Choose edit and replace the text which says "quiet splash" with "nomodeset".  Then allow the boot to proceed.  This will temporarily (for this boot only) disable kernel mode setting; the disablement often allows you to run normally and you can then make the change permanent if you want.

Edit: here is a final thought - which version of ATI graphics are you using?  If you have an ATI legacy card then it will not work with the ATI driver and you will need to use the open source driver but it doesn't sound like you have this problem now.

If none of the above helps then please get back to us with as much additional detail as seems relevant.

quadproc

---

### Post by Mamacia on 2011-02-16
Hey, Quad. Wow, a local! I am on the other side of the hill in Tygh Valley.

I realize it is hard on the machine to unplug in order to reboot, but I tried ctrl-alt-del, and esc, and pressing any key, but nothing worked.  And during the black screen, no lights were blinking, only the power button was lit and the flashing prompt in the upper left corner of the screen.  Nothing happening on any drive.  It would not power off, so I unplugged it.  I did not know about ctrl-alt-bksp - thanks for the tip.

I got the 32 bit because it was "suggested" on the download page.  Decided to grab the 64 bit today, so I've got them both. Will attempt an install of the 64, which is the one I think is preferable on this system.  Thanks.

Actually I got the same results whether using Wubi or not.  I will use the "LiveDisk" next try with the 64 bit, unless someone tells me that Wubi is preferable.

No, I did not get a drumroll.  I did not get to a log-in screen.  I did not see the Grub menu.

ATI Mobility Radeon HD 4200 Series = Display adapter.  
It is a new, within the past 6 months, computer.

---

### Post by kitsuneclem on 2011-02-16
> **Mamacia said:**
> Hey, Quad. Wow, a local! I am on the other side of the hill in Tygh Valley.

I realize it is hard on the machine to unplug in order to reboot, but I tried ctrl-alt-del, and esc, and pressing any key, but nothing worked.  And during the black screen, no lights were blinking, only the power button was lit and the flashing prompt in the upper left corner of the screen.  Nothing happening on any drive.  It would not power off, so I unplugged it.  I did not know about ctrl-alt-bksp - thanks for the tip.

I got the 32 bit because it was "suggested" on the download page.  Decided to grab the 64 bit today, so I've got them both. Will attempt an install of the 64, which is the one I think is preferable on this system.  Thanks.

Actually I got the same results whether using Wubi or not.  I will use the "LiveDisk" next try with the 64 bit, unless someone tells me that Wubi is preferable.

No, I did not get a drumroll.  I did not get to a log-in screen.  I did not see the Grub menu.

ATI Mobility Radeon HD 4200 Series = Display adapter.  
It is a new, within the past 6 months, computer.

Wubi is suggested if you want to try out Ubuntu first and dont want to install a full partisan

---

### Post by Mamacia on 2011-02-16
*do a check for cd flaws* - I tried that and got nowhere but back to the black screen.  AARG!

*press f6 and enable the stuff in there - *In reading the tutorial Graham suggested, it sounds like that's where I'll have to go to fix a Grub.  (isn't that some kind of a worm?)

Thanks, Kits

---

### Post by Mamacia on 2011-02-16
> **kitsuneclem said:**
> Wubi is suggested if you want to try out Ubuntu first and dont want to install a full partisan

Doesn't the LiveDisk offer that option?  'Cause that's how I'd prefer to start

---

### Post by kitsuneclem on 2011-02-16
> **Mamacia said:**
> *do a check for cd flaws* - I tried that and got nowhere but back to the black screen.  AARG!

*press f6 and enable the stuff in there - *In reading the tutorial Graham suggested, it sounds like that's where I'll have to go to fix a Grub.  (isn't that some kind of a worm?)

Thanks, Kits
root grub I believe where all the partisans are but i could be wrong

if you press f6 when on the start spot of the install it will up a menue When im having troubles with the disk switching them all on seems to help but it may be there is many errors on the disk

also when your on that screen try typing in the screen run disk it also seemed to help me get out of that

(ps please dont sue me if it makes it worse these are just things i tiried to do to get the install working my self if a more advanced user thinks this might be worse or better please listen to them over me)

---

### Post by kitsuneclem on 2011-02-16
> **Mamacia said:**
> Doesn't the LiveDisk offer that option?  'Cause that's how I'd prefer to start
yes but run it from inside windows not from the start up also from the ubuntu site you can download the Wubi.exe if you cant get the disk to run

---

### Post by nomomikeysoft on 2011-02-16
[SIZE=2][COLOR=Navy]**Long time listener, first time caller....**[/COLOR][/SIZE] how you doin? ):P

I'm having this same problem trying to do the installation for a friend.  It doesn't matter if it's from CD or from Wubi.

The steps were as easy as 1, 2, 3 on my own older system with a generic video card, however, I am wondering if perhaps the newer video cards may be a cause of this black screen with the blinking prompt.

What I am perplexed about though is why wouldn't Ubuntu default to a generic video card driver just to get things started.

Does anyone know if this is truly a video card issue?

The installation is going on a new system (less than a year old) which has Windows 7 pre-installed as it's primary OS.

As far as I can tell, there is nothing wrong with the CD.

Any additional help would be greatly appreciated, thank you for your time. :p

---

### Post by quadproc on 2011-02-16
> **Mamacia said:**
>   It would not power off, so I unplugged it.  I did not know about ctrl-alt-bksp - thanks for the tip.
Understood.  It was really out of it.  I don't know how your mother board is designed but some of them have an obscure power off feature which you get by holding the power button down for about 5 seconds - this is a bit better than pulling the plug ;)

> 
I got the 32 bit because it was "suggested" on the download page.  I have noticed that wording myself.  I wish that the page maintainer would update that - most CPUs these days are capable of 64 bits and most software works in the 64 bit mode so the wording could say something like "if you have a 64 bit system then select that, if you don't know then select 32 bit".  But recommending 32 bit is a little outdated.
> 
No, I did not get a drumroll.  I did not get to a log-in screen.  I did not see the Grub menu.
That is useful information.  It suggests that something went wrong fairly early in the boot process.  The really unfortunate part is that you have no way of looking into the system log unless you can get that disk into a running system, mount it, and examine the logs.

I suspect that _ssh_ is not part of the install.  If you do have _ssh_ then you can work around the fact that the system of interest does not have any output by using another computer to connect to the one of interest.  Sometimes, the computer is running OK but can't produce any output on its own hardware; in that case, _ssh_ will allow you to poke around inside the problem system.

> 
ATI Mobility Radeon HD 4200 Series = Display adapter.  
It is a new, within the past 6 months, computer.I am not aware of any particular problems with those cards but I could have missed something.  It may be worth searching for your card's model number along with a phrase such as "problem" or "fails" or something similar.

quadproc

---

### Post by Monotoko on 2011-02-16
If it is, as most people suggest, a graphics fault. Try starting out with Ubuntu Server, they are the same essentially but the server edition does not have graphical capabilities, only command line. You can then install a GUI when you get in using:

```
sudo apt-get install Xorg ubuntu-desktop
```

---

### Post by Mamacia on 2011-02-18
> **quadproc said:**
>  you may have been able to use ctrl-alt-bksp to restart the graphics system, or you may have been able to use ctrl-alt-del to reboot.  
**neither worked **but thanks for the power button tip - no more unplugging :)

Just out of curiousity, why are using the 32 bit OS when your system is 64 bit? 
**now attempting the 64 bit install**

Are you installing Ubuntu directly and not through wubi? 
**no wubi**

Did you get a short drumroll from the speakers roughly half a minute after the purple screen came up? 
**no drumroll still**

Did you get a chance to see the grub menu?
[B]still no grub

[/B] If you did, then you might succeed by changing the kernel options to be nomodeset.
[B]I did press F6 to make the nomodeset change and got nothing

[/B]
Edit: here is a final thought - which version of ATI graphics are you using?  If you have an ATI legacy card then it will not work with the ATI driver and you will need to use the open source driver but it doesn't sound like you have this problem now.
**Perhaps I should look into an open source driver?**

If none of the above helps then please get back to us with as much additional detail as seems relevant.

quadproc

I'm just not sure at this poiint that I want to make any changes to my HD.  Found a way to do a USB install.  Has anyone tried that? Any oipinions?

The only additional detail I have to date is:
attempting install of 64 bit OS
still cannot get anywhere but the black prompt screen which takes no prompts.  Even F6 gets me nowhere.

---

### Post by nomomikeysoft on 2011-02-23
*** BUMP ***

Trying to load on a newer laptop.

Once the CD begins to load (the black screen and blinking prompt on upper left), nothing happens after that.  Don't get the purple screen, or installation options.

I strongly believe this has to do with video card and/or video card drivers.

Is there no hope for resolving this problem at the current time?  Even if trying to install from USB?  (Seems you'd run into same problem from USB as you do from LiveCD)

Would an older version (not 10.10) possibly get around this issue?

Any help from the dev's would be greatly appreciated.

---

### Post by Monotoko on 2011-02-23
As I said in a previous post, use the server CD, those do not automatically boot into graphical mode and you can install the graphics once you have figured out the problem.

It will at least tell you that it is the graphics/video card that is causing the issue.

---

