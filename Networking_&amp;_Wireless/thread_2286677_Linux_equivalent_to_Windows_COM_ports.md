---
title: "Linux equivalent to Windows COM ports"
date: 2015-07-13
forum: Networking &amp; Wireless
---

### Post by lzeimet on 2015-07-13
Hello all,

Ive been doing a lot of Networking and configuring of switches and routers on PuTTy using windows.  I recently purchased a rack with some switches and routers to get more practice in at home.  Only problem is....I cannot seem to figure out / find any help in findoing out how to tell What 'COM' port my usb2serial cable is connected to on my linux desktop that I run at home.   


Looking for any help

Thanks In advance


Lucas

---

### Post by tgalati4 on 2015-07-13
Welcome to the forums.

Open a terminal:

```
man setserial
```

> tgalati4@Mint17 /dev $ setserial -a /dev/ttyS0
/dev/ttyS0, Line 0, UART: unknown, Port: 0x03f8, IRQ: 4
	Baud_base: 115200, close_delay: 50, divisor: 0
	closing_wait: 3000
	Flags: spd_normal skip_test


---

### Post by Kai_Pirttimki on 2015-07-14
Do you mean the name of the port? Probably /dev/ttyUSB0. To find out for sure, disconnect your usb2serial cable from computer and type "tail -f /var/log/syslog" and connect your cable again. You should see something like "USB Serial device converter now attached to ttyUSB0".

---

### Post by lzeimet on 2015-07-18
this is my output

coolbreeze@coolbreeze-MS-7721:~$ man setserial
No manual entry for setserial

---

### Post by lzeimet on 2015-07-18
-Kai-

I did what you said, and it told me it was ttyUSB0.  However when I open the connection it tells me immediately that its UNABLE TO OPEN SERIAL PORT


when I plug the usb back in this is what it tells me

Jul 18 11:30:24 coolbreeze-MS-7721 kernel: [137789.026235] usb 1-1.1: new full-speed USB device number 7 using ehci-pci
Jul 18 11:30:24 coolbreeze-MS-7721 kernel: [137789.119079] usb 1-1.1: New USB device found, idVendor=067b, idProduct=2303
Jul 18 11:30:24 coolbreeze-MS-7721 kernel: [137789.119087] usb 1-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Jul 18 11:30:24 coolbreeze-MS-7721 kernel: [137789.119092] usb 1-1.1: Product: USB-Serial Controller D
Jul 18 11:30:24 coolbreeze-MS-7721 kernel: [137789.119097] usb 1-1.1: Manufacturer: Prolific Technology Inc. 
Jul 18 11:30:24 coolbreeze-MS-7721 kernel: [137789.119562] pl2303 1-1.1:1.0: pl2303 converter detected
Jul 18 11:30:24 coolbreeze-MS-7721 kernel: [137789.121311] usb 1-1.1: pl2303 converter now attached to ttyUSB0
Jul 18 11:30:24 coolbreeze-MS-7721 mtp-probe: checking bus 1, device 7: "/sys/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1.1"
Jul 18 11:30:24 coolbreeze-MS-7721 mtp-probe: bus: 1, device: 7 was not an MTP device

---

### Post by MGrowl on 2015-07-19
I've had the same problem when I switched from Windows. Putty, IMO, is much easier on windows if you use it for configuring switches. Try downloading minicom for Ubuntu, that worked for me. I couldn't get connected using putty with a USB2Serial, so I googled some alternatives and Minicom seems to be the easiest. I don't have extensive knowledge using it but it should be easy enough to learn. 

BTW, if anyone out there uses putty to connect to switches on Ubuntu. What do you put in the fields? How do you find out what COM to input in the fields?

---

### Post by Lars Noodén on 2015-07-19
If you look at the device, 

```

ls -lh  /dev/ttyUSB0

```

it may show that it is in a particular group, such as "dialout".  If so, your user needs to be a member of that group in order to use the serial device.

---

### Post by MGrowl on 2015-07-20
@Lars that worked, thanks. I tried it with putty, just needed to chown the /dev/ttyUSB0.

---

### Post by tgalati4 on 2015-07-20
You can install *setserial*.  Open a terminal:

```
sudo apt-get install setserial
man setserial
setserial -a /dev/ttyS0
```

---

### Post by MGrowl on 2015-07-22
@lars I just started it up and when I checked its permissions, it was back to "root:dialout". Is there any way to make the chown permanent?

---

### Post by Lars Noodén on 2015-07-22
Well, I had actually meant that you would add yourself to the dialout group.  That's the easy way.  

If you really want to change the group of the device when it gets plugged in, you'll have to work with configuring the infamous [udev](http://manpages.ubuntu.com/manpages/trusty/en/man7/udev.7.html).  Just from skimming the topic, it looks like you might add a custom file to add your own udev rules the place to add that file would be in  **/etc/udev/rules.d/** The examples to glean configurations from would be /lib/udev/rules.d/50-udev-default. and /lib/udev/rules.d/60-persistent-serial.rules

---

### Post by MGrowl on 2015-07-22
Oh, OK. I'll try adding myself to the group. I didn't think of that. Much easier. I just thought that after ```
sudo chown currentuser:currentuser /dev/ttyUSB0
``` that it would stick after unplugging the cable and putting it back in. My mistake. Thanks for pointing me in the right direction @lars. Looks like some mighty reading in them links. Thanks again for the help, appreciate it.

---

### Post by MGrowl on 2015-07-22
Did this ```
sudo usermod -a -G dialout userName
``` solution found at: [http://askubuntu.com/questions/79565/add-user-to-existing-group](http://askubuntu.com/questions/79565/add-user-to-existing-group) (not sure if it's okay to post links, please remove if not allowed)

Much easier than having to delve into udev. BTW, I never knew of that command before.

---

