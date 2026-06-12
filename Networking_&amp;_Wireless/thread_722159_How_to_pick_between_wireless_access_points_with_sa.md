---
title: "How to pick between wireless access points with same name?"
date: 2008-03-12
forum: Networking &amp; Wireless
---

### Post by Svopp on 2008-03-12
Hey,


I am having problems with getting ubuntu 7.10s wireless to work properly on my school. theres several wireless access points on the school.

The internet is really slow and really laggy, and it is ONLY me, and ONLY WHEN IM IN MY OWN CLASSROOM that i have the problem.

There is a wireless access point in my very classroom. 7 metres away...  i am suspecting that the reason i am lagging, is that is connects to a wireless access point further away than in my classroom..
They all have the same server name, as they all link to the same network ...

I have found no UI in ubuntu which can help me choosing access points... it only shows one network, even if i stand between 5 access points ... 
i guess i need to force my computer only to use the access point in my classroom, and not jump to anywhere else ...

All the access points have got the same name: "Holstebrots.dk", so i cant choose between them.
But maybe if i get the mac address of the one in my class room i can force it to do that?


Any help appreciated. 
Thanks in advance.

---

### Post by handydan918 on 2008-03-12
IIRC, wicd will help with this. I think it's in the repos...

---

### Post by Svopp on 2008-03-12
Are those names on programs ?

---

### Post by handydan918 on 2008-03-12
> **Svopp said:**
> Are those names on programs ?

Heh. IIRC is "If I recall correctly." You use it a lot after you pickle enough brain cells...
wicd is an application for managing wireless.:)

---

### Post by aeiah on 2008-03-12
i dont know about an automatic way to do this, but you could set it up with a script. you should be able to connect to a specific mac address with this:

sudo iwconfig wlan0 ap MAC

instead of using the usual

sudo iwconfig wlan0 essid "NAME"

---

### Post by Eiríkr on 2008-03-12
As ever, actually reading the manuals provides more detail.  ;)  From th man page for iwconfig:
> **essid**

Set the ESSID (or Network Name - in some products it may also be called Domain ID).  The ESSID is used to identify cells which are part of the same virtual network.  As  opposed to the AP Address or NWID which define a single cell, the ESSID defines a group of cells connected via repeaters or infrastructure, where the user may roam transparently.

The way wireless networks are set up is an attempt at making things transparent to the end user, so that a single wirelss ESSID can be used for a whole area without the user suddenly losing the connection and having to manually select a different ESSID just because they wandered into a different room or changed floors.  So this is *not* what you need to change.  

However, reading further tells us:
> **ap**

Force the card to register to the Access Point given by the address, if it is  possible.  This address is the cell identity of the Access Point, as reported by wireless scanning, which may be different from its network MAC address. If the wireless link  is  point to point, set the address of the other end of the link. If the link is ad-hoc, set the cell identity of the ad-hoc network.

When the quality of the connection goes too low, _the  driver  may  revert  back  to automatic mode (the card selects the best Access Point in range)_.  You  may  also  use  off  to  re-enable automatic mode without changing the current Access Point, or you may use any or auto to force the card to reassociate with  the currently best Access Point.

**Example :**
```
                   iwconfig eth0 ap 00:60:1D:01:23:45
                   iwconfig eth0 ap any
                   iwconfig eth0 ap off
```

So while you can use scanning and then this **ap** parameter to pick a specific access point, the underlined portion above indicates that the default behaviour is this "automatic" mode, wherein your wireless card should automaticlly pick the best access point you've got for your current physical location.  

I hate to say it, but my wife's a teacher, and I've seen some pretty fugly setups, so the trouble might just be your IT department...

Good luck,

Eiríkr

---

### Post by Svopp on 2008-03-12
I am at home at the moment, but have installed the WICD network program as he suggested.

The problem started suddenly about 2 weeks ago, none of my friends noticed any change, and the problem occoured to me BOTH IN UBUNTU AND WIN-XP AT THE SAME TIME.

I also tried to set it to a set mac address. But this didnt give me better net.

Its quite a mystery... im looking at the percentage of connection it receives ... it jumps up and down from 3 % to 85 % to 50 %. Its really unstable. 
I dont know if it is hardware or software changes from the school. otherwise i think i may be having a lose connection in my wireless .. sounds lame ... lose connection in wireless .. 

Thanks for the help given so far.

---

