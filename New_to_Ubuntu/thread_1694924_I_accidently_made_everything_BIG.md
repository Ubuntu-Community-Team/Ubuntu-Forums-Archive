---
title: "I accidently made everything BIG"
date: 2011-02-25
forum: New to Ubuntu
---

### Post by Nikola Georgiev on 2011-02-25
I am using Ubuntu 10.04 LTS - the Lucid Lynx - released in April 2010 and supported until April 2013.
Here's the problem.
I pushed some keyboard combination (I don't know exactly what combination), and everything became bigger: the desktop, the browser, everything.
First I thought it was the firefox zoom. Well, it's not that.
Then I thought it was the monitor resolution, it's not that.
Then I researched the problem and found out that it could be some kind of Ubuntu zoom option, but my visual effects are set to "None".
Then I thought it was the video card settings or drivers. BUT I don't even know what type of video card I'm using. It's integrated to the motherboard and I think it's Intel.

Before that, everything was normal.


Any help would be useful. Thanks in advance.

---

### Post by Joeb454 on 2011-02-25
It sounds like it might be an accessibility option. I think the 'Universal Access' settings are found under the System > Preferences menu. I can't say for sure as I'm not at an Ubuntu machine at the moment.

---

### Post by Nikola Georgiev on 2011-02-25
> **Joeb454 said:**
> It sounds like it might be an accessibility option. I think the 'Universal Access' settings are found under the System > Preferences menu. I can't say for sure as I'm not at an Ubuntu machine at the moment.
I couldn't find that "Universal Access" in the System -> Preferences menu..:confused:

---

### Post by howefield on 2011-02-25
Try looking for System > Assistive Technologies.

---

### Post by Nikola Georgiev on 2011-02-25
> **howefield said:**
> Try looking for System > Assistive Technologies.
And then what?

Sorry for them stupid questions, but I'm using Ubuntu from a week ago..

---

### Post by migs73 on 2011-02-25
Try and uncheck enable assistive technologies, then click 'close and log out'.

Log back in and hopefully it should be back to normal.

Mike :)

---

### Post by Nikola Georgiev on 2011-02-25
> **migs73 said:**
> Try and uncheck enable assistive technologies, then click 'close and log out'.

Log back in and hopefully it should be back to normal.

Mike :)

It was unchecked. I tried it, didn't work. Still everything is like zoomed x2.

---

### Post by migs73 on 2011-02-25
Type```
lspci
``` into terminal and post back the results here. That'll tell what type your video card is.

---

### Post by Nikola Georgiev on 2011-02-25
> **migs73 said:**
> Type```
lspci
``` into terminal and post back the results here. That'll tell what type your video card is.

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)

---

### Post by Nikola Georgiev on 2011-02-25
So... any ideas, what should I do now? :/

---

### Post by Hakunka-Matata on 2011-02-25
How about Ctrl, Alt, - (minus key)  that's zoom function, and I don't know if it shows up anywhere in menus or not.  You can hit it repeatedly and it will make things very big, or small

---

### Post by Nikola Georgiev on 2011-02-26
> **Hakunka-Matata said:**
> How about Ctrl, Alt, - (minus key)  that's zoom function, and I don't know if it shows up anywhere in menus or not.  You can hit it repeatedly and it will make things very big, or small
Nope, didn't work...

---

### Post by Nikola Georgiev on 2011-02-27
Someone else have an idea?

---

### Post by howefield on 2011-02-27
Just to clarify, can you see all of your desktop but everything is big, or do you see only a portion of your desktop ?

---

### Post by Nikola Georgiev on 2011-02-27
> **howefield said:**
> Just to clarify, can you see all of your desktop but everything is big, or do you see only a portion of your desktop ?
I can see all of my desktop but everything is bigger.
Here's an attached screenshot (I made my icons smaller, so I could see all of them).

---

### Post by vivek.pandey on 2011-02-27
seeing your desktop , everything seems normal.but one question is that mystery zoom exists after a restart?

---

### Post by Frogs Hair on 2011-02-27
Here is some documentation for keyboard shortcuts , maybe you can figure out what you did. This could be dated because some of these don't work with my key board. [https://help.ubuntu.com/community/KeyboardShortcuts](https://help.ubuntu.com/community/KeyboardShortcuts)

---

### Post by vivek.pandey on 2011-02-27
may be you scrolled the mouse up while pressing ctrl key.(or scrolled up from your touch pad while pressing ctrl) if it is so scroll down pressing ctrl

---

### Post by Vaphell on 2011-02-27
maybe lower resolution is set or DPI settings were altered? i admit it's hard to change it by accident but who knows

---

