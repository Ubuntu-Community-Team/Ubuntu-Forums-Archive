---
title: "intermittent wireless connectivity with bcm4306"
date: 2007-01-05
forum: Networking &amp; Wireless
---

### Post by maclenin on 2007-01-05
I was scrambling to get this note out before my wireless card died on me - again...the card died on me, again, so I post this from a wired pc....

Essentially, I have just "enabled" my bcm4306 wireless card, using the bcm43xx-fwcutter tool and have been able to surf the web and download files via Firefox - relatively briskly (and happily) - for about 5 of the 10 hours it's been "enabled"....

When the card dies, I am able to "see" it via ifconfig and iwconfig and can ping it.... However, I am unable to ping the router (Linksys WRT54GS fw. 3.37.6):

```
$ ping -c 4 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3013ms
```

It seems strange that the card would "time out" like that - intermittently - i.e. connected (strongly) for a few hours and then, suddenly, die....

Any thoughts?

NOTE: My surfing / connection time, for some reason, is now only about 5 or so minutes - after "enabling" - then silence....

---

### Post by Metaljaz on 2007-01-05
Read through the below thread, maybe very helpful. Good Luck!!


[http://www.ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://www.ubuntuforums.org/showthread.php?p=1071920&mode=linear)

---

### Post by maclenin on 2007-01-06
Thanks for that link - I've soaked a few kernels of wisdom from it.... I have also found (via scattered posts) that the following commands, when used together, can tickle the wireless card back to life (assuming your wireless card is located at eth1):

```
sudo iwconfig eth1 essid <essid label>
sudo dhclient eth1
```

You might have to repeat them (together or individually) a few times - but I have used this combination with success since I came accross them, last night.

However, I am always on the prowl for other solutions....

---

### Post by maclenin on 2007-01-17
Take a look [here]("http://ubuntuforums.org/showthread.php?t=328272") for the latest words in process on these issues....

---

### Post by maclenin on 2007-01-31
The current [latest]("http://ubuntuforums.org/showthread.php?t=340689")....

---

