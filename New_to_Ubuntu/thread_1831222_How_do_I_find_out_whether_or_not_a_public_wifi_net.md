---
title: "How do I find out whether or not a public wifi network uses VPN?"
date: 2011-08-23
forum: New to Ubuntu
---

### Post by brawnypandora0 on 2011-08-23
Does VPN always mean that the network is encrypted or can it be unencrypted? 

So does it mean that it's only safe to access personal accounts over public wifi if it has VPN AND encryption?

---

### Post by androssofer on 2011-08-23
> **brawnypandora0 said:**
> Does VPN always mean that the network is encrypted or can it be unencrypted? 

So does it mean that it's only safe to access personal accounts over public wifi if it has VPN AND encryption?

not quite sure wot ya mean...?

VPN is encrypted yes.. and when you connect to a VPN its called a secure tunnel... 

i like to think of it as wrapping ur connection in diamond or sumthing as it goes accross the internet, then wen it reaches ur network it can run free knowing its safe!

but wireless doesnt use VPN. a VPN is a "virtual private network". so you would hav set up a VPN on ur home network, or your work could have 1. then u would connect to a public network, then connect to the VPN using a secure tunnel. so anything u access online, will go through this tunnel into the home or work network, then out onto the interwebz. so no1 on the public network cud c it... but if the public network doesnt use "WPA(AES or TKIP)" then its an unencrypted network.

but stuff like gmail/hotmail/facebook etc, use SSL, which encrypts your stuff until it gets to the gmail/hotmail/facebook servers, so its secure start to finish. so if ur accessing them u dnt really need to worry.

---

### Post by sanderj on 2011-08-23
> **brawnypandora0 said:**
> Does VPN always mean that the network is encrypted or can it be unencrypted? 

So does it mean that it's only safe to access personal accounts over public wifi if it has VPN AND encryption?

You can not trust a public wifi network. Solution: for personal info / logins, only use HTTPS or your own VPN.

---

### Post by brawnypandora0 on 2011-08-23
> **sanderj said:**
> You can not trust a public wifi network. Solution: for personal info / logins, only use HTTPS or your own VPN.

Why can't I trust public wifis?

How do I create my own VPN?

---

### Post by mcduck on 2011-08-23
> **brawnypandora0 said:**
> Does VPN always mean that the network is encrypted or can it be unencrypted? 

So does it mean that it's only safe to access personal accounts over public wifi if it has VPN AND encryption?

VPN is not something a network access point uses, it's something *you* can use to create a secure connection between computers through the Internet.
Why can't you trust a public wifi? Because it's a radio broadcast, the messages are not sent between the access point and a particular computer, but instead are broadcasted to the air, where anybody else with access to the same network will be able to listen to them. So unless there's some additional encryption used, all the information that is sent through the network is available to anybody on that network.

---

### Post by sanderj on 2011-08-23
> **brawnypandora0 said:**
> Why can't I trust public wifis?



Well, that's point of your own question, isn't it?

Because anybody can setup a Wifi access point, and then eavesdrop on your connection.
And even that's not needed; even someone else on the Wifi can use wireshark to listen to your traffic. And driftnet is a fun tool to see the pics others on the open Wifi network are viewing.

> **brawnypandora0 said:**
> 

How do I create my own VPN?

You need a VPN server. With a corporate laptop, you employer will provide that. If not, you can find a VPN server yourself.
However, using HTTPS in all personal traffic is much easier. The firefox plugin HTTPS-Everywhere is helpful. See [https://www.eff.org/https-everywhere](https://www.eff.org/https-everywhere)

---

