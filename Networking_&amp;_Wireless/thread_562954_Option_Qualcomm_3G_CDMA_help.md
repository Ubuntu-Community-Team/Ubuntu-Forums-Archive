---
title: "Option Qualcomm 3G CDMA help"
date: 2007-09-29
forum: Networking &amp; Wireless
---

### Post by stiggan on 2007-09-29
Hi, I'm new to posting for help in forums since I usually just seek them for help, but I'll try to post as much as I know so far here.

My modem is a Option modem, USB dongle style... it's supposed to handle Super 3G which means speeds up to 7.2 Mbit. At the back of it I can read the following in the following order, tho I'm not writing everything down. (I can misspell 0 and O somewhere since it seems to be the same character for it as it's written at the back of the dongle)

QUALCOMM 3G CDMA

ICON 7.2 EL
Model: GI0205
FCC ID NCM0GI0205
SNR: Z2377669RB
IMEI: 35623701022493


I'm using Ubuntu Feisty 7.04 (x64).

Thanks in before for your help. I tried to find help for this modem, but it seems others doesn't use the USB dongle, but the PCMCIA variant.

Oh, and also, as many other dongles from other brands I red about, this one do register itself as a storage drive first upon connection, and then changing type. Shortly after connection the modem starts blinking really quick, which means error.

dmesg shows this:

[16556.366341] usb 1-1: new full speed USB device using ohci_hcd and address 13
[16556.575330] usb 1-1: configuration #1 chosen from 1 choice
[16556.579227] scsi8 : SCSI emulation for USB Mass Storage devices
[16556.579420] usb-storage: device found at 13
[16556.579422] usb-storage: waiting for device to settle before scanning
[16559.656727] usb-storage: device scan complete
[16559.663720] scsi 8:0:0:0: CD-ROM            GT       HSDPA Modem      3.00 PQ: 0 ANSI: 2
[16559.746659] sr0: scsi-1 drive
[16559.746724] sr 8:0:0:0: Attached scsi CD-ROM sr0
[16559.746765] sr 8:0:0:0: Attached scsi generic sg1 type 5


lsusb show this upon connecting the modem:

Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 016: ID 05c6:1000 Qualcomm, Inc. 
Bus 001 Device 001: ID 0000:0000

a few seconds later lsusb goes back to showing this:

Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

Thanks in before for your help on this matter!

---

### Post by jauhari on 2007-10-24
> **stiggan said:**
> Hi, I'm new to posting for help in forums since I usually just seek them for help, but I'll try to post as much as I know so far here.

My modem is a Option modem, USB dongle style... it's supposed to handle Super 3G which means speeds up to 7.2 Mbit. At the back of it I can read the following in the following order, tho I'm not writing everything down. (I can misspell 0 and O somewhere since it seems to be the same character for it as it's written at the back of the dongle)

QUALCOMM 3G CDMA

ICON 7.2 EL
Model: GI0205
FCC ID NCM0GI0205
SNR: Z2377669RB
IMEI: 35623701022493


I'm using Ubuntu Feisty 7.04 (x64).

Thanks in before for your help. I tried to find help for this modem, but it seems others doesn't use the USB dongle, but the PCMCIA variant.

Oh, and also, as many other dongles from other brands I red about, this one do register itself as a storage drive first upon connection, and then changing type. Shortly after connection the modem starts blinking really quick, which means error.

dmesg shows this:

[16556.366341] usb 1-1: new full speed USB device using ohci_hcd and address 13
[16556.575330] usb 1-1: configuration #1 chosen from 1 choice
[16556.579227] scsi8 : SCSI emulation for USB Mass Storage devices
[16556.579420] usb-storage: device found at 13
[16556.579422] usb-storage: waiting for device to settle before scanning
[16559.656727] usb-storage: device scan complete
[16559.663720] scsi 8:0:0:0: CD-ROM            GT       HSDPA Modem      3.00 PQ: 0 ANSI: 2
[16559.746659] sr0: scsi-1 drive
[16559.746724] sr 8:0:0:0: Attached scsi CD-ROM sr0
[16559.746765] sr 8:0:0:0: Attached scsi generic sg1 type 5


lsusb show this upon connecting the modem:

Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 016: ID 05c6:1000 Qualcomm, Inc. 
Bus 001 Device 001: ID 0000:0000

a few seconds later lsusb goes back to showing this:

Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

Thanks in before for your help on this matter!
Anybody can solve this problem? I have some question too.

Please help..
Thanks

---

### Post by sweRascal on 2007-10-25
I got my Option Icon 7.2 USB Dongle modem running yesterday on Gutsy, I just followed the following tutorial.
And use kppp since gnome-ppp seems buggy right now.
Worked like a charm.

> Hi try this:

download icon_switch.c [http://www.frederick-reid.com/files/icon_switch.c](http://www.frederick-reid.com/files/icon_switch.c)
change the product id in the file from 6600 to 6901
Compile (note that you need to have libusb installed):
Code:
cc -l usb -o icon_switch icon_switch.c

Move the file to /usr/sbin/

Edit /etc/udev/rules.d/10-local.rules (add it if it doesn't exists) and add the following two rules:
Code:

BUS=="usb", SYSFS{idProduct}=="1000", SYSFS{idVendor}=="05c6", RUN+="/usr/sbin/icon_switch"
BUS=="usb", SYSFS{idProduct}=="6901", SYSFS{idVendor}=="0af0", RUN+="/sbin/modprobe usbserial vendor=0x0af0 produc
t=0x6901"


The simplest way is to reboot your computer (or reload the rules into udev and restart it). Do not have the iCON plugged in while booting,

When you computer is up and running again, plugg the iCON in.
Now list you USB devices:
Code:
# lsusb

Within 30 seconds you should have a device presenting it self as "Option"
Code:

Bus xxx Device xxx: ID 0af0:6901 Option


Now you should have three new nodes in /dev/
Code:
 ls /dev/ttyUSB*
/dev/ttyUSB0  /dev/ttyUSB1  /dev/ttyUSB2


Now your iCON should be working. I use kppp to connect. the only important things in kppp is the following:
The modem pointing at /dev/ttyUSB0 (could perhaps be 1 or 2 as well don't know the difference)
I use RTS/CTS as flowcontrol.
Deselect "wait for dial tone"
Add the connection, dial *99# and use PAP as authentication
Username and password should not matter.

Hope this helps.

Good luck!

---

### Post by jauhari on 2007-10-25
Running as ROOT? 

why when I triad run this command 

```
cc -l usb -o icon_switch icon_switch.c
```

Got this error
```

icon_switch.c:44:19: error: stdio.h: No such file or directory
icon_switch.c:45:20: error: stdlib.h: No such file or directory
icon_switch.c:46:20: error: string.h: No such file or directory
icon_switch.c:47:20: error: assert.h: No such file or directory
icon_switch.c:48:20: error: signal.h: No such file or directory
icon_switch.c:49:19: error: ctype.h: No such file or directory
icon_switch.c:50:17: error: usb.h: No such file or directory
icon_switch.c: In function ‘release_usb_device’:
icon_switch.c:56: warning: incompatible implicit declaration of built-in function ‘printf’
icon_switch.c:64: warning: incompatible implicit declaration of built-in function ‘exit’
icon_switch.c: In function ‘find_device’:
icon_switch.c:70: error: ‘NULL’ undeclared (first use in this function)
icon_switch.c:70: error: (Each undeclared identifier is reported only once
icon_switch.c:70: error: for each function it appears in.)
icon_switch.c:72: warning: incompatible implicit declaration of built-in function ‘printf’
icon_switch.c:73: warning: assignment makes pointer from integer without a cast
icon_switch.c:73: error: dereferencing pointer to incomplete type
icon_switch.c:76: error: dereferencing pointer to incomplete type
icon_switch.c:76: error: dereferencing pointer to incomplete type
icon_switch.c:77: error: dereferencing pointer to incomplete type
icon_switch.c:77: error: dereferencing pointer to incomplete type
icon_switch.c:80: error: dereferencing pointer to incomplete type
icon_switch.c:80: error: dereferencing pointer to incomplete type
icon_switch.c:82: warning: incompatible implicit declaration of built-in function ‘exit’
icon_switch.c:90: warning: incompatible implicit declaration of built-in function ‘exit’
icon_switch.c: In function ‘main’:
icon_switch.c:103: warning: incompatible implicit declaration of built-in function ‘printf’
icon_switch.c:114: warning: assignment makes pointer from integer without a cast
icon_switch.c:117: error: ‘SIGTERM’ undeclared (first use in this function)
icon_switch.c:130: warning: incompatible implicit declaration of built-in function ‘exit’
icon_switch.c:135: warning: incompatible implicit declaration of built-in function ‘exit’
icon_switch.c:142: warning: incompatible implicit declaration of built-in function ‘memcpy’
```

What's wrong? and what's should I do?

---

### Post by sweRascal on 2007-10-25
I did the compile as root but after that I ran as a standard user.
I forgot to mention that you must have usblib dev installed.
Try that and get back to me.
What version are you on? Feisty or Gutsy?

---

### Post by jauhari on 2007-10-25
I use Gutsy and How to check that usblib installed or not?

---

### Post by sweRascal on 2007-10-25
Easiest way is to just start up Synaptic and do a search for usblib and then find the usblib dev and install it. I am at work now otherwise I would love to provide more detailed information.
Lemme know if you work it out otherwise I'll try to be more specific when I get home.

---

### Post by jauhari on 2007-10-30
I was installed USBLIB but still get this error,
I was run the command with SUDO too. This the error I got it

```

icon_switch.c:44:19: error: stdio.h: No such file or directory
icon_switch.c:45:20: error: stdlib.h: No such file or directory
icon_switch.c:46:20: error: string.h: No such file or directory
icon_switch.c:47:20: error: assert.h: No such file or directory
icon_switch.c:48:20: error: signal.h: No such file or directory
icon_switch.c:49:19: error: ctype.h: No such file or directory
icon_switch.c:50:17: error: usb.h: No such file or directory
icon_switch.c: In function ‘release_usb_device’:
icon_switch.c:56: warning: incompatible implicit declaration of built-in function ‘printf’
icon_switch.c:64: warning: incompatible implicit declaration of built-in function ‘exit’
icon_switch.c: In function ‘find_device’:
icon_switch.c:70: error: ‘NULL’ undeclared (first use in this function)
icon_switch.c:70: error: (Each undeclared identifier is reported only once
icon_switch.c:70: error: for each function it appears in.)
icon_switch.c:72: warning: incompatible implicit declaration of built-in function ‘printf’
icon_switch.c:73: warning: assignment makes pointer from integer without a cast
icon_switch.c:73: error: dereferencing pointer to incomplete type
icon_switch.c:76: error: dereferencing pointer to incomplete type
icon_switch.c:76: error: dereferencing pointer to incomplete type
icon_switch.c:77: error: dereferencing pointer to incomplete type
icon_switch.c:77: error: dereferencing pointer to incomplete type
icon_switch.c:80: error: dereferencing pointer to incomplete type
icon_switch.c:80: error: dereferencing pointer to incomplete type
icon_switch.c:82: warning: incompatible implicit declaration of built-in function ‘exit’
icon_switch.c:90: warning: incompatible implicit declaration of built-in function ‘exit’
icon_switch.c: In function ‘main’:
icon_switch.c:103: warning: incompatible implicit declaration of built-in function ‘printf’
icon_switch.c:114: warning: assignment makes pointer from integer without a cast
icon_switch.c:117: error: ‘SIGTERM’ undeclared (first use in this function)
icon_switch.c:130: warning: incompatible implicit declaration of built-in function ‘exit’
icon_switch.c:135: warning: incompatible implicit declaration of built-in function ‘exit’
icon_switch.c:142: warning: incompatible implicit declaration of built-in function ‘memcpy’

```

What's wrong?
Please help me.

---

### Post by sweRascal on 2007-10-30
Have you also installed the buiild-essentials?

---

### Post by sweRascal on 2007-10-30
I can see if I can send you my compiled version of the file if you want.
Send me a pm where you want me to send it.

---

### Post by goldenshale on 2008-03-20
If you read the source code for that icon_switch utility you will see that he recommends you use a new tool, which is located here:

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

These usb dongles act like mass-storage devices by default so the host machine can automatically copy and install the built-in driver.  Of course they don't include linux drivers, but luckily it's just a usb serial device so we don't need one, except to switch the dongle into modem mode.  That's what this utility does.  Download from the page, and edit the config file so your device is setup correctly.

Internet everywhere is going to be fun.  Now if only I had good computing power without having to lug around my damn laptop...

---

