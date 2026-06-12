---
title: "[SOLVED] tsclient stopped connecting"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by doas777 on 2008-09-07
tsclient was working fine for me, connecting to my xp box over RDP until a day or so ago. now when i run it, it draws the window for a split second, and then dissapears.

when i run it from the terminal, this is what i get:
```

(tsclient:8072): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.16.4/gobject/gsignal.c:1741: instance `0x6ba540' has no handler with id `1080'

```
no messages appear in the sys log regarding the issue.

Does tsclient use any smb utilities? I did recieve a samba/smbclient update this weekend, though my smb.conf is unchanged.

also is the glib supposed to match my kernel version? 
```
Linux 21of2 2.6.24-19-generic
```

I've messed arround with all the tsclient options (resoulution/color, sound, rdp version, perf options, etc) and nothing appears to change this behavior.

I reinstalled tsclient with 
```
sudo apt-get install tsclient --reinstall
```
but no luck.

any ideas?

---

### Post by doas777 on 2008-09-07
I just purged tsclient and installed ubuntu-desktop to reinstall it. this time I get the same message above, but now it's failing and showing a connection error message stating:

```

** (tsclient:8564): WARNING **: 
Autoselected keyboard map en-us
X Error of failed request:  BadAtom (invalid Atom parameter)
  Major opcode of failed request:  23 (X_GetSelectionOwner)
  Atom id in failed request:  0x0
  Serial number of failed request:  51
  Current serial number in output stream:  51

```

I see a few bug reports related to this error on PPA, but they relate to **CLOSING** an rdp connection, not **OPENING** on. they state that they can connect fine. I cannot.

thanks,
frank

---

### Post by doas777 on 2008-09-07
ok I got it fixed. amazingly enough the problem was with the nvidia drivers on the windows terminal. i updated them for spore earlier this weekend, and it causes a failure in the rdpdd dll when mixed with sp3.

how did nvidia get whql certification if it won't support current software?

though, I would rather nvidia focus on fixing the overscan problem i'm having with nvidia-glx-new ( [http://ubuntuforums.org/showthread.php?t=851626](http://ubuntuforums.org/showthread.php?t=851626) ).

---

### Post by jijin on 2008-09-28
how did you resolve it roll back the drivers?

I rolled the nvidia drivers back to 175.16 which gave the same error.

Anybody else's help with this would be appreciated, thanks.

---

### Post by doas777 on 2008-09-29
> **jijin said:**
> how did you resolve it roll back the drivers?

I rolled the nvidia drivers back to 175.16 which gave the same error.

Anybody else's help with this would be appreciated, thanks.

well i just opened the device manager (System control panel -> Hardware -> Device manager) and navigated to the vid card. then i Rclicked -> properties -> Driver -> Rollback driver. 
that worked for me.

I have a Geforce7950 with driver version 6.14.11.7792. I'm not certian what version of the gforce driver package it is in.

hope that helps,
frank

---

### Post by doas777 on 2008-09-29
> **jijin said:**
> how did you resolve it roll back the drivers?

I rolled the nvidia drivers back to 175.16 which gave the same error.

Anybody else's help with this would be appreciated, thanks.

I'm not certian your problem is the vid driver,  but it may be. look in your windows event log for a reference to which service failed to load and what dll failed.

good luck,
franklin

---

