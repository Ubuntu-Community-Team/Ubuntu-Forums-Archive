---
title: "Desktop uses large amount of data while doing nothing"
date: 2016-11-25
forum: Networking &amp; Wireless
---

### Post by leonard032 on 2016-11-25
Hey all,

I've got an old desktop running lubuntu setup for family use and have run into a strange problem. It's using a large chunk of data our available Internet usage, 44% in fact (according to the router). Which is saying something, considering I'm often watching videos and listening to podcasts on my iPod and it has only 22%. The family isn't doing that much on the computer either, Facebook, email, checking weather etc. We use the default Firefox browser with only a couple extensions. So something is eating it up, I just don't know what.
I installed Network Traffic Monitor, and I can see the traffic going up by a hundred bytes or so every couple seconds. Is that normal? This is with no programs running. Something else that seems very strange to me is that 16 of the 44% is being used on upload... but nobody's uploading anything on that computer.

Any advice or suggestions would be much appreciated.

Thanks!

Edit: Forgot to mention that it's a wired connection, not sure if that makes a difference.

---

### Post by ian-weisser on 2016-11-25
Run 'top' or 'htop', and look for activity that corresponds to the network traffic. That will tell you which applications are hogging your bandwidth.

---

### Post by vasa1 on 2016-11-25
> **leonard032 said:**
> ..., Facebook, email, checking weather etc. We use the default Firefox browser with only a couple extensions. ...
Is Facebook left running all the time? How often is your program, whichever that is, checking the weather? Which Firefox extensions?

---

### Post by leonard032 on 2016-11-25
> **ian-weisser said:**
> Run 'top' or 'htop', and look for activity that corresponds to the network traffic. That will tell you which applications are hogging your bandwidth.
Will try that tomorrow.

> **vasa1 said:**
> Is Facebook left running all the time? How often is your program, whichever that is, checking the weather? Which Firefox extensions?
Facebook is not, though Gmail is often left open. I just meant going to a website online for the weather. Extensions are web of trust and adblock.

---

### Post by vasa1 on 2016-11-25
> **leonard032 said:**
> Will try that tomorrow.


Facebook is not, though Gmail is often left open. I just meant going to a website online for the weather. Extensions are _web of trust_ and adblock.
Re. WOT, you may want to look at [Web of Trust (WOT) - you might want to remove this browser add-on]("https://ubuntuforums.org/showthread.php?t=2342528"), not that that has anything to do with your actual problem.

---

### Post by leonard032 on 2016-11-28
> **ian-weisser said:**
> Run 'top' or 'htop', and look for activity that corresponds to the network traffic. That will tell you which applications are hogging your bandwidth.
It seems to be Firefox. When I have it open there's the steady low usage, when it's closed the traffic drops to 0. So could it just be that leaving it open day uses up a bunch of data? Im surprised as when we disconnected this computer usage dropped by around 700MB/day.

> **vasa1 said:**
> Re. WOT, you may want to look at [Web of Trust (WOT) - you might want to remove this browser add-on]("https://ubuntuforums.org/showthread.php?t=2342528"), not that that has anything to do with your actual problem.
Huh, thanks for the heads up.

---

### Post by leonard032 on 2016-12-16
Well either NTM or my Router is lying. NTM says I've had around 800MB traffic since the 4th. The router says it's used more than 4 GB. What else can I do?

---

