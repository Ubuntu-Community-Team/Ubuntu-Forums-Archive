---
title: "Hotspot a VPN for Android"
date: 2021-03-07
forum: Networking &amp; Wireless
---

### Post by alexander46 on 2021-03-07
Hey there,

its an eeePC 1005HA
Atheros Wireless Card
I got VPN working, so i can use the cable to connect to the dormitory internet. Then i establish a hotspot, i also tried the ad-hoc method with mac adressess.
in the as-hoc version the android does the 'SAVED' thing (WEP password) and during hotspot the android is 'obtaining ip address' forever.
Do i need to tweak some VPN settings on that phone? my fellow tenants told me, they dont use VPN software on their phone; but they mostly use wifi-routers instead of a laptop.

Many thanks in advance! :-)

---

### Post by hk42 on 2021-03-08
Hi
Since yesterday I'm using the same kind of trick.
Even the huge /etc/host file of the hot spot PC is active for clients.
VPN is nordvpn and mainly used to watch foreign countries IPTV.
One bad thing with nordvpn is that using system monitor you can see
that it adds about 60% to the data passing through.
Depending on the order the VPN and hot spot software were started and
 the privilege of the users who did it results may vary.

PS : As far as nordvpn is concerned there seems to be a big drawback:
Once a client is connected to the VPN protected hotspot DHCP refuses 
any other.
May be there is something I don't understand as this is quite new to me.

---

### Post by TheFu on 2021-03-08
I can't help, since I don't understand what you are trying to accomplish, but **WEP has been deprecated since 2005**. It is easier to crack a WEP passphrase than it is to look it up. WEP is not secure or even close to secure.  
WPA2 should be used these days and even it was cracked in 2018 if strong passphrases aren't used.  [https://www.zdnet.com/article/new-wi-fi-attack-cracks-wpawpa2-passwords-with-ease/](https://www.zdnet.com/article/new-wi-fi-attack-cracks-wpawpa2-passwords-with-ease/)
Even WPA was cracked in 2008. [https://www.zdnet.com/article/researchers-crack-wpa-wi-fi-encryption-in-60-seconds/](https://www.zdnet.com/article/researchers-crack-wpa-wi-fi-encryption-in-60-seconds/)
Mods: I tried to link only to news articles about the problems, not step-by-step guides. ;)

I'm confused what a VPN has to do with connecting to a dorm internet. I'm so confused. All wifi should use a VPN, since none of the popular wifi methods are secure. I use a VPN for the wifi inside my home.  In 2003, when I was deploying wifi inside a corporation, we required VPN be used with a 2FA key-fob device to ensure the data connection was secure.

Maybe if you spell out what you are trying to accomplish, someone can help?  I had a eee laptop years ago, so I'm not unfamilar with it.  Mine had 2G of RAM and an Atom N270) CPU. It could play videos at 600p resolution and less. No hidef video because the onboard GPU didn't have any video decoding built-in.  For the time, it was a good solution.  I replaced it with a relatively cheap Chromebook running Ubuntu which was probably 5x faster.

---

### Post by alexander46 on 2021-03-12
[ill come back to this on the weekend]

---

### Post by hk42 on 2021-03-19
> **hk42 said:**
> Hi
PS : As far as nordvpn is concerned there seems to be a big drawback:
Once a client is connected to the VPN protected hotspot DHCP refuses 
any other.
May be there is something I don't understand as this is quite new to me.

PS2 : If the client is using a fixed IP it doesn't seems to be affected

---

### Post by alexander46 on 2021-04-07
So what i want to achieve is, connect my smartphone to a wifi thats been established by my eeePC.
The ethernet comes from the dormitory socket and goes into the eeePC by cable.
My eeePC has to be registered at the internet provider and i have to use a VPN connection on my eeePC to access this internet.
I then tried some methods to set up wifi, using my eeePC as a 'router'.
So far i failed to connect my smartphone to that visible wifi that i successfully created with the eeepc.

---

### Post by alexander46 on 2021-04-11
,

---

### Post by alexander46 on 2021-04-20
,

---

### Post by deadflowr on 2021-04-20
> **alexander46 said:**
> ... ... should i maybe restart the topic in a new thread?

No

---

### Post by alexander46 on 2021-04-29
,

---

