---
title: "Intel Pro Wireless 3945 Install"
date: 2006-09-03
forum: Networking &amp; Wireless
---

### Post by themusicwave on 2006-09-03
I just got a wireless router(linksys WTR54GL) and have spent about 2 days trying to get wireless to work in ubuntu.  In windows it took about 10 seconds...

Anyways, I have no idea what to do to get this working.  I've been reading I need to install ieee80211 and recompile the kernel(which I have no idea how to do).  

I don't care about WPA, WEP is fine with me.  Does anyone know how to install the card and the 80211 drivers?  

I installed the gnome netwrok manager, but the card still cannot connect.

I am pretty new to linux so please keep this as simple and detailed as possible.  Thanks in advance for the help.

---

### Post by cylon359 on 2006-09-04
You shouldn't have to recompile anything, hopefully...

Is your wireless recognised?  If there is an entry for it in /etc/network/interfaces, you need to remove that before NetworkManager will work with it.

---

### Post by jonwatson on 2006-09-04
> **cylon359 said:**
> You shouldn't have to recompile anything, hopefully...

Is your wireless recognised?  If there is an entry for it in /etc/network/interfaces, you need to remove that before NetworkManager will work with it.

While we're on the subject...

I had Kubuntu 6.06 running for months off of the original release, updated as they became available. Because I'm stupid, I decided to give MEPIS a try which failed miserably. I'm now trying to come back to Kubuntu, but I can't get my Intel 3945 up and running with the 668 SMP kernel. It runs fine off of the stock 386 kernel, but when I upgrade to the 2.6.15-26-686 kernel, it stops working.

As far as I remember, all I had to do last time was to install the SMP kernel and then the linux-686-smp package and all was well. I've installed both, but the card won't come up.

Has something changed since June? Is there some other package I should install to get the card working with the SMP kernel?

Any tips are welcome...

J

---

### Post by themusicwave on 2006-09-04
Well I'm not sure what the current status of the card is, it is listed on my connections.

I can activate it, but it simply doesn't work.  I'm not sure if it's the router settings perhaps(they work fine in windows).

Right now I have SSID set to not broadcast, 128bit WEP encryption and MAC address filtering enables.  I know it's a bit paranoid but I live in a campus apartment where people love to get into other people's wireless.

I have the correct SSID, WEP key and DHCP settings for the wireless(I think).

I think I might have really screwed someting up with th 80211.  I was trying to install the intel drivers and I may have completely removed 80211 from my system.  How do I tell.

---

