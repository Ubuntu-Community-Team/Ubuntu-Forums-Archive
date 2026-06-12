---
title: "PLease Help Guys"
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by naikadit on 2008-02-20
hey guys...  I am experiencing a  problem with ADHOC in ubuntu 7.10... I have installed ubuntu 7.10 in 2 laptops we have changed the mode Ad-hoc, the frequency channel id , essid, netork name and cell id to be the same... but still we are not able to ping each other...we have taken a staitic address 10.10.0.1 and .2 respectively and subnet accordingly...please guys i would be really glad if u could reply i am desperate i need it for a project....thansk in advance,,

---

### Post by jhetrick62 on 2008-02-20
Can both properly connect to a normal managed wireless network?  If not, one or both of the drivers is probably not functioning properly.

Jeff

---

### Post by IamAcoconut on 2008-02-21
Please use informative titles. Don't require ppl to guess what your problem is. So much for "PLease Help!". 

Now, what wifi cards are the computers using? ```
lshw -C network
```
And of course try to answer jhetrick62's question.

---

### Post by naikadit on 2008-02-27
hi thanks for the reply...actually me and my friend are able to connect to the internet but we are not able to associate with each other..i.e we are not able to ping each other ...so i had checked earlier and I had som eiptbales werein ifac i and ifac o was mentioned so i used iptables -F iptables -X, iptables -Z command and it worked in my apartment was not working in my school bt now its not working in my apartment too..pleas ehelp

---

### Post by IamAcoconut on 2008-02-27
> **IamAcoconut said:**
> Please use informative titles. Don't require ppl to guess what your problem is. So much for "PLease Help!". 

Now, what wifi cards are the computers using? ```
lshw -C network
```
And of course try to answer jhetrick62's question.
**naikadit**, please read once more. And do not bug users via PM, it's considered rude. Let them benefit from our common findings. There already are notifications.
And please be **clear**. Punctuation marks are also very welcome. 
Can you connect to a managed network, or the one you mentioned is this Ad-Hoc thing?

---

### Post by naikadit on 2008-02-27
hi, I am able to connect to the managed network also I am able to change my mode to ad-hoc also I am able to access the wireless network .....  everyhting is proper I guess but I am still not able to ping the other machine...

---