### Post by Nikola Georgiev on 2011-02-27
> **neo_aryan said:**
> seeing your desktop , everything seems normal.but one question is that mystery zoom exists after a restart?
Ok, here's the screenshot (Screenshot2) without the changes I made (putting the icon view default to 66%).
At Screenshot1 you can see how big is, for example the youtube player.
The screenshots are at the end of the post.
I tried restarting, of course, it didn't work.

> **Frogs Hair said:**
> Here is some documentation for keyboard  shortcuts , maybe you can figure out what did. This could be dated  because some of these don't work with my key board. [https://help.ubuntu.com/community/KeyboardShortcuts](https://help.ubuntu.com/community/KeyboardShortcuts)

I went through the list, couldn't find anything helpful.
> **Nikola Georgiev said:**
>  I researched the problem and found out that it could be some kind  of Ubuntu zoom option, but my visual effects are set to "None".


> **neo_aryan said:**
> may be you scrolled the mouse up while  pressing ctrl key.(or scrolled up from your touch pad while pressing  ctrl) if it is so scroll down pressing ctrl
Tried that.

> **Vaphell said:**
> maybe lower resolution is set or DPI settings  were altered? i admit it's hard to change it by accident but who  knows
> **Nikola Georgiev said:**
> Then I thought it was the monitor resolution, it's not that.
The DPI is 96, it's the same as before.



Someone earlier mentioned that the drivers could be the problem. If it is, how can I reinstall them? :confused:





.

---

### Post by vivek.pandey on 2011-02-27
hey try these link
[http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)

[http://www.linuxquestions.org/questions/linux-newbie-8/please-tell-me-how-to-reset-my-screen-resolution-or-reinstall-ubuntu-via-the-terminal-621567/](http://www.linuxquestions.org/questions/linux-newbie-8/please-tell-me-how-to-reset-my-screen-resolution-or-reinstall-ubuntu-via-the-terminal-621567/)

[http://www.linuxquestions.org/questions/linux-newbie-8/please-tell-me-how-to-reset-my-screen-resolution-or-reinstall-ubuntu-via-the-terminal-621567/](http://www.linuxquestions.org/questions/linux-newbie-8/please-tell-me-how-to-reset-my-screen-resolution-or-reinstall-ubuntu-via-the-terminal-621567/)

---

### Post by Frogs Hair on 2011-02-27
When you have Firefox open and use Ctrl + Alt and move the mouse wheel are you able to zoom in and out ?

---

### Post by Nikola Georgiev on 2011-03-04
Tried  those links also, didn't work.
I now have a problem with the youtube player (maybe flash problem).
The colours are going crazy. Tried to reinstall flash, but I couldn't.
Now I'm thinking about reinstalling the whole OS from scratch..

---

### Post by Nikola Georgiev on 2011-03-05
Should I reinstall or what?

---

### Post by ikt on 2011-03-05
> **Nikola Georgiev said:**
> Should I reinstall or what?

You can reinstall if you want to, it's up to you, though I can't see the zoom issue in your screenshots :confused:

Also the flash issue has some work arounds here:

[http://ubuntuforums.org/showthread.php?t=1698956&page=8](http://ubuntuforums.org/showthread.php?t=1698956&page=8)

---

### Post by Nikola Georgiev on 2011-03-06
> **ikt said:**
> You can reinstall if you want to, it's up to you, though I can't see the zoom issue in your screenshots :confused:

Also the flash issue has some work arounds here:

[http://ubuntuforums.org/showthread.php?t=1698956&page=8](http://ubuntuforums.org/showthread.php?t=1698956&page=8)

Well, no one sees the size problem, maybe I'm going crazy, don't know... :(
A few questions:
1. If I reinstall, would the drivers install themselves automatically?
2. Would I lose some of the information on my HDD and how should I protect it (I'm new to Ubuntu).

Also, big thanks on the flash problem, I'm just reading the information you gave me right now. :)

---

### Post by Nikola Georgiev on 2011-03-07
It was a Resolution issue. Finally I fixed it. Thanks to all for the help.

---

### Post by Hakunka-Matata on 2011-03-09
Explain what settings were changed please.

---

### Post by Nikola Georgiev on 2011-03-09
> **Hakunka-Matata said:**
> Explain what settings were changed please.
It was (of course) the easiest thing. I'm dumb, haha.
There was a higher resolution (1280x1024) which is 5:4, because of which I neglected it.
I still don't know how I changed the resolution with only some shortcut key combination..


Looks like I was losing your time. Sorry about that. : )

---

### Post by Hakunka-Matata on 2011-03-09
Hey, not to worry, thanks.

---

### Post by Nikola Georgiev on 2011-03-12
... delete this post ...

---

### Post by Nikola Georgiev on 2011-03-13
... delete this post ...

---

