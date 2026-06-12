---
title: "ubuntu10.04 server installed , no suspend ; hibernate"
date: 2010-05-22
forum: New to Ubuntu
---

### Post by cllow2020 on 2010-05-22
install ubuntu10.04 server installed , with setup software RAID1,
motherboard VIA P4900-M2 bios with setup suspend enable,  but **NO** suspend; hiibernate working,  how to enable it ?

---

### Post by cariboo on 2010-05-23
Have a look at [this]("http://ubuntuforums.org/showthread.php?t=591036") thread.

---

### Post by cllow2020 on 2010-05-23
i can pm-suspend it in terminal, but it won't listen to bios to perfom suspend S3 when timeout, i mean a **_auto suspend _**that follow bios suspend timeout setting "suspend timeout to S3". ubuntu10.04 doesn't come with support auto suspend install kernel default.
 
 
add.....
need something like this, if kernel not complied it default ?
sudo update-rc.d /etc/init.d/autosuspendbioss3.sh defaults
 
or ...
 
sudo vi */etc/rc.local *
......
 
or something todo with 
/etc/pm/sleep.d/...
 
 
 
any input ?

---

### Post by cllow2020 on 2010-05-23
oop! my mistake , overlook that kernal 10.04 default , lucid loaded with  acpid....
[http://manpages.ubuntu.com/manpages/lucid/en/man8/acpid.8.html](http://manpages.ubuntu.com/manpages/lucid/en/man8/acpid.8.html)
**acpid**  is designed to notify user-space programs of ACPI events.  **acpid**
should be started during the system boot, and will run as a  background
process,  by default...
 
i unloaded pm-utils; pm-support; APM. remain simple acpid and acpitool to play around...

---

### Post by cllow2020 on 2010-05-24
weird, from manualpage [http://manpages.ubuntu.com/manpages/lucid/man8/rtcwake.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/rtcwake.8.html) found RTCWAKE, but no RTCSLEEP ???? could be put to "sleep" is more difficult than "wake"  :)

---

### Post by adamk918 on 2010-05-24
I'm not trying to be rude or anything, but since I'm still learning about Linux, why would you want to suspend or hibernate a server?

---

### Post by SRST Technologies on 2010-05-24
I too wonder why a server would ever be suspended.

---

### Post by cllow2020 on 2010-05-25
> **SRST Technologies said:**
> I too wonder why a server would ever be suspended.
 
the main resson is i want to setup samba/nas server for files shareing  [COLOR=black]**_at home_** for my kids share his home works / school projects... my wife cooking resipi...to all his/he friends and out side world. isn't that fun ? that what's mean of [/COLOR][SIZE=5][COLOR=red][SIZE=4][COLOR=lime]"UBUNTU"[/COLOR][/SIZE] [/COLOR][/SIZE]
 
server can be sleep when no using is perfact. :guitar: . besides all it need to wakwup is about couples of 10 seconds , is not critical for home using , but it gain in saving some maintences cost and electricity bill $$$$. if server need to wakeup just WOL it. if your router allow todo.
 
by the way , i found sleep doemon, [http://manpages.ubuntu.com/manpages/lucid/en/man8/sleepd.8.html](http://manpages.ubuntu.com/manpages/lucid/en/man8/sleepd.8.html)
 
anybody try it before ?

---

### Post by cllow2020 on 2010-05-25
good news sleepd doemon is working to suspend at 2 minutes.
bad news is it un-condition suspend make my system crash due to i'm on other tty while it suspending 
 
i need a smart suspend.......

---

### Post by cllow2020 on 2010-05-25
found 
[http://www.thinkwiki.org/wiki/Installing_Debian_Lenny_on_a_ThinkPad_T60#automated_sleep](http://www.thinkwiki.org/wiki/Installing_Debian_Lenny_on_a_ThinkPad_T60#automated_sleep)
look good :) 
 
but sleep doemon need some gnome device manager while installing, but my server no GUI only CLI, not sure will it crash again ?

---

