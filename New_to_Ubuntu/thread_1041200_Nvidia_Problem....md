---
title: "Nvidia Problem..."
date: 2009-01-16
forum: New to Ubuntu
---

### Post by Leo Dragonheart on 2009-01-16
I am back... I am having problems with my video card. All I know is it is nVidia G-Force FX 5600 I THINK... now when I activate the recommended driver "nVidia 173 I think" in the Hardware Drivers Panel It usually work but then when I reboot now I have like 640x480 resolution and it won't go any higher. I am wondering if there is a driver I can download and that I can install so I don't have to mess with it every time I reboot...

Help me please...everything is IN MY FACE Literally... Thanx.

---

### Post by abyssius on 2009-01-16
Leo

I've had the exact same problem with NVIDIA cards and the restricted driver. I searched for months to find an answer and I must tell you it was a painful runaround. The good news is I was able to fix it easily, simply by manually editing my xorg.conf file. In my case the problem was not with the NVIDIA driver at all. The problem was that my monitor was not correctly recognized by the X-server system. Once I identified my monitor specs in the xorg.conf file, everything worked perfectly. This is how I did it.

First you need to open your xorg.conf file in Gedit, like this:

```

sudo gedit /etc/X11/xorg.conf

```

You'll have to enter your password to gain editing privileges.

Some say you should back up the file first, but I found gedit does this automaticaliy, and right now your original file isn't doing you much good anyway.

Next, you have to add a few lines to specific sections of your xorg.conf file. BUT DO NOT CHANGE ANYTHING ELSE!

In the Monitor section add the lines that appear in bold:
```

Section "Monitor"
    Identifier     "Configured Monitor"
    [B]HorizSync       31.0 - 65.0
    VertRefresh     51.0 - 90.0	[/B]
EndSection

```

Note that these are the specs that fit my particular monitor. They'll probably work for yours also -  but if you want to you can replace the VertRefresh and HorizSync values with your monitor's actual data if you know what they are.

Next, in the Screen section add the lines that appear in bold, right before the EndSection line.

```

    [B]SubSection     "Display"
        Depth       24
        Modes      "1280x1024_60"
    EndSubSection[/B]

```

This set my monitor to my desired resolution which is 1280X1024. You can substitute the resolution data to suit your needs. Reboot your computer and you should have a high resolution display. Next, you should run the NVIDIA settings program to fine tune your system.

If this doesn't work, then you can boot in recovery mode and select the fix x-server option. This will give you a high resolution display but no special effects, etc. 

I hope this helps.

---

### Post by bailbath on 2009-01-16
What version of Ubuntu are you using?

---

### Post by Leo Dragonheart on 2009-01-16
> **bailbath said:**
> What version of Ubuntu are you using?

Ubuntu 8.10 Desktop Edition, and Gnome keeps showing up everywhere so I don't know if thats part of it or not...

---

### Post by Leo Dragonheart on 2009-01-16
I did what you said and it worked, not perfectly but way better than before...Thanx alot. I learned something new today...:-)

---

### Post by Leo Dragonheart on 2009-01-16
OK scratch that last reply. I did what you said but put in 800x600, now I went back and put in what you said to put in 1280x1024, rebooted and we are all good...Worked great, thank you for the advise, and once again I learned something new today so it is a good day...

This community ROCKS!!!

---

### Post by chkh on 2009-01-16
Good for you leo that you were able to your problem! i'm facing a  slightly different problem though but its still about the nvidia card.

Mine is a Geforce 6600 GT SLi on a desktop and i've just installed the new ubuntu 8.10 but the os cant seem to find the drivers for me. i cant activate the desktop animation:confused: 

Really hope that someone would help me on this. i'm really a newbie in linux.

---

### Post by Leo Dragonheart on 2009-01-16
chkh, try the above info, or post a new tread, I have been here for the last two days and have posted 2 times and can't even count how much help I have gotton. I got both my problems solved in less than an hour, just post your problem. Someone will help. I would but this is only my second day of Ubuntu, I just installed it yesterday... Good luck.

---

### Post by chkh on 2009-01-16
Alright. thanks for the advice btw! cheers!

---

