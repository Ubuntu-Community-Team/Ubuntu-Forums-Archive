---
title: "Wont recognize mp3 player"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by natedogg23 on 2010-01-16
Hey all. just got a new mp3 player and nothing happens on screen when i plug it in. my old one was recognized right away and the screen would pop up on its own without a driver or anything but this new one is also a recorder and pc camera [dont know if that matters at all]. ive tried a driver search but i cant find a way to maybe check usb ports? i got it on ebay from hong kong but i guess doze users have easier success with them

---

### Post by fooman on 2010-01-16
whats the make & model of the player?

---

### Post by kenuf on 2010-01-16
What version of Ubuntu are you using.

My Zen Vision:M was not picked up in 8.04 but was detected in 9.10

---

### Post by natedogg23 on 2010-01-16
there is no name on it anywhere, there was a flyer inside the package from anyts.net but there are no name brands on these items either. nor when i turn it on. the site has samsung products so maybe this is like a natty lite of samsung but im not sure. im using 9.10 currently. its a 32 gb touch screen pretty sure 2009 based on the date i had to change

---

### Post by NFblaze on 2010-01-17
Sounds like an unknown knockoff product. Is there a setting in it for different connection modes?

Though, usually those knockoff chinese devices use generic hardware that's easy to recognize, plug it in and and post the output of ***dmesg | tail***.

Also, it could be your version of Ubuntu (well, the kernel really) doesnt have the driver for it yet. You may need to update. You can use ***uname -a*** to find information about Ubuntu and the kernel you are using.

---

### Post by natedogg23 on 2010-01-17
> **NFblaze said:**
> Sounds like an unknown knockoff product. Is there a setting in it for different connection modes?

Though, usually those knockoff chinese devices use generic hardware that's easy to recognize, plug it in and and post the output of ***dmesg | tail***.

Also, it could be your version of Ubuntu (well, the kernel really) doesnt have the driver for it yet. You may need to update. You can use ***uname -a*** to find information about Ubuntu and the kernel you are using.

[132111.309337] usb 1-3: configuration #85 chosen from 1 choice
[132111.313213] scsi8 : SCSI emulation for USB Mass Storage devices
[132111.313699] usb-storage: device found at 16
[132111.313704] usb-storage: waiting for device to settle before scanning
[132116.313854] usb-storage: device scan complete
[132137.176145] usb 1-3: reset full speed USB device using ohci_hcd and address 16
[132147.556119] usb 1-3: reset full speed USB device using ohci_hcd and address 16
[132152.936082] usb 1-3: reset full speed USB device using ohci_hcd and address 16
[132163.316077] usb 1-3: reset full speed USB device using ohci_hcd and address 16
[132163.522296] scsi 8:0:0:0: Device offlined - not ready after error recovery

---

### Post by natedogg23 on 2010-01-17
2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686 GNU/Linux
- thats kernel. i plugged it in on my friends pc last night, it worked like its supposed to, unfortunately it was on vista. i thought that would happen but i know it works at least. is there a cl update i should do?

---

