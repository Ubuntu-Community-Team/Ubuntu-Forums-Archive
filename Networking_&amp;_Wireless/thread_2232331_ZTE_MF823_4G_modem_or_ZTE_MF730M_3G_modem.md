---
title: "ZTE MF823 4G modem or ZTE MF730M 3G modem?"
date: 2014-07-01
forum: Networking &amp; Wireless
---

### Post by sbutton on 2014-07-01
Hi,

I'm thinking of buying a 3G dongle for use on the train from Cambridge to Kings X (and also from Thurston to Cambridge). I'm wondering if one of the ZTE modems from Three would be a good choice, or perhaps I should choose something else?

I'm aware that 4G coverage is pretty limited right now, but I guess this will change over the next couple of years. The 4G model doesn't cost a lot more up front, so why not?

Well, I guess if it doesn't work under Linux that would be a good reason. I can't see a huge amount of support for the MF730, but it does appear that some people have managed to get it working.

I'm happy to try a different network, but Vodafone are definitely very limited on that line so they are out.

Any suggestions?

Thanks,

Steve

---

### Post by sbutton on 2014-07-02
Following on from this, I notice that my Dell E7440 laptop has a SIM card slot, so I might be better just using that. Having said that, I can find precious little about getting this working (even under Windows, let alone under Linux!)

---

### Post by jeremy31 on 2014-07-02
I think I would look at these [http://www.tp-link.com/lk/products/details/?model=TL-MR3020#spec](http://www.tp-link.com/lk/products/details/?model=TL-MR3020#spec)
And see if something like it works with the ZTE

---

### Post by sbutton on 2014-07-03
This is a completely different solution, but not practical for what I need. It's like a MiFi in that you are sharing the GSM connection over a wireless link. A neat idea for a hotel or office, but I want something that will work on a train and be practical to carry around. The very best solution would be just to use the SIM slot built into the laptop but I have no idea if this will work. For £15 I might just buy one and give it a try, as it's a one month contract.

---

### Post by gnomeza2 on 2014-09-03
Hi sbutton

The ZTE MF823 provided by 3UK is a hostless modem (by default), so it just appears as an ethernet interface (usb0 usually) having default ip 192.168.0.1.
It's trivial to get it working.

The Cambridge - Kings Cross line, on the other hand, will always have those irritating tunnels on the outskirts of London so there's no escaping that.

---

### Post by sbutton on 2014-09-04
Hi,

Thanks for the reply. That's exactly what I've found, it does just appear as an ethernet device and it DID just work. No indication of signal strength of course in the OS, but you can look at the lights on the side.

It worked fine most of the way from Thurston to Cambridge and pretty solid from Cambridge to Kings Cross (apart from those tunnels). It even worked well inside Kings Cross station waiting for the train to leave. I've now switched to the Norwich -> Liverpool Street line from Stowmarket.... sadly it hardly works at all here, perhaps 1/4 of the time if I'm lucky. So, I've ditched the monthly contract and switched to using the onboard wifi instead.

Steve

---

