---
title: "Wireless disappearing after resuming from standby"
date: 2014-10-31
forum: Networking &amp; Wireless
---

### Post by asearle on 2014-10-31
Hi Everyone,

I have a Samsung Series 5 ultrabook (535u3c) which works pretty well but is currently giving me a very(!) irritating problem with wireless:

When I am mobile I often switch wireless off (with Network Manager) to save power.  It is no problem to switch it on again.  But if I go into standby (which I often do) I find that, after resuming/re-awaking, although wireless is an available option in Network Manager, when I click it wireless doesn't come up and the option becomes greyed out.  I then need to reboot (agghhh!) to get wireless back.

I have tried the various suggestions mentioned in this post (below) but they didn't help ...

[http://askubuntu.com/questions/365112/lubuntu-13-10-laptop-loses-wireless-after-sleep](http://askubuntu.com/questions/365112/lubuntu-13-10-laptop-loses-wireless-after-sleep)

This problem a big irritation for me so any tips would be most gratefully received.

Yours,
Alan Searle

---

### Post by ibjsb4 on 2014-10-31
Next time it happens, try a restart.
```
sudo /etc/init.d/networking restart
```

---

### Post by asearle on 2014-11-01
This solution (post #92) fixed the problem most of the time ...

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1286552](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1286552)

... but sometimes I still need to do ...

sudo nmcli nm sleep false

... to get things going again.

Thanks for the last tip:  I will try the network restart command too.

As it is I really like the size and format of my Samsung Series 5 but I've had it for two years now and it is still flakey with, alongside this network problem, various inexplicable, random lock-ups (e.g. after waking from sleep or when trying to shut down).  This was the case with Ubuntu (various releases) and is also the case with Lubuntu 14.04.  I was hoping that, as new releases came out this unit would stabilize but it hasn't been the case.  Unfortunately.

This is a big shame because I have used Ubuntu with a number of PC and laptops and it was mostly "rock-solid".  I can't understand why things are different with the Series 5 (especially as this is a similar model to the ChromeBook which is designed to run Linux as default).

Any tips would be a real help.

Yours,
Alan Searle

---

### Post by wildmanne39 on 2014-11-01
Hi, would you please post the answer here so the whole community can benefit. You do know that the answer in post 92 is the second half of the answer in the first link you posted right?

---

