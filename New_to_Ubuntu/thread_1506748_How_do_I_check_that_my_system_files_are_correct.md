---
title: "How do I check that my system files are correct?"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by bwallum on 2010-06-10
Hi

I have some strange things going on following yesterday's updates. Evolution running slow, Hardware Drivers not working, lethargy due to flat out processor intermittently.

How can I check my system against the current release? 
How can I repair my system without a re-install?

---

### Post by Metrop021 on 2010-06-10
try this: Boot from a live cd, open a terminal, and type this:

```
sudo fsck -a /dev/sda1
```

except replace sda1 with whatever partition name your ubuntu is running on, that should check and repair corruption in the partition.

---

### Post by bwallum on 2010-06-11
OK that returned clean, and then some stats.

However the issues persist and I guess what I should have said is how do I check my Lucid installation against a good set of files.

The manifestations of my problem (on Lucid i386) are:

When Ubuntu boots up the Desktop background and links are up reasonably on time. It then takes another 30 seconds for the top and bottom panels to appear (about 28 seconds late).

Hardware Drivers shows a semi populated window and says that no proprietory drivers are used in this system. I am not offered any although an nVidia card is present and if I run the live cd then it is detected and I am offered a proprietory driver for it.

Evolution runs very slow. Slow to initially appear and slow to do a send/receieve, taking a good minute longer than before the updates arrived.

Something has gone wrong with the updating process. How do I check the current files setup (to include applications) with a default good, latest. set?

---

### Post by bwallum on 2010-06-11
I've done a re-install, now complete, as probably the quickest way to resolution. However it would be good to know what most likely happened with the system if you have any further ideas.

---

