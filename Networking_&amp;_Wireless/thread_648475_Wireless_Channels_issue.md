---
title: "Wireless Channels issue"
date: 2007-12-23
forum: Networking &amp; Wireless
---

### Post by burbankmarc on 2007-12-23
Hello all,

Well, I have an odd situation. I have a usb wireless card using the zd1211 chipset. Now, I'm stationed in Africa right now and they have free wireless internet across the camp. Now this card works fine, because when i go to one side of the camp, where the AP uses channel 11 it works flawlessly, but when i go down to where I live the AP uses channel 1...and it doesn't work at all. 

So, what I've tried is sudo iwconfig eth1 channel 1 with the following error


```
Error for wireless request "Set Frequency" (8B04) :
    SET failed on device eth1 ; Operation not permitted.

```

So I know there's a couple issues with changing your channel while using a hidden essid. So to change the channel I do the following:

```
sudo iwconfig eth1 mode monitor
```

That allows me to change the channel just fine. I then switch back to 'auto' mode. Yet I still receive NO packets, at all. if I leave the device in monitor mode on channel 1 i receive all kinds of traffic. But monitor mode doesn't help me out. 

Any advice?

---

### Post by HermanAB on 2007-12-23
Hmm, do a midnight acquisition and swap the APs around...

Cheers,

Herman

---

### Post by burbankmarc on 2007-12-23
That's a good plan and all, just a few problems. I'm in the Air Force, so, I have no stealth or evasion training. Also, getting in trouble in the military kind of sucks.

Any other suggestions?

---

