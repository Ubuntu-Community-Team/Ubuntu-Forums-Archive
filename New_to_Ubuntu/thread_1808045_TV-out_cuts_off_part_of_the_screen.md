---
title: "TV-out cuts off part of the screen?"
date: 2011-07-19
forum: New to Ubuntu
---

### Post by CableRage on 2011-07-19
Hello, I'm new I have an ATI 9550 video card from what I've read that card's tv out is supported with the xorg driver which I downloaded and is currently using.

I enable tv out by these commands:

> xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600
*The 3rd command I keep seeing kills the tv:
> xrandr --output S-video --set tv_standard ntscTV works but part of the screen is cut off.
[COLOR=Lime]-------------[/COLOR][COLOR=Red]---[/COLOR]
[COLOR=Lime]:...............[/COLOR][COLOR=Red]...:[/COLOR]
[COLOR=Lime]:..............[/COLOR][COLOR=Red]....:[/COLOR]
[COLOR=Lime]:..............[/COLOR][COLOR=Red]....:[/COLOR]
[COLOR=Red]----------------[/COLOR]

Red = can't see on TV screen

and when I restart the computer I gotta re-enter those commands every time how can I have it auto enabled?

Also can I change resolution to say 1024x768? I've tried and failed.

---

### Post by CableRage on 2011-07-19
Tried the tv out commands from this website: [https://wiki.archlinux.org/index.php/ATI](https://wiki.archlinux.org/index.php/ATI)

Same screen cut out when I restart it now goes past bio boot screen to the loading ubuntu screen for a few sec's then single dies.

---

### Post by CableRage on 2011-07-19
I figured part of it out.

I had to set the main display to 800x600 now nothing is cut out tho 1024x768 would be nice.

But I still gotta do those two commands every time I restart the computer how can I have it auto enabled? I'd like to remove the monitor and just have the tv connected.

---

### Post by tgalati4 on 2011-07-19
You can put those two commands in a script (such as /etc/rc.local) and they will get run on every boot.  Place the commands before the "exit 0" line.

I don't know if autodetect is possible.  Laptops with TV video use the BIOS to detect a TV and then (some of them anyway) automatically switch.  If this is a discrete video card in a desktop machine, then you won't have any BIOS support for this.  If you are using the open ATI driver, then you might file a bug report against the driver--but search first to see if one already exists.  If you are using the proprietary driver, then send an email to ATI asking for that feature to be added.

Post any response that you get.

---

### Post by CableRage on 2011-07-20
Thanks for the reply. It's a discrete video card and using the  open  ATI driver.

For the script I just add:
"xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600"

at the end of the file? before Exit0.


I just borrowed/tried a better video card ATI x1550 but it couldn't find the output s-video I'm assuming it's not supported?

> john@john-desktop:~$ xrandr --addmode S-video 800x600
xrandr: cannot find output "S-video"                      

---

