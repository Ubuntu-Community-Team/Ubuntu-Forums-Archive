---
title: "Bluetooth problem"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by starstalker on 2009-11-17
Hi
Ok here is my problem ,I installed ubuntu on my laptop useing wubi my other OS Windows Vista ,my laptop has a built in bluetooth but I cant see the bluetooth icon unless I login my windows first then restart and login ubuntu and every time I shutdown I have to login to vista first to get the bluetooth icon to appear .

Is there a way to fix it?it will make my life much easier as i dont want to use windows any more :P

Thanks for your help in advance

---

### Post by HarrisonNapper on 2009-11-17
A dual boot would probably be better for this (compared with wubi).

If you're already dual-booting, there may be a software switch in the driver for your bluetooth model. Open up a terminal in Ubuntu, type "lsusb" and post the output here, then I'll poke around for the driver and see if others have had issues.

Cheers.

---

### Post by starstalker on 2009-11-17
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04f2:b008 Chicony Electronics Co., Ltd USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 1bcf:0007 Sunplus Innovation Technology Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

here it is thanks for the Re

---

### Post by starstalker on 2009-11-18
here is some extra info
"sudo bluetoothd -nd"
 
bluetoothd[3399]: Bluetooth daemon 4.51
bluetoothd[3399]: Enabling debug information
bluetoothd[3399]: parsing main.conf
bluetoothd[3399]: discovto=0
bluetoothd[3399]: pairto=0
bluetoothd[3399]: pageto=8192
bluetoothd[3399]: name=%h-%d
bluetoothd[3399]: class=0x000100
bluetoothd[3399]: discov_interval=0
bluetoothd[3399]: Key file does not have key 'DeviceID'
bluetoothd[3399]: Starting SDP server
bluetoothd[3399]: Loading builtin plugins
bluetoothd[3399]: Loading audio plugin
bluetoothd[3399]: Loading input plugin
bluetoothd[3399]: Loading serial plugin
bluetoothd[3399]: Loading network plugin
bluetoothd[3399]: Loading service plugin
bluetoothd[3399]: Loading hciops plugin
bluetoothd[3399]: Loading hal plugin
bluetoothd[3399]: Loading storage plugin
bluetoothd[3399]: Loading plugins /usr/lib/bluetooth/plugins
bluetoothd[3399]: Can't load plugin /usr/lib/bluetooth/plugins/netlink.so: /usr/lib/bluetooth/plugins/netlink.so: undefined symbol: debug
bluetoothd[3399]: register_interface: path /org/bluez/3399/any
bluetoothd[3399]: Registered interface org.bluez.Service on path /org/bluez/3399/any
bluetoothd[3399]: /etc/bluetooth/network.conf: Key file does not have key 'Disable'
bluetoothd[3399]: /etc/bluetooth/network.conf: Key file does not have key 'DisableSecurity'
bluetoothd[3399]: /etc/bluetooth/network.conf: Key file does not have key 'Interface'
bluetoothd[3399]: /etc/bluetooth/network.conf: Key file does not have key 'Interface'
bluetoothd[3399]: /etc/bluetooth/network.conf: Key file does not have key 'Interface'
bluetoothd[3399]: Config options: InterfacePrefix=bnep%d, PANU_Script=(null), GN_Script=(null), NAP_Script=(null), GN_Interface=pan0, NAP_Interface=pan1, Security=true
bluetoothd[3399]: bridge pan0 created
bluetoothd[3399]: input.conf: Key file does not have key 'IdleTimeout'
bluetoothd[3399]: Unix socket created: 9
bluetoothd[3399]: audio.conf: Key file does not have key 'AutoConnect'
bluetoothd[3399]: audio.conf: Key file does not have key 'MaxConnected'
bluetoothd[3399]: Telephony plugin initialized
bluetoothd[3399]: HFP AG features: "Ability to reject a call" "Enhanced call status" "Extended Error Result Codes" 
bluetoothd[3399]: Entering main loop
bluetoothd[3399]: RFKILL event idx 0 type 1 op 0 soft 0 hard 0
^Cbluetoothd[3399]: Cleanup plugins
bluetoothd[3399]: unregister_interface: path /org/bluez/3399/any
bluetoothd[3399]: bridge pan0 removed
bluetoothd[3399]: Stopping SDP server
bluetoothd[3399]: Exit

---

### Post by HarrisonNapper on 2009-11-18
What Ubuntu distro do you have installed? It turns out Sunplus makes every usb device under the Sun. You might try using blueman, as it tends to be the better bluetooth manager. If it's not in synaptic:

```

wget -q http://download.tuxfamily.org/blueman/blueman.gpg -O- | sudo apt-key add -
sudo wget http://download.tuxfamily.org/blueman/hardy.list -O /etc/apt/sources.list.d/blueman.list
sudo apt-get update

```In the second line where it says "hardy.list", replace it with your distro (i.e. "jaunty.list" or "karmic.list"); though I believe for Karmic it's in synaptic by default.

---

### Post by starstalker on 2009-11-27
Sorry for the late reply I did that, everything went fine but I still need to log into my windows to activate the bluetooth on ubuntu

---

### Post by starstalker on 2009-12-02
going to try dual booting if it works i will post again

---

