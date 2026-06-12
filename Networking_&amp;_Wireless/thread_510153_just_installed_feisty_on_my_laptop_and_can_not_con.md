---
title: "just installed feisty on my laptop and can not connect to my linksys"
date: 2007-07-26
forum: Networking &amp; Wireless
---

### Post by musicphotog on 2007-07-26
i have an (older) linksys wireless router with an (older) wireless pc card in my laptop. i just installed feisty and everything looked ok. it sees the wireless card and through it i am able to see a list of available wireless networks. when i try to connect to my router (and enter the security information), it will not connect and sometimes freezes the computer. i am able to connect through the hard wire. 

could it be a driver issue even though feisty sees my card and i can see a list of networks? or is it a wireless config issue? i'm not real sure where to go with this and after searching the forum i am just more confused. 

thanks in advance :)

---

### Post by jspangler on 2007-07-26
I had similar problems. The available wireless driver seemed to install and I could see the networks, but I couldn't connect when a WEP key was required. Ndiswrapper fixed the problem for me. You should give it a try.

---

### Post by musicphotog on 2007-07-27
ok, i had a little while to play around with it last night and tried to install Ndiswrapper. i coudln't really figure that out. so i checked automatix and installed it through there...........problem is that i thought i had to install a windows driver with it. so i checked for the driver and ended up finding [a linux driver for this card]("http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859958334&packedargs=sku%3D1115416828350&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=5833428350B03&displaypage=download#versiondetail"). But i still have no idea what to do with it (please see sig). i think i need a linux for dummies or something. can anyone point me in the right direction on how to get this done?

---

### Post by adza on 2007-07-27
hi music... know how you feel, we are all n00bs :) you have probably already been here...[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29")
this guide has saved me many times!

---

### Post by kevdog on 2007-07-27
Before going and trying to install various drivers, can you please post some information about your wireless card so that we can have some specific information to better help you.  Please type at command line and provide the following output (you can cut and paste) -- make sure wireless card is plugged in:


```
lspci -nn
lshw -C network
```

---

