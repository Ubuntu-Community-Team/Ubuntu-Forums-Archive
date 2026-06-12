---
title: "Bluetooth serial problem"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by outleradam on 2010-06-06
I am having problems browsing a bluetooth device.
 
```
adam@adam-netbook:~$ hcitool scan
Scanning ...
    00:07:61:xxxxxx    adam-desktop-0
    00:26:BB:xxxxxx   Adam Outler&#8217;s iPhone
    00:0D:18:xxxxxx  CBT
adam@adam-netbook:~$ sudo hcitool cc 00:0D:18:xxxxxxx && sudo hcitool auth 00:0D:18:xxxxxxadam@adam-netbook:~$ sudo sdptool browse 00:0D:18:xxxxxxBrowsing 00:0D:18:xxxxxx ...
adam@adam-netbook:~$ sudo hcitool cc 00:0D:18:xxxxxx && sudo hcitool auth 00:0D:18:xxxxxxadam@adam-netbook:~$ sudo sdptool browse 00:0D:18:xxxxxxBrowsing 00:0D:18:xxxxxx ...
adam@adam-netbook:~$ sudo hcitool cc 00:0D:18:xxxxxx && sudo hcitool auth 00:0D:18:xxxxxx && sudo sdptool browse 00:0D:18:xxxxxxBrowsing 00:0D:18:xxxxxx...
adam@adam-netbook:~$ sudo rfcomm connect 0
Connected /dev/rfcomm0 to 00:0D:18:xxxxxx on channel 1
Press CTRL-C for hangup
ATZ 
AT Z
^CDisconnected
adam@adam-netbook:~$ 
 

```This device is a bluetooth ELM 327 device. It should register as a serial port.

---

### Post by outleradam on 2010-06-06
This is something... I got a few bits of data from it.
I started the rfcomm connect 0 and opened another terminal

```
adam@adam-netbook:~$ cat /dev/rfcomm0
>^C327 v1.3a

```

It is a ELM327 v1.3a device.

Now, why won't it communicate properly?

---

