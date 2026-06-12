---
title: "cant etablish connection with my wifi router"
date: 2006-07-23
forum: Networking &amp; Wireless
---

### Post by xace on 2006-07-23
hi all ,
i installed ubuntu dapper instead of breezy yesterday. i wanted to install the net on my ubuntu. I installed windows drivers with ndiswrapper . ndiswrapper toll me :
driver present, hardware present.
the light on my dongle switches on . i look on wifi radar and i receive my router (a inventel livebox) and too my neighbour's router ! i tried to etablish connection and wifi radar (and the gnome network configuration tool too) toll me about : cannot give ip adress. so i tried to force it entering the ip but that doesn't work. i use a thomson wlg1500a dongle (sis 163u chipset)
sorry for my bad english but i'm a french student and on the french  ubuntu forum i have no answer to my problem
Thanks for helping me.
xace

---

### Post by wieman01 on 2006-07-25
> **xace said:**
> hi all ,
i installed ubuntu dapper instead of breezy yesterday. i wanted to install the net on my ubuntu. I installed windows drivers with ndiswrapper . ndiswrapper toll me :
driver present, hardware present.
the light on my dongle switches on . i look on wifi radar and i receive my router (a inventel livebox) and too my neighbour's router ! i tried to etablish connection and wifi radar (and the gnome network configuration tool too) toll me about : cannot give ip adress. so i tried to force it entering the ip but that doesn't work. i use a thomson wlg1500a dongle (sis 163u chipset)
sorry for my bad english but i'm a french student and on the french  ubuntu forum i have no answer to my problem
Thanks for helping me.
xace

Your network card seems to work, now it's just a question of configuring your network settings.

Can you tell us what your router's configuration is? E.g. if you are using DHCP, WEP encryption/authentication, ESSID, etc.? You can use the Networking Tool in Gnome to configure your wireless network card, but you have to do so according to your NETWORK SETTINGS. 

Otherwise you won't be able to establish communication with the router.

---

### Post by philippe_carlo on 2006-07-25
Mistake made by myself yesterday while using wifi-radar:

If the wep-key is entered as a 5-character string, you need to precede it with 's:'. So if my wep key were, say "teste", then you should enter "s:teste" as the key.

Not sure if that helps you, but it's better to know anyway.

---

### Post by wieman01 on 2006-07-25
> **philippe_carlo said:**
> Mistake made by myself yesterday while using wifi-radar:

If the wep-key is entered as a 5-character string, you need to precede it with 's:'. So if my wep key were, say "teste", then you should enter "s:teste" as the key.

Not sure if that helps you, but it's better to know anyway.

True, fell into the same trap once. But naahh, you should not use WEP at all. ;-) It's not secure. Use WPA2 for your own good.

---

### Post by philippe_carlo on 2006-07-25
My attitude towards this is: if you can crack my WEP, you're free to use it. Although I sincerely doubt that any of my neighbors can and my wireless does not reach the street.

---

### Post by wieman01 on 2006-07-25
> **philippe_carlo said:**
> My attitude towards this is: if you can crack my WEP, you're free to use it. Although I sincerely doubt that any of my neighbors can and my wireless does not reach the street.

It's true, cracking somebody's network has only limited value. Nevertheless I always stress how important secure encryption, etc. is because you never know what 3rd party do with your data. But perhaps we should discuss this in another thread. :-)

Interesting topic though.

---

### Post by xace on 2006-07-27
hi,
thanks for answering me. my configuration is :
WEP key , DHCP and SSID. is there any solution for my problem...
i install ubuntu to my father and i want to he discover linux...
thanks
xace

---

