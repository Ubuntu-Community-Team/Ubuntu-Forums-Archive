---
title: "Realtek 8139 Adapter Installation"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by drohit61087 on 2010-01-12
Hi,

I am newbie to Linux, Ubuntu.
I have Ubuntu 8.04 on my computer. internet is working fine on it through my onboard ethernet adapter. I am also willing to share this connection with my laptop through another ethernet adapter on PCI slot. This adapter is something named " Realtek 8139 ".

So, my problem is :
1) How do i install drivers for this adapter ?
2) How to configure this adapter ?
3) How do i setup lan to share internet connection with my laptop(having Windows XP) ?

Please Help and I want simple steps as i dont know enything about Linux!!!!
I hope these are simple problems for intelligent people over here....

Thanks a lot in advance

---

### Post by Gone fishing on 2010-01-12
I think this is probably easy (famous last words) being a realtek it will probably just work so right click on the networking icon on the top panel and edit the connection give it a fixed IP something like 192.168.2.1 then

following this guide 

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

> You will need either two Ethernet ports, one for the incoming internet and 1 for the connection to the other computer, or a Wireless card for the incoming internet and an Ethernet port for the connection to the other computer. When logged into your computer right click on the network indicator in the top right hand corner, click on "Edit Connections..." select "Auto Eth0" and click "Edit..." then go to the "IPv4 Settings" tab and next to "Method:" select the drop down box and select the option that says "Shared to other computers". Restart your computer and then you will be able to just plug-in any computer to your Ethernet port to share the connection.

Give the client PC an IP address such as 192.168.2.2 and it should work. Personally I don't use IP forwarding but squid proxy but that is for lots of client PCs.

---

