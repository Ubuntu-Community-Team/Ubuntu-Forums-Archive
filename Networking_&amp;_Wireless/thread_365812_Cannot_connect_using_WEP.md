---
title: "Cannot connect using WEP"
date: 2007-02-20
forum: Networking &amp; Wireless
---

### Post by matt80 on 2007-02-20
Hi,

I'm having problems when connecting to my router using my WG111v2 netgear adapter. The card is present when i do 'lsusb' and it can see the network when i type 'iwlist wlan0 scan'. It will even connect to the network, but only when I set my router to use no encryption. Obviously, I don't want to do this!

I have my router settings as follows:
Encryption: WEP 64-bit, Shared key
Key: C94F606A17 ( for example, ;) )

Any ideas why it might not be working?

p.s. is there a command to view your current IP address in the terminal?

---

### Post by corosus on 2007-02-20
the command to set your wep encryption is :
 "sudo iwconfig eth1 edssid your-essid key your-key"
But i have to say i use a key hex key 

ow and the commend to see your Ip adress is ifconfig

greetz

---

### Post by matt80 on 2007-02-20
Hi - aren't I also using a Hex key? If C94F606A17 is not a Hex key please tell me, as it is supposed to be!?

---

### Post by corosus on 2007-02-20
sorry for the confusion, 
I did not mean to imply that your key was not HEX, only that mine is.
**IF**you use an ascii key you have to prefix the kley with s: " ...... key s:password"

If i read your first post correctly your command would be "sudo wlan0 essid whatever-your-essid-is key C94F606A17"

followed of course by "sudo dhclient" to get an Ip assigned

---

### Post by matt80 on 2007-02-20
Thanks for the help - I have not tried that command so will try it when I get home later, but I have checked the contents of /etc/network/interfaces and the key is listed under wireless-key - isn't that command doing the same thing? Anyway, I will give it a go

---

