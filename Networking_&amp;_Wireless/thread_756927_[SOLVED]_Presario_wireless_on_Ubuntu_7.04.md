---
title: "[SOLVED] Presario wireless on Ubuntu 7.04"
date: 2008-04-16
forum: Networking &amp; Wireless
---

### Post by Pawcatuck on 2008-04-16
I set up the WiFi card on my Compaq Presario C571NR, using the instructions on the very helpful [Feisty No-Fluff]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff?highlight=%28c571nr%29#head-b0e306f00ab3b4adea24f483a5dd5bf05fbdaf08") page. Everything seemed to go well, and after reboot I got the telltale blue light on the WiFi indicator.

I live out in the country and am not near any wireless networks, so I wasn't able to connect to anything that day.

The next morning, I planned a trip to the library, but the blue light didn't come on, and I was unable to connect to anything. It was as if, overnight, Ubuntu "forgot" that the WiFi was there.

A couple of times, I tried to go into the network connections and establish something. I didn't get anywhere, but I did notice that after doing that, when I went to a command prompt, I saw that Ubuntu was trying to load something, and was giving me the following:

Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

Here are my questions:

How do I get and install microcode5.fw, and what is it?

Can I go through the whole procedure outlined on the Feisty No-Fluff page again without ruining everything? I'm pretty good at following instructions, but maybe I missed a step.

I expect to try Ubuntu 8 when it is out of beta (yeah, I'm a coward, but this is a production machine). Is it anticipated that advancements in Ubuntu 8 will make configuration easier, and therefore I should just wait a couple of more weeks to see what happens?

The WiFi works under Vista (as much as anything works under Vista). If I can get WiFi working under Ubuntu, I can dump Vista forever.

Sorry this is so wordy. I think this is all the information I can supply.

---

### Post by dstew on 2008-04-16
It seems the native bcm43xx driver is still active, trying to load firmware. Did you blacklist it? To see if it is still loading, do```
lsmod | grep bcm43xx
```Also, do```
ndiswrapper -l
```Post the results.

---

### Post by Pawcatuck on 2008-04-16
Hi, and thanks for your reply. Here's the output of lsmod | grep bcm43xx:

```
bcm43xx               126824  0 
ieee80211softmac       31360  1 bcm43xx
ieee80211              34760  2 bcm43xx,ieee80211softmac
```

And here's the output of ndiswrapper -l:

```
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: bcm43xx)
```

Hope that makes some sense!

---

### Post by dstew on 2008-04-16
It makes a lot of sense. The native driver, bcm43xx is loaded and operating, and so is ndiswrapper. The two conflict with each other. You should not have both operating at the same time. You have to decide which one you want to use, and stop the other one from loading.

I recommend you stop the native driver from loading. To do this, you need to add this line to your /etc/modprobe.d/blacklist file:```
blacklist bcm43xx
```

---

### Post by Pawcatuck on 2008-04-16
So far, so good. I edited the blacklist file, rebooted, and I have the "blue light" on again.

Next time I get near a wireless network (tomorrow, with any luck), I'll try it out and report back what happens.

---

### Post by Pawcatuck on 2008-04-17
Greetings from the Groton, Connecticut Public Library! Thanks very much; it's working great now. My next problem is what to do with the Vista partition, which I can't imagine I'll be needing any more....

---

