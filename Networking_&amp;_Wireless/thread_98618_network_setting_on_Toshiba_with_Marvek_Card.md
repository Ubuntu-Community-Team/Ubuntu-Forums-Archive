---
title: "network setting on Toshiba with Marvek Card"
date: 2005-12-03
forum: Networking &amp; Wireless
---

### Post by huxxam on 2005-12-03
Hello folk 

Fisrt at would like to say thnk you for the ppl behind this forum in general. 

And now to my issue 

I installed Ubuntu on my laptop (toshiba) but couldnt get online. dont know why? 

Under the installation the guid asked me if i will set my network bla bla i said yes, but the settings couldnt be configured. i tried by choosing the DHCP but once again no succes. So a choosed to do it latter after the installation. 

after the installation i tried to make the device aktiv and it was ok and easy, but no connecting to the net, and i stil dont know why!!

I have a static Ip and therefor im using a router to use both my computers on then net. 
I tried to configure this issue by testing the device in Windows and it was so wasy and there were no problems. but with Ubuntu / kubuntu i do have this probem. 

As I said the devices(Marvel and a wirlesse) are there and I can see them when i need to activate them but I dont know why it wouldnt work.

I was using fedora in my last laptop but changed to Ubuntu / kubuntu in my new laptop when somebody adviced me to use Ubuntu cause it does support Marvel devices. 

so If any body can help me in this issue i will be glad, cause i dont want to go back to windows
Thank You all 

Hussam

---

### Post by huxxam on 2005-12-03
forgot to say that when im pinging my route i got nothing

---

### Post by Lambert on 2005-12-03
Please post output of these commands

iwconfig
ifconfig
iwlist <wlan0> scan

where <wlan0> =your devices logical name with out the <>

Are you using wep or wpa encryption?

---

