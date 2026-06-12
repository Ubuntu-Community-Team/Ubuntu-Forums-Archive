---
title: "wifi with wpa out-of-the-box possible?"
date: 2007-04-18
forum: Networking &amp; Wireless
---

### Post by frafu on 2007-04-18
Hello, 

Is it possible to set up wifi on ubuntu feisty, set can connect to a router with wpa encryption and that does not have to be reconfigured when ubuntu gets updated? 

The router is a dlink, but I don't remember the model. 

Maybe that I can achieve the desired goal by using the network manager with a card that has a chipset indicated on this page? 

Thanks for any reply or advice. 

Francesco

---

### Post by rufius on 2007-04-18
I've done so on Feisty with an Intel 3945 card (a/b/g). It works fine for what you describe. It shouldn't have problems with other cards assuming they're supported.

---

### Post by frafu on 2007-04-18
Thanks for your reply.

However, how can I know whether a card is supported? 

I know about this page: 
[http://live.gnome.org/NetworkManagerHardware](http://live.gnome.org/NetworkManagerHardware)
Does this mean that if I get a card with one of those chipsets that also have wpa in their comments, it will be working also through updates without having to do anything? 

There is also this page: 
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

If a card is supported, does that mean that it is directly supported by the kernel? 

When a card is supported, does that mean that it will also have wpa? 

When a card is supported, does that mean that it will work with the network manager? 

There are many explanations in the forums about how to configure wifi for specific cards, however it does not help me understand how the different things are related and especially choosing a card for a person without technical skills. 

Francesco

---

### Post by rufius on 2007-04-24
> **frafu said:**
> Thanks for your reply.

However, how can I know whether a card is supported? 

I know about this page: 
[http://live.gnome.org/NetworkManagerHardware](http://live.gnome.org/NetworkManagerHardware)
Does this mean that if I get a card with one of those chipsets that also have wpa in their comments, it will be working also through updates without having to do anything? 
Should work out of box.

> 
There is also this page: 
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

If a card is supported, does that mean that it is directly supported by the kernel? 

Not necessarily. You may have to install a 3rd party driver but Ubuntu should do it automagically for you.

> 
When a card is supported, does that mean that it will also have wpa? 

Not necessarily, only cards made after WPA become a standard will support it. Though most days non-cheapo cards support it.

> 
When a card is supported, does that mean that it will work with the network manager? 

Assuming there is a driver that will support it then it should work with Network Manager.

> 
There are many explanations in the forums about how to configure wifi for specific cards, however it does not help me understand how the different things are related and especially choosing a card for a person without technical skills. 


WPA is separate from the card actually talking to the access point. WPA is a layer on top of that between the kernel and the driver (I think thats right). Anyway, if the card supports WPA, and if there's a driver for Linux, there should be support for WPA with that card. 

The only security that is built in to wireless cards and their drivers is WEP. WPA is a layer on top of that.

Regards,

rufius

---

