---
title: "WPA Entreprise, Broadcom chipset, wl driver, PEAP, MSCHAPv2 inner auth"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by MrVincent on 2008-11-10
Hey everyone,

I am running Ubuntu 8.10 on my Dell XPS M1530. My network card is a Broadcom BCM4328 rev 03 and I have both wl and ndiswrapper installed. I run them one at a time using modprobe.

My university has a WPA Entreprise network protected with PEAP. Inner authentication goes with MSCHAPv2.

Using the ndiswrapper driver, I can connect to the network every once in a while. Most of the time, it just can't successfully obtain an IP address from the server. When I'm lucky, I get an IP and the connection works.

The wl driver doesn't work so well though. It gets up to "networkname: Validating authentication" or something similar, and then stops. Under network-manager, it simply asked me for auth info again. ndiswrapper gets past this step easily.

The signal strength is usually way better with the wl driver which is why I'd like to get it going. If you could help me set it up so that it can actually authenticate like ndiswrapper, I would really appreciate.

Thanks in advance

---

### Post by anando on 2008-11-10
Hi Vincent,

I had a similar problem - until I tried using the .pem files for CA certificates (instead of .crt files).

Try the following:

1. Set the Authentication to [FONT="Courier New"]PEAP[/FONT]
2. Set the Inner Authentication to [FONT="Courier New"]MSCHAPv2[/FONT]
3. Set the CA certificate to [COLOR="Red"][FONT="Courier New"]/etc/ssl/certs/
Thawte_Personal_Premium_CA.pem[/FONT][/COLOR] or if you have your own certificate from school, point to the [FONT="Courier New"].pem[/FONT] file
4. Username/password

See if this works for you and let us know.

Cheers,
Anand.




> **MrVincent said:**
> Hey everyone,

I am running Ubuntu 8.10 on my Dell XPS M1530. My network card is a Broadcom BCM4328 rev 03 and I have both wl and ndiswrapper installed. I run them one at a time using modprobe.

My university has a WPA Entreprise network protected with PEAP. Inner authentication goes with MSCHAPv2.

Using the ndiswrapper driver, I can connect to the network every once in a while. Most of the time, it just can't successfully obtain an IP address from the server. When I'm lucky, I get an IP and the connection works.

The wl driver doesn't work so well though. It gets up to "networkname: Validating authentication" or something similar, and then stops. Under network-manager, it simply asked me for auth info again. ndiswrapper gets past this step easily.

The signal strength is usually way better with the wl driver which is why I'd like to get it going. If you could help me set it up so that it can actually authenticate like ndiswrapper, I would really appreciate.

Thanks in advance

---

### Post by MrVincent on 2008-11-10
Well I can't set the inner authenticating in wicd, but using PEAP-TKIP and the certificate instead of PEAP-GTC, I have managed to connect, twice over about 10 attempts. The other times, either the authentication failed or I couldn't obtain an IP address.

---

### Post by anando on 2008-11-10
Sorry, I was under the impression that you were using network-manager. 

> **MrVincent said:**
> Well I can't set the inner authenticating in wicd, but using PEAP-TKIP and the certificate instead of PEAP-GTC, I have managed to connect, twice over about 10 attempts. The other times, either the authentication failed or I couldn't obtain an IP address.

---

### Post by giannimesa on 2008-12-11
Hi everybody, 
I have a same problem:

Ubuntu 8.10 on Dell XPS 1530 with mini Wireless Dell 1550.
On my home wifi network everything works fine, but at university I have a strange ubuntu crash:
when I set password and user on network manager window, it seems to working for connecting, but after some seconds system freez and I must restart by press start button for 8 second.. :( :(

I set this parameters on connection:

PEAP
peap version  0
Inner authentication MSCHAPv2
then user e pass

If I try with peap version 1, simply it doesn't connect, but at least it doesn't freez.

Please can you help me?

tkx :)

(p.s. I'm tired of this Vista.. )

---

### Post by giannimesa on 2008-12-12
Can i use ndswrapper with VISTA drivers??

---

### Post by giannimesa on 2008-12-18
yesterday a try again, after upgrading bios from A09 to A12, but as I suppose it doesn't work! 
Have you got any ideas?
I need internet connection on university department, but at moment only Vista can connect with the wireless card of my DELL XPS 1530. 

please Help me...

---

