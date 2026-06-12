---
title: "Network Manager and the ACX chipset"
date: 2006-08-12
forum: Networking &amp; Wireless
---

### Post by NetworkGuy on 2006-08-12
Hi All,

I've just started looking into the Ubuntu distribution and I am very impressed with both the distribution as well as the community support that is available for it.   These forums have answered most of my problems, but one problem still exists.  

I have a laptop with the WPC54G v2 (TI ACX 111 chipset).  While it appears that this card has given a lot of people issues (myself included),  I followed this link  [http://www.ubuntuforums.org/showthread.php?t=233565]("http://www.ubuntuforums.org/showthread.php?t=233565")   and without Network Manager, I can use the card without any issues.  Currently there is not any WEP or WPA yet as I turned it off while I try to get this working.

Now I have loaded Network Manager using Automatix and set it up by commenting out all entries in my /etc/network/interfaces file except lo.   I can see all the access points in my area including my own ;) however when I try to connect to it, Network Manager times out.

When I am not using Network Manager, I use the acx driver per the above link.  Network Manager is trying to use the acx_pci driver.  Are these actually the same driver?  If not, how can I get Network Manager to use the proper acx driver so I can continue?

---

### Post by jarocooke on 2006-08-12
/etc/network/interfaces

All those items which you commented out in the above file need to be uncommented otherwise it doesn't work.  At least that is what sorted it out for me.
:D

---

### Post by NetworkGuy on 2006-08-12
My current interfaces files has the lines back in.   While i can still see many access points, trying to connect to one using Network Manager "broke" my current connection.  Once it timed out, I had to ifdown & ifup wlan0 to get my connection back.

---

### Post by NetworkGuy on 2006-08-15
*Bump*

I currently have it working using the link in the first post, but would like to use NetworkManager for those few occasions I need to hop onto a different AP without having to change configuration files.

Thanks all

---

### Post by tessuraea on 2006-08-26
Same problem, slightly different card--I'm glad I'm not crazy...  I have the ACX 100.  Network Manager times out while trying to connect every time.  It doesn't seem to matter if I have everything in /interfaces commented out or not.

Any advice would be great; this is my school laptop and I really need to be able to access different wireless networks on it.  Currently I can but it's a bit of a pain...  and of course no WPA.

---

### Post by Kebabji on 2006-11-25
my acx 111 works if i do this - i have to log in, wait for kwalletmanager to take my password so that knetworkmanager can try to log me into my network, take out the card (otherwise itll just be stuck on 28% until it times out), put it back in and enter the network name and wep manually. sometimes i have to do these steps twice, otherwise it wont work. quite annoying :)

---

### Post by nipx on 2007-03-14
Hey,

I've got the same problem with Netgear Wg311v2 (ACX111) Network Manager won't connect however manual settings work without any troubles. Been searching for a solution but with no luck

---

