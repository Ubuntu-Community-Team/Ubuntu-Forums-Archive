---
title: "rausb0 receiving non-existing pkts all day long"
date: 2006-11-26
forum: Networking &amp; Wireless
---

### Post by Andrea_44 on 2006-11-26
I have just installed a usb wireless adapter(G122 VerC1) and able to have Internet connection. 

However, double click on the Network Connection icon (top right hand corner of the desktop), the Status of the rausb0 interface has been "Receiving" packets since the first second rausb0 is up, while wireshark (ethereal) has not captured a packet on the rausb0 interface. 

In another word, the Network Connection applet is detecting some imaginary packets being received on the interface.

Within 5 hours the applet indicated the interface has received 23 Mb, while  nothing significant is being captured. At the time of writing this, more packets are being "received" every seconds.

```

Network Connection: rausb0

Connection 
Name: rausb0
Status: Receving

Activity 
Received: 200496 packets (23.0 Mb)
Sent: 12414 packets (1.2 Mb)
```

Not sure if there is something wrong with the driver or the Network connection applet.

The rt73 driver is being installed following these instruction:
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29)

Thanks,
Andrea

---

