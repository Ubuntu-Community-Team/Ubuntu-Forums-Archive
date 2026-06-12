---
title: "WPA in Ubuntu"
date: 2007-05-13
forum: Networking &amp; Wireless
---

### Post by James.Hoffman on 2007-05-13
I am running Ubuntu 7.04 and I cannot connect to any network with wpa encryption. Any WEP or unsecured network it will connect fine. I do have wpa-supplicant installed and I've tried using the network-manager, wicd, and Wifi-radar but none of them will connect it just goes to 'acquiring ip address' then goes back to no connection.
Any help would be greatly appreciated.

---

### Post by FreakTech on 2007-05-13
Try installing knetworkmanager.  It's the only way I have gotten my WPA to work.

---

### Post by ugm6hr on 2007-05-14
Has WPA worked with any Linux disto on your system? I believe that some wireless chipsets don't support WPA directly on linux.  Occasionally, using ndiswrapper with XP drivers can work better (afraid I don't know how to do this with Ubuntu).  

Thankfully, my Atheros 5005 wireless (Acer Aspire 5051 laptop) worked on Xubunu7.04 after installing Network Manager.  Might be worth searching this forum for entries containing your wireless chipset or make / model of wireless card (or laptop if that's what you're using).

---

### Post by Suzan on 2007-05-14
WPA works flawlessly for me with networkmanager and a intel pro wireless3945 card.

See this list, if networkmanager supports your card:
[http://live.gnome.org/NetworkManagerHardware](http://live.gnome.org/NetworkManagerHardware)

Seems networkmanager works best with intel or atheros chipsets for now.

---

### Post by wieman01 on 2007-05-14
> **James.Hoffman said:**
> I am running Ubuntu 7.04 and I cannot connect to any network with wpa encryption. Any WEP or unsecured network it will connect fine. I do have wpa-supplicant installed and I've tried using the network-manager, wicd, and Wifi-radar but none of them will connect it just goes to 'acquiring ip address' then goes back to no connection.
Any help would be greatly appreciated.
What hardware have you got?

---

### Post by konik134 on 2007-05-14
dont use knetwork manager  try to uninstall knetwork manager until they fix problem simple use to setup wireles point from  system-administration-networking
in the networking open wireles card in the place were u must to place name of your network tipe name of your network and on the end of the name add (x)leter  then use aplication add to panel to get conection icon on the panel then restart comp

---

### Post by James.Hoffman on 2007-05-14
I have a broadcom 4311 card and I have gotten wpa to work on here before in 6.06 when I had to install the network manager myself.

---

### Post by stchman on 2007-05-14
> **James.Hoffman said:**
> I am running Ubuntu 7.04 and I cannot connect to any network with wpa encryption. Any WEP or unsecured network it will connect fine. I do have wpa-supplicant installed and I've tried using the network-manager, wicd, and Wifi-radar but none of them will connect it just goes to 'acquiring ip address' then goes back to no connection.
Any help would be greatly appreciated.

Did you install wpasupplicant?  It is needed for wireless encryption.  Look at the procedure on my website for Atheros cards, you can follow the network manager portion.

[http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

Hope this helps.

---

### Post by James.Hoffman on 2007-05-14
Yeah I install wpasupplicant and it still doesn't connect I even tried starting the wireless card manually after Ubuntu was started. I don't know why it does this it connected before 7.04 by following this tutorial to install the card: [link]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show")
and to install wpa.

---

### Post by stchman on 2007-05-14
> **James.Hoffman said:**
> Yeah I install wpasupplicant and it still doesn't connect I even tried starting the wireless card manually after Ubuntu was started. I don't know why it does this it connected before 7.04 by following this tutorial to install the card: [link]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show")
and to install wpa.

What kind of card do you have?  I have only had experience with Atheros (madwifi) and Broadcom (ndiswrapper).  I understand the Intel cards work out of box.  If you have an Atheros then install madwifi.

---

### Post by James.Hoffman on 2007-05-14
I have a broadcom 4311 card built in on a dell latitude d500. I appreciate all the help with this issue, I love the Linux support community!

---

### Post by stchman on 2007-05-15
> **James.Hoffman said:**
> I have a broadcom 4311 card built in on a dell latitude d500. I appreciate all the help with this issue, I love the Linux support community!

Go to my website as I have a procedure on there to get Broadcom 43xx cards working.

[http://www.stchman.com/install_ndis_broadcom.html](http://www.stchman.com/install_ndis_broadcom.html)

Hope it helps.

---

### Post by James.Hoffman on 2007-05-15
I tried replacing the driver but to no avail. It still wont connect to a wpa encrypted network.

---

### Post by wieman01 on 2007-05-16
> **James.Hoffman said:**
> I tried replacing the driver but to no avail. It still wont connect to a wpa encrypted network.
Maybe you have chosen the wrong Windows driver, possibly a version that does not support WPA.

---

### Post by stchman on 2007-05-16
> **James.Hoffman said:**
> I tried replacing the driver but to no avail. It still wont connect to a wpa encrypted network.

Try removing ndiswrapper and following my procedure.

---

### Post by James.Hoffman on 2007-05-17
OK I will remove ndiswrapper and do the procedure again using that driver.

---

### Post by Jamie Jackson on 2007-05-17
Here's a step-by-step that I contributed to. I couldn't get anything to work until I did this: [WifiDocs/Device/Broadcom BCM4311 rev 01 (ndiswrapper)]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)")

Lots of success stories logged.

Thanks,
Jamie

---

### Post by tekdata on 2007-05-17
I'm having exactly the same problem with 64-bit Feisty.

---

### Post by James.Hoffman on 2007-05-18
Finally resolved! I removed the driver and ndiswrapper completely and reinstalled it using this guide [here.]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show")
I don't know why it didn't work the first time but it works now thanks for all your help.

---

