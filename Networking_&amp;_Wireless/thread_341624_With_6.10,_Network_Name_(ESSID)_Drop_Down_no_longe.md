---
title: "With 6.10, Network Name (ESSID) Drop Down no longer shows network list"
date: 2007-01-18
forum: Networking &amp; Wireless
---

### Post by ileavache on 2007-01-18
In 6.06, the network name drop down (*) was able to present the same network list as the one detected by the wifi radar. This was quite practical and it no longer works in 6.10.
Now, I have to view the network list with the radar and type the name in the properties panel.
Not a big deal but a little bit annoying when you move from one site to another.
Does anybody know about this regression? 


(*) System > Administration > Networking > Properties for the Wireless connection.

---

### Post by gabrieliscool on 2007-01-19
Same here dude, I've had this same problem since edgy came out, but i never said anything because if you just type in manually the essid, it will connect.

---

### Post by Dygear on 2007-01-19
So ubuntu could see wifi networks in an older version? Man that sucks, big time. I'd really like to see the networks in my area so I don't have to keep connecting the RJ-45 in each time I'm at the core on an Over Night.

---

### Post by ileavache on 2007-01-21
I ended up installing the network manager. It's actually handier. Shows the list of networks in the 'hood and connects to the one you pick.

---

### Post by sceptre0 on 2007-03-04
I am having the same problem.  I tried NetworkManager, but it does not recognize any wireless networks, even the one I am currently connected to.  My network card info is below.

Vendor: Realtek Semiconductor Co., Ltd.
Product: RTL8180L 802.11b MAC

OEM Vendor: Realtek Semiconductor Co., Ltd.
OEM Product: Unknown (0x8180)

I have had this problem since I installed 6.10.  Everything worked fine in 6.06.  I believe I did a fresh install of 6.10. 

Any help would be appreciated.  Thanks!

---

### Post by sceptre0 on 2007-03-04
I got NetworkManager to work.  I had to deconfigure my network card and restart.  Thanks, ileavache.

---

### Post by Sepp1 on 2007-06-01
I experienced the same after upgrtading to Edgy, and had to type the networks in manually - rather tiresome - after upgading to Feisty, it does display the list, but only if there are no networks that it has previously connected to. I am almost sure that it is a setting somewhere, because I can see how it would be handy in some situations - unfortunatly not for me though.

Sepp1

---

