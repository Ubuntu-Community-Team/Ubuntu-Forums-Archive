---
title: "Ubuntu boots to command line"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by SkyDragon on 2010-12-01
Hey everyone! Hopefully one of you could help me resolve this issue I'm having. I installed Ubuntu the other day, and I'm actually kind of surprised with how much trouble it's been giving me. I've had to reinstall it several times; if I update to the "recommended" graphics drivers, display effects no longer work; and if I let a second finger touch the touchpad, the mouse goes crazy (it should support multitouch, but I would be happy if it just acted normal when I used to fingers).

My real problem now, however, is that whenever I try and boot Ubuntu, it shows the purple "Ubuntu 10.10" screen for a few seconds and then goes into command line. The only way to get the GUI is to boot in recovery mode, then failsafeX, and then select "Restart X." It comes up normally after that, but it's a really inconvenient way to start up. Anybody have any suggestions?

---

### Post by Hippytaff on 2010-12-01
hi and welcome

what graphics card do you have?

---

### Post by SkyDragon on 2010-12-01
It's a Nvidia Geforce GT 335M for an Alienware M11x. Well, actually, it's switchable with an integrated chip, I'm really just assuming that it's using the Nvidia card.

The [Recommended] driver is the NVIDIA accelerated graphics driver, but although it says "if you wish to enable desktop effects, this driver is required," they work fine UNLESS I install the driver.

Thanks.

EDIT:
One more thing - my computer seems to run a little hotter than usual in Ubuntu, too.

EDIT2:
Specifically, "lspci | grep VGA" lists
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
01:00.0 VGA compatible controller: nVidia Corporation GT215 [GeForce GT 335M] (rev a2)

---

### Post by Hippytaff on 2010-12-01
When you get drpped into the command line hit F6 and then Esc to see the boot line
file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
remove quiet splash;
and replace with nomodeset
so it looks like like this:
file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz nomodeset --
press Enter

if this doesn't work post back, if it does, you should be able to install the correct drivers for the nvidia card to fix the problem :-)

---

### Post by SkyDragon on 2010-12-01
After logging in, pressing F6 inserts a "~" and then escape seems to list commands that start with "~", none of which look anything like that. Am I doing something wrong?

---

### Post by Hippytaff on 2010-12-01
sorry, my mistake...try pressing e to be dropped into the grub menu or just typing nomodset :-s

can't remember how you get to edit this from being dumped into cli...hoping someone with more knowledge can jump in here :-)

Though I do believe nomodset will allow you to log in, maybe google it :-)

must sleep :-D

---

### Post by tad1073 on 2010-12-01
at the grub menu press "e" then select the kernel you are using and press "e" again. you should be able to edit from there.

---

### Post by SkyDragon on 2010-12-01
Alright, thanks for your time!

I guess this is the screen you were referring to?
[IMG]http://i54.tinypic.com/wi2d92.jpg[/IMG]

Should I remove the 'quiet splash' part? The 'nomodeset' appears to be there already.

---

### Post by daneforce on 2010-12-01
There are issues with switchable graphics in Ubuntu. I had to disable the switchable option in BIOS and set it to discrete in order for the proprietary NVIDIA drivers to work.

---

### Post by SkyDragon on 2010-12-01
That's pretty inconvenient, because I forgot my BIOS password (I really don't remember even setting it).

---

### Post by sandyd on 2010-12-01
Learn how to compile your own kernel
Check it out.... -> [http://img804.imageshack.us/img804/9523/snapshot4.png](http://img804.imageshack.us/img804/9523/snapshot4.png)

---

### Post by anewguy on 2010-12-01
Well, there are a couple of ways to approach the video thing - if you have 2 adapters, 1 discreet and the other part of the motherboard, and you have forgotten your BIOS password, why not remove the discreet one and try booting/running with the builtin graphics adapter. 

Another option, and one you can try if you get onboard graphics working as well, is to go to the manufacturers web site support section and see if there is anything there, or an ask for help section, that can help you get your BIOS password cleared.  I know how it works on a few machines, but each machine is different and I have never worked with one like yours.

If/once you get the BIOS password cleared, then try putting the discreet video adapter back in and setting the BIOS to reflect that the onboard graphics should be disabled.

Dave ;)

---

### Post by SkyDragon on 2010-12-01
Thanks again for you help guys. I would rather go through the awkward recovery-mode boot than remove my discrete card simply because it's way more powerful, plus I think that might cause some issues [SIZE="1"]when I boot windows[/SIZE] and I would have to open my case. (I've never been much of a hardware guy, unfortunately).

I called support about my BIOS issue before, and they said there was nothing that could be done short of replacing the motherboard, which I'm a little hesitant to believe.

Ubuntu did boot fine when it was first installed; I'm pretty sure it started doing this after I installed all of the updates.

---

### Post by anewguy on 2010-12-02
Well, since it isn't doing any good (apparently), try removing nomodeset from the boot line.  I doubt it will help but it's worth a try.

---

### Post by anewguy on 2010-12-02
> **SkyDragon said:**
> ....might cause some issues when I boot windows 

Does this mean you dual-boot Windows and Ubuntu?  If so, boot up Windows, go into the device manager, check on the display adapters and see if 1 or both are shown as enabled in this profile.  Post back the names, which is enabled, etc..

I think you're going to have a tough time getting around this without access to your BIOS, unless you know which updates may have messed you up.

If worse comes to worse, try logging in to the command line (terminal) window and do the following:

sudo apt-get update <press enter>

Perhaps another update has been posted which might help whatever broke.

---

### Post by SkyDragon on 2010-12-02
I'm dual booting with Windows 7. Both Mobile Intel(R) 4 Series Express Chipset Family and NVIDIA GeForce GT 335M appear to be enabled in the Device Manager. I'll see if removing 'nomodeset' does anything.

---

### Post by SkyDragon on 2010-12-02
And, sure enough, that seems to have fixed it! Thanks, I guess this is solved now.

Is there any reason I should try to install that driver again?

---

### Post by anewguy on 2010-12-02
I'm an ex-systems programmer on large scale, mini and micro (PC) computers, and sometimes there comes a point of diminishing returns.....so, with things as they currently are, are the graphics working as you want?  If so there is probably no need to install the driver.  If not (resolutions, the eye-candy desktop effects, etc., not working) then you could try the driver.  That's just my 2-cents worth.

Glad it at least works now!

Dave ;)

---

