---
title: "O2 Broadband"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by thechillum on 2008-05-08
Hello.

I got connected up to O2 broadband today coming from Tesco Broadband.

I now have a wireless router/modem that I now use to connect to the internet. Previously I had a USB Modem (Speedtouch 330).

Currently I have a direct connection between it and my PC via ethernet cable.

Essentially all I did was connect up the ethernet cable from my router/modem to my PC, use the Network Manager icon on the top panel to enable networking and it worked.

I have a couple of questions / concerns.

- Is it really properly connected? I connected to the internet via a USB modem from my previous provider and that took a little while to resolve. This in comparison was easy. Now i'm starting to think if it might have been a little too easy.

- As I am using a wireless router/modem, should I be taking any particular precautions in securing it to prevent unauthorised individuals from connecting? If yes, how? I tried going through the thread on wireless security ([http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)) but typing in "iwconfig" tells me I have no wireless extensions.

I'm still pretty new to Ubuntu and would appreciate any guidance provided.

Thanks.

---

### Post by superprash2003 on 2008-05-08
iwconfig output says that either you dont have a wifi LAN card in that machine or the drivers havent been installed..Since you got everything working.. i guess its connected alright.. to secure your network.. you need to login to your router's settings and look for a wireless tab and ensure that you have WPA enabled and insert a security key for it

---

### Post by TryMe on 2008-05-08
Your fine as long as you have a router that gives you a LAN address. something like 192.168.x.x or 10.x.x.x. If it gives you a WAN address that means you are directly connected to the internet. Not such a good idea if you don't have a need to do it.

The USB connection on most isp modems is a wast. It's a throw back from when most PCs didn't have a ethernet port from the factory and ethernet cards where expensive. This is not the case today and USB is a much slower way to connect to the internet.

oh, and to configure your router just put your gateway address into firefox. Something like 192.168.1.254

---

### Post by thechillum on 2008-05-09
Yes.

I do appear to have a lan IP address starting 192.

I believe it already has some security enabled though I wish I were able to check via the configuration web page. That page holds a distinct lack of information and options.

The router/modem appears to be a Thomson TG585v7.

How would I be able to tell if someone were to connect via WiFi to my broadband? Would it be indicated anywhere in particular?

---

### Post by superprash2003 on 2008-05-09
its normally mentioned in your router's configuration page.. typically under connected devices or something like it..it would normally mention the ip address of the machine connected and sometimes also the machine name

---

### Post by TryMe on 2008-05-09
> **thechillum said:**
> Yes.

I do appear to have a lan IP address starting 192.

I believe it already has some security enabled though I wish I were able to check via the configuration web page. That page holds a distinct lack of information and options.

If you have wpa enabled with a good password it's not very likely anyone would spend the time cracking in. So don't worry too much.

> **thechillum said:**
> 
How would I be able to tell if someone were to connect via WiFi to my broadband? Would it be indicated anywhere in particular?

look for something like : dhcp client list. 

> **thechillum said:**
> 
The router/modem appears to be a Thomson TG585v7.


There is a firmware update that may give you new options or turn your router into a paperweight. :)
[http://www.thomson-broadband.co.uk/codepages/content3.asp?c=7&ProductID=544]("http://www.thomson-broadband.co.uk/codepages/content3.asp?c=7&ProductID=544")

---

