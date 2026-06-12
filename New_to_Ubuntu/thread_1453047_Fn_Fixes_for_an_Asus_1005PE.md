---
title: "Fn Fixes for an Asus 1005PE"
date: 2010-04-12
forum: New to Ubuntu
---

### Post by theweasel2345 on 2010-04-12
I just installed Ubuntu 10.04 and none of the Fn keys work besides the brightness. This is what I need:
1)Fixes for the random brightness cycling
2)Fix for the Fn keys for sound

---

### Post by dionblundell on 2010-04-18
You need to tell the kernel about ACPI.

     To fix this, edit **/etc/default/grub** as root, and  locate the line starting with **GRUB_CMDLINE_LINUX_DEFAULT**:
so open a terminal and do this
 ```
sudo nano /etc/default/grub
```Find the line:
GRUB_CMDLINE_LINUX_DEFAULT="something"
and change to
GRUB_CMDLINE_LINUX_DEFAULT="something acpi_osi=Linux"

Now save the file:
   CTRL+O
now exit
   CTRL + X
Now you need to update grub
```
sudo grub-mkconfig
sudo update-grub2
```I originally found out how to fix it by reading this:
[http://martinml.com/en/linux-on-asus-eeepc-1005p/](http://martinml.com/en/linux-on-asus-eeepc-1005p/)

---

### Post by anemptygun on 2010-05-25
Does this fix the fn sound keys as well? Your source for the response had no mention of sound fixes...

Thanks :)

---

### Post by dionblundell on 2010-05-26
I don't know, all I can tell you is the sound keys work for me. My issue was with screen brightness, and maybe in fixing that, I stumbled across another issue I didn't know about?

---

### Post by anemptygun on 2010-05-26
Hmmm odd. On the default installation of 64 bit 10.04 my Fn brightness keys function normally but my sound keys do not. Maybe I will try this and see if it fixes the issue. Surprisingly this is the only issue I had on a default installation (yay!).

---

### Post by dionblundell on 2010-05-26
I upgraded by BIOS to 1103, and noticed that the screen brightness worked better, then it started to play-up again, so I changed back to acpi_osi=Linux

Incidentally, the issue with the nrightness was that ASUS don't follow industry standards with their BIOS, and you shouldn't have to set OSI. Sigh.

Maybe they've fixed it?

---

### Post by anemptygun on 2010-05-26
I updated my BIOS before I did my install so maybe that is what prevented the brightness errors. I believe it was the 1103 version.

Anyone else out there experiencing problems with the Fn sound keys?

---

### Post by dionblundell on 2010-05-30
Okay, I can confirm this:
1) with out acpi_osi=Linux
   a) brightness control works in a chunky but linear fashion
   b) brightness on-screen-display OSD works
   c) mute does NOT work
   d) vol -/+ do NOT work

2) with acpi_osi=Linux in the boot line
   a) brightness works in a smooth and linear fashion
   b) OSD does NOT work
   c) vol mute works
   d) vol -/+ work

---

### Post by ndrbvl on 2010-06-01
Try to add the option "acpi_backlight=vendor" as well, such that you'll get

GRUB_CMDLINE_LINUX_DEFAULT="something acpi_osi=Linux acpi_backlight=vendor"

Talking about Fn issues, have you guys experienced that turning on/off the WiFi with Fn-F2 also enables/disables the ethernet? Any fix for that?

---

### Post by anemptygun on 2010-06-01
I ended up adding the acpi_osi=Linux line and this **did** resolve my issues! :) What will the extra vendor line provide?

---

### Post by ndrbvl on 2010-06-01
The vendor line fixes the brightness OSD, or at least that worked for me. I updated the bios some months ago, I have the 0804 version; don't know if it makes any difference.

Any suggestion on the Fn-F2 issue?

---

### Post by dionblundell on 2010-06-01
That BIOS is very old (Feb 2010). I have never had any issues with enabling/disabling the wireless (I assume that is what Fn+F2 does on yours?)

