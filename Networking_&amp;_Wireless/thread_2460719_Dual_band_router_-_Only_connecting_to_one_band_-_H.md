---
title: "Dual band router - Only connecting to one band - HughesNet Internet"
date: 2021-04-16
forum: Networking &amp; Wireless
---

### Post by crltxjojojo on 2021-04-16
Greetings!

I have an Acer Aspire laptop with the latest Ubuntu running, no dual boot. My modem/router has two bands. It's only connecting to wifi through the 5g band and not the 2g band.
The laptop recognizes/sees both, I can access both of their settings.
It automatically connects to the 5g, but when I try to connect to the 2g the password window keeps popping out, I click enter and it loads for some time then the window comes out again with the right password and all.
On that window it also tells me I can press the WPS button to get the connection. I've tried that, but doesn't do anything.
It's HughesNet Satellite Internet BTW.

I've tried disabling the 5g and forgetting it, but still doesn't connect to the 2g.

This doesn't occur on my other devices, yet this laptop is the only device with Ubuntu.

Any suggestions? Questions? Ideas?

---

### Post by TheFu on 2021-04-17
"latest Ubuntu" isn't clear and usually, it isn't actually true.  Today, non-experts shouldn't be running the "latest ubuntu", so please be exact.
**lsb_release -a** is the command.
or
**inxi -b**

WPS shouldn't be used ... ever. It is a huge security failure.

2g wireless has been killed by many cellular providers, so I doubt that will ever work again.  5g has very limited availability in the world today. To get it, I'd have to drive a few miles.

To even begin to help, we'd need to know the exact modem used inside the ubuntu system.

I am confused that if you are trying to connect with 2g and 5g then what is satellite for?

Or am I missing something completely? Sometimes my brain is scattered.

---

### Post by jeremy31 on 2021-04-17
TheFu, I would bet the 2g and 5g are the 2.4GHz and 5GHz wifi bands, not cellular

crltxjojojo any chance the router is using TKIP encryption on 2.4GHz?  See the wireless script link in my signature and post results

---

### Post by chili555 on 2021-04-17
> 2g wireless has been killed by many cellular providers, so I doubt that will ever work again. 5g has very limited availability in the world today. To get it, I'd have to drive a few miles.

To even begin to help, we'd need to know the exact modem used inside the ubuntu system.

I am confused that if you are trying to connect with 2g and 5g then what is satellite for?
I believe you are referring to 5G cellular but crltxjojojo is actually referring to the 2.4 gHz and 5 gHz bands of his 802.11x router. I also suspect that, in his case, internet connectivity is delivered, not by a wire or fiber optic cable, but from a satellite. This is often the only alternative in rural settings where the installation cost of a wire is quite high.

I would like to see the result of these terminal commands:
```
nmcli device wifi list
iwlist freq 
```

---

### Post by TheFu on 2021-04-17
Ah ... 2.4 Ghz and 5.8 Ghz wifi bands. <slaps forehead>!  The 2.4 Ghz stuff is clearly 2.4 Ghz, but the 5.8 Ghz stuff ... seems to be from 5.18 GHz - 5.7 GHz. Confusing, at least to me.

Not that any of this actually matters except that 2.4 Ghz can generally go through most non-concrete walls and the 5Ghz channels really dislike walls.

Hopefully, the OP will return with some data.

---

### Post by crltxjojojo on 2021-04-26
You're correct on what I meant by 2g and 5g. Ghz.


This is one of the lines, number 180 of the txt file I made using your instructions.

WIFI-PROPERTIES.TKIP:                   yes

Says yes, so I need to remove/change that? You need other info besides that?

---

### Post by chili555 on 2021-04-26
> This is one of the lines, number 180 of the txt file I made using your instructions.
May we see it, please? As it is probably rather lengthy, please post it here and give us the link: [http://paste.ubuntu.com](http://paste.ubuntu.com)

---

### Post by crltxjojojo on 2021-05-16
> **chili555 said:**
> May we see it, please? As it is probably rather lengthy, please post it here and give us the link: [http://paste.ubuntu.com](http://paste.ubuntu.com)

[https://paste.ubuntu.com/p/shBHfn62DX/](https://paste.ubuntu.com/p/shBHfn62DX/)

There... I hope I did it correctly...

---

