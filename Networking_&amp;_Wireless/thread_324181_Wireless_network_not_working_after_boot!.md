---
title: "Wireless network not working after boot!"
date: 2006-12-23
forum: Networking &amp; Wireless
---

### Post by intovoid on 2006-12-23
I configured the wireless network in Edgy (kubuntu).  When i reboot i don't have access to the internet, but when i start the "Wireless Assistant" i can see the ESSID of my network and when i click it, it connects nicely and i have access to the internet, this makes me think the configuration is okay.

How can i make it so that kubuntu connects to my network at startup ?

Thank you in advance.

---

### Post by stupidkid on 2006-12-23
Edit the /etc/networking/interfaces file like this

iface wirelessinterface inet dhcp
wireless-essid ESSID
wireless-key KEY

For example

iface ath0 inet dhcp
wireless-essid Home
wireless-key 1111111111

---

### Post by intovoid on 2006-12-23
do i have to include the "auto eth1" to ?

---

### Post by intovoid on 2006-12-23
Tried it without the "auto eth1", didn't work.
Tried it with the "auto eth1", i took kubunto about 2 minutes longer to boot, but still it isn't working.

Anyone ?

---

### Post by stupidkid on 2006-12-23
Ok post your /etc/networking/interfaces

Yea, sorry I missed auto eth1, you need that.

---

### Post by intovoid on 2006-12-23
You know what's strange, when i do a "sudo ifdown eth1" and after that a "sudo ifup eth1", the connection is working.

Maybe that helps anyone finding an answer for me.

---

### Post by intovoid on 2006-12-23
Does anyone know how i can automate this at startup ?

---

### Post by syracus on 2006-12-30
Just place a script into /etc/init.d like forceath0 and link it into your runlevel(s) which simply does 'ifdown ath0; ifup ath0'. This solved this issue for me so far.

But anyway. Noone has a real solution for this problem ? Can't believe that ;)

Take on Ubuntu guys!!

---

### Post by DaveQB on 2007-01-08
Exact same problem here.

No Solution ?

---

### Post by DaveQB on 2007-01-09
knetworkmanager fixed it for me.  What a great app.

Hint, you need to totally comment out all reference to your wireless NIC in /etc/network/interfaces

Otherwise knetworkmanager will not take over control of it. Wise move by the dev's I think.  Curious that it never writes to the interfaces file, must keep its configs somewhere else.

---

### Post by game_plan on 2008-04-15
I wish I could even get that far! I've tried adding wlan0 including all network info (SSID, encryption type, etc) and it actually makes it worse since then I can't even start it manually.

My /etc/network/interfaces file only has the loop back, yet the LAN is working on boot?

Any help would be great :)

---

### Post by uniuk2000 on 2008-04-15
I'm having exactly the same problem with 7.1 and the new 8.04. If I could find how to automate the 'ifdown' and 'ifup' commands (believe me, I've tried) it would make life so much easier. Bear in mind though, I'm a ubuntu user of less than a week and still alot to learn lol.

---

### Post by game_plan on 2008-04-20
Has anyone found a solution to this yet?

---

