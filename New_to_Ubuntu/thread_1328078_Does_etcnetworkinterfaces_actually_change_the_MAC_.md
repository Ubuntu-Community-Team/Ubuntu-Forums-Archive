---
title: "Does /etc/network/interfaces actually change the MAC address of wlan0?"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by JamesParnell on 2009-11-16
does it? or does it just clutter up the file more? if not, how do i actually change it, and is there a way of finding out if it has worked?

---

### Post by mbzn on 2009-11-16
Not sure about your way, Could work?

Here's the way i know

ifconfig eth0 down hw ether 00:00:00:00:00:01

ifconfig eth0 up

Just change eth0 to the device you need to change.
Hope this helps

---

### Post by JamesParnell on 2009-11-16
thanks for that,  i remembe3r being told the terminal way before, but i forgot it, thanks for the command. 
 
ok when i do it (as i cant get acces to wifi i will have to read off the moniutewr and type it out) i get this message:
 
**SIOCSIFFLAGS: **Permission denied
**SIOCSIFHWADDR: **Operation not permitted.
 
 
how can i get around that

---

### Post by t0p on 2009-11-16
There's also a command-line program, **macchanger**.  I don't know if it's in the repositories though, you may have to google it.

Once you've used macchanger, or the ifconfig commands in the previous post, you can check if the mac number has changed by typing into the terminal

```
ifconfig
```

It will list your internet interfaces, with mac numbers etc.

Also, note that this doesn't actually *change* your mac number permanently, it just spoofs it.  The mac number will return to normal next session.

---

### Post by t0p on 2009-11-16
> **JamesParnell said:**
> thanks for that,  i remembe3r being told the terminal way before, but i forgot it, thanks for the command. 
 
ok when i do it (as i cant get acces to wifi i will have to read off the moniutewr and type it out) i get this message:
 
**SIOCSIFFLAGS: **Permission denied
**SIOCSIFHWADDR: **Operation not permitted.
 
 
how can i get around that

Hmm, permissions issue.  Prefix the commands with 'sudo'.

---

### Post by JamesParnell on 2009-11-16
ah yes, our friend sudo. thanks

---

