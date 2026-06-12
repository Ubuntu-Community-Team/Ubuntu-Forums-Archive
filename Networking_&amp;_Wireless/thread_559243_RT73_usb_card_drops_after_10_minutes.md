---
title: "RT73 usb card drops after 10 minutes"
date: 2007-09-24
forum: Networking &amp; Wireless
---

### Post by stringkarma on 2007-09-24
I have seen a few other people have this same issue but I haven't found a resolution that works for me.
I am using a usbkey sized wireless adapter on my notebook. I have a driver (rt73) that is module based (I hope I am saying this correctly I am young on linux, but no longer green). 

I can get the card up and running perfectly. It works for about 10 minutes and then disconnects. I can then use :

sudo ifconfig rausb0 down
sudo ifconfig rausb0 up

and then using a gui manager I reconnect to my router, giving me another 10 minutes.

I have a few suspicions.

1) the timing tells me that perhaps the card or the software are going into a powersave mode ( the card is in use continuously however).

2) I have to configure the connection in RutilT, as the Network Manager can't seem to get it right, however I can not get rid of it (because I need wired internet at work, and I can't seem to find out how.)

Any help you guys can give would be great. Thanks

---

