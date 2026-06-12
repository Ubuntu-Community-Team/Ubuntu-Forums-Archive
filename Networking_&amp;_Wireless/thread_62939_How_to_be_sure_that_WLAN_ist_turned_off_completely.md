---
title: "How to be sure that WLAN ist turned off completely?"
date: 2005-09-06
forum: Networking &amp; Wireless
---

### Post by phibuntu on 2005-09-06
I am using Ubuntu 5.04 (Hoary) and want to be sure the wireless lan is turned off completely.

I don't want my system to look for w-lan-points (hotspots) every now and then.

How do I find out, if the system is not trying to find hotspots. In other words: How do I guarantee that my system is not polluting the air with "microwaves".

(PS: I am using a DeLL Inspiron 9300 with an Intel centrino-chip)

Do I find out this disabling a runlevel-started-deamon or a loaded module?? Which is it :?:

---

### Post by Steve1961 on 2005-09-06
Just go to system/administration/networking and deactivate your wireless card.  That should do it.

---

### Post by phibuntu on 2005-09-06
I see the configuration dialog. But I can either activate nor deactivate the card. 

Sure it is deactivated?

---

### Post by SqdnGuns on 2005-09-06
Fn + F2 or just disable it in the BIOS.

---

### Post by Steve1961 on 2005-09-06
You have to highlight the card by clicking on it first before you can use the activate or deactivate buttons.

---

### Post by cbudden on 2005-09-06
Your worried about producing microwaves.  Do you have a mobile? or a cordless phone or live in a area that has mobile reception?

---

### Post by phibuntu on 2005-09-07
Thanks

@SqdnGuns: I turned it off in the Bios. I have seen that I should post questions AFTER turning on my Brain ;-)


@cbudden: Because we have a one year old child in our household, we do not have mobile (cellular) nor wireless phones. I personally do not "feel" the waves and I think I am realy "robust" against them. But I do not know about my son. A friend of mine worked on a project to find out the "negative" effects (like leukaemia) caused by cellular phones. As soon as he was finding the first results the phone companies stopped the money for his researches. I am not sure, but I think there must be some risk especially for small children :?: 
But thanks anyway for your replay. 

phi

---

### Post by Buffalo Soldier on 2005-09-07
[QUOTE=phibuntu]I see the configuration dialog. But I can either activate nor deactivate the card. 

Sure it is deactivated?[/QUOTE]If that's the case than the wlan/eth0 card is not configured. I assume that is a lot safer than simply being deactivated.

Just in case you want to re-activate it, click properties and then check **This device is configured**

---

