---
title: "BSNL Huawei ETS 1201 Modem installation error in Ubuntu9.10"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by ravi89 on 2010-05-04
Hi Ubuntu geeks, I am N.Ravikumar from Tamilnadu. I am beginner in ubuntu, I had installed ver 9.10, I am using **BSNL WLL HUAWEI ETS 1201** to connect to internet. In windows it works perfectly at **COM3** port.I tried out my best but I cannot figure it out the reason for error, Finally I am posting my works here please help me:)

1. I had installed wvdial,just checked it by
```

developer@ubuntu:~$ which wvdial
/usr/bin/wvdial

```2.
```

developer@ubuntu:~$sudo wvdialconf
ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   

Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at http://open.nit.ca/wiki/?WvDial

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.

```3.
```

developer@ubuntu:~$ lsusb
 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 003 Device 002: ID 12d1:1010 Huawei Technologies Co., Ltd**. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```I figured out that my vendor Id -12d1 and Product Id-1010

4.I disconnect USB cable and give and give the following command:
```

 developer@ubuntu:~$ dmesg
[ 2691.910890] type=1503 audit(1273012930.537:22): operation="open" pid=2171 parent=1 profile="/usr/bin/evince" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/dev/bus/usb/001/001"
[ 2699.581202] type=1503 audit(1273012938.209:23): operation="open" pid=2177 parent=1 profile="/usr/bin/evince" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/dev/bus/usb/003/002"
[ 2717.175948] type=1503 audit(1273012955.800:24): operation="open" pid=2182 parent=1 profile="/usr/bin/evince" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/dev/bus/usb/004/001"
[ 2724.905871] type=1503 audit(1273012963.532:25): operation="open" pid=2186 parent=1 profile="/usr/bin/evince" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/dev/bus/usb/005/001"
[ 2766.804416] type=1503 audit(1273013005.429:26): operation="open" pid=2193 parent=1 profile="/usr/bin/evince" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/dev/ttyS0"
[ 3102.400049] usb 3-2: USB disconnect, address 2

```5. Now I connect the cable and give the command
```

developer@ubuntu:~$ dmesg
[ 2691.910890] type=1503 audit(1273012930.537:22): operation="open" pid=2171 parent=1 profile="/usr/bin/evince" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/dev/bus/usb/001/001"
[ 2699.581202] type=1503 audit(1273012938.209:23): operation="open" pid=2177 parent=1 profile="/usr/bin/evince" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/dev/bus/usb/003/002"
[ 2717.175948] type=1503 audit(1273012955.800:24): operation="open" pid=2182 parent=1 profile="/usr/bin/evince" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/dev/bus/usb/004/001"
[ 2724.905871] type=1503 audit(1273012963.532:25): operation="open" pid=2186 parent=1 profile="/usr/bin/evince" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/dev/bus/usb/005/001"
[ 2766.804416] type=1503 audit(1273013005.429:26): operation="open" pid=2193 parent=1 profile="/usr/bin/evince" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/dev/ttyS0"
[B][ 3102.400049] usb 3-2: USB disconnect, address 2
[ 3288.916025] usb 3-2: new full speed USB device using uhci_hcd and address 3
[ 3289.136108] usb 3-2: configuration #1 chosen from 1 choice[/B]

```6. Now i give 
```

developer@ubuntu:~$sudo gedit /etc/udev/rules.d/026_ti_usb_3410.rules
#TI USB 12d1
SUBSYSTEM==?usb_device? ACTION==?add? \
**SYSFS{idVendor}==?1010?,SYSFS{idProduct}==?12d1? \**
SYSFS{bNumConfigurations}==?5? \
SYSFS{bConfigurationValue}==?1? \
RUN+=?/bin/sh -c ?echo 2 > /sys%p/device/bConfigurationValue??

```7.Editing wvdial configuration
```

developer@ubuntu:~$sudo gedit /etc/wvdial.conf
[Dialer bsnl]
Modem = /dev/ttyUSB0
Baud = 230400
Phone = #777
Init1 = ATZ
Stupid Mode = 1
Dial Command = ATDT
Username = MY_USER_NAME
Password = MY_PASSWORD
PPPD Options = lock noauth refuse-eap refuse-chap refuse-mschap nobsdcomp nodeflate

```8.I think the error Ignoring.... is due to space but i felt can be ignored.can u guess why this error occurs an how to solve it?. 
```

[B]developer@ubuntu:~$wvdial bsnl
--> Ignoring malformed input line: "nobsdcomp nodeflate"
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory[/B]

```[B]I think its due to ttyUSB0 may be something override it but I dont know which one.

[/B]9.
```

developer@ubuntu:~$ dmesg | grep -e "modem" -e "tty"
[    0.001111] console [tty0] enabled
[    0.840752] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.841213] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

```10.
```

developer@ubuntu:~$ sudo ln -s ttySHSF0 /dev/modem

```11.
```

developer@ubuntu:~$ ls -l /dev/modem
lrwxrwxrwx 1 root root 8 2010-05-04 19:15 /dev/modem -> ttySHSF0

```12.
```

developer@ubuntu:~$ ls /dev | grep tty
tty
tty0
tty1
tty10
tty11
tty12
tty13
tty14
tty15
tty16
tty17
tty18
tty19
tty2
tty20
tty21
tty22
tty23
tty24
tty25
tty26
tty27
tty28
tty29
tty3
tty30
tty31
tty32
tty33
tty34
tty35
tty36
tty37
tty38
tty39
tty4
tty40
tty41
tty42
tty43
tty44
tty45
tty46
tty47
tty48
tty49
tty5
tty50
tty51
tty52
tty53
tty54
tty55
tty56
tty57
tty58
tty59
tty6
tty60
tty61
tty62
tty63
tty7
tty8
tty9
ttyS0
ttyS1
ttyS2
ttyS3

```I dont exactly know what the commands for ,can u guess the solution to my problem! I am anxiously waiting for the solution:)

---

### Post by madjr on 2010-05-04
what type of modem is this?

i found this

[http://www.linuxquestions.org/questions/linux-newbie-8/connect-huawei-usb-modem-with-linux-698050/](http://www.linuxquestions.org/questions/linux-newbie-8/connect-huawei-usb-modem-with-linux-698050/)

---

### Post by ravi89 on 2010-05-04
I had solved the problem finally, Link to my blog

[http://mr-greens.blogspot.com/2010/05/bsnl-huawei-ets-1201-modem-installation.html](http://mr-greens.blogspot.com/2010/05/bsnl-huawei-ets-1201-modem-installation.html)

---

### Post by spiritumsantorini on 2010-05-04
:p Thanks!!! Thats works for me!

---

