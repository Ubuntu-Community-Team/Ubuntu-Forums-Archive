---
title: "ONLY not able to browse internet"
date: 2008-10-03
forum: Networking &amp; Wireless
---

### Post by mohsin123 on 2008-10-03
I am part of a network and I am having a strange problem in getting my internet connection on Ubuntu.

Aparently, I can do folllowing all the time:

[LIST=1]
[*]I can ping any host
[*]I can do nslookup also
[*]I can use aptitude to install software
[*]I can use pidgin to do chat.
[/LIST]

What I cant do is that I cannot browse internet via my browser (FireFox). Initially I suspected it a proxy settings problem, but its not. My next doubt was about DNS, but its also not the case.
I am able to browse internet some of the times on my Ubuntu installation but I am unable to determine the conditions under which this occurs.

My configuration is as under:
3.2 GHz
1 GB RAM
1 Gigabit Broadcom Ethernet
Ubuntu Hardy.

And network settings are as under:
Static IP (given by me though DHCP also works fine)
DNS entries are set to OpenDNS servers.

I used wireshark to examine the situation and found that the TCP packets for all the HTTP requests have invalid checksums. Why is it so, I wonder. Can anyone guide me what the problem might be?

Best regards,
Mohsin

---

### Post by aurelieng on 2008-10-03
Did you try to change your MTU to something like 1492 or less ? 

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=5417956](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=5417956)

---

### Post by superprash2003 on 2008-10-03
Changing MTU values may help [http://prash-babu.blogspot.com/2008/06/how-to-change-mtu-values-in-linux.html](http://prash-babu.blogspot.com/2008/06/how-to-change-mtu-values-in-linux.html)

---

### Post by lukjad on 2008-10-03
Do you use a proxy?
If you do, go to Edit->Preferences->Advanced->Network and select Settings. Then choose Manual Proxy Settings and enter your Proxy Address and Port Number. Make sure to check "Use this proxy server for all protocols". That may do the trick. If not, try to muck around in there.

---

