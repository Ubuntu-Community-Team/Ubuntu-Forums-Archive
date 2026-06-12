---
title: "everything CRASHED"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by dubboi on 2009-12-28
ok

i managed to burn the image to cd and it rebooted  onto my pc
was working for maybe 5mins 
 

now its just crashed EVERYTHING 
i can get a single thing to work at all
i just have a dark grey screen

no keys work ,i cant eject the cd
a big fat zero!!!!!!!!!!!

iv had to unplug it at the wall to turn it off
when i plugged it back in again i had to quickly eject the cd(as i turned it on once and it just went straight to grey screen and froze the whole thing again)

then all the windows went all to cok the display screen was all about 100mm to the left and i had to do a system restore for it all to work again

i was recomended this ubuntu by a friend and now im wondering if it gonna do more damage than good!!!!!

any answers?

id still like to use it but i dont wanna have to keep unplugging it  or have it damage my pc

---

### Post by brad_c6 on 2009-12-28
"i managed to burn the image to cd and it rebooted onto my pc
was working for maybe 5mins "

What version of Ubuntu are you using?
Can you give me a Model, or specs of your computer?

"now its just crashed EVERYTHING
i can get a single thing to work at all
i just have a dark grey screen"

Do you get to GRUB? (Where you select are OS you want to use.)

Cheers

---

### Post by dubboi on 2009-12-28
Do you get to GRUB? (Where you select are OS you want to use.)

Cheers[/quote]
i installed  9.10
comp is a hp slimline3230

sorry  complete noob  so dunno what GRUB is:confused:

---

### Post by mörgæs on 2009-12-28
Do you have anything of value on the pc? If not, then a clean install of 9.04 would be a quick solutuion. Remember to select 'use the entire disk for the installation' (or similar) in the process.

---

### Post by dzon65 on 2009-12-28
Is the iso burned at low speed?

---

### Post by scratman on 2009-12-28
It sounds like OP is trying to run a Live CD, but it has failed and hung his system.  He has then unplugged the base unit, plugged it back in, and now has issues booting.  I also get the impression that he has another OS installed.  My advice would be to leave the base unit alone for 5-10 minutes, then try booting again into the Operating System already installed again, see if that works.  If so, check the MD5 sum of the Ubuntu Image you are using against those provided on the Ubuntu website.  I suspect that the Ubuntu disc you burnt may have an error.  Bump for dzon65, always burn an operating system image at the slowest speed that your machine will allow you to, and run the a check afterwards.

Hope that helps.

---

### Post by kansasnoob on 2009-12-28
Sounds to me like X froze. It's certainly smart to check the integrity of the Live CD but hardware compatibility could be an issue.

I assume you still have Windows running so I'd use it to find out the specific graphics card info or you could use HP's tools to find hardware info if it's still stock:

