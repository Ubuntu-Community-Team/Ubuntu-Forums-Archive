---
title: "traceroute"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by Drenriza on 2010-05-04
Why is the traceroute command no longer avaliable in ubuntu? when changing to 10.04.
 
And if this command is no longer avaliable, what has substituted it?
i see a command traceroute6 but i just keep getting.
 
Unknown command error.

---

### Post by r-senior on 2010-05-04
You can install it with 

$ sudo apt-get install traceroute

As to the "why". Don't know. ;)

---

### Post by Drenriza on 2010-05-04
then what is the traceroute6 command?

---

### Post by xumuk37 on 2010-05-04
```
sudo apt-get install traceroute
traceroute www.google.com
```

> **r-senior said:**
> You can install it with 


As to the "why". Don't know. ;)

:lolflag:

---

### Post by r-senior on 2010-05-04
> **Drenriza said:**
> then what is the traceroute6 command?
For ipv6, presumably ...

[http://en.wikipedia.org/wiki/Ipv6]("http://en.wikipedia.org/wiki/Ipv6")

[http://ubuntuforums.org/showthread.php?t=87798]("http://ubuntuforums.org/showthread.php?t=87798")

---

### Post by Grenage on 2010-05-04
> **Drenriza said:**
> Why is the traceroute command no longer avaliable in ubuntu? when changing to 10.04.

I've had to install it for the last few released.  I can't even recall when it *was* included.

---

### Post by VinDSL on 2010-12-03
Er...

Just use tracepath instead of traceroute.  

It's installed (by default) and it's better!  ;)

---

### Post by The Cog on 2010-12-03
I prefer **mtr** to traceroute/tracepath. Can't remember if it's installed by default though.

---

### Post by Rubi1200 on 2010-12-03
mtr-tiny is installed by default on 10.04; don't know about other versions.

---

### Post by VinDSL on 2010-12-03
> **The Cog said:**
> I prefer **mtr** to traceroute/tracepath. Can't remember if it's installed by default though.mtr is great too!  And, it's installed by default in Ubu 10.10 (at least).

The only thing is, it's rather hard to select the output (capture the text) for inclusion in posts.

I suppose I could take a screenie, but tracepath is quicker, for demo purposes.

Am I missing something?

Is there some way to freeze mtr (with a switch, or whatever), and copy n' paste the results in posts?!?!?

---

### Post by trunx on 2012-10-12
> **VinDSL said:**
> Is there some way to freeze mtr (with a switch, or whatever), and copy n' paste the results in posts?!?!?

You can simply change the ping interval to 999 (pressing i and then enter 999)and you will get your freeze.

---

### Post by wildmanne39 on 2012-10-12
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

