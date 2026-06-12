---
title: "Newbie Wireless Card Help"
date: 2009-09-07
forum: New to Ubuntu
---

### Post by bvill on 2009-09-07
I am an absolute newbie to Ubuntu but am learning.  I am trying to get my 9.04 64 bit system set up but am having trouble with my wireless adapter.  I have a dual boot system with Windows XP Pro 32 bit and Jaunty 64 bit.  My wireless adapter in Linksys WMP300N and it works fine in XP.  I have spent hours trying to configure it by browsing the forums and help sections but am still having trouble.  I installed ndiswrapper and used the instructions to install bcmwl5 driver and blacklist bcm43xx.  It looks like the device is recognized in lshw but I get no wireless options in Network Manager.  I found what I think is an updated bcmwl5.inf driver from Linksys.  Could it be that the driver I installed does not have 64 bit support but the new one I found does?  If so how do I uninstall the original bcmwl5 driver and install the new one?  I am a complet novice at the terminal so I apologize in advance.  If anyone could hold my hand and walk me through some suggestions, I would really appreciate it.  I am looking forward to migrating away from Windows, but still have a lot to learn.  Thank you in advance.

---

### Post by mapes12 on 2009-09-07
Hello bvill

You may get other posts where you will be typing stuff into Terminal and, if my experience is anything to go by, getting nowhere. I have never had any success with ndiswrapper. My first experience got the wifi working but then after a few days it kept dropping the connection. It's much easier to get a native supported wifi card: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=(supported)|(wifi)#head-e669905d73a32156274930398b3d3c3468508d45](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=(supported)|(wifi)#head-e669905d73a32156274930398b3d3c3468508d45)

These always work: [http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/) I have 3 of them in different machines

---

### Post by zkriesse on 2009-09-07
Go to System/Preferences/Network Connections. In Network Connections go to Wireless. It should have your wireless networks that you can connect to. Click the one that you want and choose edit. In the edit menu make sure that connect automatically. Hope this helps you.

---

### Post by bvill on 2009-09-07
> **Zachk18 said:**
> Go to System/Preferences/Network Connections. In Network Connections go to Wireless. It should have your wireless networks that you can connect to. Click the one that you want and choose edit. In the edit menu make sure that connect automatically. Hope this helps you.


Thank you for the suggestion, but when I go through that progression there is nothing listed under the wireless tab.  I does not bring up any wireless netorks.

---

### Post by pastalavista on 2009-09-07
Have you connected your Ubuntu box to the internet via a wired ethernet connection? Just plug it into your router. Ubuntu will automatically download and install the drivers you need for wifi and graphics.

---

### Post by bvill on 2009-09-07
> **pastalavista said:**
> Have you connected your Ubuntu box to the internet via a wired ethernet connection? Just plug it into your router. Ubuntu will automatically download and install the drivers you need for wifi and graphics.

It has been connected via a wired connection, which works fine, but still no wireless.

---

