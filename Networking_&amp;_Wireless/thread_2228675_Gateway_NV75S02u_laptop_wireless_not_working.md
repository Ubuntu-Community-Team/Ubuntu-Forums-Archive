---
title: "Gateway NV75S02u laptop wireless not working"
date: 2014-06-08
forum: Networking &amp; Wireless
---

### Post by bahram2 on 2014-06-08
Hi,
I am using ubuntu 14.04 LTS on this laptop. I have read most of the relevant posts about this and so i will post the results of the commands i think you would be most interested in. The problem is that the [Fn]F3 which typically turns on the hardware wireless, does not work. I have connectivity through wired connection. When i purchased this laptop 2 or so years ago, it came with windows 7, it still has windows 7 and i use it. Sometimes back, i installed ubunto version 11.x.x hoping that you guys may now have figured out the problem, i installed ubuntu 14.04 LTS and i see that the same problem exists (i can not turn on my wireless trhough my keyboard). Wireless works and the [Fn]F3 key toggles the wireless in windows 7.I have attached the outputs of the various commands: (lspci - v), (nm-tool), (iwconfig), (dmesg | grep -e bcma -e atl1c), (modinfo bcma, modinfo atl1c).  Your web site only allows up to 5 attachments, so here is the last one (modinfo atl1c):


   [HTML]```
filename:      
/lib/modules/3.13.0-24-generic/kernel/drivers/net/ethernet/atheros/atl1c/atl1c.ko version:        1.0.1.1-NAPI license:        GPL description:    Qualcom Atheros 100/1000M
Ethernet Network Driver author:         Qualcomm Atheros Inc.,
<nic-devel@qualcomm.com> author:         Jie Yang srcversion:     77A3FAB53265A7C9ACA8A49 alias:         
pci:v00001969d00001083sv*sd*bc*sc*i* alias:         
pci:v00001969d00001073sv*sd*bc*sc*i* alias:         
pci:v00001969d00002062sv*sd*bc*sc*i* alias:         
pci:v00001969d00002060sv*sd*bc*sc*i* alias:         
pci:v00001969d00001062sv*sd*bc*sc*i* alias:         
pci:v00001969d00001063sv*sd*bc*sc*i* depends:        
intree:         Y vermagic:       3.13.0-24-generic SMP mod_unload
modversions 
signer:         Magrathea: Glacier signing key sig_key:       
00:A5:A6:57:59:DE:47:4B:C5:C4:31:20:88:0C:1B:94:A5:39:F4:31 sig_hashalgo:   sha512
```[/HTML]
Thank you,
Bahram

---

### Post by praseodym on 2014-06-09
Hi,

for this device you need the Broadcom STA driver:
```

sudo apt-get install bcmwl-kernel-source
```

---

### Post by bahram2 on 2014-06-09
> **praseodym said:**
> Hi,

for this device you need the Broadcom STA driver:
```

sudo apt-get install bcmwl-kernel-source
```


Does the keyboard [Fn]F3 supposed to work after this switch? I  went to our local electronic store and found almost 90% or so of the laptops now have the keyboard method of turning on/off the wireless.

---

### Post by bahram2 on 2014-06-09
Thank you [**[COLOR=#000000]praseodym[/COLOR]**]("http://ubuntuforums.org/member.php?u=1411497")  !

I tried to install the package from the USB memory stick and it failed due to missing dkms dependency. So, i installed dkms from the usb's ./pool/main/d/dkms directory by double clicking on the .deb installer. When it came up, it ran the checks and then the "install" button appeared on the right and then i clicked the install key, i.e. i installed it or it did it :p.  Then i went back to the directory /pool/restricted/b and installed the package "bcmwl-kernel-source_6.30.223.141+bdcom-0ubuntu2_amd64.deb".  It turned on the wireless. Then i disconnected from the wired connection and tried to connect on the wireless to my SSID. It took a few minutes and i got a "Report a problem" dialog which i sent its contents but one thing to note at the bottom of the message it says glxinfo (Error: [Errno 2] No such file or directory: 'glxinfo').
I recreated the connection in the connection manager and retried and now it works. I am going to try to reboot and see if i get this error.
Bahram

---

### Post by bahram2 on 2014-06-09
After rebooting, i no longer get an error. My wireless is working.

---

