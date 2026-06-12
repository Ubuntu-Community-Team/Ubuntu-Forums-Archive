---
title: "connecting to open public wireless"
date: 2007-01-24
forum: Networking &amp; Wireless
---

### Post by pliumbum on 2007-01-24
in windows, i can automatically connect to the wireless network that is in range. i knew that the same in ubuntu is network manager. i tried to install it, i was told that it doesnt support i386 system. i then downloaded the i386 version from dapper drake, but when installing it with package installer i get an error message "dependency is not satisfiable: libdbus-1-2".
I just want to connect to the wireless internet, which is free and open connection. I dont think i have any cards, nor do i know the configuration of my network adapter. in windows it used to work automatically.. maybe i should try something else? i cant even see the wireless connection indicator blinking, which meant that it is turned on. maybe ubuntu doesnt support? can i connect to the open wireless net without any network managers, just with what i got on ubuntu? i dont need any passwords.

---

### Post by rmartz on 2007-01-24
I am by far, no expert, but will give you a quick reply. A Network manager kind of manages the network. Without one, wifi's don't just work. There are protocols and stuff that needs to be negotiated even in an "open" or password free network. 

Not all wifi adapters set up automatically in Ubuntu. Some do, and some are real pains. Some of this will be worked out in later versions (many of us hope). One has to remember that those who are working on this and other issues in Ubuntu are doing so unpaid and in their free time, so sometimes these things are a little slower. 

With that said, you will have to find out what network adapter you have then post this info here and some will help point you in the right direction. 

Hope that helps a little.

Peace.

---

### Post by pliumbum on 2007-01-25
everything is almost fine now.. i configured all by myself, after much much pain.. but i have one more problem, which i will post in another thread..

---

### Post by nike984 on 2007-01-25
I'm not sure wheter this will be the right answer, but this is how I did it.
I've installed ["Wifi-radar" package]("http://packages.ubuntu.com/edgy/net/wifi-radar") using synaptics. 
Then, whenever I'm able to use the public AP, open the Wifi Radar, 
(application=>internet=>Wifi-Radar), choose the AP that is on the list, press "connect".
Then your all set. :D

---

