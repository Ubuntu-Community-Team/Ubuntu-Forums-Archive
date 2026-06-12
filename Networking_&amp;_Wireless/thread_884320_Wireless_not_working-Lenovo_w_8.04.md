---
title: "Wireless not working-Lenovo w/ 8.04"
date: 2008-08-08
forum: Networking &amp; Wireless
---

### Post by wmerrell on 2008-08-08
I have just installed Ubuntu 8.04 on a Lenovo 3000 N100 Laptop. 

It looks like the right drivers are there, lspci reports the right thing, iwconfig reports sensible things, all the commands in several of the messages here and various help documents look like the right things are happening.

What isn't happening is, it is not connecting. It looks like the radio hardware is not being turned on. The machine has a switch and a light on the front. The switch controls both the wireless and the bluetooth. When I switch it on, the light for the bluetooth comes on, but the light for the wireless does not.

Does anyone know what to check to get the wireless radio hardware to turn on?

BTW, I am fairly new to Linux, but not completely green.

Thank you,
--Will Merrell

---

### Post by wmerrell on 2008-08-09
Any body have any idea how to turn on the wireless hardware on a Lenovo?:confused:

---

### Post by ranchersd on 2008-08-10
No help other than to say I have the same problem with the R51 IBM thinkpad. Only difference is that I do not have the physical switch to disable wireless.

I would assume someone knows how to turn the Thinkpad wireless devices on. Looking forward to you help.

---

### Post by stevebag on 2008-08-30
There is a page with the Lenovo 3000 n100 specs and problems listed, with a particular solution for wifi at the following link

[https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N100_0768](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N100_0768)

I followed the directions there with success.

---

### Post by sahilbhrany on 2008-08-31
I had the same problem as well but when i selected a previous kernel from grub, wireless worked. And now after a recent upgrade, wireless works fine for me.

---

