---
title: "New install of 10.04 wifi worked, then quit"
date: 2010-08-20
forum: New to Ubuntu
---

### Post by hiloguy37 on 2010-08-20
On a Dell XPS M1530, I installed Ubuntu 10.04 inside Vista Ultimate.  As soon as the install completed, it found and connected my wireless router!  After lots of wifi issues with other Ubuntu installs in the past, I was SO stoked!  Next time I booted it up, no connection and I have not been able to get it to find any available connections.  Any ideas why it worked straight away and then never again?

Thank you!

---

### Post by mabynke on 2010-08-20
I've had the same problem, sometimes I can connect to networks, and sometimes not. When I try to disable and enable wireless networks, I get the message 'Device not ready'. The only tips I have is to restart your computer a couple of times, and maybe boot into Vista and disable/enable the wireless network card.

---

### Post by moody_mark on 2010-08-20
I was working on a old tosh laptop that showed similar problems. I discovered that the wireless was enabled by a toggle on / off button on the front panel, sometimes I was hitting this button just before or as the machine was booted. If I switched it on once booted it NM would not recognise it.

I found the best way was make sure the thing was switched on (led showing) and then rebooted, if the device was on upon boot wireless worked everytime.

I though this was worth mentioning in case its worth a check

---

### Post by hiloguy37 on 2010-08-22
Thanks for the suggestions!  The switch is on, the wireless works in Vista (this is, for now, a dual-boot), it worked the first time I rebooted into the new 10.04 install and then never again.  so I know it can find the connection.  I checked all sorts of suggestions about making sure the correct driver was installed, jumped through all those hoops, and still nothing. But why would I have to change a drive anyway, if it worked once?

I've gotta say I am very disappointed.  I SO wanted this to work so I can get back into using Ubuntu, and I was SO hoping that since Ubuntu is actually offered on this laptop from Dell, that somehow, somebody could come up with a fix.  It's these things that make people abandon Ubuntu.  I'm pretty tech savvy, had been working with computers from the beginning, but not being able to find ANYONE in the Ubuntu community who can do better than offer yet more guesses about what I might try next, well, that is disappointing.

This should be a simple issue, but apparently is is not, what with the hundreds of posting here addressing wifi issues.  I've even had the suggestion to use one of those pre-historic wireless cards stuck in the side of my state-of-the-art laptop.  All it would take for me to whole-heartedly get back into Ubuntu is to get the wireless working on this laptop.

---

### Post by jonnywombat on 2010-08-22
30 secs on [google]("http://tinyurl.com/36krcek") came up with this....


> Go to bios (F2 at Dell splash screen) on 'Wireless' go to 'Wi-Fi Catcher' and switch it to 'OFF'

HTH

---

### Post by Fableflame on 2010-08-22
I also could not find my wireless network earlier with Ubuntu. 

Jonnywombat: Will what you posted work on any BIOS, or just the BIOS that came with his computer? (I apologize if this is a stupid question, I don't know a whole lot about BIOS)

---

### Post by jonnywombat on 2010-08-22
Hi Fableflame...

The search I did was for the OPs laptop. It would be BIOS specific, but your laptop MAY run a similar or the same BIOS. 

Why not take a look, alter the option if it exists, and if not nothing is lost.

---

### Post by hiloguy37 on 2010-08-22
> **jonnywombat said:**
> 30 secs on [google]("http://tinyurl.com/36krcek") came up with this....

HTH

OK, I tried that (disabled it), no change.  Went back in an enabled it again, no change.

Now what?

When I click on the wifi icon, the "enable wireless" option is grayed out.  Why did it work the first time I booted into the new Ubuntu install?  If it found the connection that time, at least we know ( don't we?) that everything is there to make it work.

Frustrating . . .

---

### Post by blackmail on 2010-08-22
Have you ever tried using the Wireless without network manager, just from command line and disabling the network manager? Anyway this whole network thing is so cryptic on both Win and Linux...

---

### Post by jonnywombat on 2010-08-22
[Did you read the rest of the thread I pointed you to?]("http://ubuntuforums.org/showpost.php?p=5220565&postcount=12")

You need to be running bios version A07 for that fix to work. There is a link to a how to downgrade bios to that should you need to.

Also it says try adding "noacpi" to your kernal options in grub. It may get it working (but also it may disable a processor core). Looking through both options the fix works for some people and not for others.

---

### Post by jonnywombat on 2010-08-22
Having now read a load of threads here and in other places I have found that loads of people having a wide range of experiences from working out of the box, to not working at all.

[This suggests]("http://lists.us.dell.com/pipermail/linux-desktops/2009-November/003323.html") that adding the "noacpi" kernal option is the only consistent method to get it working.

Having now read through the [bug in launchpad]("https://bugs.launchpad.net/dell/+bug/190664") "noacpi" is the only workaround. Unfortunately for you the bug is marked as "won't fix" and is unassigned. 

good luck

---

### Post by hiloguy37 on 2010-08-22
> **blackmail said:**
> Have you ever tried using the Wireless without network manager, just from command line and disabling the network manager? Anyway this whole network thing is so cryptic on both Win and Linux...

No, I haven't, mainly because I am clueless on exactly how I would do that.  I'm still new at this, trying hard to learn it and would love to know just how I would use the wireless network from the command line.

Would that get it to work to the point that Ubuntu would find and make the connection on boot?  I was so happy when my new install of 10.04 found the connection straight away.  I thought, YES!! They have finally figured out this thing!

It still surprises me that as advanced as Ubuntu has become, that there is not one, simple, predictable procedure to get the wireless working on at least the most common laptops on the planet.  And all the comments I read here about how Windoze has similar issues, I have yet to configure a Windoze computer and not have it find the wireless connection.  At least not since XP.

I just want to stick with Ubuntu, but I can't with no wireless connection. That's all it would take for me, and probably for many others!

---

