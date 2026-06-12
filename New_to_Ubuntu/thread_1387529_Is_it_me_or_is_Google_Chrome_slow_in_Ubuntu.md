---
title: "Is it me or is Google Chrome slow in Ubuntu"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by abhiroopb on 2010-01-22
I use Chrome at home on my laptop on Ubuntu 9.10 (specs in my signature).

At work I also use Chrome on a desktop with the following specs:

2.6 Ghz Core Duo, 2GB RAM.

Obviously the processor at work is MUCH faster. However, at home whenever I open more than 5-6 tabs the browser slows down a LOT. Happens with firefox as well.

Is this a settings issue or is it merely because of the slow CPU?

---

### Post by SymphonicNerd on 2010-01-22
Im not the authority on this by any means, but it seems that if it only happens when you have 5-6 tabs open and in firefox or chrome then I would have to imagine its processor speed. On an old dell desktop I had a similar problem and i solved it by opening different instances of firefox and limiting each one to 2 tabs, so try fiddling. But i imagine that your problem lies with your hardware and not your software

---

### Post by abhiroopb on 2010-01-22
Thanks, and you don't think it may be OS related? I guess I could check out how Chrome works on Windows on my laptop. 

methinks it's time to upgrade!

---

### Post by lovinglinux on 2010-01-22
I don't think it is your processor speed. I had a Pentium 4 single core that could do better than that.

Nevertheless, since the problem can be replicated on both Firefox and Chromium, it suggests it's a system issue. It could be a hardware problem too, but your processor is fast enough to deal with five browser tabs.

---

### Post by abhiroopb on 2010-01-22
To be honest I haven't used firefox for a while so I'm not totally sure whether it is exactly the same.

In Chrome if I go into google reader, and start opening new tabs with feeds after about 5 tabs google reader becomes unresponsive and I have to wait a bit before I can continue opening tabs.

I can also hear my computer making a lot of noise.

My laptop is about 3.5 years old, so I'm not expect anything magical. But, it's great at work where I can open up 20 tabs without any problem at all.

Any ideas on what system issues it could be? Naturally if it's hardware not much I can do, but, anything Ubuntu 9.10 specific?

---

### Post by lovinglinux on 2010-01-22
> **abhiroopb said:**
> To be honest I haven't used firefox for a while so I'm not totally sure whether it is exactly the same.

In Chrome if I go into google reader, and start opening new tabs with feeds after about 5 tabs google reader becomes unresponsive and I have to wait a bit before I can continue opening tabs.

I can also hear my computer making a lot of noise.

My laptop is about 3.5 years old, so I'm not expect anything magical. But, it's great at work where I can open up 20 tabs without any problem at all.

Any ideas on what system issues it could be? Naturally if it's hardware not much I can do, but, anything Ubuntu 9.10 specific?

Does it happen with any site? Some sites have some weird javascript code that causes high CPU usage. It could also be flash content.

---

### Post by Soul-Sing on 2010-01-22
> I can also hear my computer making a lot of noise.

cpu isn't noisy, maybe it is your harddisk....

---

### Post by ikt on 2010-01-22
> **leoquant said:**
> cpu isn't noisy, maybe it is your harddisk....

Indeed, very rarely do I have less than 10 tabs open and chrome is extremely quick, so it does seem to be a hard drive issue.

---

### Post by abhiroopb on 2010-01-22
Very good chance it is the HD actually.

Actually it happened just now.

I went into google reader, opened up about ten tabs in one go and the HD started spinning really fast and made a lot of noise. Then suddenly I got this message on the NEWLY opened tabs:

```

Aw Snap!
Something went wrong while displaying this webpage. To Continue, press Reload or go to another page.

```

This seems to happen quite a bit in Chrome when I try and launch a number of tabs.

Could it be the HD? Or something on the page itself that's messing it up?

Thanks!

---

### Post by 311005901 on 2010-01-22
> **abhiroopb said:**
> I use Chrome at home on my laptop on Ubuntu 9.10 (specs in my signature).

At work I also use Chrome on a desktop with the following specs:

2.6 Ghz Core Duo, 2GB RAM.

Obviously the processor at work is MUCH faster. However, at home whenever I open more than 5-6 tabs the browser slows down a LOT. Happens with firefox as well.

Is this a settings issue or is it merely because of the slow CPU?

Your problem may simply be with flash. Have you tried disabling it?

---

### Post by abhiroopb on 2010-01-22
Thanks. Yes I just downloaded Flash Blocker. I tried opening some tabs and after loading a few the error came up again :(

---

### Post by ubunterooster on 2010-01-22
I have a 1ghz amd cpu and a 200gb hdd. Chrome only occasionally acts up on mine but it's always dealing w/ flash heavy pages anyway. Go to: system-adminisration and start system monitor. This should show all ram, hdd, cpu activity.

---

### Post by abhiroopb on 2010-01-22
I use conky to monitor my stats. The CPU usually spikes when a lot of tabs are open. It has gotten better since I disabled Flash (using Flash Blocker).

---

### Post by 311005901 on 2010-01-22
> **abhiroopb said:**
> I use Chrome at home on my laptop on Ubuntu 9.10 (specs in my signature).

At work I also use Chrome on a desktop with the following specs:

2.6 Ghz Core Duo, 2GB RAM.

Obviously the processor at work is MUCH faster. However, at home whenever I open more than 5-6 tabs the browser slows down a LOT. Happens with firefox as well.

Is this a settings issue or is it merely because of the slow CPU?

What OS do you have on the computer at work?

---

### Post by abhiroopb on 2010-01-22
Windows XP

---

### Post by 311005901 on 2010-01-22
Do you have Chrome unstable installed? Sometimes these releases aren't the best...

Also, which version of Flash and Java do you have installed?

---

### Post by abhiroopb on 2010-01-22
I just downloaded whatever was the latest one on the website.

I just checked the build: 4.0.249.43

---

### Post by Durden on 2010-02-26
Chrome is disgustingly slow on my system too. Both my desktop and my laptop. Firefox is too if I have ipv6 enabled. I've disbaled ipv6 system wide though and Chrome is still dog slow, feels like 1998 and using Netscape again. I just gave up on it.

It's perfectly fast on Windows on the same machines. I've tried both Beta and Unstable, both equally slow. Stick to Firefox in my opinion.

---

### Post by abhiroopb on 2010-02-26
I'm on Windows 7 now and Chrome is blazing through everything!

see my blog for more info :)

---

### Post by laidback on 2010-02-26
Would it be possible to try your laptop at work so you can compare the laptop attached to a different internet connection, one that you know gives VG results.

---

### Post by lgalford on 2011-02-07
Hi, 

I have this  same problemen  and after digging a little bit on the internet I apply this solution and it worked great 

sudo aptitude -remove gnash gnash-common mozilla-plugin-gnash 

after I did that chrome and firefox started to work like a charm 

I hope this help 

Luis :guitar:

---

### Post by Oskenso on 2011-06-06
I seem to have a similar problem with chrome.. Loading and switching tabs in chrome is very slow on ubuntu, but fast on linux (same hardware). firefox however doesn't have this problem but, I prefer chrome to firefox. :(
edit: the tabs only seem to load slowly when a page is being re-rendered.

---

### Post by uRock on 2011-06-06
Necromancy - Please start a new thread. This thread was last active in February 2010.

Thread Closed

---

