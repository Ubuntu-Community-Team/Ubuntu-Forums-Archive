---
title: "[SOLVED] Router won't accept WEP key"
date: 2007-12-08
forum: Networking &amp; Wireless
---

### Post by coolbrook on 2007-12-08
I finally got my TEW-424UB 3.0 adapter to see wireless networks but I can't get it to connect to my own.  I have 2 problems.

1) I enter my WEP key and it won't accept it, so I can't get an IP address for my LAN.  It just prompts me to re-enter the key and the process loops.

2) I also notice that I must run the ndiswrapper terminal commands to see the wireless networks.  Where do I save those so I don't have to enter manually for each reboot?

Any help will be appreciated.

---

### Post by csat on 2007-12-08
Check this guide on how to troubleshooting your wireless.

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by coolbrook on 2007-12-08
Gave that a try and I get the message.

No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I'm just starting a search on this result.

---

### Post by hvac3901 on 2007-12-08
for me the issue was the default setting was passphrase, i needed to change that to HEX to set my router key. I had the same issue initially.

---

### Post by coolbrook on 2007-12-08
I have to set it to Hex too on my other computers.  I've tried every combination while ensuring that I enter the key correctly.

---

### Post by coolbrook on 2007-12-08
I'm open to any suggestions and advice.  I installed wicd to see what would happen.  That app couldn't even detect any networks in my area.  I'll like to get this working with the basic Network manager.

---

### Post by coolbrook on 2007-12-10
I set my wireles device to wlan0 in wicd and I can see networks but I still can't connect to my router.  It attempts to connect and then it just stops and remains unconnected.

---

### Post by coolbrook on 2007-12-10
I'm having this same problem with a Netgear WG111v2 USB adapter.  I can see the networks but I can't connect to my router, so perhaps it's a minor configuration issue that I can tweak.

---

### Post by Lostincyberspace on 2007-12-10
Are you in roaming maybe?

---

### Post by mdurham on 2007-12-10
>  Are you in roaming maybe?

That's a good question. If you are, turn it off and set up manually using the WEP key (hexadecimal)
It worked for me with a WG111 v3.
Cheers, Mike

---

### Post by coolbrook on 2007-12-11
Funny how it never lights up.

Thanks boys!

:cool:

---

