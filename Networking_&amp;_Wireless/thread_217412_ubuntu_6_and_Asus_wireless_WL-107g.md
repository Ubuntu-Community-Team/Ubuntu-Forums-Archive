---
title: "ubuntu 6 and Asus wireless WL-107g"
date: 2006-07-17
forum: Networking &amp; Wireless
---

### Post by oziris on 2006-07-17
i'm new to linux world so ...
i have installed ubuntu 6 on my old laptop HP NX9005. ubuntu don't recognize my wireless adaptor Asus WL-107g. what to do to solve this problem?

thx

---

### Post by Stinger on 2006-07-17
If I'm right your wireless card uses the [Ralink RT2500 chip](http://www.ralinktech.com/supp-1.htm) which is supported in linux just like my [Asus WL-167g]("http://dk.asus.com/products4.aspx?l1=12&l2=42&l3=136&model=57&modelmenu=1").

I presume your wireless card was present during installation ? If it was , it should show up in System > Administration > Networking , probably as ra0 , mine shows as rausb0 cause it's an usb device , does it show ?

---

### Post by oziris on 2006-07-18
thx, that solved the problem!
however, how do i get the MAC adress of my card (in router if i turn on MAC adress control i cannot connect to internet)?

---

### Post by Stinger on 2006-07-18
If you decide to enable mac address filter, you'll have to add the MAC address into the router.

On the backside of your wireless card you'll find the label with the 
MAC adress , like this,
[IMG]http://eduroam.prf.cuni.cz/hw/wl-107g.jpg[/IMG]

---

### Post by tturrisi on 2006-07-18
You can get the card's mac  address by going to:
System > Administration > Networking > Support tab

---

