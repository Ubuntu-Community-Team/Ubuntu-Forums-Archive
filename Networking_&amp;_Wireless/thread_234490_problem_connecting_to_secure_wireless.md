---
title: "problem connecting to secure wireless"
date: 2006-08-11
forum: Networking &amp; Wireless
---

### Post by dahagama on 2006-08-11
Iam a newbie and i have a Belkin Wireless box in my home and i enabled security and i know the WEP key too. But where should i enter this WEP key on ubuntu box?? When i click on wireless device (eth0) nothing happens ....What should i do now???

Naresh

---

### Post by jeff_ on 2006-08-11
Go to System > Administration > Networking. Select your wireless interface and click on Properties. You can enter your WEP key there.

---

### Post by dahagama on 2006-08-11
I cannot do what you said.... When i do that it asks for root password and when i enter the root password the window vanishes and nothing happens .....

---

### Post by jeff_ on 2006-08-12
> **dahagama said:**
> I cannot do what you said.... When i do that it asks for root password and when i enter the root password the window vanishes and nothing happens .....

Wow, never heard of that happening. Try typing 'sudo iwconfig key s:mykey' in a terminal and see if that will at least temporarily work. If it does we'll have to do something permanent since that'll only work until you restart. After you execute that type 'iwconfig' in the terminal and post the output.

---

