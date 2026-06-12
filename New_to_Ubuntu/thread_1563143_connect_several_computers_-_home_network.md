---
title: "connect several computers - home network"
date: 2010-08-28
forum: New to Ubuntu
---

### Post by valllllll2000 on 2010-08-28
Hello everybody,

I would like some help to connect several computers.

Here is what I have:

-rooter Comtrend HG536+

-laptop ubuntu 10.04 + vista

-netbook ubuntu 10.04

- hp printer with wifi

-laptop windows xp

All the computers conect to the internet with wifi cards

Only the windows xp laptop can print using the wifi, the ubuntu one's I have to connect the cable.

I would like them all to be in a network through wifi and especially to be able to print. Samba is installed on both ubuntu computers but I cannot modify the config file it doesn't let me (I don't know how to open it in root) so when I share some directories the other computer doesn't see them. So the tutorial I have found around are very complicated could anyone give e a link for an easy one, step by step configuration.

Thank you very much in advance

---

### Post by Zzl1xndd on 2010-08-28
If Samba is installed you may already be able to access the other machines.

First for the Printer access System > Administration > Printing.

Then select Add >  Network Printer > Windows Printer Via Samba and browser for the printer. (Provided it doesn't Auto Populate.)

For the network shares check Places > Network > Windows Network.

If nothing is listed attempt to access the shares by going to Places > connect to server, select windows share and input the ip address of the machine you are attempting to access.

---

### Post by valllllll2000 on 2010-08-29
Thank you tweakedenigma
Nothing was listed so I did how you told and it worked just fine. 
Just out of curiosity: I connected 2 ubuntu computers: why is it called windows network?
thanks

---

