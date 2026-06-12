---
title: "no bluetooth devices detected"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by satipera on 2009-11-11
When I try to run blueman I get a message that says bluez daemon not running. btscanner will not detect anything, generally my bluetooth just will not work at all, help gratefully received.   

dell mini 10v, karmic, dell bt travel mouse.

Help!

ian@ian-laptop:~$ sudo hciconfig hci0 reset
Can't get device info: No such device
ian@ian-laptop:~$

---

### Post by satipera on 2009-11-13
New information, does this help anyone to help me?


ian@ian-laptop:~$ sudo bluetoothd -nd
bluetoothd[2441]: Bluetooth daemon 4.51
bluetoothd[2441]: Enabling debug information
bluetoothd[2441]: parsing main.conf
bluetoothd[2441]: discovto=0
bluetoothd[2441]: pairto=0
bluetoothd[2441]: pageto=8192
bluetoothd[2441]: name=%h-%d
bluetoothd[2441]: class=0x000100
bluetoothd[2441]: discov_interval=0
bluetoothd[2441]: Key file does not have key 'DeviceID'
bluetoothd[2441]: Starting SDP server
bluetoothd[2441]: Loading builtin plugins
bluetoothd[2441]: Loading audio plugin
bluetoothd[2441]: Loading input plugin
bluetoothd[2441]: Loading serial plugin
bluetoothd[2441]: Loading network plugin
bluetoothd[2441]: Loading service plugin
bluetoothd[2441]: Loading hciops plugin
bluetoothd[2441]: Loading hal plugin
bluetoothd[2441]: Loading storage plugin
bluetoothd[2441]: Loading plugins /usr/lib/bluetooth/plugins
bluetoothd[2441]: Can't load plugin /usr/lib/bluetooth/plugins/netlink.so: /usr/lib/bluetooth/plugins/netlink.so: undefined symbol: debug
bluetoothd[2441]: register_interface: path /org/bluez/2441/any
bluetoothd[2441]: Registered interface org.bluez.Service on path /org/bluez/2441/any
bluetoothd[2441]: /etc/bluetooth/network.conf: Key file does not have key 'Disable'
bluetoothd[2441]: /etc/bluetooth/network.conf: Key file does not have key 'DisableSecurity'
bluetoothd[2441]: /etc/bluetooth/network.conf: Key file does not have key 'Interface'
bluetoothd[2441]: /etc/bluetooth/network.conf: Key file does not have key 'Interface'
bluetoothd[2441]: /etc/bluetooth/network.conf: Key file does not have key 'Interface'
bluetoothd[2441]: Config options: InterfacePrefix=bnep%d, PANU_Script=(null), GN_Script=(null), NAP_Script=(null), GN_Interface=pan0, NAP_Interface=pan1, Security=true
bluetoothd[2441]: bridge pan0 created
bluetoothd[2441]: input.conf: Key file does not have key 'IdleTimeout'
bluetoothd[2441]: Unix socket created: 9
bluetoothd[2441]: audio.conf: Key file does not have key 'AutoConnect'
bluetoothd[2441]: audio.conf: Key file does not have key 'MaxConnected'
bluetoothd[2441]: Telephony plugin initialized
bluetoothd[2441]: HFP AG features: "Ability to reject a call" "Enhanced call status" "Extended Error Result Codes" 
bluetoothd[2441]: Entering main loop
bluetoothd[2441]: RFKILL event idx 0 type 1 op 0 soft 0 hard 0
bluetoothd[2441]: RFKILL event idx 1 type 2 op 0 soft 0 hard 0

---

### Post by satipera on 2009-11-13
Hmmmmm, it seems that the bios showing bluetooth enabled and the bluetooth applet showing "bluetooth on" does not mean that I have on board bluetooth :)  One bluetooth dongle later all is well.

---

### Post by rustutzman on 2009-11-13
Try installing Blueman bluetooth manager. That's what I ended up doing to get it working on my Asus eee

Russ

edit: The info is at [http://blueman-project.org/downloads.html](http://blueman-project.org/downloads.html)

---