You can go here and check for the latest version:
[http://support.asus.com/download/download.aspx?SLanguage=en-us](http://support.asus.com/download/download.aspx?SLanguage=en-us)

Select: Eee Family / Eee PC / Eee PC 1005PE

The latest version is 1104

This is a direct download link.
[http://dlcdnet.asus.com/pub/ASUS/EeePC/1005P/1005P-ASUS-1103.zip](http://dlcdnet.asus.com/pub/ASUS/EeePC/1005P/1005P-ASUS-1103.zip)

I make the assumption that you still have windows 7 on?
Then run Asus Updater and specify the file you extract from this zip file.

---

### Post by anemptygun on 2010-06-02
Yes, the vendor line was useful as well. Thank you for the suggestion.

---

### Post by ndrbvl on 2010-06-03
@[anemptygun]("http://ubuntuforums.org/member.php?u=380663"): glad that it was useful

@[dionblundell]("http://ubuntuforums.org/member.php?u=818803"): thanks for the suggestion. I updated the bios to the latest version (btw wiping off windows 7 was the first thing I did when I bought the 1005pe...), but unfortunately that did not solve the problem . The issue is not with the wireless itself (which works fine), but with the ethernet. In order to connect to the ethernet (wired connection), I have to switch the wireless on via Fn-F2. In other terms, the Fn-F2 combination switches on/off the ethernet besides the wifi, which is undesired.

---

### Post by formaldehyde_spoon on 2010-06-03
Thanks very much guys!

GRUB_CMDLINE_LINUX_DEFAULT="something acpi_osi=Linux acpi_backlight=vendor"
fixed my flickering brightness and function keys.

Off topic, what is your power consumption reported by powertop (in the repositories) when the computer is just sitting idle, with screen on and only running powertop in a terminal window in Gnome?

Mine is anywhere from 5.3W to 6.0W, depending on what mood the computer is in (?), just wondering if anyone has got theirs lower, and so has some power saving tips to share?

---

### Post by formaldehyde_spoon on 2010-06-03
Hmm, I spoke too soon; out of the frying pan, into the fire.

Brightness control is all very smooth now, but whenever my screen dims after inactivity (which happens even if I turn it off in Power Management!) it won't automatically brighten when I move the mouse, I have to manually brighten it with the function keys.

Does anyone have a fix for this?  The flickering was a little annoying, but I'm starting to miss it... ;)

---

### Post by dionblundell on 2010-06-03
@formaldehyde_spoon
The problem is the bit you added:
acpi_backlight=vendor

I have read that you SHOULD add this, but it has always created issues for me, it has never solved anything, at least not on a 1005pe and from memory the original source of the suggestion was in 2005 to do with a ACER netbook or similar. Try without, and see what happens. The issue with power saving means you have to manually change the settings for power management in gconf. It's a hassle but the only way I've found.

@ndrbvl
The issue with wireless and wired being turned on and off at the same time is a long time gripe. My understanding is that it relates to the way the kernel handles it. On investigation, I couldn't see it being fixed anytime soon, I did come across a bug report on his at one stage, and it ended up being classified as "wish-list" so very unlikely to be solved.

---

### Post by gmargo on 2010-06-03
Is there a convenient list of what all the Fn- combinations mean?  Like the others, some things work (like brightness) and some don't (like volume, but I haven't tried the acpi change yet) but I've no clue what some of these symbols mean.  Like the "running man" on the space bar. (Apologies if you don't have a "running man" - I just got an Asus 1201t but assume the keyboard is the same or close.)

Update: Darn, should have researched more.  The list is in the user manual.  (FYI, the "running man" is the "Super Hybrid Engine", whatever that is.)

---

### Post by wqtty on 2010-10-23
im on ubuntu 10.10 and got the brightness problem as well.
i googled for a while and finally i decide to update my bois from 0804 to 1202,and the issue is gone!
hope this will help

---

### Post by wqtty on 2010-10-23
bad news:
i get the bios to 1202 and the fn+f2 doesnt work any more,which means i can't turn on/off wifi within ubuntu.
anyone knows something?

---

### Post by wqtty on 2010-11-04
news:
 
i added acpi_osi="Linux" acpi_backlight=vendor and the backlight control is just fine.
but Fn+F2 doesnt work any more.
 
if i remove  acpi_osi="Linux" acpi_backlight=vendor ,Fn+F2 will work.
but if i boot ubuntu with wifi off,when i turn wifi on in ubuntu with Fn+F2,the system can setup connection with wifi.
 
any ideas?

---

### Post by dionblundell on 2010-11-08
Have you tried with just:
acpi_osi="Linux"

I find this makes my backlight work okay, and wireless [Fn]+[F2] then works for me

---

### Post by zapaces on 2010-11-25
Hi there,
I've had my Eee PC 1005pe for 5 months now. When I first got it the first thing I did was to get rid of stinky Win7. Now I regret a bit (you will see why). I installed then Linux Mint and worked great. But since then, I've tried different ubuntu-based distros. I ended up installing Ubuntu 10.10 (Desktop Edition). I find it great, love the colors, the font, everything.
The only problem seems that the new Maverick (10.10) doesn't get along with my BIOS as well as Lucid (10.04) did.
Ever since I upgraded to Maverick I've had problems with Fn keys.

