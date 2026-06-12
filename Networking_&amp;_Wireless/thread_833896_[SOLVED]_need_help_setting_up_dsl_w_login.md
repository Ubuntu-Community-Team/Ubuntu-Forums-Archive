---
title: "[SOLVED] need help setting up dsl w/ login"
date: 2008-06-19
forum: Networking &amp; Wireless
---

### Post by 64dragon on 2008-06-19
i'm pretty new to linux and not sure how to set up my dsl that requires a login of username and password to get online. in windows i have a broadband pppoe icon in the network connections that resembles kppp in kubuntu and when i open the pppoe in XP i just need to have the username and password of the account, no phone # to dial. my computer is not directly connected to the modem, i'm connected to a router then the modem. i found the kppp program thats buried in kubuntu hardy and when i create a modem it is asking for a location, i dont know what to select from the drop down. and if i dont create a modem then i cant put in my username and password

---

### Post by SpaceTeddy on 2008-06-19
out of curiosity... why do you dial in with your computer when you have a router in between you and your modem ? shouldn't the router do the dialing and serve the internet connection to you via the normal network ?

besides that, try running 
> sudo pppoeconf
in a console and follow the instructions. That usually works for me (as i don't use graphical tools if i can help it)

hope it helps :)

---

### Post by 64dragon on 2008-06-19
i have no idea why i have to "dial in" for a while i didnt but now its the only way i can get on.

---

### Post by 64dragon on 2008-06-19
the sudo pppoeconf worked, thanks

---

