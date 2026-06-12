---
title: "No WPA-option?"
date: 2006-09-06
forum: Networking &amp; Wireless
---

### Post by john deere on 2006-09-06
[My old thread]("http://www.ubuntuforums.org/showthread.php?t=242922") about this didn't get any replies so instead of bumping it a second time, I'll just write another post. Hopefully I can explain the problem a little better too. (If this should go under the newbie section, feel free to move the thread) 

I have a Gigabyte wireless network card in my Thinkpad A31. It's a PC-card and the model name is GN-WMKG. The network I'm trying to connect to is my wireless home network. It's just a Netgear Wireless router and my main computer.

I double boot XP and Dapper Drake and the card works just fine with the former OS, but it just won't work on Ubuntu. The card is detected (looking in device manager), but no matter how I change the network settings, I just can get it running. I've tried both DHCP and fixed IP.

One thing I noticed is that there is no option for WPA-keys in Ubuntu's network settings, only WEP. In my router settings I have ticked WPA and set a password, because I've been told WPA is a whole lot better than WPA. Is this the problem and if so, how do I get solve it?

Any suggestions would be dearly appreciated.    

Thanks.

---

### Post by wieman01 on 2006-09-06
Perhaps this thread helps. You'll have to configure your network settings manually if you are using Static IPs. NetworkManager is of no help as it only supports DHCP.

[http://www.ubuntuforums.org/showthread.php?t=225290]("http://www.ubuntuforums.org/showthread.php?t=225290")

The last page posts the solution.

---

### Post by wieman01 on 2006-09-06
This thread may be useful as well:

[http://www.ubuntuforums.org/showthread.php?t=202834&highlight=wpa2+rsn]("http://www.ubuntuforums.org/showthread.php?t=202834&highlight=wpa2+rsn")

---

### Post by john deere on 2006-09-06
wieman,

huge thanks for the links. Lots of useful info in there, I'll look into it as soon as get some free time.

Thanks.

---

### Post by PacketPaul on 2006-09-06
Try this:

[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=1468922](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=1468922)

Paul

---

