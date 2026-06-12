---
title: "Bluetooth GPS going down after a few minutes"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by ulrick on 2008-09-09
Hello guys,

I'm really puzzled by this problem, and i really do hope some of you will have a small idea for me.

I have a laptop with hardy, and 2 bluetooth GPS mouse (a recent gosget, and a sirf3 global sat).

I configure them using:

   modprobe hci_usb
   modprobe bluetooth
   modprobe l2cap
   modprobe rfcomm

   hciconfig hci0 up
   hcitool scan (to check my gps is detected)

   gedit /etc/bluetooth/rfcomm.conf (to verify i have the correct MAC)
 
   rfcomm bind rfcomm0 
   gpsd -n -N -D3 /dev/rfcomm0

It works like a charm, i see the gps info comming, i see my position in xgps and kismet ... but after a few minutes the GPS (same problem with both) are going down, on the gpsd debug i see ...

[INDENT]....
gpsd: transfer mask on GGA: 01
gpsd: transfer mask on GGA: 01
gpsd: transfer mask on GGA: 01
gpsd: transfer mask on GGA: 01
gpsd: transfer mask on GGA: 01
gpsd: transfer mask on GGA: 01
gpsd: GPS is offline (2.003033 sec since data)
gpsd: GPS is offline (1220946999.552793 sec since data)
gpsd: closing GPS=/dev/rfcomm0 (5)
[/INDENT]

And gpsd crash (freeze), no way to stop it, killall, kill -n 9 ... nothing works.
It's the latest version of gpsd.

I guess it has something to do with the "intelligent power saving mode" of the GPS but how can i solve this, is there a way ?

Thanks a lot in advance for your hints.

Ulrick

---

