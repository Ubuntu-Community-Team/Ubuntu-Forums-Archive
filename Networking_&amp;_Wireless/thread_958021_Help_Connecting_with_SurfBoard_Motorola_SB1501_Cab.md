---
title: "Help Connecting with SurfBoard Motorola SB1501 Cable Modem"
date: 2008-10-24
forum: Networking &amp; Wireless
---

### Post by cjmabry25 on 2008-10-24
Hi all. First I just wanna say this is the best forum I have ever visited for help and support. Thanks guys. :KS

Anyways,I just switched over to Charter cable from Frontiernet DSL, and I'm having trouble getting my computer networking working. First of all, the ethernet cable coming directly from the SurfBoard Motorola SB1501 modem is going directly into my computer. When I click the toolbar, a drop-down box appears with the choices "Wired Network", "Connect to 802.1X Protected Wired Network" and "Manual Configuration...". When I select "Wired Network," it acts as if it is connecting and then shows an icon of two computers, but I cannot access the internet. When I select "Connect to 802.1X Protected Wired Network", it asks me for a bunch of options, like Name, Password, Identity, and stuff like that. I'm not sure where I could get this info or if it is even needed, but I am lost on what to do...

With DSL I just plugged the ethernet cable directly into my PC, and I was on the internet, but for some reason Cable isn't working :(. Could it be that the modem's not compatible with Linux?

I'm a noob when it comes to Linux, so if you have any commands I could run in the terminal or trouble-shooting tips I'd be glad to hear them. Thanks :)

---

### Post by cariboo on 2008-10-25
It sounds like yu are using Intrepid RC left click on the network icon and select Connection Information, it should show you information like the network card driver. It should look like the attached screen shoot with out the ip addresses.

If there is a driver listed, in a terminal type:

```
sudo dhclient eth0
```

This should initiate a network connection.

Jim

---

### Post by cjmabry25 on 2008-10-25
> **cariboo907 said:**
> It sounds like yu are using Intrepid RC left click on the network icon and select Connection Information, it should show you information like the network card driver. It should look like the attached screen shoot with out the ip addresses.

If there is a driver listed, in a terminal type:

```
sudo dhclient eth0
```

This should initiate a network connection.

Jim

Thanks :) I found that answer while waiting for a reply, and it worked!

Thanks so much!

---

### Post by Malswon on 2012-08-09
> **cariboo907 said:**
> It sounds like yu are using Intrepid RC left click on the network icon and select Connection Information, it should show you information like the network card driver. It should look like the attached screen shoot with out the ip addresses.

If there is a driver listed, in a terminal type:

```
sudo dhclient eth0
```This should initiate a network connection.

Jim

DAMN that was easy!! lol you should receive an ubuntu nobel peace prize, because I was ready to get very unpeaceful.

nice.

---

### Post by wildmanne39 on 2012-08-09
Old thread closed.

---

