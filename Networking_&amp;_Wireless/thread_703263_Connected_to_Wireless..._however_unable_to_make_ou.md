---
title: "Connected to Wireless... however unable to make outbound connections"
date: 2008-02-21
forum: Networking &amp; Wireless
---

### Post by markbusu on 2008-02-21
Hi,

First of all im pretty new to the linux scene, so excuse me if the answer to my question is easy :)

I have a the following Wifi Network Controller (Output of lspci) :

Broadcom Corporation BCM4368 882.11b/g Wireless Lan Controller (rev 03)

I have a Wifi Router at home... which uses a simple WEP Key... 12 character

When attempting to connect to the Wifi Router i need to enter the pass key.. the only method which i successfully managed to authenticate to the router is by using the WEP 64/128-bit HEX...  no other method has managed to authenticate...

Now... it appears that i have obtained an IP address from the DHCP Server from the router... and am able to connect to it... however i cannot ping any machine within my local lan nor browse the internet.

If i connect the Laptop via a UTP cable to the Router... Internet Works Fine....

Note... i am currently using the restricted drivers BCM43xx.

I believe this has got to do with the pass key in some sort... since normally i never get these issues when an Access Point doesn't have any Pass Key (Not that that is recommended) :)

Thanks for any feedback you can give!

Mark

---

### Post by markbusu on 2008-02-21
Ps... this is a dual boot... if i boot with Win XP or any other machine within my local lan with Wifi... i get access... so i doubt this might be a router mis configuration..

Thanks once again

---

