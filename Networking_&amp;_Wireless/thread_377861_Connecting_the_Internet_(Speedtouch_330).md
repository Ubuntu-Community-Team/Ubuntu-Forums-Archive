---
title: "Connecting the Internet (Speedtouch 330)"
date: 2007-03-06
forum: Networking &amp; Wireless
---

### Post by simonpearson on 2007-03-06
Hi there,

I've recently reinstalled Dapper Drake, and the first task I am trying to perform is to connect to the internet (I have done this successfully before), however, I do not seem to be able to connect.

I am following the instructions from: [http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html)

So far I have: 

 - Installed the Firmware
 - Created Chap/Pap files (and DOUBLE checked the username / password for errors)
 - Created and installed the PPPOATM script
 - Created and installed the boot script.

By all accounts in the instructions I should be able to reboot and be online, but I'm not.  Heres the output from my syslog:

```
Mar  6 17:45:27 HOMEPC kernel: [4295006.471000] usb 1-1: USB disconnect, address 2
Mar  6 17:45:28 HOMEPC kernel: [4295008.438000] usb 1-1: new full speed USB device using ohci_hcd and address 4
Mar  6 17:45:29 HOMEPC kernel: [4295009.204000] usb 1-1: reset full speed USB device using ohci_hcd and address 4
Mar  6 17:45:30 HOMEPC firmware_helper[5486]: main: error loading '/lib/firmware/speedtch-1.bin.4.00' for device '/class/firmware/1-1:1.0' with driver 'speedtch'
Mar  6 17:45:30 HOMEPC firmware_helper[5491]: main: error loading '/lib/firmware/speedtch-1.bin.4' for device '/class/firmware/1-1:1.0' with driver 'speedtch'
Mar  6 17:45:30 HOMEPC kernel: [4295009.512000] speedtch 1-1:1.0: found stage 1 firmware speedtch-1.bin
Mar  6 17:45:30 HOMEPC firmware_helper[5499]: main: error loading '/lib/firmware/speedtch-2.bin.4.00' for device '/class/firmware/1-1:1.0' with driver 'speedtch'
Mar  6 17:45:30 HOMEPC firmware_helper[5502]: main: error loading '/lib/firmware/speedtch-2.bin.4' for device '/class/firmware/1-1:1.0' with driver 'speedtch'
Mar  6 17:45:30 HOMEPC kernel: [4295009.641000] speedtch 1-1:1.0: found stage 2 firmware speedtch-2.bin
```

I have a revision 4 speedtouch 330 usb adsl modem.  By the looks its checking three firmware possibilities, failing on two but successful on the third.  I also get upstream/downstream speeds after the above in /var/log/messages.

Any help in getting me online would be appreciated!

TIA,


Simon

---

### Post by kubaknopp on 2007-03-06
On kubuntu work fine:
[http://kubuntuforums.net/forums/index.php?topic=12645.0](http://kubuntuforums.net/forums/index.php?topic=12645.0)

v

---

### Post by simonpearson on 2007-03-06
kubaknopp thanks for your post, however, I unfortunately do not speak the language this program was written for (polish maybe?)

[COLOR="Silver"]Is there an English alternative?[/COLOR] <-- ignore that.. just read the rest of your kubunut post :)  Will try it out..

Also, I still would like to understand what is not working, so I can fix in the future..

---

### Post by simonpearson on 2007-03-07
Well, the above didn't work for me either so I decided to reinstall but put Edgy on this time.  Followed the same instructions, and voila - I'm online.

I simply must have missed something out ... I suspect it was the vci I missed but will never know now!

Thanks for any readers...

Simon

---

