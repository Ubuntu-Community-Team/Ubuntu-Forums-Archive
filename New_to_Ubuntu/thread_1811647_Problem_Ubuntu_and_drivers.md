---
title: "Problem: Ubuntu and drivers"
date: 2011-07-25
forum: New to Ubuntu
---

### Post by nishant032 on 2011-07-25
I just installed Ubuntu 11.04 on my Acer Aspire 4736Z and I am facing problems with the screen: it's dark, the only refresh frequency that I can set is 60Hz which is quite bad ( I can actually see the screen flashing...) and sometimes when I boot the screen is so dark that it's impossible to use it. I have to turn it off and then on again hoping that the next time it will be fine.

I don't know what to do about it. Where can I find drivers for my integrated Intel video card? Does anyone know how to solve the "dark screen" problem?

please help a newbie!

---

### Post by kaldor on 2011-07-25
I found [_this_]("http://ubuntuforums.org/showthread.php?t=1789447") and [_this_]("http://ubuntuforums.org/showthread.php?t=1354707"). Maybe the steps shown, especially the first link, will help. Let us know. Also, Intel produces only open source graphics drivers for Linux. This means the drivers are always preinstalled and ready to go. Intel drivers are not the issue here.

---

### Post by nishant032 on 2011-07-26
Hello Kaldor
thanks for the reply.

I did what the first and second solution said and now my grub file looks like this

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\"Linux\" acpi_backlight=vendor"

Now the screen is brighter but still i can't change the refresh rate, which is important because i am using the pc many hours a day.

So here is a screenshot of the "Monitors" menu in system settings 

[IMG]http://img215.imageshack.us/img215/8527/snapshotmonitors.jpg[/IMG]

I still have only the 60Hz option. Any hint about that?

Thanks! ps. ubuntu rocks!!!

---

### Post by fdrake on 2011-07-26
i do have an acer aspire one to and i have your same settings, but i do not have the black screen or issue like you do...

---

### Post by Peter09 on 2011-07-26
Check that you do not have an old Xorg.conf file set up. Ubuntu does not need one now, however it will attempt to use one if one exists.
 
check in /etc/X11/ for xorg.conf and if its there do:
 
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.saved
```

---

### Post by mcduck on 2011-07-26
Since that's a laptop, you'll have an LCD display. And those don't usually even support anything higher than 60Hzs. Not that you'd even need higher refresh rates with an LCD display, as the whole image doesn't get redrawn every frame but instead only the parts of the image that actually have changed so you don't get the same kind of flicker as you'd get with a CRT display running at low refresh rate

If you are having graphics problems, it's definitely because of something else than the display's refresh rate.

---

### Post by nishant032 on 2011-07-26
Ok thanks everybody for your replies:

@peter: i don't have such file

@mcduck: I do agree with what you say but I can still see the screen refreshing while looking at it, it's very bad for my eyes especially after few hrs on the pc

Now i have found another issue: if i go away from the pc for 5 mins the screen saver is on. Then after 5 mins the screen goes black. Which is fine. The problem arises when i go back to my pc, I move the mouse and the screen displays the last snapshot of my screensaver but the desktop doesn't show up. There is no way to go back to the normal environment, I have to shut down the pc with the power button :(

Any idea?

---

### Post by mcduck on 2011-07-26
> **nishant032 said:**
> O
@mcduck: I do agree with what you say but I can still see the screen refreshing while looking at it, it's very bad for my eyes especially after few hrs on the pc


Well, I wasn't saying you weren't seeing any alg on the screen. But instead whatever is causing it, it sure isn't the screen's refresh rate. So you shouldn't bother trying to change that, not that it would even be possible as your display won't support anything else than 60Hz anyway. :)

If you see the whole screen flashing, that could be a problem with the backlight. Especially since you seem to already have some problems with the backlight.

For other types of lag, tearing etc. issues, they would most likely be related to graphics card and it's driver, so updating to as new driver version as possible might help.

---

### Post by nishant032 on 2011-07-26
well the effect I see is similar to that you can see on an old  screen when the refresh freq is low. Where do you suggest I should look for update drivers? 

Directly on Intel website or some Ubuntu directory?

---

### Post by Peter09 on 2011-07-26
Just to clarify things can you post the output of:
 
>  
lshw -C video


---

### Post by nishant032 on 2011-07-26
here you go

```
  *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:90000000-903fffff memory:80000000-8fffffff ioport:6120(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:94400000-944fffff

```

---

### Post by Jack Brown on 2011-07-26
time to troubleshoot.

Is screen flickering / 'refreshing' when you are in bios?

Is screen flickering / 'refreshing' when you are in another OS? (windows, other distro / flavor)

---

### Post by Peter09 on 2011-07-26
On the grub command line try the option
 
```
 
NOMODESET

```
 
see how that goes.

---

### Post by nishant032 on 2011-07-26
not in Bios, just when Ubuntu loads (when the purple screen comes up).

to the 2nd question: I only have ubuntu now but previously i had XP and I had no such problem

---

### Post by Peter09 on 2011-07-26
As above try
 
```
NOMODESET
```
on the grub command line

---

### Post by nishant032 on 2011-07-26
I tried nomodeset already, the result is that the resolution is quite low. Flickering still present.

---

### Post by mcduck on 2011-07-26
> **nishant032 said:**
> well the effect I see is similar to that you can see on an old  screen when the refresh freq is low. Where do you suggest I should look for update drivers? 

Directly on Intel website or some Ubuntu directory?
Then that's more likely a problem with the display's backlight and/or power management, or it could be actual hardware problem as well.

In that case updating graphics driver's probably won't help, but if you want to try that anyway Ubuntu's X.org team maintains PPA repositories which might have a newer version of the driver for you graphics card.

[https://launchpad.net/~xorg-edgers/+archive/drivers-only]("https://launchpad.net/~xorg-edgers/+archive/drivers-only")
[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa")

---

### Post by nishant032 on 2011-07-27
I guess it's not an HW problem because if it was so I should have had the same problem running XP, which I used for 2 yrs until 3 days ago, right?

What other things can affect power and backlight management?

---

### Post by nishant032 on 2011-07-27
besides that I can't understand which of the drivers i should install:confused:

---

### Post by nishant032 on 2011-07-29
still nothing?
I still have this back-light problem going on... I wonder if someone out there has a hint for that.:popcorn:

---

### Post by nishant032 on 2011-12-06
bump

---

### Post by Chronon on 2011-12-06
Hi.  What version are you running now?  Have you tried with other LiveCDs to see if they have the same behavior?

---

