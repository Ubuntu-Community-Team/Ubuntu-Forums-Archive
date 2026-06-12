---
title: "Wireless 54g 802.11b/g WLAN with 125hsm*/speed booster + broad range - HOW TO WORK?"
date: 2007-02-06
forum: Networking &amp; Wireless
---

### Post by r1u on 2007-02-06
Hello, I have been trying to get my wireless card to work for some time now, I have tried NDIS wrapper or at least I am sure I tried it properly, but no luck, How/What can I try/Do to get this card to work? It is simply not found

Thanks so much

---

### Post by MeeMaw on 2007-02-06
It would help to know exactly what brand of wireless card (and driver) you have - some use ndiswrapper and some don't. You probably need to open a terminal and type 

sudo lspci 

(you will be asked for your root password too)

and post the results here

(someone correct me if I'm wrong - I'm stilll a noob myself!)  :)

and which version of Ubuntu are you using?

---

### Post by jgf621 on 2007-02-08
I have the same problem with a new HP laptop.

Running    sudo lspci      gives me

Network controller: Broadcom Corporation Unknown device 4311 (rev 01)

How can I make this work?

Thanks

> **MeeMaw said:**
> It would help to know exactly what brand of wireless card (and driver) you have - some use ndiswrapper and some don't. You probably need to open a terminal and type 

sudo lspci 

(you will be asked for your root password too)

and post the results here

(someone correct me if I'm wrong - I'm stilll a noob myself!)  :)

and which version of Ubuntu are you using?

---

### Post by MeeMaw on 2007-02-08
> **jgf621 said:**
> I have the same problem with a new HP laptop.

Running    sudo lspci      gives me

Network controller: Broadcom Corporation Unknown device 4311 (rev 01)

How can I make this work?

Thanks

jgf621       There is a how-to for the broadcom 4311 here -- 
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show)

You need to follow it exactly. I hope it helps!!!!

r1u  Have you been successful?    I hope so!  You both will find after the work involved in some configurations, it is a joy to sign on to your Linux box and just be able to use your computer without all the garbage jobs you had to do on that other OS!    :)

---

