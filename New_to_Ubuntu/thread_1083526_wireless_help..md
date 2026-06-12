---
title: "wireless help."
date: 2009-03-01
forum: New to Ubuntu
---

### Post by ja660k on 2009-03-01
Hi, 
i patched my windoze driver using ndiswrapper months ago. It work's well sometimes.

im not sure what the problem is, but recently (a few weeks ago) half the time i connect via wireless. it goes through the motions and that little radar thing shows it connected but when i right click-> connection info 

it gives 0.0.0.0 as all my addresses ip, subnet, everything.

i use WPA password
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

im wondering if i should change to madwifi? 
i dont know how to use it... 

what should i do?

---

### Post by diablo75 on 2009-03-01
You should check to make sure your network settings (System>Administration>Networking.... I think, and then in the Wireless tab) shows that you are using DHCP and not static IP addressing.

Something else you might try is opening ndiswrapper up and uninstalling the driver you put in to get your wireless adapter to work, and then reinstall it.  I'd recommend using drivers that were intended for Windows 2000 if you can find them on the manufacturers website.

---

### Post by binbash on 2009-03-01
I wrote 2 methods to get it working, please read and comment or write here etc if it works for you or not. :

[http://www.ubuntu-inside.me/2009/02/how-to-get-your-atheros-ar242x-working_25.html](http://www.ubuntu-inside.me/2009/02/how-to-get-your-atheros-ar242x-working_25.html)
[http://www.ubuntu-inside.me/2009/02/how-to-get-your-atheros-ar242x-working_27.html](http://www.ubuntu-inside.me/2009/02/how-to-get-your-atheros-ar242x-working_27.html)

---

