---
title: "[SOLVED] Wireless slow and unreliable, no fix?"
date: 2008-08-20
forum: Networking &amp; Wireless
---

### Post by daltonlaffs on 2008-08-20
Hello forum peoples,

I just recently got a customized HP Pavillion a6500z desktop computer, which arrived at my house yesterday. I quickly put Windoze on a smaller partition and installed Ubuntu (my OS of choice), to see that my wireless was actually working out-of-the-box! Weee!

...But of course NOTHING I do is that easy. About 40 minutes later, the Internet stopped working -- the package I was downloading with apt-get stopped counting upwards, and Firefox gets stuck on "Looking up google.com...". I had to restart the computer to be able to reconnect -- nothing else I could do would fix the problem.

The wireless card is a PCI card that is identified by its driver as a Ralink RT73 (aka 2573), which connects to an external antenna through what looks kind of like a cable input, but smaller. I've tried using ndiswrapper to use the Windoze driver, but it had absolutely no effect (wlan0 actually disappeared from the network manager), presumably because it's a Vista-oriented driver.

Also, I took a speed test with this generic Linux driver and the speed averages 1000kb/s -- in Windoze, I can top 4000.

I could live with the slower speed if it would just stop breaking the connection so randomly! Any ideas would be greatly appreciated, because I *really* don't want to have to buy a different wireless card.

---

### Post by daltonlaffs on 2008-08-20
Well, I assumed in 40 minutes I'd at least have a generic "do something obvious" post by now.

But no matter! The problem is solved, now it's totally reliable and I have a higher speed than in Windoze.

I followed this guide, except on the step where you remove network-manager I just disabled it in System->Preferences->Sessions:

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=400236](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=400236)

It works PERFECTLY now. Super-props to whoever made that thread, and I'll probably be posting about that solution elsewhere :guitar:

---

