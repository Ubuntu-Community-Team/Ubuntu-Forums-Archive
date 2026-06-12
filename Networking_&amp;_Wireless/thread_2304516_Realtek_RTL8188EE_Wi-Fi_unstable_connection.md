---
title: "Realtek RTL8188EE Wi-Fi unstable connection"
date: 2015-11-27
forum: Networking &amp; Wireless
---

### Post by rammar on 2015-11-27
Hi, I tried everything, I installed an alternative driver rtlwifi_new but nothing ...
I tried to compile the drivers downloaded from the realtek and I received errors in compilation ...
The connection is not constant, when I connect to wifi university is very slow, no more than 0.10 mb / s download ...
It is unusable, while at home is fine.
I exclude that the network is a problem because other people with Ubuntu does everything correctly.
I have 3.19.0-33-generic x86_64 as kernel and Ubuntu 14.04 LTS.


I hope we can find a solution
Thanks a lot

---

### Post by Hadaka on 2015-11-29
Hi, carefully follow these instructions.
[http://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again](http://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again)
good luck

---

### Post by bathynomusBLUE on 2015-11-29
I have a RTL8192EE, not a RTL8188EE

However, this fix worked for me.
[http://ubuntuforums.org/showthread.php?t=2255911&p=13183240#post13183240](http://ubuntuforums.org/showthread.php?t=2255911&p=13183240#post13183240)

---

### Post by Hadaka on 2015-11-29
@bathynomusBLUE ,rather than hijack a thread that isnt even the
same issue or card as yours,Please start your own thread and perhaps
someone will help you.
thanks.

---

### Post by bathynomusBLUE on 2015-11-29
> **Hadaka said:**
> @bathynomusBLUE ,rather than hijack a thread that isnt even the
same issue or card as yours,Please start your own thread and perhaps
someone will help you.
thanks.

Hadaka, you sent me an IM as well as posted here that I was attempting to "[COLOR=#000000]hijack[/COLOR]" this thread. My attempt was to help Mario_Ramundo. If you examine the link, it is related to his card. Have a good day.

One can also see that the Git has his specific card mentioned: [https://github.com/lwfinger/rtlwifi_new](https://github.com/lwfinger/rtlwifi_new)

---

### Post by Hadaka on 2015-11-29
@bathynomusBLUE,
 You are correct and I apologize for misunderstanding.

---

### Post by rammar on 2015-11-30
> **Hadaka said:**
> Hi, carefully follow these instructions.
[http://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again](http://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again)
good luck

I followed the instructions contained in the link and doing a speedtest download speed is 1.69 MB/s, up from 0.53 MB/s.
Before:
[IMG]http://i66.tinypic.com/2j3645g.png[/IMG]
After: 
[IMG]http://i65.tinypic.com/1ooq5z.png[/IMG]

> **bathynomusBLUE said:**
> I have a RTL8192EE, not a RTL8188EE

However, this fix worked for me.
[http://ubuntuforums.org/showthread.php?t=2255911&p=13183240#post13183240](http://ubuntuforums.org/showthread.php?t=2255911&p=13183240#post13183240)

I tried to put these drivers, but did not work :(

---

### Post by Hadaka on 2015-11-30
hi, please go here [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
read the instructions and post the the wireless file.
you may also want to give this a try..
[http://ubuntuforums.org/showthread.php?t=2218087&page=2](http://ubuntuforums.org/showthread.php?t=2218087&page=2)
post#14

---

