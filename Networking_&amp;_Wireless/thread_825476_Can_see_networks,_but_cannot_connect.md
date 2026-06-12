---
title: "Can see networks, but cannot connect"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by shaggy1054 on 2008-06-11
I'm using Ubuntu 8.04 with an AR5212 atheros-based wireless card. I have configured my wireless as described in this thread: 

[http://ubuntuforums.org/showthread.php?t=795984](http://ubuntuforums.org/showthread.php?t=795984)

I use the wicd program mentioned in that thread. My connection to the internet (through a linksys router that runs dd-wrt firmware) worked fine for about a day, but has since refused to connect. I can see every wireless network around, and see that I have access to the dd-wrt network to which I want to connect at 65-80% (depending upon where I am in the house), however Wicd hangs on the "obtaining an IP address" stage. I have tried reconfiguring my connection to use a static IP and DNS address - this causes Wicd to register me as connected, however I still cannot access the internet or internal network. This is very frustrating - my wireless hasn't worked since the kernel update from 16 to 17 (previously it worked fine), and I am considering switching back to windows. Can anyone help me prevent this by helping me fix this problem?

One small problem, I am typing this from a computer that is not the computer in question. I would copy/paste results from iwconfig and so on, however I cannot. If there are parts of that kind of command-line input/output that would be helpful, however, I'd be more than willing to transcribe. Thanks in advance!

---

### Post by Peter09 on 2008-06-11
Check that your security key is configured correctly, as a first pass that may be Wicd does not obtain an ip address.

PC

---

### Post by shaggy1054 on 2008-06-11
The security key is indeed correct. The strange thing to me is that I cannot connect at all if I attempt to use DHCP. If I input an IP from the acceptable range, I can connect, but get no internet or network access. This leads me to believe this is not a key issue.


Something I just noticed is that when I use dmesg, I can see that i'm getting a notice of "ath0: no IPv6 routers present" - could this have something to do with what is going on here?

---

### Post by shaggy1054 on 2008-06-11
Just an update to say that I got a wired connection so I can copy/paste now if that helps.

---

### Post by Peter09 on 2008-06-12
I think your static ip connection is just a figment of the process of connection as your machine does not require any network activity to get do that. I have seen this happen before and it was then a bad driver. What is your network device?

Can you post the output of ```
ifconfig
``` and ```
lshw -C network
```

PC

---

