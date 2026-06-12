---
title: "Want to use  TangoGPS"
date: 2010-07-07
forum: New to Ubuntu
---

### Post by Sandy.1 on 2010-07-07
So far I have used a USB Bluetooth to connect with my RoyalTek RBT3000 GPS. The BlueTooth New Device applet is reporting Set Up Completed and | Have ticked the box for  GeoLocation services.

Now it appears I have to address gpsd !!!!
[http://gpsd.berlios.de/bt.html](http://gpsd.berlios.de/bt.html) takes me to an article that I shall attempt to follow


1 I have installed Bluez, I think,

2 and 3  

[LIST=1]
[*]Install bluetooth for your device with the "rfcomm" module to allow for serial port emulation.
[*]Next, load the modules: 
	# modprobe hci_xxx (xxx depend on your type of device)
	# modprobe bluez
	# modprobe l2cap
	# modprobe rfcomm
[/LIST]
Now on these last two instructions I need help, please

Sandy

---

### Post by Sandy.1 on 2010-07-08
Can someone please explain how I carry out the operations listed above or at least advise me where I can find instructions

Sandy

---

### Post by mn_voyageur on 2010-09-11
Did you ever get your GPS to work?

MarkN

---

