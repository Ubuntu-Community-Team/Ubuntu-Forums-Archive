---
title: "Well i gut some issues, problems :) take a look ty"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by b0necry on 2009-01-07
Sorry for my week english, trying my best.
Well Short to the point. i need to make a SB Network.(in 2 days) 
This is what i gut:

A new computer (mb: ECS P4M900T-M2, CPU Core2Duoe E7300 3GHz, 1x2G DDR2 667Mhz, 2x SataII 1T Samsung 32mb, DVD-RW, 2 network card)
4 Computers different configurations each whit Assus NX 1101 GBNA
1 whit TRENDnet Wireless N PCI Adapter
1x Webstar modem (from ISP), 
1x TRANDnet Wireles N Gigabit Router TEW-633GR (4 ports)
1x Static ip address   

Soft
 4x Windows Xp Pro and 1x Vista

What did i done:
- i installed ubuntu on the server (the new computer)
- i meet the first bug :) the static ip thing i managed to resolved it after 8 h's.
- i played a little bit whit samba but still seeking some help whit in 5 rows not 200 tutorials/pages/links:)
- i played a little bit whit print server but i still didn't found an adapter for Parallel port to usb. 
- i played a little bit whit users mad some deleted some to accomodate myself. 

What i need to do: 
(hear is the part i need 99% help not to lose 30 days to make it alone)
- To make a folder wher everybody can save files from the network (whit samba i guess,) i think i managed it but i would like if u could show me the each terminal command if i done it ok.)
- How to make my ubuntu a good server well at least so can give the network, internet connection and act good for Print Server and folder share.
- To make a way of mirroring the hard drive because i gut 2x 1T and one should be the backup if something happens all the data should remain on the other Hard Drive. (this i need to do in 1 week no rush)

i will edit this post for progress so i will not replay to overload the thread.

Ty for your help, looking forward in the morning to find some here :)

---

### Post by blueridgedog on 2009-01-07
> **b0necry said:**
> 
- To make a folder wher everybody can save files from the network (whit samba i guess,) i think i managed it but i would like if u could show me the each terminal command if i done it ok.)
- How to make my ubuntu a good server well at least so can give the network, internet connection and act good for Print Server and folder share.
- To make a way of mirroring the hard drive because i gut 2x 1T and one should be the backup if something happens all the data should remain on the other Hard Drive. (this i need to do in 1 week no rush)


The first will use samba and you should start with good howto.  All the advice you will need is located here:

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

The second will require NAT and the use of routing.  This is a great place to start:

[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

The last will require either a hardware raid card or port on the MB or will require software raid via ubuntu.  Do you have hardware raid?

As far as the first two items, help in the forum will be better if you separate you needs into chunks and focus on what you are working on at the time and what problem you have hit.  Such as "I am setting up samba per the doc, but when I try XXXXX I get error YYYYY".

---

### Post by donkyhotay on 2009-01-07
It also helps if you have a more descriptive title.

---

