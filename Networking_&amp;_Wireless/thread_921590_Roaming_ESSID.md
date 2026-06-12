---
title: "Roaming ESSID"
date: 2008-09-16
forum: Networking &amp; Wireless
---

### Post by MaindotC on 2008-09-16
Is this normal?  It seems that my card is not staying put on one AP:

```

Sep 16 07:45:10 z9432cjkl234a-desktop NetworkManager: <debug> [1221565510.671573] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:0C:E6:51:76:02 to 00:0C:E6:E3:7E:02 on wireless network 'MSCt61' 
Sep 16 07:45:10 z9432cjkl234a-desktop NetworkManager: <debug> [1221565510.675264] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'MSCt61' 
Sep 16 07:47:20 z9432cjkl234a-desktop NetworkManager: <debug> [1221565640.671724] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:0C:E6:51:76:02 to 00:0C:E6:E3:7E:02 on wireless network 'MSCt61' 
Sep 16 07:47:20 z9432cjkl234a-desktop NetworkManager: <debug> [1221565640.676041] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'MSCt61' 
Sep 16 07:49:30 z9432cjkl234a-desktop NetworkManager: <debug> [1221565770.671692] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:0C:E6:51:76:02 to 00:0C:E6:E3:7E:02 on wireless network 'MSCt61' 
Sep 16 07:49:30 z9432cjkl234a-desktop NetworkManager: <debug> [1221565770.676012] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'MSCt61' 
Sep 16 07:51:40 z9432cjkl234a-desktop NetworkManager: <debug> [1221565900.671697] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:0C:E6:93:77:02 to 00:0C:E6:E3:7E:02 on wireless network 'MSCt61' 
Sep 16 07:51:40 z9432cjkl234a-desktop NetworkManager: <debug> [1221565900.676642] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'MSCt61' 
Sep 16 07:53:50 z9432cjkl234a-desktop NetworkManager: <debug> [1221566030.680043] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:0C:E6:51:76:02 to 00:0C:E6:E3:7E:02 on wireless network 'MSCt61' 
Sep 16 07:53:50 z9432cjkl234a-desktop NetworkManager: <debug> [1221566030.684712] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'MSCt61' 
Sep 16 07:56:00 z9432cjkl234a-desktop NetworkManager: <debug> [1221566160.711726] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:0C:E6:51:76:02 to 00:0C:E6:E3:7E:02 on wireless network 'MSCt61' 

```

I have a laptop running Hardy and it uses an Intel 3495 and it doesn't have this problem.  Is there a way to stop it from roaming unless I want it to?  I live on a campus that has 900 AP's and they're all centrally managed with a wireless controller so I can walk from one end of campus to another and not lose signal, but in this instance I want it to stay put.  I'm having a lot of latency and I'm just assuming that this roaming may be the issue.  Thanks!

---

### Post by MaindotC on 2008-09-19
bump - using Belkin [Wireless G USB adapter](http://catalog.belkin.com/IWCatProductPage.process?Product_Id=179211) and the [B43 Driver](http://linuxwireless.org/en/users/Drivers/b43) from linuxwireless.org.

---

### Post by MaindotC on 2008-09-23
*bump* - what other information do you need?

---

### Post by superprash2003 on 2008-09-23
go to system->admin->network and go to your wifi card properties.. and uncheck "enable roaming mode" and manually select the wifi network you wish

---

### Post by MaindotC on 2008-09-24
Thanks, superprash.  I should have concluded that myself :(  My bad.

---

