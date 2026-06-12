---
title: "How to Install ATI Proprietary Display Driver in Ubuntu 10.04?"
date: 2010-06-28
forum: New to Ubuntu
---

### Post by spid3y on 2010-06-28
Hi, 

Just scraped XP from my PC and moved to Ubuntu 10.04, lovin' it! :)
Few Questions. 

1) I have ATI Radeon Xpress 200 Graphic card, How can I make ubuntu utilize it. Should I install a specific driver for it? Tried ATI binary x.org driver from Ubuntu Software Center. Gives an error. 

2) Also have Creative 2.1 channel Speaker system. Sound is not as loud as it used to be in XP. I had Realtek Audio Driver in XP. Where would I find a similar thing for Ubuntu?

Thanks and Regards.

PS: Linux Rocks!

---

### Post by alphacrucis2 on 2010-06-28
> **spid3y said:**
> Hi, 

Just scraped XP from my PC and moved to Ubuntu 10.04, lovin' it! :)
Few Questions. 

1) I have ATI Radeon Xpress 200 Graphic card, How can I make ubuntu utilize it. Should I install a specific driver for it? Tried ATI binary x.org driver from Ubuntu Software Center. Gives an error.

I believe you would have to go back to around the old ATI Catalyst 9.2 or 9.3 version binary driver to support that card. ATI dropped support for those in later Catalyst releases. The problem being that Catalyst 9.3 doesn't work with Ubuntu 10.4 (or 9.10 or 9.04 for that matter). In any case Ubuntu should be using the Radeon Open Source driver for that card. Not sure what 3D support you get with that.
 

> 2) Also have Creative 2.1 channel Speaker system. Sound is not as loud as it used to be in XP. I had Realtek Audio Driver in XP. Where would I find a similar thing for Ubuntu?

Thanks and Regards.

PS: Linux Rocks!

Probably something to do with the alsa or pulseaudio config. I'm sure someone with the necessary knowledge will show up to help before long.

---

### Post by Mark Phelps on 2010-06-28
> **spid3y said:**
> ... 1) I have ATI Radeon Xpress 200 Graphic card, How can I make ubuntu utilize it...
If you're getting a graphical desktop, Ubuntu is already utilizing it.

Current Ubuntu versions will only work with that card with the default open source drivers -- which are automatically installed when you install the OS.

---

### Post by philinux on 2010-06-28
> **spid3y said:**
> Hi, 

Just scraped XP from my PC and moved to Ubuntu 10.04, lovin' it! :)
Few Questions. 

1) I have ATI Radeon Xpress 200 Graphic card, How can I make ubuntu utilize it. Should I install a specific driver for it? Tried ATI binary x.org driver from Ubuntu Software Center. Gives an error. 

2) Also have Creative 2.1 channel Speaker system. Sound is not as loud as it used to be in XP. I had Realtek Audio Driver in XP. Where would I find a similar thing for Ubuntu?

Thanks and Regards.

PS: Linux Rocks!

1. has been answered.

2. Left click on the volume applet and choose preferences. Turn up the output volume to suit. The sound driver is already installed.

---

### Post by spid3y on 2010-07-02
@alphacrucis2 and @Mark Phelps: Thanks, I see what you mean :)

@philinux: That worked, now its louder than it was in XP, lol.

Thank you guys for all the help.
Happy Computing ;)

$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$

Whoa...I did a 'zcat /vmlinuz > /dev/audio' and I think I heard God...
-- mikecd on #Linux

---

