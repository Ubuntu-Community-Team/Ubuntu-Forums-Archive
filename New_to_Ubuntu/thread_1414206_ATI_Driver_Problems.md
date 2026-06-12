---
title: "ATI Driver Problems"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by psyte on 2010-02-23
I just started using linux about a week ago so bear with me here, I don't have much knowledge of how things work yet.

Basically I am trying to set up dual monitors on a laptop with an ATI video card (from what I can tell from using lspci, the model is RS690).
The open source drivers that came with Ubuntu 9.10 will let me enable both monitors but the external monitor appears to have some refresh problem and just looks terrible. Also, I keep one of my panels on the right side of the display and when maximizing windows they end up underneath the panel.

Anyway... after doing some research I found out about the ATI Catalyst Control Center and installed it from the Ubuntu Software Center. When I tried to run the program I got the following error:

```
There was a problem initializing Catalyst Control Center Linux edition. It could be caused by the following.

No ATI graphics driver is installed, or the ATI driver is not functioning properly.
Please install the ATI driver appropriate for you [sic] ATI hardware, or configure using aticonfig.
```So I did a bit more research and decided to install EnvyNG.

From here on I can't give the exact code used as the following actions basically led to me only being able to boot into the terminal and I cannot install EnvyNG from the live cd I am now running as I get a message saying "Not available in the current data."

So... for some reason EnvyNG would not run in the GUI mode so I ran it from the terminal using envyng -t. I selected the option to install an ATI driver (I believe it was option 3). It then presented me with the driver that it found (sorry don't recall the details but I think it said something about the version being 8.04). I then made the mistake of letting it install the driver without researching to confirm it was the correct one. Next I selected the option to reboot.

My computer then rebooted in terminal mode and now appears to be unable to boot into the GUI environment. In an attempt to fix it, I ran envyng -t again and selected the option to uninstall the ATI driver (option 4 I believe it was). It appeared to be successful as the data it spit out didn't seem to have any errors. I then rebooted but still am brought to the terminal.

Sorry for being so long winded here, just wanted to give as much info as possible.
Any help would be greatly appreciated as I would really hate to have to reinstall Ubuntu at this point.

---

### Post by psyte on 2010-02-23
I think I probably wasn't very clear on what exactly I'm asking here. What I am looking to do right now is just reverse the changes I made via EnvyNG. I'll do some more research on the dual monitor setup on my own. For now I'd just like to be able to get back to being able to use Gnome.

Thanks.

---

### Post by psyte on 2010-02-23
Well after many hours of trying different commands it turns out that restoring the backup of xorg.conf was the solution. So if anyone else ever has this problem, I ran the following commands:

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo rm /etc/X11/xorg.conf

```

---

