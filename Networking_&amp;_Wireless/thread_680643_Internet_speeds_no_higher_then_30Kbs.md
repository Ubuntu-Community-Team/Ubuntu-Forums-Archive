---
title: "Internet speeds no higher then 30Kbs"
date: 2008-01-28
forum: Networking &amp; Wireless
---

### Post by Mauzer on 2008-01-28
Hey,

I've recently changed from windows to Ubuntu. I've been using Fedora in school for a while and I started to prefer Linux over Windows.

However, since I installed Ubuntu, my internet speed hasn't been any higher then 30Kb/s. Unlike the usual 550Kb/s I had with Windows. At first I suspected it to be a driver problem. Since I use the rt2400 ralink wireless networkcard I had to get beta drivers. It didn't work for me though. However, lateron when I had linked my computer to the router by wire, the problem remained.

I'm using a Linksys BEFW11S4 router and tried installing the latest firmware in the hope it'd solve anything, but it has been without success.

I've also tried Kubuntu, and I had exactly the same problem. I really want to fix this, because I don't want to go back to Windows. But I've had enough of these horrible speeds.

Motherboard: Asus K8V-MX
Processor: AMD Sempron 3000+

Thanks in advance,
 Maurice

---

### Post by wieman01 on 2008-01-28
See this thread:

[http://ubuntuforums.org/showthread.php?t=282034]("http://ubuntuforums.org/showthread.php?t=282034")

As I suspect that **IPV6 **is the culprit, disabling it **globally **as well as in **Firefox **might help. It did the trick for me on a number of occasions.

Check it out and post back if it has not helped.

---

### Post by Mauzer on 2008-01-28
I entered **lsmod | grep ipv6**, but I got no output. Thus indicating that IPv6 isn't enabled, right?

P.S. I use Opera. ;)

---

### Post by wieman01 on 2008-01-28
> **Mauzer said:**
> I entered **lsmod | grep ipv6**, but I got no output. Thus indicating that IPv6 isn't enabled, right?

P.S. I use Opera. ;)
Try Firefox?

---

### Post by Mauzer on 2008-01-28
All applications are limited to ~30Kb/s.

---

### Post by wieman01 on 2008-01-28
Then blacklist the module as explained in the tutorial, restart the PC and see if it's any better. It won't do any harm.

Apart from this, no QoS running on the router?

---

### Post by Mauzer on 2008-01-28
Added IPv6 to the blacklist and rebooted. I'm still getting the same speeds.

As far as I know there's no QoS on my router. There are two other pc's using the router. Both getting normal speeds and running on WinXP.

---

### Post by Mauzer on 2008-02-01
This is my first try with Linux, and it's turning out to be a very bad one. If noone knows what's wrong I guess I'm forced to go back to Windows.

---

### Post by Mauzer on 2008-02-04
Tiny breakthrough, while downloading a file of ~10MB I suddenly reached 180KB/s. I was so suprised that I did a speed test. That showed 110KB/s. The next I did after showed 70KB/s. It kept going down and now I'm back to where I were.

I'm even more confused now.

---

### Post by wieman01 on 2008-02-04
Please keep us posted on the progess. I have seen other posts describing similar issues, but I have not seen a single solution yet apart from disabling IPV6.

---

### Post by Mauzer on 2008-02-04
The thing is, I didn't do anything. I just got back from university, tried to download something and when I checked it progress (I'd expected it to take much longer because of the slow speed) it was done. And the average speed according to Opera van 180KB/s. And the rest is known.

---

