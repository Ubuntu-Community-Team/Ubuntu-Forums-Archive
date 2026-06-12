---
title: "Wireless Netwrok Troubles"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by MikesGuitar on 2009-03-10
When I am at my girlfriends house for some reason I cannot connect to her wireless. The same was the case before I even had Ubuntu. I hit connect to the network, type in the password, but then it does not connect. Any other toruble shooting I can do?

---

### Post by stanz on 2009-03-10
Ya need to pass over some more information here.
What brand of wireless does your girlfriend have? What type of security is it using?

What are you using? Carry'ing your pc tower...or a laptop? Brand? Wireless card?

Things like that will help someone....help you!

---

### Post by jimi_hendrix on 2009-03-10
try the old school way...

```

#anything preceded by a # is a comment
iwconfig #find the interface you want...normally wlan0 for wifi...we will 
         #call this $interface for now
sudo ifconfig $interface up
sudo ifconfig $interface essid <your essid/ssid>
sudo dhcpcd $interface

```

post any errors

i am not a networkng pro but this always has worked for me

---

### Post by MikesGuitar on 2009-03-11
Hey sorry, I am using a inspiron 1420, and her wireless router is a Linksys something or other. I have heard that these routers are pretty unreliable. This prob has more to do with an issue with the router and Dell then anything with Ubuntu. Anyone experience simililar situation with similar technology

---

