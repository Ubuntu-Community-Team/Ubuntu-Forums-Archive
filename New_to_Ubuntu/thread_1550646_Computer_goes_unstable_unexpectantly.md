---
title: "Computer goes unstable unexpectantly"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by Kafubie on 2010-08-11
I have this old computer that handles Ubuntu and Xubuntu very well.

I don't like the terminal to say this whenever I open the it.
It's too long.
```
nathaniel-desktop@nathaniel-desktop:~$
```


I think changing the host name makes the computer go unstable whenever.  That's what it prompted me with when i changed it.
"Xfce might go unstable"

I changed the host name using these commands.
```
sudo gedit /etc/hosts
sudo gedit /etc/hostname
```

I changed it back as soon I found it was unstable.
I restarted back up and changed it in tty1.  It's good now, but now it still does it if I am doing something.

Like downloading pictures and some normal browsing.

**When the computer goes unstable, it goes like this..**

1. Browsing web, turns black.

2.It shows the [ok] status thing (like if you first start up computer, setting up pulseaudio and cups)

3. Blank screen

4. Black and white screen stripes flashing.

What's up still.  I recently converted the computer to linux, It's fast, but now it's unreliable

_Random specs._
Pentium 4 Brookdale running @ 2.6 ghz (not oc.)
256 megs of P2100 ram.

I just want the computer to work.
What should I do?

And if you have an correct way to change the name, that would be greatly appreciated too.

Thanks 
:frown:

---

### Post by jtarin on 2010-08-11
You say its an old computer...how old? Give us some hardware specs like ...video card.

---

### Post by Kafubie on 2010-08-11
> **jtarin said:**
> You say its an old computer...how old? Give us some hardware specs like ...video card.

It's an Sony Vaio PCV-RS 410
It's not 'old, old'.

-7 Years old.
-LCD monitor
-Intel Integrated graphics
-120GB harddrive
-It has ps/2 ports and 4 usb ports.
-Works with my usb keyboards.
-Can't boot into liveusb
-Floppy Drive
-Has an WLAN card! broadcom 4318 which I got to work by updating repos and installing updates.
-DVD/CD writer and reader
-(whatever i stated ^^^)

If it's the computer hardware then I would be disapointed.

256 mb ram is good, since swap compensates for it.

---

### Post by jtarin on 2010-08-11
Try turning off visual effects. "Start Menu>System>Preferences>Appearance>Visual Effects (Tab)>None".

---

### Post by Kafubie on 2010-08-11
> **jtarin said:**
> Try turning off visual effects. "Start Menu>System>Preferences>Appearance>Visual Effects (Tab)>None".

I don't think that option is available with xfce.
I checked with an GNOME session, it's was off anyways.

But the CPU maxes out whenever I open up a program.  When I open it up, it goes to 100% usage.  That might be something that could be a factor.

---

### Post by Kafubie on 2010-08-12
bump

---

### Post by georgemc on 2010-08-12
OK back to your original post where you want to change the terminal prompt to some thing shorter from:

```

nathaniel-desktop@nathaniel-desktop:~$

``` to say
```

Shell:

```The terminal prompt is the environment variable "PS1" (that is a numeral one and not a small "el"). As I "researched" (i.e. played with) this; I found that it can be set in various places and you need to check and see what will work for you.

Check these files:
<Home Directory>/.bashrc
/etc/bash.bashrc
/etc/profile

If you have a "<Home Directory>/.bashrc" script, change it there, else go to the next on the list and search for "PS1".   My main user for example does not have a ".bashrc" script whereas other users do.  The /etc/bash.bashrc script should change it system wide.  In my .bashrc script its around line 53.   After you modify a file (I use gedit) it should be changed in the new terminals sessions.


Moving to the instability issue.

As far as the instability goes I would reboot and run the memory test to awhile.  I usually run it for 30 minutes to an hour to see if it picks any errors.  If it does then most likely a marginal memory stick.

In any case I would also look first for mechanical things like loose connectors, clogged fans and vents,  in general devices generating heat to much to touch.  I know it sounds very vague and basic however I have experienced that dusted up heat sinks and poorly running fans can make a system marginal and are very hard to trouble shoot.

If you haven't all ready you might want to look into "Lm-sensors" and "smartmontools".  "smartmontools" also has a graphic UI called "gsmartcontrol".  All available in synaptic and see if that helps to pin point any heat related stability issues.  Because of the age of your system these might not yield much useful information.  My laptop is about 9 years old now and all I get is the CPU and HDD temp, where as on the newer desktops all kinds of information is available.

Hope this helps and post back what you found.

George

P.S. I am using Lucid U10.04.1LST and Gnome.

---

