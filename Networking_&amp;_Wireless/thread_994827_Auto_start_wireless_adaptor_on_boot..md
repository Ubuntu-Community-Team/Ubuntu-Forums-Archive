---
title: "Auto start wireless adaptor on boot."
date: 2008-11-27
forum: Networking &amp; Wireless
---

### Post by john.james127 on 2008-11-27
Following these two post I managed to get my D-Link DWA-140 working with Xubuntu. 

[http://ubuntuforums.org/showthread.php?t=578744&highlight=dwa+140]("http://ubuntuforums.org/showthread.php?t=578744&highlight=dwa+14")

[http://ubuntuforums.org/showthread.php?t=766850&page=1]("http://ubuntuforums.org/showthread.php?t=766850&page=1")

Everything works even my WPA2 my problem is that when I restart my system the wireless network adaptor won't start automatically.

I have to renter these 2 lines of code in Terminal

$/sbin/insmod rt2870sta.ko
$/sbin/ifconfig ra0 inet 192.168.0.1 up

then go in to the wireless Network section and change the set up from WEP to the correct WPA2 setting, the wireless name is correct its the encryption type thats wrong.

Is the any way to auto start the adaptor and have the correct encryption type and password?

I added the below line to /etc/rc.local file the light on the adaptor lights up but no connection or Wireless Network Section available

sudo ifconfig ra0 up
sudo sbin/insmod rt2870sta.ko

Thanks

---

