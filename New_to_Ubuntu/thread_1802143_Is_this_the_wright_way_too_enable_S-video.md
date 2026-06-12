---
title: "Is this the wright way too enable S-video?"
date: 2011-07-11
forum: New to Ubuntu
---

### Post by Org1 on 2011-07-11
Useing ubuntu 10.04 and the open source x.org drivers from here: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")

I got a S-Video to Red White Yellow cable when it first turn on it shows the boot screen and then goes to unable to read signal.


I Google'ed and found this:

[http://www.x.org/wiki/radeonTV](http://www.x.org/wiki/radeonTV)
> TV-out may be enabled by using a recent driver and xrandr utility: 

[LIST=1]
[*]xrandr --addmode S-video 800x600
[*]xrandr --output S-video --mode 800x600
[*]xrandr --output S-video --set tv_standard ntsc
[/LIST]
But I wanna make sure that's wright for my card/tv (ATI x1550/2003 RCA standard TV) and do I need to download the xrandy utility somewhere?

---

### Post by jtarin on 2011-07-11
> **Org1 said:**
> Useing ubuntu 10.04 and the open source x.org drivers from here: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")

I got a S-Video to Red White Yellow cable when it first turn on it shows the boot screen and then goes to unable to read signal.


I Google'ed and found this:

[http://www.x.org/wiki/radeonTV](http://www.x.org/wiki/radeonTV)
But I wanna make sure that's wright for my card/tv (ATI x1550/2003 RCA standard TV) and do I need to download the xrandy utility somewhere?Xrandr should already be included in y
our distro. Open a terminal and type ```
man xrandr
```

---

### Post by Org1 on 2011-07-11
I tried enter the first line it:

> adam@adam-desktop:~$ xrandr --addmode S-video 800x600
xrandr: cannot find output "S-video"


VGA is hooked to monitor
S-video is hooked to tv
Tv is on with unusable signal

BTW:I messed up I've got 11.04 ubuntu not 10.04.

---

### Post by jtarin on 2011-07-11
> **Org1 said:**
> I tried enter the first line it:



VGA is hooked to monitor
S-video is hooked to tv
Tv is on with unusable signal

BTW:I messed up I've got 11.04 ubuntu not 10.04.[URL="http://ubuntuforums.org/archive/index.php/t-625435.html"]I'm gonna let you read this post rather than cite it.
[/URL] Take note of the mention of using Catalyst and which ATI drivers to use. There's a script posted there you might try.

---

### Post by Org1 on 2011-07-12
I messed something up.

I rebooted and now it goes pass the boot screen to a:

 unbuntu
.............

white letters black background  and stays there forever on ether tv or normal monitor or both.

---

### Post by jtarin on 2011-07-12
> **Org1 said:**
> I messed something up.

I rebooted and now it goes pass the boot screen to a:

 unbuntu
.............

white letters black background  and stays there forever on ether tv or normal monitor or both.At the Grub boot screen, choose "recovery mode"

---

### Post by Org1 on 2011-07-12
How do I get to the Grub boot screen?

I'm really new.

---

### Post by jtarin on 2011-07-12
Restart your PC and it comes up looking something  like this:(older Ubuntu Grub screen)
[IMG]http://i28.tinypic.com/308llcy.jpg[/IMG]
If you only have ubuntu on the disk it might go by too fast to see....then hit the "Esc" key.

---

### Post by Org1 on 2011-07-12
I've seen it before but its not comeing up for me.

---

### Post by jtarin on 2011-07-12
> **Org1 said:**
> I've seen it before but its not comeing up for me.Look at my instructions under the pic.

---

### Post by Org1 on 2011-07-12
I tried the ESC and mass rapid pushing of ESC.

I'm going reinstall and start over and try again. [not much on that computer]

---

