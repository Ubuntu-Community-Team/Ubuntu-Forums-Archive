---
title: "WiFi connection detected as Ethernet - iwconfig no wireless extensions"
date: 2017-12-26
forum: Networking &amp; Wireless
---

### Post by aryary88 on 2017-12-26
Hi everyone! New to the forum and also an Ubuntu noob.
I've been driving myself up a wall for several hours now, so I'm caving and asking for help.

So, since I'm studying network security, I thought I'd give this tutorial [https://www.makeuseof.com/tag/wpaprotected-wifi-secure-reaver](https://www.makeuseof.com/tag/wpaprotected-wifi-secure-reaver) a try and see if I could get my WiFi password to show up. I have a VM with Lubuntu 16.04 on it.

After several bumps along the way, I finally got to the last step, "airmon-ng start wlan0". This gives me a short list of processes that might interfere, then there's: Interface/Chipset/Driver and... absolutely nothing below them.

So I tried iwconfig and indeed, what I get is:
lo           no wireless extensions.
enp0s3   no wireless extensions.

This is weird, seeing as I'm on a laptop and connected through WiFi (which I know for a fact, as the Ethernet cable is not even physically plugged in!).
That's when I went to check the Network Connections panels and realised my WiFi connection is actually marked down as Ethernet.

Any help or pointers at all on what might be wrong? I'm really at my wits' end over here.
I will supply all necessary extra info of course!!

Thanks in advance.

---

