---
title: "Wireless Driver"
date: 2006-07-27
forum: Networking &amp; Wireless
---

### Post by andgeo000 on 2006-07-27
I am attempting to get wireless connection for my Compaq Presario 2100 laptop.  The most information I could find about what it is using is that it is a Broadcom 802.11 b/g WLAN.
I tried a few of the dirrections I've found on here, but they didn't seem to work.  I'm still new to Linux, and aren't very familar with it.
Will it even be possible to get a wireless driver for it?

---

### Post by navilon on 2006-07-28
This is a tutorial on how to get wireless cards to work on linux. Let me know if it doesnt work for you.

[ HOWTO: WLan via Ndiswrapper]("http://www.ubuntuforums.org/showthread.php?t=31926")

---

### Post by andgeo000 on 2006-07-28
Thanks for the help, I figured there was same basic instructions some where, I just couldn't figure out where.
I seem to be having some problems with the dirrections, not sure what I'm missing.
When I try the first step, I get these messages:
[INDENT]FATAL: Module bcmwl5 not found.
ERROR: Module ndiswrapper does not exist in /proc/modules[/INDENT]
I assume this might just be because I haven't installed the old version, like the author had.

However, the second step doesn't work either, where would I get the linux-headers it refers to?  Are they already installed?

I'm not sure if these first to steps are crucial, but maybe they are why the rest won't work.
When I try installing the drivers, I get this message:
[INDENT]perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").[/INDENT]

Did I mess up with those first few steps.  How do I get them to work?
Thanks for the help.

---

### Post by andgeo000 on 2006-07-28
Ok, I think it is telling me I have the driver installed,
[INDENT]Installed ndis drivers:
netbc564                driver present, hardware present[/INDENT]

 but I can't seem to do any of the next steps.

[INDENT]sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.[/INDENT]

Can anyone help me with this?

---

