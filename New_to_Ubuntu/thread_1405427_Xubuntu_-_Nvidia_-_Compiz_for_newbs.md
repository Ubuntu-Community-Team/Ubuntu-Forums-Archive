---
title: "Xubuntu - Nvidia - Compiz for newbs?"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by sozcaps on 2010-02-12
Hi all,

I just discovered Xubuntu and I'm really starting to fall for it. However,
I don't know how to install my 9600GT nvidia driver, and when I google it I get technical mumbo jumbo. Same goes for guides to installing compiz on Xubuntu - I get pages that assume I'm already an expert.

What I'm looking for is a simple(!) guide to get  nvidia drivers and compiz working on Xubuntu. Preferrably through the terminal. Is this doable, or is there only the hard way with Xubuntu?

Thanks in advance

---

### Post by achase79 on 2010-02-12
If you have an internet connection you just use system->settings->hardware drivers and look to see if the nvidia driver is listed and install it from there.

---

### Post by Scunizi on 2010-02-12
Before doing anything do a full system upgrade.. "sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade".. Dist-upgrade will not take you to the next release.

Now in your menus (and it's been a couple years since I've looked at xubuntu) you should have a menu option for "Hardware Drivers" and in there should be an nvidia driver just waiting to be enabled.. enable it then restart the machine for it to take effect.

---

### Post by sozcaps on 2010-02-12
> **Scunizi said:**
> Before doing anything do a full system upgrade.. "sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade"

Done. 

[COLOR="White"][COLOR="DarkSlateGray"]Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/COLOR][/COLOR]


> **achase79 said:**
> If you have an internet connection you just use system->settings->hardware drivers and look to see if the nvidia driver is listed and install it from there.
Done.

Looks good so far. And by that I mean, my computer hasn't blown up or anything. Restarting, brb :)

---

### Post by sozcaps on 2010-02-12
Gah. Now it boots into a resolution my monitor can't handle. 	:-({|=

A very black screen is all I get now.

If I reinstall and start over, is there anything I can do to prevent the Nvidia drivers from again defaulting to some strange resolution?

---

### Post by Scunizi on 2010-02-12
xrandr will now handle the settings for resolution and refresh rate.. if you have a crt vs. a LCD monitor it may not have picked up the right resolution.. from cli (ctrl+alt+F1-6) login and type xrandr.. it will list the resolutions the graphics server is currently capable of displaying.. if what you want is listed then a google search for xrandr will show you how to change the default OR correct a missing resolution from the list.

---

### Post by sozcaps on 2010-02-12
Thank you, I'll try and see what happens.

---

### Post by sozcaps on 2010-02-13
Tried
[COLOR="SeaGreen"]sudo xrandr -output LVDS -mode 800*600[/COLOR]
can't remember the error message and I tried
[COLOR="SeaGreen"]sudo xrandr -s 800*600[/COLOR] and got and it says [Can't open display]

other than those two examples I'm clueless as to how to use xrandr. When I do xrandr --help, it scrolls past the text and it won't do x[COLOR="SeaGreen"]randr --help|more[/COLOR] :(

How do I get xrandr to switch my xubuntu to a displayable resolution and refresh rate - like 800*600@50 hz?

---

