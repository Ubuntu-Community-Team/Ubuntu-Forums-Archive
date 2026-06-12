---
title: "Chatting AT commands with modem when connected?"
date: 2014-12-04
forum: Networking &amp; Wireless
---

### Post by xWEkxhW on 2014-12-04
Hi Folks,

I'm using a 3G/4G USB modem (it's a Huawei E3276). It works really nice, I'm using wvdial to connect and initiate pppd. The problem I have is once the device is connected I am unable to chat AT commands with the modem any more. I'd like to be able to chat with it and issue AT+CSQ commands to assess signal RSSI while connected. It should be possible somehow because the Windows application does it while the device is connected.

The modem has 3 devices - /dev/ttyUSB0 (used by wvdial) and also there is: /dev/ttyUSB1 and /dev/ttyUSB2
I've tried opening a minicom session with /dev/ttyUSB1 and /dev/ttyUSB2 but they are non-responsive while the modem is connected.

Is there a way to chat with the modem over ppp? Does anyone know how to do this. I'm struggling to find any info!

Any help would be greatly appreciated!

Thanks

---

### Post by carlwsnyder on 2014-12-04
I am confused.  You can't communicate with _any_ modem once you have connected to the on-line service.  You must take the modem off-line to send AT commands, if I recall correctly.

---

