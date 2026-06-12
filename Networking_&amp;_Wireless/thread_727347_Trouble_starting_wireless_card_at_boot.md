---
title: "Trouble starting wireless card at boot"
date: 2008-03-17
forum: Networking &amp; Wireless
---

### Post by SpiggidyBob on 2008-03-17
Hey guys, I've finally got Ubuntu up and running, but I've still got one problem.  I can't get my wireless card to connect at startup.  To start it I have to run ```
sudo /etc/init.d/networking restart
``` After that it connects fine.  I used [this]("http://ubuntuforums.org/showthread.php?t=684495") link to set everything up (great guide by the way) but even after editing the rc.local file and making it executable it still doesn't work.    None of the other threads seemed to help out either.  So any help would be appreciated.

---

### Post by SpiggidyBob on 2008-03-17
> disregard, just rebooted and it came right up.  not sure what the deal was, but hey, it's working

Just rebooted and it didn't come up automatically.  Any ideas?

---

### Post by SpiggidyBob on 2008-03-18
Anyone?

---

### Post by Megatog615 on 2008-03-18
This seems to be a weird bug with Gutsy. Before I upgraded to the Hardy Development version I had to have a script that runs on startup that does sudo /etc/init.d/networking restart. Just put it in a script that runs on login(ON LOGIN! Not /etc/rc.local!), except substitute sudo with gksudo. Once Hardy comes along in April you won't have this problem.

---

### Post by SpiggidyBob on 2008-03-19
Where do I put it so it runs at login?  Is it .bash_login or .bashrc?  I tried googling them, but nothing I read really made them seem any different.

---

### Post by Megatog615 on 2008-03-22
If you're running GNOME then there's a tool for setting up apps that run on login.

---

### Post by zujik on 2008-03-22
Go to:

```
SYSTEM -> PREFENCES -> SESSIONS -> ADD
```

---

### Post by Eiríkr on 2008-03-22
The interfaces that get listed when you run [font=courier]sudo /etc/init.d/networking restart[/font] are listed in the [font=courier]/etc/network/interfaces[/font] file.  Often times for some reason or another, the interfaces that don't come up properly on boot are missing the "auto" flag, and thus are *not* marked for automatic configuration on boot.  Assuming your wireless interface is [font=courier]wlan0[/font], you would add the following line to the [font=courier]/etc/network/interfaces[/font] file (assuming it's not there already):
[code]auto wlan0[/font]
Once marked for "auto" config, the interface will be subject to the following commands:
[code]sudo ifup -a
sudo ifdown -a[/font]
The [font=courier]-a[/font] flag specifies "auto" intefaces, and these commands are the very ones the system uses on bootup and shutdown, and for the [font=courier]sudo /etc/init.d/networking restart[/font] command.  

If the "auto" line is already there, you've got a different problem entirely.  Let us know what you find.  

Cheers,

Eiríkr

---

