---
title: "Broke bluetooth while trying to enable wireless headphones and microphone"
date: 2014-01-07
forum: Networking &amp; Wireless
---

### Post by jondiced on 2014-01-07
Hi guys,

I was trying to get my new bluetooth headphones/microphone working with Kubuntu (12.04 LTS). It was fine in the one-way configuration, but not two-way. My bluetooth adapter is IOGear Bluetooth 4.0 USB ([http://www.iogear.com/product/GBU521/](http://www.iogear.com/product/GBU521/)), which worked out-of-the-box. 
After installing different bluetooth-related software to get the microphone working, the computer can no longer even find the adapter. Here is the output from lsusb and hciconfig:

```

(11:16) jaguilar@jaguilar-lab:~] lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub                                                                       
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub                                                                       
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub                                                                       
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub                                                            
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub                                                            
Bus 001 Device 003: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business                                                           
Bus 001 Device 004: ID 046d:c05a Logitech, Inc. Optical Mouse M90                                                                    
Bus 001 Device 005: ID 0b0e:094d GN Netcom                                                                                           
Bus 002 Device 003: ID 058f:6364 Alcor Micro Corp. Hi-Speed 7-in-1 Flash Card Reader/Writer [Sabrent]                                
(11:16) jaguilar@jaguilar-lab:~] hciconfig                                                                                      
(11:16) jaguilar@jaguilar-lab:~]                                                                     

```

dmesg shows that the kernel has the bluetooth module there, but detects no bluetooth adapter. 

Here's the package manager history from that day:

```
bluez-gstreamer (4.98-2ubuntu7) Removed at 10:13
ubuntu-docs (12.04.6) Installed at 10:06
bluez-tools (0.1.38+git662e-2ubuntu1) Purged at 10:06
bluedevil (1.2.2-0ubuntu1) Installed at 10:01
obex-data-server (0.4.6-0ubuntu1) Installed at 10:00
obexd-server (0.44-0ubuntu1) Removed at 10:00
obexd-server (0.44-0ubuntu1, automatic) Installed at 9:40
bluez-gstreamer (4.98-2ubuntu7) Installed at 9:40
bluez-tools (0.1.38+git662e-2ubuntu1) Installed at 9:40
obex-data-server (0.4.6-0ubuntu1) Removed at 9:40
bluedevil (1.2.2-0ubuntu1) Removed at 9:40
```

I returned to having only bluedevil and its dependencies installed. Can someone please help me get my bluetooth adapter recognized again?

Thanks,

jondiced

---

### Post by cpbl on 2014-04-04
Did you have any more luck?

Which headset are you using? I am just looking for any wireless headset whose microphone and speakers work with Ubuntu...

I've bought and returned two so far  (Logitech H800 and August EP650).

---

