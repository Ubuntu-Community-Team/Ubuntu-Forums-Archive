---
title: "Ralink 8188ee Wireless card poor performance"
date: 2014-01-23
forum: Networking &amp; Wireless
---

### Post by Tim_Hallett on 2014-01-23
Hello all: 

After installing 13.10, performance seemed good for quite a while, but now wireless connection is intermittent and slow. Following the procedure in 
[http://ubuntuforums.org/showthread.php?t=2162026&page=2&p=12896662#post12896662](http://ubuntuforums.org/showthread.php?t=2162026&page=2&p=12896662#post12896662)
I updated my drivers with the backports from 3.12-1, but after sucessfully installing these, performance is even worse, with upload speeds slower than download speeds. 

Varunedra, as per your advice, I have posted the output of you Wi-fi script. What to do, Adjust something?, Roll-back the update? Ndswrapper?
[ATTACH]249680[/ATTACH]

---

### Post by chili555 on 2014-01-23
> **Tim_Hallett said:**
> Hello all: 

After installing 13.10, performance seemed good for quite a while, but now wireless connection is intermittent and slow. Following the procedure in 
[http://ubuntuforums.org/showthread.php?t=2162026&page=2&p=12896662#post12896662](http://ubuntuforums.org/showthread.php?t=2162026&page=2&p=12896662#post12896662)
I updated my drivers with the backports from 3.12-1, but after sucessfully installing these, performance is even worse, with upload speeds slower than download speeds. 

Varunedra, as per your advice, I have posted the output of you Wi-fi script. What to do, Adjust something?, Roll-back the update? Ndswrapper?
[ATTACH]249680[/ATTACH]If you have administrative privileges over the router, I'd suggest you change the encryption from mixed mode WPA and WPA2 to single mode WPA2-AES only. I'd also experiment with 802.11N disabled; use B and G only.

Next, if those steps don't fix it, I'd try compiling the backports package here: [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.13-rc8/backports-3.13-rc8-1.tar.gz](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.13-rc8/backports-3.13-rc8-1.tar.gz) In other words, the latest available.

You could also try a driver parameter:```
sudo modprobe -r rtl8188ee
sudo modprobe rtl8188ee swenc=1
```If none of those help, I'd git me a big old crowbar and git that durned wireless card outa there.

---

### Post by Tim_Hallett on 2014-01-23
Hi Anton, since wireless is now totally non-functioning, telts move thhis over to the newer "Lost drivers" thread

---

### Post by chili555 on 2014-01-23
> **Tim_Hallett said:**
> Hi Anton, since wireless is now totally non-functioning, telts move thhis over to the newer "Lost drivers" threadWho is Anton?

---

