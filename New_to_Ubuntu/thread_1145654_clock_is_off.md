---
title: "clock is off"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by DarinB on 2009-05-01
i was on my vista partition for about three hours today and when i booted to jaunty., my clock was off reboot didn't fix it
i can't seem to sync it it wont take so i changed it my hand and not it is off.
any ideas what to do

---

### Post by llamabr on 2009-05-01
If I understand your question, your clock is not syncing?  try:

```
sudo ntpdate rolex.peachnet.edu
```

Or your favorite server (this one is at georgia tech).

---

### Post by DarinB on 2009-05-01
what does this mean 
darin@darin-desktop:~$ sudo ntpdate rolex.peachnet.edu
sudo: timestamp too far in the future: May  1 21:56:36 2009
[sudo] password for darin: 
 1 May 21:02:12 ntpdate[4677]: the NTP socket is in use, exiting
darin@darin-desktop:~$

---

### Post by DarinB on 2009-05-01
i thought there was a sync button or something in admin>time and date it is set to here is a screenshot
[ATTACH]112088[/ATTACH]

---

### Post by llamabr on 2009-05-01
Hi.  I have no idea how to do it with gui.

What's the output of

```
date
```

---

### Post by DarinB on 2009-05-01
darin@darin-desktop:~$ date
Fri May  1 21:17:36 EDT 2009
darin@darin-desktop:~$ 
 it is two minutes off though with my cell phone

---

### Post by llamabr on 2009-05-01
Right.  Besides medium roast ubuntuland, where are you?  On the east coast?

---

### Post by llamabr on 2009-05-01
The "socket in use" error is because you're running ntpd already, and can't run both.  You can confirm this with

```
ps aux | grep ntpd
```

It should update your clock occasionally.  Try restarting that daemon, and see if that helps.

Actually the man page says it makes small adjustments over time, so maybe it'll just eventually fix itself.

---

### Post by 73ckn797 on 2009-05-01
Is the clock set right in the bios?

---

### Post by DarinB on 2009-05-01
darin@darin-desktop:~$ ps aux | grep ntpd
ntp       3544  0.0  0.0   4220  1176 ?        Ss   20:50   0:00 /usr/sbin/ntpd -p /var/run/ntpd.pid -u 112:123 -g
darin     5404  0.0  0.0   3336   800 pts/0    R+   21:38   0:00 grep ntpd
darin@darin-desktop:~$ 

this is the read out

---

### Post by DarinB on 2009-05-01
i read somewhere that if you use windows it messes up the ntp??????

---

### Post by 73ckn797 on 2009-05-01
> **DarinB said:**
> i read somewhere that if you use windows it messes up the ntp??????


My experience was in Windows not having correct time. Ubuntu was fine but the system bios clock was off affecting Windows.

---

### Post by DarinB on 2009-05-02
to catch up today when i booted up the pc and went directly in to Ubuntu the clock was right on, i wonder if being on windows for few hours did it, It was like the clock stopped and when i booted to ubuntu the clock was behind the exact time i was on windows. Maybe since i was on windows so long my ubuntu died of a broken heart. lol
But today all is fine, funny thing

---

