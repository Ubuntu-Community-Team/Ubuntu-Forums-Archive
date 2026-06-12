---
title: "Small problem with mobil phone and internet."
date: 2006-08-26
forum: Networking &amp; Wireless
---

### Post by Ausus on 2006-08-26
Hi All,

I have a small problem.
I managed to setup my mobile phone for Internet.
When I dial out my normal onboard network cards interfer.
I dont get a connection.
When I both disable them then I can use my mobile for the internet.

I have a message file at home that point to my network IP address the interfer from getting any connection.
My IP address setings are as follow:192.168.1.10 subnet mask 255.255.255.0 the othe one is 192.168.1.15 subnet mask same as other network card.

regards](*,)

---

### Post by Jussi Kukkonen on 2006-08-27
Don't take this the wrong way, but understanding the problem from your post is a bit hard. I think you'll have to be a little more specific... 

Some things I'm not sure of:
* Do you want to use your phone as a modem, to connect your PC to the internet through it?
* If yes, how are the devices connected, bluetooth? Does that connection work -- e.g. file transfer?
* You seem to be setting a LAN IP-address for the mobile... Normally mobile phones connect to ISPs gateway (and get something different for their IP-address), not your home network. Do you really have a wlan-enabled phone or did I misunderstand?

> When I dial out my normal onboard network cards interfer.
Some details are needed here... What did you try, and what actually happens?

> I have a message file at home that point to my network IP address the interfer from getting any connection.
I'm not sure what you mean here, can you phrase that differently?

---

### Post by Ausus on 2006-08-27
Hi Jussi Kukkonen,

[HTML]* Do you want to use your phone as a modem, to connect your PC to the internet through it?[/HTML]

Yes and it is working.

[HTML]* If yes, how are the devices connected, bluetooth? Does that connection work -- e.g. file transfer?[/HTML]

Yes I'm using a Nokia N70 via USB port.

[HTML]* You seem to be setting a LAN IP-address for the mobile... Normally mobile phones connect to ISPs gateway (and get something different for their IP-address), not your home network. Do you really have a wlan-enabled phone or did I misunderstand?[/HTML]

Yes I have two onboard ethernet cards wich are configured as per first post.
I dont use thes ethernet cards, they are not connected to a network.

When I run the following command.
Code:
[HTML]tail -f /var/log/messages[/HTML]
Then when I looked into this message file I found that ethernet card IP address 192.168.1.10 also came up in this message file. I tried a couple of times to log in via my mobil phone.I did not work.
Then out of desparation I disabled both ethernet cards.
Viola my internet connection I could establish.


regards

---

### Post by Ausus on 2006-08-28
Hi Jussi Kukkonen,

I supplied feedback, no answer.

regards

---

### Post by Jussi Kukkonen on 2006-08-28
> **Ausus said:**
> Hi Jussi Kukkonen,

I supplied feedback, no answer.

Hey, I have to sleep too, you know :)

One thing that I'm still not sure about: What do you want to happen? I understood that at the moment you don't use the ethernet adapters and the network-through-usb/mobile is working -- would you like to have a connection through ethernet also, or what is the problem?

> Yes I'm using a Nokia N70 via USB port.

Ok. I'm not too familiar with this ppp-over-usb (which I'm guessing this is). Someone else will probably have to chime in if there's a problem with this.

The fact that you get IPs for those onboard ethernet cards  at all implies that you  either have set some static IPs or that you are connected to a gateway and get a dynamic IP whether you want it or not (you said you're not connected at all, so the static-IP-theory is probably correct). See *System-->Administration-->Networking* or look at */etc/network/interfaces* config file to find out... (you must have have some funky motherboard by the way, to have two onboard network adapters). 

What does "disabling ethernet cards" mean, by the way -- did you disable them in BIOS or something?

---

### Post by Ausus on 2006-08-28
Hi Jussi Kukkonen,

Sorry Jussi from time to time I also sleep.
Tnx for replying.

[HTML]One thing that I'm still not sure about: What do you want to happen? I understood that at the moment you don't use the ethernet adapters and the network-through-usb/mobile is working -- would you like to have a connection through ethernet also, or what is the problem[/HTML]

No ethernet connection required. I dont have a networked setup at home.

[HTML]What does "disabling ethernet cards" mean, by the way -- did you disable them in BIOS or something?[/HTML]

I disabled the ethernet cards from Linux, made them in active.


Regards

---

### Post by Jussi Kukkonen on 2006-08-28
...ok, but is there still a problem? Did you need help with anything?

---

### Post by Ausus on 2006-08-28
Hi Jussi Kukkonen,

No problems at all.
Why I ask so many question is because I a Technical person.
I'm still in my infant stages of learing linux.
I dont want to see Linux as a Black Box.
I want freedom to do what I have to do.
I would like to see how the Linux platform is intergrared.
See the working inside of Linux.
What makes Linux tic.

I see summer for you is comming to and end.
Spring will start by use in a few day's.

Regards
Greeting from South-Africa

---

