---
title: "Edimax AC600 USB (RTL8812AU) stopped working"
date: 2017-04-27
forum: Networking &amp; Wireless
---

### Post by brunocassol on 2017-04-27
**edit: Please ready my reply below as I got it to list networks.**

Lubuntu 16.04, fully updated. [Edimax AC600 USB wifi adapter]("http://www.edimax.com/edimax/merchandise/merchandise_detail/data/edimax/in/wireless_adapters_ac600_dual-band/ew-7811uac/").

Initially it worked by installing this manually: [https://github.com/diederikdehaas/rtl8812AU](https://github.com/diederikdehaas/rtl8812AU). I didn't setup DKMS.

Then came kernel updates, i reinstalled the driver and it stopped connecting but it still listed wifi networks. After fiddling around it stopped listing wireless networks.

I removed the manually installed module and did: ```
sudo apt-get install rtl8812au-dkms
``` but it still doesn't work. Not even lists networks.

This is what shows up in dmesg -w when I plug the USB adapter:

```
[ 1735.236053] usb 3-1: new high-speed USB device number 11 using xhci_hcd
[ 1735.364445] usb 3-1: New USB device found, idVendor=7392, idProduct=a812
[ 1735.364450] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1735.364453] usb 3-1: Product: Edimax AC600 USB
[ 1735.364467] usb 3-1: Manufacturer: Realtek
[ 1735.364469] usb 3-1: SerialNumber: 00e04c000001

```

Please help. I'm having to rely on phone USB tethering to stay connected.

This is the pastebin of the wifi script pinned in this forum: [http://paste.ubuntu.com/24466070/](http://paste.ubuntu.com/24466070/)

---

### Post by brunocassol on 2017-04-27
Progress. It now lists wireless networks again! But doesn't connect.

I did ```
sudo apt-get remove rtl8812au-dkms
``` then:

```
git clone https://github.com/diederikdehaas/rtl8812AU
cd rtl8812AU
make CC=/usr/bin/gcc-5
sudo make install
sudo modprobe 8812au

```

Suddenly it now lists networks but doesn't connect. This is dmesg last lines:

```
[ 1730.420690] usb 3-1: USB disconnect, device number 9[ 1735.236053] usb 3-1: new high-speed USB device number 11 using xhci_hcd
[ 1735.364445] usb 3-1: New USB device found, idVendor=7392, idProduct=a812
[ 1735.364450] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1735.364453] usb 3-1: Product: Edimax AC600 USB
[ 1735.364467] usb 3-1: Manufacturer: Realtek
[ 1735.364469] usb 3-1: SerialNumber: 00e04c000001
[ 2517.360305] RTL871X: module init start
[ 2517.360312] RTL871X: rtl8821au v4.3.14
[ 2517.360316] RTL871X: rtl8821au BT-Coex version = BTCOEX20150128-51
[ 2517.434212] RTL871X: rtw_ndev_init(wlan0)
[ 2517.435326] usbcore: registered new interface driver rtl8821au
[ 2517.435328] RTL871X: module init ret=0
[ 2517.436870] rtl8821au 3-1:1.0 wlx801f02fedc9a: renamed from wlan0
[ 2517.462690] IPv6: ADDRCONF(NETDEV_UP): wlx801f02fedc9a: link is not ready
[ 2517.721098] IPv6: ADDRCONF(NETDEV_UP): wlx801f02fedc9a: link is not ready
[ 2517.775917] IPv6: ADDRCONF(NETDEV_UP): wlx801f02fedc9a: link is not ready
[ 2519.489405] RTL871X: nolinked power save enter
[ 2519.757028] RTL871X: nolinked power save leave
[ 2521.469290] RTL871X: nolinked power save enter
[ 2575.175251] IPv6: ADDRCONF(NETDEV_UP): wlx801f02fedc9a: link is not ready
[ 2575.435913] RTL871X: nolinked power save leave
[ 2577.149249] RTL871X: nolinked power save enter
[ 2578.256281] RTL871X: nolinked power save leave
[ 2579.969449] RTL871X: nolinked power save enter
[ 2601.267178] RTL871X: nolinked power save leave
[ 2602.977238] RTL871X: nolinked power save enter
[ 2634.280190] RTL871X: nolinked power save leave
[ 2635.993241] RTL871X: nolinked power save enter
[ 2677.265119] RTL871X: nolinked power save leave
[ 2678.977157] RTL871X: nolinked power save enter
```

This is the updated wifi script output: [http://paste.ubuntu.com/24466171/](http://paste.ubuntu.com/24466171/)

---

### Post by brunocassol on 2017-04-27
Finally managed to connect to the wifi network!

When I edit wifi connections, all fields appear gray. So I did:


[LIST]
[*]run connection editor with `sudo nm-connection-editor`
[*]edit wifi you previously tried to connect to
[*]type password
[*]mark [x] allow all users to connect
[*]save
[*]restart network with: `sudo service network-manager restart`
[/LIST]

I can now connect to the edited wifi. But I still have to do this manual process for new wifi networks.

Does anyone know how to fix this? It's as if my normal user suddenly doesn't have permission to edit wifi networks. These are my user groups:

dev adm cdrom sudo audio dip plugdev netdev nopasswdlogin lpadmin sambashare chrome-remote-desktop

How can I debug this?

---

### Post by brunocassol on 2017-05-10
bump. still need sudo to edit/connect to wifi.

---

### Post by jeremy31 on 2017-05-10
I wonder if wifi power management isn't the problem
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
```
systemctl restart network-manager.service
```

See if it works better even though I didn't see power management for wifi being enabled in the script results but the dmesg shows it trying to be turned on

---

### Post by brunocassol on 2017-05-10
That was a good shot jeremy31. But it still doesn't connect to a wifi unless I:


[LIST=1]
[*]run connection editor with **sudo nm-connection-editor**
[*]edit wifi you previously tried to connect to
[*]type password
[*]mark [x] allow all users to connect
[*]save
[*]restart network with: [B]sudo service network-manager restart
[/B]
[/LIST]

It's as if my network service suddenly is running as a user that doesn't have permission to alter wifi connection settings.

---

### Post by jeremy31 on 2017-05-10
You shouldn't need sudo to run the connection editor.  You might want to look at /etc/NetworkManager/system-connections to find your connection and use
```
sudo rm /etc/NetworkManager/system-connections/{wifi-name}
```
To remove that and then use Network under system settings to add the network back and hopefully the permissions will be back to normal.

The file in /etc/NetworkManager/system-connections/ will have a permissions=user: under [connection] and it may be set to root

---

### Post by brunocassol on 2017-05-10
The wifi name is "Lidia". So there is a "Lidia" file there:

```
ls -la /etc/NetworkManager/system-connections

drwxr-xr-x 2 root root 4096 Mai 10 17:38 ./
drwxr-xr-x 8 root root 4096 Abr 27 22:46 ../
-rw------- 1 root root  411 Mai 10 17:38 Lidia
```


I deleted the file as you instructed, restarted network service and tried connecting to the same wifi.
It created the same "Lidia" file inside /etc/NetworkManager/system-connections but it was still owned by root and I couldn't not connect still unless I sudoed to edit it.

All new wifi connection files are owned by root. Not sure if this is correct or why this happens.

---

