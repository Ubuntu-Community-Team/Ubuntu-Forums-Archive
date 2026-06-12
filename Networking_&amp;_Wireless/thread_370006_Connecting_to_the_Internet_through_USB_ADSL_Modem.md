---
title: "Connecting to the Internet through USB ADSL Modem"
date: 2007-02-25
forum: Networking &amp; Wireless
---

### Post by madfrageris on 2007-02-25
Hello,

I've been trying to make my modem, D-Link DSL-200 Generation II, work in Linux for two days already, all without luck. Having followed the complete documentation at EciAdsl website, I still didn't make my modem work: when I type "eciadsl-config-tk" or "eciadsl-config-text" terminal returns there are no such commands.

Ok, I've reinstalled my Linux system and downloaded these packages: [pppoe](http://packages.ubuntu.com/edgy/net/pppoe) and [eciadsl](http://packages.ubuntu.com/edgy/net/eciadsl), installed them with "sudo dpkg -i <...>" command and made sure they appeared in Synaptic. IT STILL DIDN'T WORK.

I've tried installing .tar package, but ./configure command failed, showing "it can't compile executables".

This is how my modem looks like:
[center][img]http://www.sigmacomputers.ru/images/catalog/picture-3221.jpg[/img][/center]

This modem is supported by EciAdsl:
[http://eciadsl.flashtux.org/modems.php?modem=65](http://eciadsl.flashtux.org/modems.php?modem=65)

At this time, I wish I bought another one, with Ethernet connection...

Even my network provider is shown there (Lietuvos Telekomas, now called "TEO LT").

Just... what's wrong? Why EciAdsl doesn't work, even though if it's installed? Is it possible to connect using other program, not necessarily EciAdsl?

---

### Post by dstath on 2008-01-04
have a look here [http://ubuntuforums.org/showthread.php?t=375846](http://ubuntuforums.org/showthread.php?t=375846)

---

