---
title: "no sound after latest update"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by rocka on 2010-07-28
Hi,

this machine has been running fine for ages now, but recently I got one of those updates that pops up now and then, and this time it asked me to reboot. Now, I have no sound.

It was working fine before [only a few minutes ago] I haven't changed anything else, certainly not any hardware been unplugged or anything.

I did a quick little search around here, and saw some other ppl did "aplay -l" so I did that:

```
merlin@merlin-desktop:~$ aplay -l
aplay: device_list:223: no soundcards found...
merlin@merlin-desktop:~$ 
```

how do I fix this?

---

### Post by rocka on 2010-07-28
Hi,
this is getting weirder...


I thought I'd try restarting, but now I find that the computer will not reboot or restart - when I try, it just gives me the log in screen again and again.

wtf do I do now???

---

### Post by rocka on 2010-07-28
...

it's bizarre.

I ended up doing
sudo shutdown now
and now it's back, sound and all!

:confused:

---

### Post by khelben1979 on 2010-07-28
I've seen this before and to my experience it's because the Linux kernel get's replaced by a newer one, a so called kernel upgrade. The new kernel which is responsible for the Linux sound module works better after the system has been restarted, or... shall we say, it starts working again! :)

---

