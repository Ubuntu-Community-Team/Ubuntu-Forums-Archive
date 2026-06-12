---
title: "I can't get my Wireless re-enabled..."
date: 2008-01-15
forum: Networking &amp; Wireless
---

### Post by RudolfMDLT on 2008-01-15
Hi

I needed to test for DHCP on a network on an AP's Ethernet port so I disabled the Wireless on Ubuntu by right clickig on the networking icon and unticking the Wireless box. Now the wireless won't come back.

When I do a > iwlist ap


I get this back:
> 
lo        Interface doesn't have a list of Peers/Access-Points

eth0      Interface doesn't have a list of Peers/Access-Points

wifi0      Interface doesn't have a list of Peers/Access-Points

ath0      No Peers/Acces-Point in range

irda0   Interface doesn't have a list of Peers/Access-Points


When I press the WiFi button on the laptop the WiFi light never dies but the bluetooth icon comes and goes. No matter whether the Bluetooth works or not, the Wifi doesn't come back.

I have also restarted the laptop.

There is an AP 5 meters from the laptop with NO encryption what so ever and it can't even connect to it when I try a manual config.

Is there a command to force the adapter to power on? :)

Thanks for any replies,

Rudolf

---

### Post by accord on 2008-01-15
try ```
iwconfig
```
Does it say "radio off" in your wireless entry? If it does, then your wireless is probably turned off, due to a hardware switch or Fn key.

---

### Post by RudolfMDLT on 2008-01-15
Where would it say that? 

Can I turn the radio on with a command?

anyway - the darn thing has fixed itself somehow after a day. I have no idea why.

Do you know how to turn a Wifi Card on and off with a command. This is not the first time that this happend and I was hoping to find a way to actually force the thing to come back to life rather than fixing it by prayer and will power? :)

I appreciate the reply,

Thanks,

Rudolf

---

