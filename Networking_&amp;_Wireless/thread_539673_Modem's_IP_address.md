---
title: "Modem's IP address"
date: 2007-08-31
forum: Networking &amp; Wireless
---

### Post by davholla on 2007-08-31
How can I find my modem's IP address ?  I have lost the instructions.

---

### Post by Steve1961 on 2007-08-31
> **davholla said:**
> How can I find my modem's IP address ?  I have lost the instructions.

sudo ifconfig

---

### Post by davholla on 2007-09-01
Thanks but when I put the inet addr in the browser I get problem loading page.  Is that right.
 What I want is (what sadly I did not save as favourite) the address to log on to the controls

---

### Post by Steve1961 on 2007-09-02
Ah, I presume you mean the controls for a router page.  What is the IP address you got from ifconfig?

---

### Post by davholla on 2007-09-03
This is what I get :-

```
 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:C7:C5:DA:FC
          inet addr:192.168.1.98  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3781 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3307 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1289183 (1.2 MiB)  TX bytes:388617 (379.5 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1172 (1.1 KiB)  TX bytes:1172 (1.1 KiB)

```

---

### Post by Steve1961 on 2007-09-04
Try 192.168.1.1

---

### Post by davholla on 2007-09-05
Thanks but that is my modem which is separate from my router :(

Ie they both have 2 different ip addresses.

---

### Post by Steve1961 on 2007-09-06
Ah right, in that case all I can suggest is going to the modem manufacturers website to see if the ip address is quoted in one of their manuals.

---

### Post by davholla on 2007-09-06
Thanks.

---

### Post by Steve1961 on 2007-09-06
Here's a shot in the dark though.  Try:

192.168.100.1

that's the ip address used with an ntl/virgin media cable modem

---

### Post by PeterF on 2007-09-06
With tracepath you should get all the ip addresses required for the connection, your modem should be in this list.

---

### Post by kevdog on 2007-09-06
What kind of router do you have??  A lot of time within the router settings the WAN address is listed.  I wrote a perl script to extract this address from my Linksys WRT54G router.  I call this through a script and display it into Conky.  With a few small modifications it could be used to query your router.  I originally used this script as a dynamic update client that would query the router for the WAN address, compare it to the old WAN address, and if not identical would submit the new WAN address to noip.com.  It worked for a while, but noip.com kept changing there update locations/procedues that I eventually gave up modifying the script.  It does come in handy however for finding the WAN address of the router however.

---

### Post by subzero316 on 2008-05-13
> **davholla said:**
> How can I find my modem's IP address ?  I have lost the instructions.

Y cant you just connect the modem to your p.c then,
```
ifconfig
```
it` ll show u.

---