[http://h10025.www1.hp.com/ewfrf/wc/siteHome?lc=en&dlc=en&cc=us&lang=en&product=top](http://h10025.www1.hp.com/ewfrf/wc/siteHome?lc=en&dlc=en&cc=us&lang=en&product=top)

Also, why pull the plug?

If Ubuntu freezes always try this first:

[http://kember.net/articles/231/reisub-the-gentle-linux-restart](http://kember.net/articles/231/reisub-the-gentle-linux-restart)

Then the power button!

Most importantly slow down! If you have Windows running take some time to check out system specs, etc, etc.

---

### Post by sandyd on 2009-12-28
ive taken the effort to google, and it seems that on many hp slimlines, there is some kind of conflict between X and the onboard video card.

perhaps try starting in safe graphics mode?

---

### Post by dubboi on 2009-12-28
> **kansasnoob said:**
> Sounds to me like X froze. It's certainly smart to check the integrity of the Live CD but hardware compatibility could be an issue.

I assume you still have Windows running so I'd use it to find out the specific graphics card info or you could use HP's tools to find hardware info if it's still stock:

[http://h10025.www1.hp.com/ewfrf/wc/siteHome?lc=en&dlc=en&cc=us&lang=en&product=top](http://h10025.www1.hp.com/ewfrf/wc/siteHome?lc=en&dlc=en&cc=us&lang=en&product=top)

Also, why pull the plug?

If Ubuntu freezes always try this first:

[http://kember.net/articles/231/reisub-the-gentle-linux-restart](http://kember.net/articles/231/reisub-the-gentle-linux-restart)

Then the power button!

Most importantly slow down! If you have Windows running take some time to check out system specs, etc, etc.



thanks,,

i had to pull the plug cos as i said b4" NOTHINING WORKED"

NOT EVEN THE POWER OFF 


absolutely nothing on the whole computer would work

it was just a dark grey screen

no keys worked at all not even alt delete  nothing nada siltch

windows is working again now cos after i unplugged and restarted i did a system restore


so how do i find out  which graphic card i have on it?


thanks for the advice btw  im sorry but im no computer techy  ,,,,,,,,,,,,,  im a carpenter  hahaha

---

### Post by dubboi on 2009-12-29
would i be better off trying to load an older version ?
or maybe get a cd from the website and then try again?

---

### Post by lotharmat on 2009-12-29
This has been insinuated in an earlier post but; Have you been able to use the live CD as 'Try Ubuntu without making any changes to my system'?

---

### Post by dubboi on 2009-12-29
> **lotharmat said:**
> This has been insinuated in an earlier post but; Have you been able to use the live CD as 'Try Ubuntu without making any changes to my system'?


no i dont think  there was  that option

---

### Post by mörgæs on 2009-12-29
> **dubboi said:**
> would i be better off trying to load an older version ?
or maybe get a cd from the website and then try again?

Ordering a cd from the website could take a while. I would just burn 9.04 from an ISO at slow speed and try again.

---

### Post by t1nm@n on 2009-12-29
dude the same thing happened to me..i guess u too are using a reolution of more than 1440x900 (widescreen)

after u booted on to the  cd boot menu hit F4 and change the mode to "Safegraphics mode"
and then highlight install ubuntu and start the install ..

the problem was that karmic comes with the latest Xorg which automatically detects the screen for best resolution.. if no driver module is included in the cd bam its all over.
cheers

---

### Post by margazhang on 2009-12-29
Do not panic, it was an known issue with HP and some of the Compaq computers. Basically, you need to install NVIDIA drivers before installing Ubuntu.

What you saw was simply that you were running from your Ubuntu live CD without altering anything - so it did not change anything to your computer. But you did not know this so had to unplug the power to stop this process. When you replugged the power and rebooted, it rebooted from the CD again - you set it that way from the BIOS so that you could start the installation process - thus this blank screen process repeated again and again.

Instead of unplugging the power, you just press the power button down long enough, e.g. 30 seconds, to turn off the computer.

Right now I have to find for you how to install NVIDIA drivers before going through the default Ubuntu installation process. I did it once following instructions given by others - I have to find where.

---

### Post by margazhang on 2009-12-29
OK, found it. The solution was posted here:

[http://ubuntuforums.org/showthread.php?p=8448809](http://ubuntuforums.org/showthread.php?p=8448809)

but for you as someone new to Ubuntu, I show all the processes step by step below...

(1) Boot from Ubuntu live CD

(2) Depending on what type of Ubuntu live CD you use (Ubuntu, Kubuntu, Edubuntu, Ubuntu Studio, etc.) you pick an option that allows you to run it in Recovery mode and then pick to run from the **command line with networking** (you need to have a wired internet connection). I would recommend [Linux Mint (GNOME)](www.linuxmint.com) or [Kubuntu (KDE)](www.kubuntu.org) live CD as it looks and function similar to Windows and Mac.

(3) Now post the following at the command line prompt:

```
sudo apt-get install envyng-core envyng-qt
```

this command allows you to download and install an utility called EnvyNG.

(4) After download and installation are complete, run this EnvyNG by issuing this command:

```
envyng -t
```

(5) This will guide you to select and install the correct NVIDIA driver.

(6) After the above process is finished, reboot from the CD and choose to install normally.

That's it!

---

### Post by dubboi on 2009-12-30
> **margazhang said:**
> OK, found it. The solution was posted here:

[http://ubuntuforums.org/showthread.php?p=8448809](http://ubuntuforums.org/showthread.php?p=8448809)

but for you as someone new to Ubuntu, I show all the processes step by step below...

(1) Boot from Ubuntu live CD

(2) Depending on what type of Ubuntu live CD you use (Ubuntu, Kubuntu, Edubuntu, Ubuntu Studio, etc.) you pick an option that allows you to run it in Recovery mode and then pick to run from the **command line with networking** (you need to have a wired internet connection). I would recommend Kubuntu live CD as it looks and function similar to Windows and Mac - get it from [www.kubuntu.org]("http://www.kubuntu.org")

(3) Now post the following at the command line prompt:

```
sudo apt-get install envyng-core envyng-qt
```this command allows you to download and install an utility called EnvyNG.

(4) After download and installation are complete, run this EnvyNG by issuing this command:

```
envyng -t
```(5) This will guide you to select and install the correct NVIDIA driver.

(6) After the above process is finished, reboot from the CD and choose to install normally.

That's it!



thank you very much buddy il try this out 

cheers

---

### Post by dubboi on 2009-12-30
> **mörgæs said:**
> Ordering a cd from the website could take a while. I would just burn 9.04 from an ISO at slow speed and try again.


thanks but iv tried to get the 9.04 but it always just redirects me straight back to new one



where can i get it from??

---

### Post by margazhang on 2009-12-31
If it was simply a NVIDIA driver issue, you do not need to download 9.04 - 9.10 is OK to install just you have to boot to the Recovery mode first to install EnvyNG and then run the rest of the installation procedures.

---

### Post by mörgæs on 2010-01-04
> **dubboi said:**
> thanks but iv tried to get the 9.04 but it always just redirects me straight back to new one



where can i get it from??


[http://releases.ubuntu.com/9.04/](http://releases.ubuntu.com/9.04/)

---

