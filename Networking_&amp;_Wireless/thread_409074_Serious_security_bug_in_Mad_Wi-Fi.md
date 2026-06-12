---
title: "Serious security bug in Mad Wi-Fi?"
date: 2007-04-14
forum: Networking &amp; Wireless
---

### Post by whitefort on 2007-04-14
I just came across this article on my Yahoo page:

[http://news.yahoo.com/s/pcworld/20070413/tc_pcworld/130717](http://news.yahoo.com/s/pcworld/20070413/tc_pcworld/130717)

---

### Post by elamericano on 2007-04-14
I wouldn't worry about it. I use the latest driver just for performance benefits, but the security exposure is minimal in any case. Notice the article says that they exploited this on Windows and Mac - which is utter BS. An exploit may not exist for this crash. It certainly doesn't for the Mac.

Other mitigating factors: The attacker would have to be in wireless range of you, a few hundred feet. You need to be running a vulnerable driver. The attacker needs to know what OS and what OS version you are using. You may need to be using the specific chipset the attacker expects. The attack needs to work - apparently, even the rigged demo was hit or miss.

A wireless vulnerability seems more threatening than an internet worm, but it is much less so. Remember, fuzzing can cause a crash, but it won't write an exploit. Maynor and Ellch can't write you one either ;-)

---

### Post by elamericano on 2007-04-14
Oh, by the way, the patched driver version is 0.9.2.1, released 2006-12-07.

Try modinfo ath_pci to see what you have. 

Maybe someone else can say which is the first version of ubuntu to have it.

---

### Post by whitefort on 2007-04-14
Thanks for the reassurance.  A couple of recent things have turned me into a total computer paranoid.

1) I'm new to Ubuntu/Linux (First installation round about Jan/Feb this year)
2) I'm new to wireless (about March)
3) I'm new to owning a laptop (April)
4)  I've been reading stuff about computer security.

On my non-wireless desktop Windows machine, I was well up to speed on security (or rather, I trusted propriatory software to do the job for me!).  As a new Linux/wireless/laptop user, I'm scared stiff that I'm overlooking something vital!!  :) 

Thanks again!

---

