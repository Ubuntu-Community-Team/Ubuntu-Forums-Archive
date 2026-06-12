---
title: "Networking config wiped at reboot"
date: 2006-12-08
forum: Networking &amp; Wireless
---

### Post by ubuntwinkel on 2006-12-08
I'm having the same issue as [brentoboy]("http://ubuntuforums.org/showthread.php?t=217199"). I have static IPs for my 2 local machines. No dhcp in use.

One machine has Ubuntu and dns never gets reset on that one. The other machine has Kubuntu installed and at every reboot it resets my dns config and my domain name (as set-up in the menu item, System:Administration:Networking).

I tried the fix of using prepend-domain-name-servers in dhclient.conf, but my dns config was still wiped at reboot (and I didn't expect this fix to do anything since I don't use dhcp--but I tried).

My searching reveals that others have this issue, specifically those who have static IP setups and use either Kubuntu or Xubuntu. My searching also reveals that the fixes offered are usually for dhcp setups, so those solutions are of little help.

I have re-entered my dns config so many times now that I can do it in my sleep. Is there a solution to this issue for static IP users? Or (misquoting Peggy Lee) "Is dhcp all there is?"

---

### Post by DaveBorealis on 2006-12-09
> **ubuntwinkel said:**
> at every reboot it resets my dns config and my domain name

Hello,

I'm not certain where the domain name is stored, and therefore where it's being changed, but your dns is held in '/etc/resolv.conf'.  One work-around would be to store that info in another file, like '/etc/resolv.conf.copy', and at bootup run the command 'cat /etc/resolv.conf.copy > /etc/resolv.conf'

You could add the line to '/etc/rc.local'.  However, if you want that DNS info for any bootup processes, you'll probably be out of luck because I believe /etc/rc.local' gets read and executed at the end.

Dave

---

### Post by handy on 2006-12-12
Sorry it didn't work **Ubuntwinkel**, I'll be interested in the solution when it comes through?

Before I learned about the [_**prepend fix**_]("http://ubuntuforums.org/showthread.php?t=282034"), I was running a script at boot time:

[B]#!/bin/sh
cd /etc
sudo cp resolve.conf resolv.conf[/B]

Where obviously **resolv_e_.conf** had my correct settings.

Also, you could put an icon on a panel so you can just hit it, rather than type in all the numbers *again*! Untill the real fix comes in that is... :-)

If you are interested in the boot time work around [_**here is the link**_]("http://ubuntuforums.org/showthread.php?t=245618"), **Huygens** is the one with the very clever answers re safely running sudo in a script without having to enter your password. :-)

---

### Post by ubuntwinkel on 2006-12-19
@handy + @huygens: Thank you!  It seems my issue will be resolved.  Will report back how it tests out.

Thanks again.

---

### Post by ubuntwinkel on 2006-12-19
Sadly, it doesn't work for me.  At reboot not only do my dns's still get wiped, but the changes (per huygens) I made to resolv.conf (chgrp priver and chmod g+w) also get reset.  

However, now I know how to restore my dns config semi-automatically with ```
sudo cp /etc/resolvconf.copy /etc/resolv.conf
``` which is definitely an improvement.  

As an aside, I also experimented with uninstalling all things dhcp using synaptic.  Nothing really changed, except now when when I ```
sudo /etc/init.d/networking restart
``` I get a lot of simple errors instead of a lot of elaborate dhcp errors.  

:D

---

### Post by handy on 2006-12-20
bugger! ](*,)

With the amount of time you would have spent on this one, you probably would have solved it by just doing a re-install!  

Sorry, I spent too much time working on windoze machines... :rolleyes:  Old habits & all that.

---

### Post by Iowan on 2006-12-20
Of course I can't find it now, but I (vaguely) remember a thread that told how to change permissions on **resolv.conf** so it *couldn't* be overwritten.

---

### Post by handy on 2006-12-21
The following command makes **resolve.conf** immutable:

**sudo chattr +i /etc/resolv.conf**

This one makes it writable:

**sudo chattr -i /etc/resolv.conf**

---

### Post by Iowan on 2006-12-21
THAT'S the one! (or the meat of it, anyway...)

---

### Post by ubuntwinkel on 2006-12-22
I thought this would work.  Thanks for the idea.  However:
```
hp@hpbox:~$ sudo chattr +i /etc/resolv.conf
chattr: Inappropriate ioctl for device while reading flags on /etc/resolv.conf
```
it looks as though it doesn't.  And I have no idea yet what that response might be telling me.  Meantime, my little command ```
gksudo cp /etc/resolvconf.copy /etc/resolv.conf
``` works a charm every time, and I have set it up as an icon on the panel, as you suggested.  It's as good as perfect, really.

---

### Post by handy on 2006-12-22
I look forward to a master like Mips or Stream303 picking up your problem, because it is a real challenge beyond most of us mere mortals.

The thing that I did just do that I wont be appreciated for, is that I just passed the buck...

?

---

