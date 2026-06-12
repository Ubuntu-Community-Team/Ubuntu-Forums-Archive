---
title: "desktop locking up"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by x0prah_Winfr3yx on 2008-12-18
Hello all, for those who have helped me this week know that i'm having issues, now it's getting out of hand.

my desktop has been 'locking up'. 

i'm not running any more than three applications, this instance is 'firefox, evolution mail, and an ftp'. last night it was the music player, firefox, and apache'. my cpu monitor is saying the processes are running around 20-30 percent

this problem has happened three times now, all since updating my video card's driver (geforce 8200 to version 180). that update didn't help my issues with the graphical 'lag' i was experiencing either.

i have a brand new system, Acer with 4gb of ram, triple core processor (64 bit) and i'm running the latest version of Ubuntu.

-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=

i should also point out that this desktop has had all kinds of problems. sometimes it'll boot fine, sometimes it hangs, sometimes it goes into 'terminal mode' and won't boot, just gives me a terminal prompt.

also, during every boot i'm given a warning that states:

[B]> Aperture pointing to e820 RAM. ignoring
Your BIOS doesn't leave a aperture memory hole
Please enable the IOMMU option in the BIOS setup
This cost you 64mb of RAM
Not responding[/B]

it'll either hang or load from there on out.

---

### Post by ibuclaw on 2008-12-18
Woah, that is serious... you have better specs that my old AthlonXP machine, and that still performs like a dream.

Have you posted quite a bit of info in your previous posts about the issue?

If so, I'll review them now and try to come up with a possible cause.

As it seems at the moment, your hardware should be more than capable as is.

Regards
Iain

---

### Post by x0prah_Winfr3yx on 2008-12-18
[click here]("http://ubuntuforums.org/showthread.php?t=1013915&highlight=x0prah_Winfr3yx")

there's a link to my forum about my video card. it's been downhill since.

---

### Post by Izek on 2008-12-18
> Aperture pointing to e820 RAM. ignoring
Your BIOS doesn't leave a aperture memory hole
Please enable the IOMMU option in the BIOS setup
This cost you 64mb of RAM

Try this: [Click Here](http://ubuntuforums.org/showpost.php?p=6363181&postcount=7)

---

### Post by ibuclaw on 2008-12-18
Yeah, definitely looks like the graphics driver/card is ruining your experience for you.

There is alot of bad comments here on it: [http://www.nvnews.net/vbulletin/showthread.php?t=115916](http://www.nvnews.net/vbulletin/showthread.php?t=115916)
With some possible solutions/workarounds that may not work.

Have you tried switching to the newest beta drivers ?

Regards
Iain

---

### Post by x0prah_Winfr3yx on 2008-12-18
> **Izek said:**
> Try this: [Click Here](http://ubuntuforums.org/showpost.php?p=6363181&postcount=7)

great! that part has been fixed.

now if anyone has any ideas why my desktop is locking up?!?

---

### Post by donkyhotay on 2008-12-18
When it locks up are you still able to ctrl-alt-f# to a terminal or does it look up to a point you can't do that?

---

### Post by ibuclaw on 2008-12-18
If it's to do with GUI locking up, then it will be your graphic card drivers.

This won't fix the overall problem, but may help lessen the extremity of your current situation with the drivers.
Run in a terminal:
```
sudo gedit /etc/X11/xorg.conf
```
Enter your password and scroll down the opened file to find something that looks like the following:
```
Section "Device"
    Identifier  "Configured Video Device"
    Driver  "nvidia"
    Option  "NoLogo"    "True"
EndSection

```
Now add the following two lines to it, so it now looks similar to this:
```
Section "Device"
    Identifier  "Configured Video Device"
    Driver  "nvidia"
    Option  "NoLogo"    "True"
[B]    Option  "InitialPixmapPlacement" "2"
    Option  "GlyphCache" "1"[/B]
EndSection

```
And save and quit. Then restart your computer.

Also, I noticed that you have a multi-core processor too.
Again, this will probably not help with fixing the overall problem, but I've found the application irqbalance to be a nifty little background process tool to handle the even distribution of IRQ processes across all cores on computers. (whereas usually, they are only sent to the first)
```
sudo apt-get install irqbalance
```

Regards
Iain

---

### Post by probin51 on 2008-12-21
Hi There!

I had the same problem. I solved it... by moving home!!!

Well, not quite, but sort of...

I had this "hanging" problem, but the whole PC (not just the desktop) was locking up. Also using the 64-bit version of 8.0.4 Ubuntu on a brand-new, shiny Quad-Core machine. 

As a newbie, I eventually traced it down to the WLAN card.

You may want to switch to a big long cable (like I did), and see if that maybe helps identify the culprit.

I'm new to UBUNTU and a DEBIAN-frend told me he thinks its an Interrupt (IRQ) conflict maybe?

I just moved home, the router is right next to my table amd so now I don't need a WLAN any more.

But really. I hope you find the cause!!! I tore my hair out two weeks until I attached a LAN cable.

:P

---

