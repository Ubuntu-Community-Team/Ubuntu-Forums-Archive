---
title: "TKIP? EAP-MSCHAP v2? WPA Enterprise? WHAT?"
date: 2008-02-07
forum: Networking &amp; Wireless
---

### Post by deviantfire on 2008-02-07
Ok here's my issue I have bought a 3com wireless card in order to log onto my college eduroam network, HOWEVER! I am having trouble getting some settings right!

So heres what they want me to do! I was wondering if anyone could help?

Security Type : WPA-Enterprise
Encryption Type : TKIP
No validation of server cert
Enable fast reconnect
Authentication method : Secured Password (EAP-MSCHAP v2)
Deselect automatically use my windows password

Then it should ask me for my user name and password (which of course I won't post here!)

Anyway any takers?

---

### Post by wieman01 on 2008-02-07
Question is if your wireless adapter really support WPA-Enterprise. When you fire up Network Manager, are you given the option "WPA-Enterprise" next to "WPA-Personal"? What other options are there?

---

### Post by deviantfire on 2008-02-07
It's a 3com OfficeConnect 3CRGPC10075

I get WPA Key (hexadecimal)
WPA Key (ascii)
WPA Personal
WPA2 Personal

Is it possible that it could be a download I need?

Also I should not that I had to use the Windows driver to make it work, but I understand that's average for Wireless PCMCIA cards on Ubuntu.

---

### Post by wieman01 on 2008-02-07
There is not WPA-Enterprise option? Guess then you are out of luck.

The only other way to make it work (that's no promise though) is by installing 'ndiswrapper' and deploying the Windows driver. If the Windows (XP) driver can cope with WPA-Enterprise, there is a good chance you'll get it working. That said, however, there is no guarantee.

---

### Post by deviantfire on 2008-02-07
Ok think I have already installed that but maybe if I get the updated windws driver off 3com that might help? I have used a gui for ndiswrapper and got the card running, guess that's what you mean?

---

### Post by wieman01 on 2008-02-07
> **deviantfire said:**
> Ok think I have already installed that but maybe if I get the updated windws driver off 3com that might help? I have used a gui for ndiswrapper and got the card running, guess that's what you mean?
Yes, exactly. Updating the driver to the latest (XP) version is also recommended. But you have to blacklist the old (Linux) driver, I hope you have done that.

---

### Post by wieman01 on 2008-02-07
By the way, you should read this to get some background information:

[http://en.wikipedia.org/wiki/Wi-Fi_Protected_Access]("http://en.wikipedia.org/wiki/Wi-Fi_Protected_Access")

It'll help you immensely in understanding what you are doing. :-)

---

### Post by deviantfire on 2008-02-07
ok so how do I do that??!!!

---

### Post by wieman01 on 2008-02-07
> **deviantfire said:**
> ok so how do I do that??!!!
Could you please post the following:
> sudo iwlist scan
> sudo lshw -C network
> sudo ndiswrapper -l
Just to see what's going on. What guide have you followed while installing 'ndiswrapper'?

---

### Post by deviantfire on 2008-02-07
Dude I didn't use any guide I just kinda did it......

---

### Post by wieman01 on 2008-02-07
> **deviantfire said:**
> Dude I didn't use any guide I just kinda did it......
Haha... No problem. Please post the results of the commands I have posted above.

---

### Post by harrydb on 2008-02-26
See my post in this thread for a howto connecting to eduroam using the network manager applet:
[http://ubuntuforums.org/showthread.php?t=708148#post4410798](http://ubuntuforums.org/showthread.php?t=708148#post4410798)

---

