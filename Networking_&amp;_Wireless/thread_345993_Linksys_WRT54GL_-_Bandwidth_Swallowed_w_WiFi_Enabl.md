---
title: "Linksys WRT54GL - Bandwidth Swallowed w/ WiFi Enabled"
date: 2007-01-25
forum: Networking &amp; Wireless
---

### Post by Rev. Nathan on 2007-01-25
Howdy there ladies and gentleman,

So I've got a wireless problem of a grave importance. I address this because I feel almost as though the solution may be very simple, but my situation is full of complexities and many nights of anger.

Backstory: So I bought a WRT54GL because I needed WiFi for my Nintendo Wii. I chose the L for Linux, but was alas disappointed when I could have just as easily bought the non-L model and loaded in GNU GPL firmware.

Frontstory: So more recently, My internet speed was declining very swiftly. I took at speedtest where it actively shows you your down/up rate, and I was slowly declining from 100 KB/s, until slowly reaching 0. Turned off my WiFi, and everything is good again. Turn it back on... and a few seconds later... I've turned my Ferrari into a Fiat, with then turns into roadkill.

What you need to know: I'm running Tomato firmware, the latest version. My network is secured VIA WPA2, with AES encryption; a scrambled password 13 characters in length. When I check my device list, it's just be and the outgoing wireless signal (and the Wii, if I connect to it). So I don't think anyone is intruding... unless I'm not getting something.

The statement: Can anyone help me? I really want to get my Wii online because my mother wants to use the Internet browser on it.

Thanks,
Nathan

---

### Post by eXisor on 2007-01-25
I have a wrt54gl v1.1 and am using dd-wrt software v2.3 sp3. (I tried tomato and openwrt and liked some features, but found both currently not quite as feature rich as dd-wrt). 

A few questions:

1) is wired internet still OK when the problem occurs, or is all internet slow?
2) is lan traffic affected?
3) what is the router's memory usage when this happens?
4) how many connections are active when this happens? Has the connection limit been reached?
5) are you running ptp apps when this occurs? If so, what? Do you use QOS?
6) has anyone reported a similar problem on the tomatio forums?

It doesn't sound like bandwidth stealing problem, more as if there is a memory leak in a wireless module: as if the router is running out of memory.

---

### Post by Rev. Nathan on 2007-01-25
> **eXisor said:**
> 
1) is wired internet still OK when the problem occurs, or is all internet slow?
2) is lan traffic affected?
3) what is the router's memory usage when this happens?
4) how many connections are active when this happens? Has the connection limit been reached?
5) are you running ptp apps when this occurs? If so, what? Do you use QOS?
6) has anyone reported a similar problem on the tomatio forums?

It doesn't sound like bandwidth stealing problem, more as if there is a memory leak in a wireless module: as if the router is running out of memory.
1) Using wired internet is a-ok. As it was always, with or without the router.
2) No. Tomato runs fine; any .com I point to fails.
3)14.18 MB / 5,960.00 KB (41.06%) Disabled, 14.18 MB / 5,900.00 KB (40.64%) after enabled for 1 minute (and .com gets real slow
4) No; just me and my Nintendo. Nothing else is connected wired, nothing is obtained wirelessly
5) ...No? I don't use QoS, no.
6) Google search gave me people suffering the same problem, but with no answer.

---

### Post by Nik_Doof on 2007-01-25
Sounds like your upload is strangling your download. Check for an option called "Prioritize ACKs" in your router's options, switch it on and see if it improves, If not its something else, if it improves then you need to check whats going on with your network to see if anything is hogging all the bandwidth.

---

### Post by eXisor on 2007-01-25
OK, scratch the memory leak idea.

Maybe you should revert to the original linksys software and see if the problem persists. (If only to prove tomato is the culprit).

If it's tomato, dd-wrt and openwrt are alternatives you can try.

---

### Post by Rev. Nathan on 2007-01-25
> **Nik_Doof said:**
> Sounds like your upload is strangling your download. Check for an option called "Prioritize ACKs" in your router's options, switch it on and see if it improves, If not its something else, if it improves then you need to check whats going on with your network to see if anything is hogging all the bandwidth.
Gah, that didn't seem to go.
> **eXisor said:**
> OK, scratch the memory leak idea.

Maybe you should revert to the original linksys software and see if the problem persists. (If only to prove tomato is the culprit).

If it's tomato, dd-wrt and openwrt are alternatives you can try.
I heard good things about DD-WRT, trying now

---

### Post by Nik_Doof on 2007-01-25
I use DD-Wrt at the moment on my GS, well worth it :)

---

### Post by Rev. Nathan on 2007-01-27
Switched firmwares to DD-WRT. I don't know how it's different, but it solved it. I guess the lesson learned it for now, Tomato isn't the way to go. The only difference I notice is that now the  router/internet seems to dip down to a very slow speed for about a minute, then comes back to full pace. That happens maybe on an avarage of a few times a day.

I'm guessin' this is hardware though; since I read this somewhere before buying it.

---

