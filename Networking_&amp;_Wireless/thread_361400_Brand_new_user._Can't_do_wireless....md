---
title: "Brand new user. Can't do wireless..."
date: 2007-02-14
forum: Networking &amp; Wireless
---

### Post by supernewbie on 2007-02-14
Hi all, brand new Linux user here. Installed just fine, but I have now Clue how to hook up to my wireless router. Ubuntu 6.0.10 is installed on an HP laptop, and I'm using the new Belkin N1 router. I know there's probably something obvious I'm missing here, but I can't seem to figure it out through the normal 'hook-up' screens. Please help! It's greatly appreciated. :)

Thanks,

Mark

---

### Post by Brian625 on 2007-02-14
Open a Terminal - Applications->Accessories->Terminal
type in **iwconfig**
make sure your configuration looks similar to this (will be on eth1 or eth0 shouldn't matter):
lo        no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"belkin54g"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:11:50:4A:C0:88   
          Bit Rate=11 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=31/100  Signal level=-71 dBm  Noise level=-69 dBm
          Rx invalid nwid:0  Rx invalid crypt:335  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

if there is no wireless information there then your wireless device was not recognized and you will have to install the drivers. You can do that with something like ndiswrapper or fwcutter.

---

### Post by Brian625 on 2007-02-14
If you want you can try my wireless guide at [http://www.ubuntuguides.net]("http://www.ubuntuguides.net"). If you have broadcom 4318 drives try following the whole guide it may work for you. If your drivers are installed already skip to **wireless step 5** for a walkthrough on configuring your wireless. Let me know if it helps.

---

### Post by sumgi on 2007-02-14
Here is another [guide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") you can look at.

That one is pretty good for trouble shooting general wireless issues.

Here are some good newbie [links]("http://ubuntuforums.org/showthread.php?t=232059").

---

### Post by banditti on 2007-02-14
To assist via gui, you can try adding network manager, which will add a tool by the clock in the tray.

From a terminal window:

```
sudo apt-get install network-manager network-manager-gnome
```

This is to help on the client side.

---

