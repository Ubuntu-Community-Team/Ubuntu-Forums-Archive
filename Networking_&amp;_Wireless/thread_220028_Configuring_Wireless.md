---
title: "Configuring Wireless?"
date: 2006-07-20
forum: Networking &amp; Wireless
---

### Post by Rudy507 on 2006-07-20
Hey guys,
I'm running a Dell Inspiron 2200 with Dapper. This laptop has an internal wireless card. I have no idea how to set it up and configure it. I know that if a linux driver isn't available, I will need to use ndiswrapper. 

Anyway, on a whim just for fun, I ran "iwconfig". Here are the results:
> 
lo        no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.



Does this mean that my wireless card is already working just fine on eth1? If so, all I have to do is follow the instructions here to configure it, correct? :[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking)

Thanks for any help,
David

---

### Post by wieman01 on 2006-07-21
Luckily Ubuntu has recognized & installed your wireless card (Broadcom) so there is no need to do anything else in terms of installing the hardware. You can proceed configuring your wireless network now.

I don't know the link you have included in your post but it looks a bit intimidating & complex. Figure out what kind of network (wireless) setup you have/need and then simply search for appropriate posts/howtos in the forum. If you are only using DHCP with or without WEP, the setup is super-easy. 

You'll find more in this forum. But if you don't let us know here.

---

