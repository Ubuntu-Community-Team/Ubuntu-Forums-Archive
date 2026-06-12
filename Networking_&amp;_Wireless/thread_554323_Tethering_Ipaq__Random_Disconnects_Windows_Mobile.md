---
title: "Tethering Ipaq / Random Disconnects Windows Mobile"
date: 2007-09-18
forum: Networking &amp; Wireless
---

### Post by DarkGreen16 on 2007-09-18
I am currently trying to tether my ipaq 6925 through a USB cable, I have followed various guides on the internet for wvdial and pppd and have not had much success. Every time i initiate the dialer I can see the phone is communicating because i will see "Connecting to Host" on my phones screen and then just 2 seconds later i will get "Modem not Responding" in terminal.


       I also noticed that the phone seems to randomly connect and disconnect to the laptop. For example, the charging is normally indicated by a solid orange light at the top - this light will remain lit for about 8 seconds and then go out for about 3 seconds and then come back on for 8 (repeat forever) I believe this is why i am unable to get a connection. Any ideas on why the phone would be connecting/disconnecting so often? 

Thanks in advance

---

### Post by DarkGreen16 on 2007-09-18
This is what dmesg shows if that helps any - the usb address will keep increasing by 1 


usb 1-1: USB disconnect, address 5
 ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
ipaq 1-1:1.0: device disconnected
usb 1-1: new full speed USB device using ohci_hcd and address 6
ipaq 1-1:1.0: PocketPC PDA converter detected
usb 1-1: PocketPC PDA converter now attached to ttyUSB0

---

