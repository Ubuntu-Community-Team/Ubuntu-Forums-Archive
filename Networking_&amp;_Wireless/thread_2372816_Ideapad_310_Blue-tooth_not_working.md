---
title: "Ideapad 310 Blue-tooth not working"
date: 2017-09-29
forum: Networking &amp; Wireless
---

### Post by bobsone on 2017-09-29
Hi
 I have a Win10 and Ubuntu Mate (16.4) dual boot Lenovo Ideapad 310.
 Since the install I have been unable to get the Bluetooth to work (it works in Win10).  Also, I had a problem with my WIFI randomly dropping out which is now fixed (see thread at [https://ubuntuforums.org/]("https://ubuntuforums.org/showthread.php?t=2372356") )
 
 The Bluetooth appears to be activated, there is an active logo in the panel and a right click brings up a functioning menu e.g. Turn Bluetooth Off, Make Discoverable... Devices, Adaptors... etc.  Using the Devices option I can Search for devices but it doesn’t find any, I have tested it with a Zopo and MotoG phone and a cheap Bluetooth speaker.

 I have spent some time online but haven’t found much that addresses my problem, I did find a *Bluetooth Setup* page but it covers 10.04 and 11.04 so I haven’t tried it,   [https://help.ubuntu.com/]("https://help.ubuntu.com/community/BluetoothSetup") .  

 I have run the update and upgrade commands and I have created a current *Wireless Info Script* at    [http://paste.ubuntu.com/25637461/](http://paste.ubuntu.com/25637461/) 

 Any input that can be offered is appreciated.
 
Regards.

---

### Post by jeremy31 on 2017-09-29
You could try it in terminal
```
bluetoothctl
```
```
power on
```
```
scan on
```
Use CTRL + d to exit bluetoothctl
It seems to be detected and firmware is loaded for bluetooth

---

### Post by bobsone on 2017-09-29
Hi
I tried the commands, unfortunately although it looks like the Bluetooth is working it didn’t solve the problem.  Also, I neglected to mention this before, the phones cannot detect MATE Ideapad.
 (I have all devices set to Always Visible).

[HTML]bearthold@Another-problem:~$ bluetoothctl
[NEW] Controller C8:3D:D4:89:5B:BA Another-problem [default]
[bluetooth]# power on
Changing power on succeeded
[bluetooth]# scan on
Discovery started
[bluetooth]# quit
[DEL] Controller C8:3D:D4:89:5B:BA Another-problem [default]

[/HTML]

Thanks

---

