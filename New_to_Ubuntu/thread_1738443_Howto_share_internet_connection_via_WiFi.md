---
title: "Howto share internet connection via WiFi"
date: 2011-04-24
forum: New to Ubuntu
---

### Post by uppersnatch on 2011-04-24
Hey, I'm new to ubuntu. I have established an internet connection through Modem, with a cable. Now, I need to share the internet over wifi, so that my friend can also use the internet in his laptop. He uses windows 7 (if it's necessary). Please, give me a suggestion how to do it. I would be grateful for any kind of help.
Regards

---

### Post by 3rdalbum on 2011-04-24
If your computer doesn't already have one, plug in a wifi adapter that works with Ubuntu.

Go to the Network Manager applet on the computer that will be sharing, and go to "Create Wireless Network". Set a network name (SSID), WPA2 security, and a password. That's it, pretty easy! You can connect on Windows 7 in its usual way.

If this is going to be a permanent arrangement, it might be better to buy a modem that already has wifi capability, so it creates the wireless network rather than your client computer.

---

### Post by cjazz on 2011-04-24
Well, that's all true assuming there's a means of broadcasting a wireless signal. Probably the most common way is through a wireless-enabled router or if the cable modem itself has wireless capability. I mention this since the original post did not mention a router or any other wireless broadcasting equipment -- only a modem and a cable.

---

### Post by uppersnatch on 2011-04-28
Thanks for helping. Sorry for late answer. As I said I'm new to Ubuntu,  so it took a bit longer time to figure out things. The Modem is Alice  Wlan 1121. It has its own wifi too. I just understood it. My friend has  tried to connect to it by typing in the security key, in a usual way.  The connection was established but the Internet didn't appear. I have  tried the next possibility that you have here suggested (to create a new  wifi). Didn't work. It seems to me that the problem is not with ubuntu  settings, but with the windows settings. I have to search for the  reasons through the net. If you have any suggestions for windows 7  wireless connection settings, so please write it to me, otherwise no  problem I will search the net for it. Anyways, I will let you know the results. Thanks to you both again.

---

### Post by stevenwscott on 2011-05-02
You will not find what you seek. The problem is multi-fold, the biggest issue being that Ubuntu isn't starting DHCPD against the wireless nic so it's not assigning IP addresses when others connect. Beyond that it's not applying correct routing and forwarding. 

I have it working but it's not pretty. 
I posted my notes here --> [http://ubuntuforums.org/showpost.php?p=10757443&postcount=19](http://ubuntuforums.org/showpost.php?p=10757443&postcount=19)

Hope it helps!

---

### Post by uppersnatch on 2011-05-02
Thanks stevenwscott for your notes on that issue. I am not good at ubuntu functions, so I decided to solve problem in windows 7. And it worked finally. In order to connect to wireless I should have used CD of Modem. That was the thing that I didn't expect. So, for normal cable connection, there was no need for CD, but for wireless the CD should be used.-)

---

