---
title: "System Freezes after Suspend"
date: 2010-03-23
forum: New to Ubuntu
---

### Post by Wataru8675 on 2010-03-23
Hi all,

Lately I've been having an issue with Ubuntu where I'll put it into Suspend mode, and when I try to bring it back up, the screen goes black, but the password entry box doesn't show up and my mouse is arrested.  The only way that I know of out of it is to hold Power (which always gives me the heebie jeebies).

I thought this problem may have occured around the time I switched to the High desktop effects option, but I've turned it back to the lowest setting since with no change.

Any ideas as to what to do?  It does this in multiple kernels, too...

Thanks!
Wataru8675

---

### Post by Wataru8675 on 2010-03-23
Is this maybe a bug that I should report?

---

### Post by patchwork on 2010-03-23
This isn't a fix, but it may prevent you from having to hard-shutdown.

When the screen goes black, try hitting CTRL ALT F1.  Hopefully this will bring you to a console login prompt.  Log in, and issue the one of the following commands:```
sudo shutdown -r now #reboot
sudo shutdown -P now #shutdown
sudo service gdm restart # Attempt to restart the GUI X server, if an error msg appears saying unknown instance, use start instead of restart
```

How much swap space and RAM do you have?  It is recommended that the swap space be twice the available RAM.  If the swap space is insufficient, the current session cannot be properly saved to swap upon suspend or hibernate.

---

### Post by Wataru8675 on 2010-03-26
I wanna say I have...4GB RAM?  But I'm not sure what swap space is or how I can know how much I have.  It SHOULD be sufficient.  This is only a recent problem.  I've been using Ubuntu for almost a year now, and have only  had this problem this last month.

---

### Post by fromthehill on 2010-03-26
what kind of laptop/computer do you have?

I have a similar problem with my acer aspire 8930g.
according to the logfiles the system just seems to eject my hard drive when resuming from suspend (which results in everything slowly disappearing from my desktop)
I'm running arch right now but it does the same thing with ubuntu

---

### Post by Wataru8675 on 2010-03-26
> **fromthehill said:**
> what kind of laptop/computer do you have?

I have a similar problem with my acer aspire 8930g.
according to the logfiles the system just seems to eject my hard drive when resuming from suspend (which results in everything slowly disappearing from my desktop)
I'm running arch right now but it does the same thing with ubuntu

That sounds horrifying. xD  I'm running on a Toshiba Satellite.  It's pretty sturdy hardware-wise, so I'm guessing that it's something in the programming or my settings that's mucking it up.

---

### Post by scc4fun on 2010-06-16
I am having a similar issue. When my IBM (pre-Lenovo) ThinkPad T42 goes into suspend for longer than an hour it becomes unresponsive. Next time I will try Ctrl-Alt-F1 so that I could at least get it to shutdown/reboot properly. I used the default settings when installing Ubuntu 10.04 so I am using 2x the RAM as swap and ext4 as the filesystem.

---

### Post by philinux on 2010-06-16
When a system freezes either try Alt+SysRq+k or if that doesn't work this.

[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

---

### Post by ppp0 on 2010-07-21
Same Thing with my Sony Vaio fw31e with Lucid.
But... My swap is about 2.5GB with 4GB of RAM... May be of this.

---

### Post by azitizz on 2010-11-23
Yes, Me too. I have been having this problem intermittently with my Toshiba Satellite L350D. But not that I've upgraded to 10.10 it happens every time. 

Ill be trying the alt+syst trick.
I would love it if there were a good solution to this.
My only two issues with Ubuntu are the overheating and the suspend. Otherwise Everything else is great.

---

### Post by azitizz on 2011-01-05
> **winnie666 said:**
> Try pressing "alt + F2" to launch gconf-editor.

Type "gconf-editor" and then press enter.

In the directory tree to the left, navigate to "/apps/gnome-power-manager/lock/"

Uncheck the boxes "gnome_keyring_hibernate" and "gnome_keyring_suspend"

If that fails, uncheck also the boxes "hibernate" "suspend" and "use_screensaver_settings". Unfortunatly that will dissable the screen lock completely.

Let us know if that helps!

Hi, Thanks but it doesent seem to have helped for me. I unchecked all of them as the first two didnt make a difference. I had to force a shutdown. Second time, same thing.

It appears as if the computer goes into suspend fine, then it seems to wake up when I press on the space bar and I even hear some system sounds, but the screen never turns on. 

Perhaps the computer is actually working except for the screen I have to wonder, because I can see the hard drive light flicker with mouse clicks and keyboard strikes. But as I cant see what Im doing I have to force quit.

---

