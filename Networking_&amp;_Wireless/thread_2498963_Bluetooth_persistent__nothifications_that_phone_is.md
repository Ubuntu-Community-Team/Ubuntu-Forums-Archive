---
title: "Bluetooth: persistent  nothifications that phone is connecting/disconnecting"
date: 2024-07-05
forum: Networking &amp; Wireless
---

### Post by makem2 on 2024-07-05
[https://pastebin.ubuntu.com/p/Pg3SVcmN3c/](https://pastebin.ubuntu.com/p/Pg3SVcmN3c/)

```

makem-22:~$ sudo hciconfig
[sudo] password for makem: 
hci0:    Type: Primary  Bus: USB
    BD Address: 8C:55:4A:9A:FA:00  ACL MTU: 1021:4  SCO MTU: 96:6
    UP RUNNING PSCAN 
    RX bytes:20112092 acl:46887 sco:90128 events:8797 errors:10
    TX bytes:6672181 acl:4863 sco:90076 commands:3565 errors:8


makem@makem-22:~$

```

```

makem@makem-22:~$ sudo systemctl status bluetooth.service
&#9679; bluetooth.service - Bluetooth service
     Loaded: loaded (/usr/lib/systemd/system/bluetooth.service; enabled; preset: enabled)
     Active: active (running) since Fri 2024-07-05 15:56:19 BST; 3h 23min ago
       Docs: man:bluetoothd(8)
   Main PID: 1156 (bluetoothd)
     Status: "Running"
      Tasks: 1 (limit: 18907)
     Memory: 3.4M (peak: 4.2M)
        CPU: 372ms
     CGroup: /system.slice/bluetooth.service
             &#9492;&#9472;1156 /usr/libexec/bluetooth/bluetoothd


Jul 05 19:12:34 makem-22 bluetoothd[1156]: bnep0 connected
Jul 05 19:12:34 makem-22 bluetoothd[1156]: bnep0 disconnected
Jul 05 19:17:36 makem-22 bluetoothd[1156]: bnep0 connected
Jul 05 19:17:36 makem-22 bluetoothd[1156]: bnep0 disconnected
Jul 05 19:17:36 makem-22 bluetoothd[1156]: bnep0 connected
Jul 05 19:17:36 makem-22 bluetoothd[1156]: bnep0 disconnected
Jul 05 19:17:36 makem-22 bluetoothd[1156]: bnep0 connected
Jul 05 19:17:36 makem-22 bluetoothd[1156]: bnep0 disconnected
Jul 05 19:17:36 makem-22 bluetoothd[1156]: bnep0 connected
Jul 05 19:17:36 makem-22 bluetoothd[1156]: bnep0 disconnected
makem@makem-22:~$ 

```

As you will see, there are constant connection attempts made between my new Samsung S24 mobile phone and my Xubuntu PC via Bluetooth.

The first notification announces a connection made and 1 second later a second notification announces a disconnection. This is repeated every few seconds. At time is it takes away the cursor focus.

I have been in touch with Samsung support and they have tried to cure the problem assuming it is a phone problem (I think it is), but they have failed to find anything other than the phone is paired with my PC.

I know over the years I have found that Ubuntu Bluetooth can be flaky. (Maybe my fault :frown: )

I have been asked if it could be the PC trying to connect to the phone. Can anyone assist with this?

---

### Post by currentshaft on 2024-07-10
Turn bluetooth off? Does it need to even be enabled? You never said what it is you're trying to do, only the errors you're getting.

---

### Post by #&amp;thj^% on 2024-07-10
Just my effort to help, my phone Moto7 power did the same as you show now.
I edited "/etc/bluetooth/input.conf" and removed the "#" from "UserspaceHID=true":
```
# Enable HID protocol handling in userspace input profile
# Defaults to true (Use UHID instead of kernel HIDP)
UserspaceHID=true
```
Then restarted bluetooth:
```
systemctl restart bluetooth
```
Some have still reported a session restart was needed.
```
bluetoothctl 
Agent registeredct to bluetoothd...[bluetooth]#         moto g(7) power
[moto g(7) power]# 

```

Good Luck

---

### Post by makem2 on 2024-07-11
> **1fallen said:**
> Just my effort to help, my phone Moto7 power did the same as you show now.
I edited "/etc/bluetooth/input.conf" and removed the "#" from "UserspaceHID=true":
```
# Enable HID protocol handling in userspace input profile
# Defaults to true (Use UHID instead of kernel HIDP)
UserspaceHID=true
```
Then restarted bluetooth:
```
systemctl restart bluetooth
```
Some have still reported a session restart was needed.
```
bluetoothctl 
Agent registeredct to bluetoothd...[bluetooth]#         moto g(7) power
[moto g(7) power]# 

```

Good Luck

I gave your first suggestion a try and I noticed that the WiFi icon started spinning. Hovering over it shows an attempt at making a mobile connection to my S24 Network. I then had the same two errors Iv'e had previously along with a repeat of both immediately.

A couple of minutes later the same thing occurred. That suggests to me that the system is not trying to make a connection to the phone per se, but the connection is being made to and disconnected from the S24 WiFi network. The phone remains connected to the 5G WiFi connection.

I will liaise with a Samsung tech. who has Uni knowledge of IT and understands Linux. We had dawn a blank so far but this new info may help. In the meantime, as I have never had this problem before I am wondering why I have an S24 WiFi network in the first place. But then I notice I can see my wife's phone network in the list of available networks. Maybe this is a new thing or is it something I have failed to notice which has always been the case?

My wife uses MS-Windows and she does not have this error, nor does my phone attempt connecting to her computer. I will check my Linux laptop to see if I can repeat the error there too.

---

### Post by makem2 on 2024-07-11
[COLOR=#000000][COLOR=#222222][FONT=Verdana]I found an 11 year old post which mentioned that WiFi connections could be edited by selecting the option Edit Connections in the WiFi drop down list[/FONT][/COLOR][/COLOR]

[https://askubuntu.com/questions/284018/is-there-a-way-to-make-ubuntu-forget-a-network-connection](https://askubuntu.com/questions/284018/is-there-a-way-to-make-ubuntu-forget-a-network-connection)

The Editor showed three Bluetooth not WiFi, network connections has been made but never used. I removed the three networks in the editor.

I rebooted the machine and checked the Editor again. I found the the Bluetooth connections I had removed had been replaced again. (Still showed never used).

I returned the [COLOR=#000000]*/etc/bluetooth/input.conf file *[/COLOR]to default settings.

I will mark this thread as solved because what I did solved my repeated connection annoying error. It does remind me of Windows, 'reboot to fix it' solutions.

[COLOR=#000000][COLOR=#222222][FONT=Verdana]EDIT: For completeness:

[/FONT][/COLOR][/COLOR]```
makem@makem-22:~$ sudo systemctl status bluetooth.service
[sudo] password for makem: 
&#9679; bluetooth.service - Bluetooth service
     Loaded: loaded (/usr/lib/systemd/system/bluetooth.service; enabled; preset: enabled)
     Active: active (running) since Thu 2024-07-11 18:08:15 BST; 40s ago
       Docs: man:bluetoothd(8)
   Main PID: 1442 (bluetoothd)
     Status: "Running"
      Tasks: 1 (limit: 18907)
     Memory: 3.1M (peak: 3.6M)
        CPU: 38ms
     CGroup: /system.slice/bluetooth.service
             &#9492;&#9472;1442 /usr/libexec/bluetooth/bluetoothd


Jul 11 18:08:25 makem-22 bluetoothd[1442]: Endpoint registered: sender=:1.55 path=/MediaEndpoint/A2DPSource/aptx_ll_1
Jul 11 18:08:25 makem-22 bluetoothd[1442]: Endpoint registered: sender=:1.55 path=/MediaEndpoint/A2DPSource/aptx_ll_0
Jul 11 18:08:25 makem-22 bluetoothd[1442]: Endpoint registered: sender=:1.55 path=/MediaEndpoint/A2DPSource/aptx_ll_duplex_1
Jul 11 18:08:25 makem-22 bluetoothd[1442]: Endpoint registered: sender=:1.55 path=/MediaEndpoint/A2DPSource/aptx_ll_duplex_0
Jul 11 18:08:25 makem-22 bluetoothd[1442]: Endpoint registered: sender=:1.55 path=/MediaEndpoint/A2DPSource/faststream
Jul 11 18:08:25 makem-22 bluetoothd[1442]: Endpoint registered: sender=:1.55 path=/MediaEndpoint/A2DPSource/faststream_duplex
Jul 11 18:08:25 makem-22 bluetoothd[1442]: Endpoint registered: sender=:1.55 path=/MediaEndpoint/A2DPSink/opus_05
Jul 11 18:08:25 makem-22 bluetoothd[1442]: Endpoint registered: sender=:1.55 path=/MediaEndpoint/A2DPSource/opus_05
Jul 11 18:08:25 makem-22 bluetoothd[1442]: Endpoint registered: sender=:1.55 path=/MediaEndpoint/A2DPSink/opus_05_duplex
Jul 11 18:08:25 makem-22 bluetoothd[1442]: Endpoint registered: sender=:1.55 path=/MediaEndpoint/A2DPSource/opus_05_duplex
makem@makem-22:~$

```
[COLOR=#000000][COLOR=#222222][FONT=Verdana]


[/FONT][/COLOR][/COLOR]

---

### Post by #&amp;thj^% on 2024-07-11
Interesting find makem2...I have to wonder how long this holds up though. :)

Thanks for posting your methods.

---

### Post by makem2 on 2024-07-16
> **1fallen said:**
> Interesting find makem2...I have to wonder how long this holds up though. :)

Thanks for posting your methods.

Still holding up :-)

---

### Post by #&amp;thj^% on 2024-07-16
I like a happy ending...:)
Thanks makem2

---

### Post by makem2 on 2024-08-09
Still working as normal :D

---

