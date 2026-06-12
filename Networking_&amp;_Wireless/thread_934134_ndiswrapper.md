---
title: "ndiswrapper"
date: 2008-09-30
forum: Networking &amp; Wireless
---

### Post by iraqb on 2008-09-30
hi
after install windows driev i reseve this 

see the img 

what i must do to start use wlan0 ? and how make i start with start up ?

---

### Post by nixscripter on 2008-09-30
It says "hardware not detected". What is your wireless card? Post the output of these two commands: ```
lshw -C network
``````
ndiswrapper -l
```

---

### Post by iraqb on 2008-09-30
Hello,
im use Engenius Senao EUB-362 200mW USB adapter 

[IMG]http://www.keenansystems.com/nub362ext.jpg[/IMG]

the first comint give me

> rody@rody-laptop:~$ sudo lshw -C network
[sudo] password for rody: 
  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:87:ed:f7
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:19:7e:b7:57:a2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
rody@rody-laptop:~$ 



and the second

> net5523 : driver installed


now what ?

---

### Post by iraqb on 2008-09-30
help

---

### Post by superprash2003 on 2008-09-30
try this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by iraqb on 2008-09-30
> **superprash2003 said:**
> try this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

please my english is not good
i need explain

---

### Post by nixscripter on 2008-09-30
It looks like something besides ndiswrapper is capturing the device before it is.

Add this line to the file **/etc/modprobe.d/blacklist**: ```
blacklist ssb
```

And add this line so your ethernet still works to **/etc/modules**: ```
b44
```

---

### Post by iraqb on 2008-09-30
hi
im use this /etc/modprobe.d/blacklist but i get this error

> bash: /etc/modprobe.d/blacklist: Permission denied

and if i use sudo get this error

> bash: /etc/modprobe.d/blacklist: coment not found

---

### Post by nixscripter on 2008-10-01
I meant edit the file, using a program like gedit. Don't run it.

---

### Post by iraqb on 2008-10-01
done

now what i must do ?

---

### Post by nixscripter on 2008-10-01
Try rebooting. Make sure your ethernet connection works. If it doesn't, undo those steps and we can try something else.

If the ethernet does work, hopefully ndiswrapper will work as well.

---

### Post by iraqb on 2008-10-01
im try but it is not work
i think the ndiswrapper dod not support my internet cart or wlan0

what you suggest ?
try use madwifi?

---

### Post by Ayuthia on 2008-10-01
> **iraqb said:**
> im try but it is not work
i think the ndiswrapper dod not support my internet cart or wlan0

what you suggest ?
try use madwifi?

Can you post the results of lsusb?  Do you also have a wireless card in your computer?  The picture that you provided shows that it is a USB device, but the information that you provided in lshw -C network seems to show that you have a wireless card in the computer.  Is this correct?

---

### Post by iraqb on 2008-10-02
results of lsusb is

> Bus 005 Device 002: ID 0cf3:0002 Atheros Communications, Inc 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 15ca:00c3  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

and i use USB device in the pic becouse the wireless card in the computer did not work with internet in my contry so i use the usb

---

### Post by Ayuthia on 2008-10-03
Where did you find your windows driver for ndiswrapper?  Also, are you using 32 or 64 bit?  If you are not sure about the 32/64 bit, please post the results of uname -a from the Terminal.

I am not able to find too much about your your USB device.  All I can tell you is that it is an Atheros card and probably needs to use ndiswrapper.  As for madwifi, the site says that they do not support USB devices.

---

### Post by iraqb on 2008-10-03
Hello,

i found it in the cd m use and i use 32 bit

it this mean i can not use internet on linux ?

---

### Post by executor on 2008-10-03
i think you mabye have the wrong .sys .inf fil installed?

this did happen to me. i used the bcm inf for a rt2500 card did not work:) but it, did say, driver installed

---

### Post by Ayuthia on 2008-10-03
> **iraqb said:**
> Hello,

i found it in the cd m use and i use 32 bit

it this mean i can not use internet on linux ?

It does not mean that, but like executor says, it just means that you have not found the right driver for it.

By the way, why does the Broadcom card not work in your country?  I would think that the card should work.

---

### Post by iraqb on 2008-10-03
the internet in my contry is very Stupid and did not work with any card Except  this usb

i think like yoy say i have problem with install

i will try again 

thanks [COLOR="Red"]Ayuthia[/COLOR] for your help :)

thanks [COLOR="red"]executor[/COLOR] for youe help too :)


have a nice day

---

