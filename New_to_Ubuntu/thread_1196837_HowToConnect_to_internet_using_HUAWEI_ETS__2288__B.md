---
title: "HowTo:Connect to internet using HUAWEI ETS  2288  BSNL WLL  Wireless Fixed Internet"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by rraj.be on 2009-06-25
BSNL WLL is a Dial up- Fixed wireless Internet connection available in INDIA, provided by BSNL. But we have a problem in configuring Internet connection using these devices in Linux Distros. Try the following to connect to Internet in ubuntu using HUAWEI ETS 2288 phone.

1)    Plug in the modem.

Type the following in terminal


```
sudo wvdialconf
```

2) 	If you are unable to detect your modem, Then Continue.
Else, Go to step 7.

3) 	
  Unplug your modem.
  Type the following in terminal

```
sudo dmesg -c
```

      Type in your password.

	Now plug in you usb cable connected to Phone.

	
4)	Now type

	```
lsusb
```

	If it display's like

> raj@raj-TheLinuxHacker:~/Documents$ lsusb

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 003 Device 003: ID 0451:3410 Texas Instruments, Inc. TUSB3410 Microcontroller

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

raj@raj-TheLinuxHacker:~/Documents$ 


Then, it indicates your device is connected properly.
Else unplug and reconnect your device properly.
Here,the Fourth indicates your Device.

In the above output, we could see two numbers '0451' and '3410',in 4th line and these are product ID and vendor ID respectively.

5)	Now type 

```
dmesg |grep usb
```

It will display some lines like

> raj@raj-TheLinuxHacker:~/Documents$ dmesg 
| grep usb
[  728.020519] usb 3-1: new full speed USB device using uhci_hcd and address 5

[  728.242380] usb 3-1: configuration #1 chosen from 2 choices

[  728.245328] ti_usb_3410_5052 3-1:1.0: TI USB 3410 1 port adapter converter detected

[  728.245346] ti_usb_3410_5052: probe of 3-1:1.0 failed with error -5

[  728.255572] ti_usb_3410_5052 3-1:2.0: TI USB 3410 1 port adapter converter detected

[  728.255676] usb 3-1: TI USB 3410 1 port adapter converter now attached to ttyUSB0

raj@raj-TheLinuxHacker:~/Documents$ 



These lines indicates that your device is available but not configured.


6) 	Now we have to define few rules for new device. To do that type the 	following in terminal

```
sudo gedit /etc/udev/rules.d/026_ti_usb_3410.rules
```

It will open a new text editor and in that paste the following content exactly.


> 
#TI USB 3410
SUBSYSTEM==?usb_device? ACTION==?add? \
SYSFS{idVendor}==?0451?,SYSFS{idProduct}==?3410? \
SYSFS{bNumConfigurations}==?5? \
SYSFS{bConfigurationValue}==?1? \
RUN+=?/bin/sh -c ?echo 2 > /sys%p/device/bConfigurationValue??


Remember to replace your product ID and Vendor ID correctly in the above rules.
Save the file and close it.


7) 	Now type the following in the terminal.

```
sudo gedit /etc/wvdial.conf
```

It opens another text file.

> [Dialer bsnl]
Modem = /dev/ttyUSB0
Baud = 230400
Phone = #777
Init1 = ATZ
Stupid Mode = 1
Dial Command = ATDT
Username = Add_your_username_here
Password = Add_your_password_here
PPPD Options = lock noauth refuse-eap refuse-chap refuse-mschap nobsdcomp nodeflate


Save and close the file.


8)	Type  the following in terminal.

```
sudo wvdial bsnl 
```

This may display like,

> raj@raj-TheLinuxHacker:~$ sudo wvdial
 bsnl
[sudo] password for raj: 

--> WvDial: Internet dialer version 1.60

--> Initializing modem.

--> Sending: ATZ

OK

--> Modem initialized.

--> Sending: ATDT#777

--> Waiting for carrier.

ATDT#777

CONNECT

--> Carrier detected.  Starting PPP immediately.

--> Starting pppd at Wed Jun 24 20:38:54 2009

--> Pid of pppd: 4530

--> Using interface ppp0

--> pppd: (&#65533;&#65533;[08]

--> pppd: (&#65533;&#65533;[08]

--> pppd: (&#65533;&#65533;[08]

--> pppd: (&#65533;&#65533;[08]

--> pppd: (&#65533;&#65533;[08]

--> local  IP address 10.2.15.90

--> pppd: (&#65533;&#65533;[08]

--> remote IP address 192.168.52.12

--> pppd: (&#65533;&#65533;[08]

--> primary   DNS address 218.248.240.181

--> pppd: (&#65533;&#65533;[08]

--> secondary DNS address 208.67.220.220

--> pppd: (&#65533;&#65533;[08]


9)	Note the two DNS address and type the following in a new terminal.

```
sudo gedit etc/resolv.conf
```

Type the adress in the file as following and close it after saving it.

> nameserver 218.248.240.181

nameserver 208.67.220.220

10)	Now unplug the device and re-plug in the device and reboot your computer.

11)	After reboot, In terminal, type

```
sudo wvdial bsnl
```

Now your Internet connection will be connected.

Hope it helps.

---

