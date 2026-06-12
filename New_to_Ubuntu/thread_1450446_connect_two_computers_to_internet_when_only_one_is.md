---
title: "connect two computers to internet when only one is connceted via wireless"
date: 2010-04-09
forum: New to Ubuntu
---

### Post by antonio_ing on 2010-04-09
hi guys

i have a problem. A friend of mine has a computer with no wireless and he would like to connect to internet via my laptop which is connected to internet via wireless. We both have ubuntu on our laptops. (me 9.10 he 8.10). How can he do that through ethernet cable?

---

### Post by Temposs on 2010-04-09
Well, the easiest way would be if you have access to the wireless router you're connecting to, just have him plug in an ethernet cable into that.

---

### Post by antonio_ing on 2010-04-09
sadly there is only a wireless access point with no plugs

---

### Post by Dayofswords on 2010-04-09
then what is the wired connected to?


and what router doesn't have Ethernet ports! outrageous

---

### Post by antonio_ing on 2010-04-09
actually i am just wireless connected (i do not know where is the access point :-) ) and my friend's wireless does not work

---

### Post by lisati on 2010-04-09
> **antonio_ing said:**
> hi guys

i have a problem. A friend of mine has a computer with no wireless and he would like to connect to internet via my laptop which is connected to internet via wireless. We both have ubuntu on our laptops. (me 9.10 he 8.10). How can he do that through ethernet cable?

It almost sounds like the answer lies in him hooking up his computer to yours via a crossover ethernet cable and using your computer as a gateway.

---

### Post by Dayofswords on 2010-04-09
> **antonio_ing said:**
> actually i am just wireless connected (i do not know where is the access point :-) ) and my friend's wireless does not work

let me get this straight:

1 computer, wired only, not connected
1 computer, wireless (only?), connect to wifi
1 access point, dont know where it is, no ports, (do you even own it?)
1 friend, broken wireless

if he gets his wireless working, you could ad-hoc it, idk how on ubuntu though

---

### Post by lisati on 2010-04-09
> **antonio_ing said:**
> actually i am just wireless connected **[COLOR="Red"](i do not know where is the access point :-) )[/COLOR]** and my friend's wireless does not work

Do you have permission to use the access point?

---

### Post by antonio_ing on 2010-04-09
lisati got what i meant. Is that possible under ubuntu? because i got another friend which uses Mac and he said that for mac it is easy

---

### Post by antonio_ing on 2010-04-09
no, just university connection

---

### Post by Dayofswords on 2010-04-09
you could do like the person up there said with a crossover, but thats not like a normal one, different wiring inside

---

### Post by Mykk on 2010-04-09
You will require a cross over cable to do this,

All they are is reverse wiring inside the ethernet heads. For example (trying to remember all/some of the colours) if you had:

Orange
Orange and white
Brown
Brown and white
Green
....ETC ETC

It would be on the otherside:

Green
Brown and white
Brown
Orange and white
Orange


If you dont have the equipment to hand like me to make one just go out and buy one - they arent expensive.

---

### Post by antonio_ing on 2010-04-09
i have a crossover cable with me

---

### Post by Mykk on 2010-04-09
> **antonio_ing said:**
> i have a crossover cable with me

Then it should be just a case of using the laptop with internet connection as a gateway. I know how to do this in windoze but not in ubuntu - should be pretty easy and im sure one of the nice people on this forum will give you instructions ;)

---

### Post by zengzhangsong on 2010-04-09
You need use a wireless router!

---

### Post by Mykk on 2010-04-09
> **zengzhangsong said:**
> You need use a wireless router!

He is?

---

### Post by Chronon on 2010-04-09
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

> **Ubuntu 9.10 Method**

You will need either two Ethernet ports, one for the incoming internet and 1 for the connection to the other computer, or *a Wireless card for the incoming internet and an Ethernet port for the connection to the other computer*. When logged into your computer right click on the network indicator in the top right hand corner, click on "Edit Connections..." select "Auto Eth0" and click "Edit..." then go to the "IPv4 Settings" tab and next to "Method:" select the drop down box and select the option that says "Shared to other computers". Restart your computer and then you will be able to just plug-in any computer to your Ethernet port to share the connection. 

---

### Post by antonio_ing on 2010-04-09
i have changed the method in my computer which is wireless connected. What about the other pc? internet there (connected to auto eth0) does not work

---

### Post by Chronon on 2010-04-09
Did you reset your computer?

What kind of cable are you using?  The page doesn't mention a crossover cable, so I would try a normal cable if the crossover doesn't work.

---

### Post by albert s on 2010-04-09
wireless USB stick would be the easiest. and simpliest solution I think,
try edimax

---

### Post by Benic on 2010-04-20
> [https://help.ubuntu.com/community/In...nectionSharing](https://help.ubuntu.com/community/In...nectionSharing)

Quote:
Ubuntu 9.10 Method

You will need either two Ethernet ports, one for the incoming internet and 1 for the connection to the other computer, or a Wireless card for the incoming internet and an Ethernet port for the connection to the other computer. When logged into your computer right click on the network indicator in the top right hand corner, click on "Edit Connections..." select "Auto Eth0" and click "Edit..." then go to the "IPv4 Settings" tab and next to "Method:" select the drop down box and select the option that says "Shared to other computers". Restart your computer and then you will be able to just plug-in any computer to your Ethernet port to share the connection. 

Update: Finally it works! First I've put the host eht0 in share mode and then I've set manually the guest eth0 using the host eth0 ip as gateway. Finally I've added this address in guarddog. As simple as that!

---

