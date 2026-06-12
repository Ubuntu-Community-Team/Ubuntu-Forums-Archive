---
title: "Wireless needs restarting to connect ??"
date: 2007-01-27
forum: Networking &amp; Wireless
---

### Post by glenn69 on 2007-01-27
My wireless is configured as rausb0.

When I first try to connect to a wireless signal, I have to type the following to get a connection :

sudo ifdown rausb0
sudo ifup rausb0

Then the connection is made.

Shouldn't this happen automatically at boot?  

My /etc/network/interfaces lists the rausb0 as follows :

auto rausb0
iface rausb0 inet dhcp

What should I do to automate this task?

---

### Post by glenn69 on 2007-01-28
OK, in case anyone needs the solution, here is how I fixed it :

edited /etc/rc.local

added both lines to that file

ifdown rausb0
ifup rausb0


Now it works!

---

### Post by abygomez on 2007-01-28
hi,

i am new to ubuntu. i was able to configure my wifi card (belkin) using this procedure.

[https://help.ubuntu.com/community/Wi...211b_driver%29](https://help.ubuntu.com/community/Wi...211b_driver%29)

It works well in a 64 bit wifi atmosphere because the password length is small. but when it comes to a 128 bit wifi atmosphere i could not type in all the 26 charecters in to the password box. is there any way to enter all the 26 hexadecimal charecters in to the password box.

---

### Post by nomowindows on 2007-02-16
thanks glenn69! :)  the rc.local edit worked for me too!

---

