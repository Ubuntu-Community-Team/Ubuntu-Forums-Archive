---
title: "Internet won't connect"
date: 2007-01-30
forum: Networking &amp; Wireless
---

### Post by neufelni on 2007-01-30
I am having trouble setting up a DSL internet connection with Ubuntu. I tried setting it up from Network Settings at System > Administration > Network Settings. When I go there, the two things there are Ethernet Connection and Modem Connection. I've tried going to properties of both of them, and entered all the right info, and it appears to setup correctly. But when I open up Firefox, a window pops up saying [www.google.ca](www.google.ca) not found, Re-enter and try again. Also in the modem connection properties, when i try to auto detect the modem, it says it can't detect it, it might be busy or not connected to the computer.

I'm not sure why it's not working, it works fine when I use Mandriva. To set it up with Mandriva I went to Set-up a new network interface in the Control Center. I then choose DSL for the connection I want to configure > 3Com Corp for the network interface I want to configure > Unlisted for provider > PPP over Ethernet (PPPoE) for connection protocol > and then I enter the account username and password, and everything works fine.

Any help is greatly appreciated.

---

### Post by Stemp on 2007-01-30
Open a terminal and try : 

```
sudo ppoeconf
```

---

### Post by neufelni on 2007-01-30
I tried that, it still does the same thing.

---

### Post by the.phantom on 2007-01-30
i am a light weight but
1. did you disable the modem
and enable the network?

i just changed from dialup to dsl and 
what do you show in 
firefox/preferences/advanced/network


and i think the post above me wants you to copy and paste what ppoeconfig shows ;-)
or your settings
and did U find your network card?

i'm on dynamic dsl and didn't need a password

---

