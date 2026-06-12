---
title: "Networking: Static mode not working under hardy"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by GrumpyOldMan on 2008-05-17
Hello ubuntu world.

I used to have my computer set up in static IP mode as my kids' ubuntu laptops used to use my computer to store files and access printers etc..

I updated to hardy heron and this continued to work for a week or two, but suddenly my computer has ceased its ability to communicate on the network and internet in static mode. If I set it to roaming mode, everything is fine, with access to the internet and everything. However, the laptops then don't know where to find the printer and shared folders as the IP address keeps changing as it is allocated dynamically by the wireless router.

Has anyone any ideas?

Many thanks.

---

### Post by Bob Unitt on 2008-06-15
I've just installed Heron and have exactly the same problem - has anyone got any answers ?

---

### Post by lswb on 2008-06-15
Perhaps the easiest solution is to configure your router to always give the same ip address to your computer. Your computer will still use DHCP to ask the router for an address, so it can be left in roaming mode. 

Most routers these days are configured by pointing a web browser at their IP address. Often the default is 192.168.2.1 but it can be changed. If you don't have documention for your router you can probably find it on the web.

---

### Post by Xanatos Craven on 2008-06-15
> **lswb said:**
> Perhaps the easiest solution is to configure your router to always give the same ip address to your computer. Your computer will still use DHCP to ask the router for an address, so it can be left in roaming mode. 

Most routers these days are configured by pointing a web browser at their IP address. Often the default is 192.168.2.1 but it can be changed. If you don't have documention for your router you can probably find it on the web.
Not everybody has 'most routers'. I somehow used to before it died on us, but as I don't live on my own quite yet and my dad can't be arsed to do any research on anything he ever buys or ask me about it first, that situation's somewhat out of my control, and I'm stuck with my Linksys WRT54G. So, apparently the only way I could have set a static IP is on my computer... which isn't working.

---

### Post by geezerone on 2008-06-15
> **GrumpyOldMan said:**
> Hello ubuntu world.

I used to have my computer set up in static IP mode as my kids' ubuntu laptops used to use my computer to store files and access printers etc..

I updated to hardy heron and this continued to work for a week or two, but suddenly my computer has ceased its ability to communicate on the network and internet in static mode. If I set it to roaming mode, everything is fine, with access to the internet and everything. However, the laptops then don't know where to find the printer and shared folders as the IP address keeps changing as it is allocated dynamically by the wireless router..

Which router do you have as it is possible for some to associate a MAC address to an IP address and thus dynamically allocate your 'static' address ,if you like?

---

### Post by lswb on 2008-06-15
Xanatos, there are a lot worse routers to be stuck with. The WRT54G is one of the better consumer-grade routers as far as configurability is concerned. The OEM ip address for configuring this router is 192.168.2.1. IIRC, the OEM login is "admin" and the OEM password is also "admin" These all can be changed by the user. There is a reset button on the back that if pushed in for 30 seconds will reset all setting to the factory defaults, including the login and password; don't do this if you are not prepared, but it is likely that they have never been changed from the factory settings.

You can find all the documentation you need for the WRT54G on the web, including a .pdf copy of the user manual at [www.linksys.com](www.linksys.com). There were several revisions made to the firmware and hardware of this router over the years, you will need the version and model number to get the correct user manual for your specific router.

Actually, the older models are more desireable than the newer ones, as they had more memory installed and ran a linux-based software that could be customized or fully replaced to give the unit a lot more features than the stock firmware.

---

### Post by chili555 on 2008-06-15
Do you have a DHCP conflict? That is, has one of the kids machines has received 192.168.1.105 via DHCP from the router? If you then boot your machine which asks for a static address, 192.168.1.105, you won't connect.

Set up your router to give just 5 or 10 DHCP addresses and set your static at 192.168.1.115 or similar.

In my network, using a Linksys WRT54G, the DHCP server is set to give 10 addresses from x.100 to x.109. My several static machines are set from x.115 on up.

---

