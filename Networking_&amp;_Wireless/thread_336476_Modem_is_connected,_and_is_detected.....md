---
title: "Modem is connected, and is detected...."
date: 2007-01-11
forum: Networking &amp; Wireless
---

### Post by Jekento on 2007-01-11
I have a Qwest Actiontec DSL modem. It is connected via Ethernet cable to my computer, the DSL, Internet, Ethernet, and Wireless lights are all solid as they should be. 
     
The modem is on eth0, it is configured and active. It is sending and receiving, no reception or transmission errors at all. 
i clicked on firefox and typed in my modems IP, it brought me to the modem;s control panel and everything looked fine so i tried surfing the internet a little and it just loaded and loaded, eventualy coming to an unable to connect page. 
     
So i went to system>administration>networking. the modem is still configured, sending and receiving. so i went into fire fox edit>prefrences>connection settings. it is set to direct connection to the internet as its should be with my dsl. but that wasnt working so i changed it to Auto-detect proxy settings fort this network and clicked ok. 
     
At first it came up with an unable to connect so i tried [www.google.com](www.google.com) as it is a very simple page, it took a while to load but it did. 
     
Now it is random sometimes i can surf the internet but it is always very very slow or it comes up with an unable to connect. 
Although it barely works, ubuntu asked if i wanted to update and ofcourse i did, and it updated just fine. 
We have other computers running off of this modem (windows XP) and the internet works flawlessly and fast. 

I am re-trying linux because i think it is awesome, but i got too frusturated with just trying to get connected to the internet. Also, i did search for similar problems and looked at the faqs so dont yell at me like all the other forums, please. If you know of a post that will fix my problem you can just link the post if it is that big of a deal. but i would highly appretiate a conversation with you all, i learn best person to person. thank you all. =D

-Jek

---

### Post by Jekento on 2007-01-11
It was working for the longest time probably four hours, i was using GAIM and Firefox (which was terribly slow still). But once again, it just stopped. Everything is still the same, receving, sending, modem lights, everything. Anyone? please.

---

### Post by Floppyjoe on 2007-01-11
I don't have a solution but am curious? Is your modem a combination modem and wireless access point?

---

### Post by Jekento on 2007-01-12
yes it is, it has a built in wi-fi router. but it is broadcasting it just fine to other computers.

---

### Post by Floppyjoe on 2007-01-12
That's interesting. I've not ever seen something like that myself. The combo I mean.
How many wired ethernet ports does it have? Could there be a problem with the port or the network cable?

---

### Post by Jekento on 2007-01-12
It only has one ethernet and one usb. the cable and port is fine. i just took it off of the family computer. i had the same problem when i tried ubuntu before. is there a setting somewhere like in firefox that isnt utalizing the speed? or connection? i dunno, but i want this to work i dont want to go back to windows [-(

---

### Post by Floppyjoe on 2007-01-12
I wish I could help but this has not happened to me before so i don't know what the problem is. I did have one computer that had some microsoft proprietary hardware for the ethernet card and this card was not supported in previous versions of Ubuntu. Now it does work and i was able to install updates and drivers for a wireless usb adapter.

---

### Post by Jekento on 2007-01-12
well i tried the USB from my modem to the computer instead of Ethernet cable, still the same problem. c'mon you guys are geniuses i know you can figure it...please *tear*

---

### Post by Floppyjoe on 2007-01-12
What does your DNS settings show? Go to System/Administration/Networking and then click the DNS tab.

---

### Post by Jekento on 2007-01-13
it has 2 IP adresses, a 192.*** and a 205.***

---

