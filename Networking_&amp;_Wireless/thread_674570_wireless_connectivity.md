---
title: "wireless connectivity"
date: 2008-01-21
forum: Networking &amp; Wireless
---

### Post by rahul rai on 2008-01-21
i have desktop of following configuration :
amd athlon(tm) 64 processor
3500+
2.20ghz,448 mb ram

wifi chipset: D-Link AirPlus G DWL-G510 Wireless PCI Adapter(rev.C)

i am not getting connected to net in ubuntu 7.10
i have installed ndisgtk package and installed .inf file from the driver cd ,
but it is displaying the message: "invalid driver".

tell me the solution

---

### Post by bodymind on 2008-01-21
maybe you should search before posting... 
try this:
download: [ftp://ftp.dlink.co.uk/wireless/dwl-g520m/dwl-g520m_drv_v1-1b3.zip](ftp://ftp.dlink.co.uk/wireless/dwl-g520m/dwl-g520m_drv_v1-1b3.zip)
unzip it
open a terminal

6. Install the Windows drivers (using ndiswrapper):
```
sudo ndiswrapper -i file.inf
```

7. Make sure ndiswrapper loads up every time we start Linux:
```
sudo modprobe ndiswrapper
echo "ndiswrapper" | sudo tee -a /etc/modules
```


from: [http://ubuntuforums.org/showthread.php?t=464139&highlight=DWL-G510](http://ubuntuforums.org/showthread.php?t=464139&highlight=DWL-G510)
and
[http://ubuntuforums.org/showthread.php?t=512828&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=512828&highlight=ndiswrapper)

---

