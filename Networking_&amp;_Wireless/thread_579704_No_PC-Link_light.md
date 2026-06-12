---
title: "No PC-Link light"
date: 2007-10-18
forum: Networking &amp; Wireless
---

### Post by slink on 2007-10-18
Hi, 

if my DSL modem PC-link light is always off, what do I have to undersand?

Is my NIC malfunctioning?

I can:

```
lspci |grep eth
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
```

But does that mean that it is working OK ?

---

### Post by tkharris on 2007-10-18
That means that the Nic is present in the computer.  It can still have problems, but it's less likely to have problems.

The big question is: does the machine connect to the internet through the modem?  Are you having networking problems?  If you're not having any problems, the light in the modem might be out.

If you are having problems I would:

A)  Check that the ethernet cable is okay ( try with a different cable )
B)  Check if another computer lights it up and works fine ( laptop? Friend's laptop? )
C)  Replace the modem if the internet is still not working after tested with a known-good computer.

---

### Post by louie55 on 2007-10-18
If the link light is off, then you either have a bad cable, a bad connection, a bad NIC, or just a bad light as the above poster mentioned.

Is the link light off on the PC too??

Make sure the cable is plugged in all the way. Maybe even try a different ethernet cable if you have one laying around. They can get loose connections internally once in a while.

Your lspci output only means that Ubuntu sees your card, it doesn't neccessarily mean it is working ok. 

Louie

---

### Post by slink on 2007-10-19
> A) Check that the ethernet cable...
B) Check if another computer lights it up ...
C) Replace the modem ...

Good advise. I bought a new cable... in fact is more expensive than a NIC. 

I'll do B & C. Thanks.

---

### Post by slink on 2007-10-19
> lspci output only means that Ubuntu sees your card, it doesn't neccessarily mean it is working ok

Is there any way to know if it is working ok?

I'm not a Windows user but I've been told that in Windows, if a driver is not working well, it is shown with a yellow triangle or red cross. Isn't there any equivalence in Ubuntu ?

---

### Post by Hero of Time on 2007-10-19
> **slink said:**
> Is there any way to know if it is working ok?

I'm not a Windows user but I've been told that in Windows, if a driver is not working well, it is shown with a yellow triangle or red cross. Isn't there any equivalence in Ubuntu ?
Third topic within 2 days, what's next? :-P

As for Windows with a yellow triangle or red cross, those only mean that either the device cannot start or has another error code and red means disabled. You can try to ping to 127.0.0.1 (localhost, internal loopback).

First thing I would do, is take the modem to a friend with a working network, or get a good working computer/laptop and connect it to the modem.

In your earlier topic, you mentioned a thunder storm. It's possible that it struck the internet connection and fried it's NIC. It doesn't have to be your house that got struck, it can be the ground where the cable just happens to be buried, or the switchboard outside got hit. So first you need to make sure your modem is working as it should. If that doesn't work, your network light won't light up. If your modem is alright, then your onboard NIC is fried. Nothing to do about it but to buy a new one. If you have a laptop, it's somewhat more difficult to get it fixed. You either need a pcmcia card or usb to ethernet adapter.

---

### Post by slink on 2007-10-19
> As for Windows with a yellow triangle or red cross, those only mean that either the device cannot start or has another error code and red means disabled. You can try to ping to 127.0.0.1 (localhost, internal loopback).

I don't understand the relation between detecting disabled/disconfigured devices and pinging localhost. 

```
ping 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.066 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.057 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.054 ms
64 bytes from 127.0.0.1: icmp_seq=4 ttl=64 time=0.052 ms

--- 127.0.0.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3000ms
rtt min/avg/max/mdev = 0.052/0.057/0.066/0.007 ms
```


> take the modem to a friend with a working network, or get a good working computer/laptop and connect it to the modem

I believe this is a good advice. 

> it struck the internet connection and fried it's NIC

I couldn't believe that a storm (electrical overhead) could affect the NIC and not the modem, but I guess you're right. I'll do those checks.

> Third topic within 2 days, what's next? 

Thanks for patience. My ISP just ignore me because I don't have Windows and I needed to figure out if it is a NIC or MODEM related problem...

---

### Post by Hero of Time on 2007-10-19
> I don't understand the relation between detecting disabled/disconfigured devices and pinging localhost.
If the device is malfunctioning or disabled, you shouldn't be able to ping to your localhost address.

---

### Post by slink on 2007-10-19
> If the device is malfunctioning or disabled, you shouldn't be able to ping to your localhost address.

So my NIC is OK ! I am pinging with 0% packet loss !

---

### Post by Hero of Time on 2007-10-19
That seems to be the case. Still, to be 100% sure, take the modem to a computer with a functioning NIC (or your NIC instead of the modem).

Oh, another thing. Set a manual IP to your NIC and ping that.

---

### Post by slink on 2007-10-19
> That seems to be the case. Still, to be 100% sure, take the modem to a computer with a functioning NIC (or your NIC instead of the modem).
OK. I'll do that.

> Set a manual IP to your NIC and ping that.

Do you mean... ?
```
ifconfing eth0 inet xxx.xxx.xxx.xxx
ping xxx.xxx.xxx.xxx
```

I wonder if I can assign any whatever adress  (example 1.1.1.1 ) for that purpose

---

### Post by Hero of Time on 2007-10-19
You can use anything, aslong if you set the right subnet. E.g. 10.0.0.1 255.0.0.0. Private ip addresses recommended, but doesn't matter much since it's in a stand alone enviroment.

---

