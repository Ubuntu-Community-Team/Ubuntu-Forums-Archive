---
title: "Help with frequent spontaneous logouts/shutdowns :("
date: 2011-05-21
forum: New to Ubuntu
---

### Post by dinostabOMG on 2011-05-21
Brand new install of Natty on a brand new Dell XPS 15 (model P11F). Using Ubuntu Classic session and the on-board intel graphics card.

Frequently I will be spontaneously logged out of my session and dropped back to the login window, or worse, the computer will just stop without warning or going through any kind of shutdown process. I notice that when this happens, the next time I log in I get an error message saying 

> "The panel encountered a problem while loading "MultiLoadAppletFactory::MultiLoadApplet". Do you want to delete the applet from your configuration?

(It's not always that applet, sometimes the indicator applet or the application list applet). So I think gnome panel might have to do with this problem? But I'm not sure. Anyway, a lot of the time the logout will happen very soon after I log in, even before the login sound is finished playing.

What gives?

---

### Post by audiomick on 2011-05-21
The spontaneous shutdown sounds like a possible hardware problem. The error message on startup afterwards *might* be because of a messy shutdown.

How "brand new" do you mean? Did you unpack it, install Ubuntu then start seeing problems? Or, from the other side, had you used the machine for a while with a different install so that you can say for sure that the hardware is all ok?

What happens when you run the machine from a live CD? If that works ok, then your hardware is likely good, but something is wrong with the install. If that also has problems, you may have a hardware problem.

Don't forget, brand new hardware *can* be broken out of the box...

---

### Post by dinostabOMG on 2011-05-21
Well, I've had the machine for less than a month. I am dual booting with Windows 7 and although I use the Windows install a lot less frequently, I am not having this issue in Windows. I have a hunch that it has to do with the graphics card perhaps? This model comes with two graphics cards and is supposed to switch between them, but that's a Windows-only feature. The Nvidia card is not accessible in ubunto so I'm using the motherboards Intel graphics card. That said, I have had time to customize a bit, but other than switching to the intel graphics and make use of a bunch of compiz effects I haven't done much to the install.

---

### Post by audiomick on 2011-05-21
Ok, so it looks like your machine is ok.

I can't tell you how, I am sorry, but if you can figure out how to get the machine to use the nVidia card, I think you will be happier. As far as I know, nVidia graphics work better (with the nVidia proprietary drivers) than Intel.

I don't have any idea where, but I am pretty sure I read something a year or so ago about how to dictate which graphics card the machine is to use. Not much help,  I know. I just want to indicate that I am sure that it is possible somehow.

---

### Post by wildmanne39 on 2011-05-21
> **dinostabOMG said:**
> Well, I've had the machine for less than a month. I am dual booting with Windows 7 and although I use the Windows install a lot less frequently, I am not having this issue in Windows. I have a hunch that it has to do with the graphics card perhaps? This model comes with two graphics cards and is supposed to switch between them, but that's a Windows-only feature. The Nvidia card is not accessible in ubunto so I'm using the motherboards Intel graphics card. That said, I have had time to customize a bit, but other than switching to the intel graphics and make use of a bunch of compiz effects I haven't done much to the install.HI, to activate the nvidia card go into additional drivers and click the driver for your card, there is a bug in natty that says it is not currently in use, when it really is after you have activated it.

---

### Post by dinostabOMG on 2011-05-22
Thanks guys, I did read up about that Natty bug but unfortunately it seems that there is actually an *additional* problem with trying  to get the nvidia card working on this particular family of dell laptop which involves technology that was implemented in Windows only, and until there is a fix for it in Ubuntu it's seems it will be impossible to get the nvidia card working at all. Unless anyone knows any different...

---

