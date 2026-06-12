---
title: "can't auto connect to hidden network"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by auisce on 2008-06-24
Okay,

I have an 802.11g wireless network with a netgear router and netgear network cards (wg311t (Atheros)). All is well... except:

I recently unticked the box in my router config which says "broadcast SSID" so as you might expect, my router now nolonger broadcasts its SSID.

Since making this single change, Ubuntu (Hardy) cannot auto connect to the network and I have to use "connect to other network" every time even though seahorse or whatever has all the settings and even then it takes a few attempts.

What really gripes me is that both Vista and Backtrack 3 on the same box connect straight away with no fuss and have a more stable connection.

Any suggestions?????

PS. Yes I really do need Vista so please don't flame me for it.

---

### Post by spd106 on 2008-06-24
Have you tried turning broadcast back on?

---

### Post by yipperzz on 2008-06-25
> **auisce said:**
> Okay,

I have an 802.11g wireless network with a netgear router and netgear network cards (wg311t (Atheros)). All is well... except:

I recently unticked the box in my router config which says "broadcast SSID" so as you might expect, my router now nolonger broadcasts its SSID.

Since making this single change, Ubuntu (Hardy) cannot auto connect to the network and I have to use "connect to other network" every time even though seahorse or whatever has all the settings and even then it takes a few attempts.

What really gripes me is that both Vista and Backtrack 3 on the same box connect straight away with no fuss and have a more stable connection.

Any suggestions?????

PS. Yes I really do need Vista so please don't flame me for it.

Same issue here.  I have XP and Hardy on the same laptop and while XP can auto-connect, Hardy is having issues finding it unless I manually add at each bootup (PITA).  I'm running the 32-bit version.  My desktop running the AMD64 version is finding the hidden AP's fine.  I'm wondering what the differences are there?  I'm using Network Manager.

---

### Post by auisce on 2008-06-26
Okay for now I've had to turn broadcast back on but I'd really like to have that little security feature back but with Ubuntu at the moment It's just not worth the hassle. 
Ideas or fixes very welcome.

Oh I'm also running 32bit as I keep hearing about problems with 64 bit and still needing 32 bit dlls or something. Maybe I'll try a 64 bit install inside Windows with the Wubi wotsit. If it works It still wont help my 32 bit celeron based Ubuntu only laptop.

---

### Post by yipperzz on 2008-06-26
I've tried uninstalling Network Manager as one of the posts suggested while doing a search and that didn't help.  Since I'm running one AP with WPA, I can live with broadcasting it.  But I have to use WEP on another for my roommate's older laptop and wanted to disable broadcasting since WEP is so easy to crack.  Oh well.

---

### Post by jrusso2 on 2008-06-26
> **auisce said:**
> Okay for now I've had to turn broadcast back on but I'd really like to have that little security feature back but with Ubuntu at the moment It's just not worth the hassle. 
Ideas or fixes very welcome.

Oh I'm also running 32bit as I keep hearing about problems with 64 bit and still needing 32 bit dlls or something. Maybe I'll try a 64 bit install inside Windows with the Wubi wotsit. If it works It still wont help my 32 bit celeron based Ubuntu only laptop.

Not broadcasting SSID is not much of a security feature.  The network can still be easily found by anyone who really wants to.

If you use WPA2 with a strong password its pretty secure.

---

### Post by auisce on 2008-06-30
I noticed that airodump-ng can figure out a hidden ESSID but beyond that I havn't seen anything else which can (certainly not Wireless Zero) so I've been thinking of it almost as a second password. Maybe I'm wrong to do so, but I'm using WPA as I havn't yet figured out WPA2 and I figure any extra security however small is worth having.
Oh well, WPA and MAC filtering for now.

---