[LIST]
[*]Adding the mentioned appendix to the grub line
 ```
sudo gedit /etc/default/grub
```
then making look the line like: ```
 GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi_osi=Linux acpi_backlight=vendor splash"
```, then updating grub ```
sudo grub-mkconfig
sudo update-grub2
```fixes the problems of brightness, but I still have to fix the problem of Fn+F2 (Wireless) and Fn+F3 (Touchpad), none of which work at all.

[*]Volume Keys work great (F10, F11, F12), same as external monitor (F8) and sleep (F1). 

[*]F4, F7 and F9 don't work and don't know what are they for.

[*]I just tried something that I didn't believe that would work.... I changed "Linux" in the lines added to grub conf to "linux" (non-capital L).... now Fn+F2 work, then I can turn off wireless when not using it. I find this extremely  moody and not reliable. I don't think there's an explanation to it. Now it looks like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi_osi=linux acpi_backlight=vendor splash"
```. 

[*]It's important to mention that this last days trying to solve stuff I've been using ```
sudo grub-mkconfig
``` before updating grub ```
sudo update-grub2
```. I don't know what is the technical reason but somehow there's a different result (wireless Fn+F2 working now)

[*]I'm still wondering about the Touchpad stuff... 

[*]I've read that updating the BIOS could be a solution for this matters. I'm not fond of doing this, but I tried nonetheless. And I couldn't. It seems that no all pendrives work. Mine didn't.

[*]Trying to update BIOS with flashrom didn't work, I got:
```
Calibrating delay loop... OK.
No coreboot table found.
Found chipset "Intel NM10", enabling flash write... OK.
This chipset supports the following protocols: FWH.
No EEPROM/flash device found.
Note: flashrom can never write if the flash chip isn't found automatically.

```
And I'm a bit lost there...

[*]Cd is clearly not an option, since i don't use CDs at all (eeepc and mp3, no cd's at home, ... not to mention floppy disks)

[*]Had I kept Win7 (or even the backup which flew away weeks later the working version) I would be able to update the BIOS from Win7... I just hate the idea of it. 
[/LIST]

Well, just to let you know... any feedback would be greatly appreciated and I must say that it IS a bit frustrating updating the system to Maverick (great name, BTW) and having some things that previously worked not working... dunno, what do you think?.

(well, it seems I'm inspired today, g'day to y'all).

---

### Post by dionblundell on 2010-11-27
Must admit I've just gone back to 10.04 because of Fn+F2 not working.

I have also had huge problems with sleeping, where it seems to either lock up, or something weird happens with the monitor when I come out of sleep. I use sleep alot.

Fn+F3 doesn't "work" because of the mouse, turn off the option "turn touchpad off while typing" in mouse properties and Fn+F3 will work.

Fn+F4 is a screen stretch thing (never actually used it)
Fn+F7 is a blank screen thing (I've added some scripts to do this)
Fn+F9 is meant to bring up task manager (I've re-mapped it to change the scalling governor)

---

### Post by zapaces on 2010-12-03
Downgraded to 10.04. Everything works great.

---

### Post by ressaw on 2011-02-26
Ok. So, sorry to revive this thread, but a long time ago I tried to install 10.10 on my 1005PE and after the fn + f2 trouble I went back to 10.04, 

Because there are no new replies since November I would like to know if someone was able to find a solution. Or maybe I will have to wait until 11.04 appears?

Thanks

---

### Post by zapaces on 2011-02-26
As said before, the best solution was to downgrade to 10.04 and stay there. I think i will stick with LTS releases, because the Eeepc seems to dislike constant changes. Haha, sorry for the personification but since I disabled upgrades, the fella is working great. I just run security upgrades once in a while.  Good luck and cheers.

---

### Post by dionblundell on 2011-02-26
I have never got 10.10 working right, and Fn+F2 does not work. One thing 10.10 does better than 10.04 LTS is hotswap monitors, and resume from sleep and the detection of monitors. 10.10 seems a bit broken, but I've lived with it for a few months now.

---

### Post by ankanaan on 2011-09-24
I got a 1201T asus eee pc.

Ubuntu 10.04/3

If I add acpi_osi=Linux to my grub file the sound keys Fn+F10-12 work, however, my video (fn f7 turns video off, f5-f6 dim/bright) keys stop working :-(

And fn f8 never works.

cheers,

Antonio

---

### Post by dionblundell on 2011-09-25
> **ankanaan said:**
> If I add acpi_osi=Linux to my grub file the sound keys Fn+F10-12 work, however, my video (fn f7 turns video off, f5-f6 dim/bright) keys stop working :-(
My brightness on a ASUS 1005PE does not work until I add acpi_osi=Linux
I suspect that your 1201 needs something different. Why are you adding acpi_osi=Linux? What are you trying to get to work>

---

