---
title: "Lost on boot problem"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by FoFa on 2010-01-11
I did a search, but no anwser (but can't say I am searching properly). So thought I would ask.

I have ubuntu 8.1. (4 I think) loaded via WABI.

My ran a Reg. Clean (which I have done before) on my XP, and awhile later it started Blue Screening on me. So I restored the Reg. settings, but it still blue screens with Multiple_IRP_Complete_Requests. Crap, so boot into Ubuntu and research that (thinking it was a XP problem). NOTE Ubuntu has saved me a time or two before.
It starts the ububtu boot, the ubuntu load screen (the graphics status load window) starts, runs about 5-10 seconds, then it goes to a text screen (bear with me, I didn't write it all down) with a prompt of initramfs (but the I can't remember the program it was running, something I am sure yall know, but appears like a command front end).

So Now I am totally lost. What should I do at that point?

BTW Windows still doesn't run either.
Could it be hardware, and if so, is there a way to determine it via ubuntu?

---

### Post by Bucky Ball on 2010-01-11
Not really but from the LiveCD you could check the ram. If you can get the LiveCD to run that is. If not it probably is hardware but sounds a lot like it. In your BIOS you could also look for any self tests as a first step. Many have RAM and HDD self-tests.

There is the long term support release, Hardy Heron 8.04 LTS (currently at 8.04.3) and Intrepid Ibex 8.10.

---

### Post by mbzn on 2010-01-11
This looks like a RAM problem, you can check it on memtest you'll find as an boot option on the live cd. You should be able to run it, and usually gives errors quickly but long testing could be necessary.

---

### Post by FoFa on 2010-01-11
How would one create a "live" cd?

---

### Post by audiomick on 2010-01-11
> **FoFa said:**
> How would one create a "live" cd?

The live CD is probably the one you installed from. Or download and burn a new one
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

There are instructions here
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

