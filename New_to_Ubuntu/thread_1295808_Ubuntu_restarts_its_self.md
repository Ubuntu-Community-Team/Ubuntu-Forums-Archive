---
title: "Ubuntu restarts its self"
date: 2009-10-19
forum: New to Ubuntu
---

### Post by aja on 2009-10-19
Could someone help?

I have a duel boot machine Ubuntu 9 / windows xp. I have just noticed that the other day that it has been starting by its self.
And I have no ideal weather it is windows or ubuntu??  

Could anyone tell me has this been a issue in jaunty jackalope? If so how to go about fixing it??

Thanks

aja

---

### Post by martrn on 2009-10-19
Firstly you need to know which OS was responsable when the computer went for a restart.  There are 4 (or more) answers.

1.  It went for a restart during a windows sesstion
2.  It goes for a restart during an ubnutnu session.
3.  It goes for a restart during both sessions.
4.  It goes for a restart when my next door neighbour plugs his cement mixer into the plug-socket on the wall agacant to my apartment.

Check your hardware first, and if only happens with ubuntu, then check your kernel modules aka also known as drivers.

---

### Post by ikt on 2009-10-19
system log may help as always.

System > Admin > log file viewer.

---

### Post by aja on 2009-10-20
Thank you for your respons

The last time it started, I had just out of bed when i heard it start right out the blue. I had been using windows and ubuntu the night before. But when I left I instructed both OS to shut down.

I have checked system log and below is what i copied from it: But I am not sure if it means anything, as I have Ubuntu as my default OS to start when i start my duel boot computer.

If putting the computer in to suspend mode be responsable for this ??




syslog
Oct 19 06:39:37 me-desktop syslogd 1.5.0#5ubuntu3: restart.

Messages

Oct 19 06:39:37 me-desktop syslogd 1.5.0#5ubuntu3: restart.


Daemon log

Oct 19 06:39:42 me-desktop ntpd[2889]: ntpd 4.2.4p4@1.1520-o Wed May 13 21:05:42 UTC 2009 (1)

Auth.log

Oct 19 06:39:45 me-desktop dbus-daemon: Rejected send message, 5 matched rules; type="error", sender=":1.13" (uid=0 pid=3186 comm="/sbin/wpa_supplicant -u -f /var/log/wpa_supplicant") interface="(unset)" member="(unset)" error name="fi.epitest.hostap.WPASupplicant.InvalidInterface" requested_reply=0 destination=":1.12" (uid=0 pid=3174 comm="/usr/sbin/NetworkManager --pid-file /var/run/Netwo"))


Userlog

Oct 19 06:39:47 me-desktop hp: io/hpmud/pp.c 627: unable to read device-id ret=-1

---

### Post by martrn on 2009-10-20
> **aja said:**
> 
If putting the computer in to suspend mode be responsible for this ??


Firstly check your bios settings.  If there is an option in your BIOS that says "automaticly shutdown/start computer at" ,....., then check that this is empty.  Check any suspend/resume Wakeup on Lan/Sound/modem/usb requests and ensure they are all off so that it will only resume on keyboard events and mouse settings. Wakeup on lan is daft becuase there are always wakeup on lan requests any-way.  I used to have wakeup on lan set to four computer and hey presto switch one on and all the computer wake up and spring to life whenever you go near one of them.  Funny at first but a little annoying later.

If it is really annoying you that a computer springs to life at any given moment, it should be possiale to prevent suspend/wakeup-on requests via the bios.  Another option would be to ensure your OS settings do not suspend and fully power down when you press the off button or reset switch.

I don't see a problem personally with a computer starting by itself, but some people do not like it.

Do you have a cat that lies across a keyboard or anything like that ?

---

### Post by stalkier on 2009-10-20
You may want to run MemTest. I recently was working on a PC for a friend. Her PC restarted over and over. I ran the LiveCD and chose MemTest. It showed errors on one stick of RAM. I pulled the stick and it ran fine.

---

### Post by martrn on 2009-10-20
> **stalkier said:**
> ...I pulled the stick and it ran fine.

Also PSU (power supply unit) problems are notorious for resetting a computer if you do not expect it to be doing what it is doing another would be bad / malfunction power lines, and spikes and surges on the line.

---

