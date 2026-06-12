---
title: "can see the wireless link, but does not link"
date: 2006-07-18
forum: Networking &amp; Wireless
---

### Post by dmanjra on 2006-07-18
Hi,

Hope someone can help as i really want to move away from MS. 

I have an IBM laptop, D-Link wirless card and router and installed 6.06 the other day. 

I can get the system to see the wireless link, it says there is 80% strength. i put in the WEP key, but it just says it is disconnected all the time. 

In MS, i plug in and it goes straight away. i was told that this should be the same for 6.06 - can anyone offer any help!

---

### Post by swamytk on 2006-07-18
Have you enabled this wireless card in System->Administration->Network?

---

### Post by bigken on 2006-07-18
I had the same problem with a netgear wg311 v2 card it showed the signal strength as 90% but showed as diconected I got round this by using ndiswrapper to install the drivers have you also tried disabling the wep ;)

---

### Post by tturrisi on 2006-07-18
Try entering the wep key using a hyphen between every 4 charachers like so:
[b]Key Type: Hexadecimal
WEP Key: abcd-efgh-ij[/b]

---

### Post by dmanjra on 2006-07-18
> **swamytk said:**
> Have you enabled this wireless card in System->Administration->Network?

Hi,

Not sure. I loaded the OS with the card in, so it recognised it. I have clicked the default field to tell it to use this connection too. It is listed as activated in the network section.....

---

### Post by dmanjra on 2006-07-18
> **tturrisi said:**
> Try entering the wep key using a hyphen between every 4 charachers like so:
[b]Key Type: Hexadecimal
WEP Key: abcd-efgh-ij[/b]

I'll try this tonight. Thanks for your help

---

### Post by dmanjra on 2006-07-18
> **bigken said:**
> I had the same problem with a netgear wg311 v2 card it showed the signal strength as 90% but showed as diconected I got round this by using ndiswrapper to install the drivers have you also tried disabling the wep ;)

I would have tryed this, but i cant log into the ip address to reconfigure the router either.... great stuff!

---

### Post by bigken on 2006-07-19
dont you have a onboard nic so you can use cat45 cable to get into the router ;)

---

### Post by forkd on 2006-07-19
> **dmanjra said:**
> I would have tryed this, but i cant log into the ip address to reconfigure the router either.... great stuff!
In case you're like me.....only a wireless adapter on my laptop because the onboard went to Jesus a long time ago...


I've been able to use the liveCD to get into my router and change settings.  If you know your router settings you can also press the "hard reset" button on the router and then connect to it using the default settings.

---

