---
title: "gnome-cups-add hangs while reading printer database"
date: 2006-08-22
forum: Networking &amp; Wireless
---

### Post by foos on 2006-08-22
Hi,

I've just updated cups to latest versions using synaptic, now I have no printers detected, and can't add any.

The cups-printer-add window displays "reading printer database" and hangs. 

There are no messages in cups log, syslog or on STDOUT/STDERR. Probably related are processes like this that just won't die, no matter how I try to kill them:

cupsys   19053 19050  0 16:18 ?        00:00:00 /usr/lib/cups/backend/epson

They are children of these processes, which go away when I stop cupsd using init scripts:

cupsys   19012     1 92 16:18 ?        00:08:49 /usr/sbin/cupsd
cupsys   19050 19012  0 16:18 ?        00:00:00 /usr/lib/cups/daemon/cups-deviced 1 0 100 requested-attributes=all


Any help appreciated.

---

### Post by richbl on 2006-08-23
I can confirm this on my Dapper install as well.

Running from console, I get the following:

(gnome-cups-add:4808): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
- using device default
- using device default
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave

Seems to me that gnome-cups-add is incorrectly calling the ALSA libs(!?). Not sure why this is, but then again, I only know ALSA for sound, and maybe that lib does a bunch more.

In any case, I'm dead in the water. 

BTW, empty error_log in cups, which is also mighty odd.

rich

---

### Post by richbl on 2006-08-23
> **richbl said:**
> I can confirm this on my Dapper install as well.

Running from console, I get the following:

(gnome-cups-add:4808): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
- using device default
- using device default
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave

Seems to me that gnome-cups-add is incorrectly calling the ALSA libs(!?). Not sure why this is, but then again, I only know ALSA for sound, and maybe that lib does a bunch more.

In any case, I'm dead in the water. 

BTW, empty error_log in cups, which is also mighty odd.

rich

Well, I can further confirm that the problem I was having was **resolved** when I re-installed Xserver (from 10.3 to 10.4). Apparently, this issue goes well beyond just printing.

In any case, after the Xserver upgrade and a reboot. I now have no problems with printing.

rich

---

### Post by Apostata on 2006-09-11
> **richbl said:**
> Well, I can further confirm that the problem I was having was **resolved** when I re-installed Xserver (from 10.3 to 10.4). Apparently, this issue goes well beyond just printing.

In any case, after the Xserver upgrade and a reboot. I now have no problems with printing.

rich
I'm having the same problem, but I don't understand what you say about Xserver...do you mean the 'xserver-xorg' package? The version I have (Dapper) is listed as 7.0.0-0ubuntu45, so I don't understand where the "10.3 to 10.4" comes from. Thanks for any clarification.

---

### Post by richbl on 2006-09-11
> **Apostata said:**
> I'm having the same problem, but I don't understand what you say about Xserver...do you mean the 'xserver-xorg' package? The version I have (Dapper) is listed as 7.0.0-0ubuntu45, so I don't understand where the "10.3 to 10.4" comes from. Thanks for any clarification.

Actually, it's xserver-xorg-core.

For details, see [http://ubuntuforums.org/showthread.php?t=241254](http://ubuntuforums.org/showthread.php?t=241254)

---

