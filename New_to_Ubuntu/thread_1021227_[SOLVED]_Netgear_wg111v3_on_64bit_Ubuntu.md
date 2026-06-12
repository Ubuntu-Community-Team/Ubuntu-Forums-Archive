---
title: "[SOLVED] Netgear wg111v3 on 64bit Ubuntu"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by Tony Flury on 2008-12-25
I am running Hardy Heron on an HP pavillion Dv6000 laptop.

The internal Broadcom wireless card seems to have died (again), and i am trying to use a Netgear wG111v3 Wifi USB Dongle (which i know works on Windows XP).

What I have done so far :

I know i have 64 bit ubuntu : 
```

tony@laptop:~$ uname -mr
2.6.24-18-generic x86_64

```

I also know that this rules out an ndiswrapper solution.

I know that the dongle is recognised on the USB port : 

```

tony@laptop:~$ lsusb
Bus 002 Device 004: ID 0c45:62c0 Microdia 
Bus 002 Device 002: ID 0846:4260 NetGear, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 105: ID 04fc:0015 Sunplus Technology Co., Ltd 
Bus 001 Device 003: ID 03f0:171d Hewlett-Packard 
Bus 001 Device 001: ID 0000:0000  

```

```

lshw -C network
 Produces no output

```

but
```

lshw -C generic
....
  *-usb:0 UNCLAIMED
       description: Generic USB device
       product: NETGEAR WG111v3
       vendor: Manufacturer_NETGEAR
       physical id: 1
       bus info: usb@2:1
       version: 2.00
       serial: 001E2AB6719B
       capabilities: usb-2.00
       configuration: maxpower=500mA speed=480.0MB/s
....

```

I know i need a 64 bit driver for this (and I have followed this thread [http://ubuntuforums.org/showthread.php?t=848305](http://ubuntuforums.org/showthread.php?t=848305) as you can see - but with no success - i am guessing things might have moved on) - can someone help ?

The dongle does work on 8.10 - although not completely - but that is not a driver issues.

---

### Post by sjnims on 2008-12-26
Some things that come to mind w/out diving too deep into this as I'm at work, LOL...

Try bringing the wireless network up:

```
sudo ifconfig wlan0 up
```

[LIST][*]Substitute your wireless interface name for "wlan0"[/LIST]

If that works and no errors are reported then try setting the wireless network:

```
sudo iwconfig wlan0 essid "linksys"
```

[LIST]
[*]Again, replace "wlan0" with you network interface name
[*]Replace "linksys" with the name of the wireless network you want to join
[/LIST]

If that works then you should be able to start the DHCP daemon and then you'll be set:

```
sudo dhcpcd wlan0
```

Try that and let's see what happens...

Steve

---

### Post by Tony Flury on 2008-12-26
The problem here is that the i have no wireless interface : 

```

tony@laptop:~$ iwconfig
lo        no wireless extensions.

eth2      no wireless extensions.

```

So i have nothing to start up.

The problem - i think is that Ubuntu recognises the device - i.e. it can see i have attached something, but it does not recognise what it is - or what to do with it.

---

### Post by sjnims on 2008-12-26
Sounds like the module hasn't been loaded.

Don't know if this is local to Arch or not but give it a try:

```
hwdetect --show-net
```

then load the correct module...

```
modprobe <name_of_module>
```

---

### Post by Tony Flury on 2008-12-26
looks like i am missing something 

```
tony@laptop:~$ hwdetect --show-net
bash: hwdetect: command not found

```

Just found out something else - which is probably/possibly relevant : in the System -> Administration Hardware Drivers application, there is a Linux driver for the Realtek8187 listed as enabled but **not in use**. I have tried disabling and re-enabling but to no effect. Does that help ?

---

### Post by Tony Flury on 2008-12-27
Any further help on thsi would be appreciated - thanks :-)

---

### Post by Tony Flury on 2009-01-02
Can anyone help ? I have survived christmas using a wired conection - but having a cable trailing across the house is not a permanent solution.

---

### Post by Tony Flury on 2009-01-06
going to mark this one as solved - but basically - for posterity reasons - I gave up.

Concluded that 64 bit support on Hardy heron was almost non-existant - so i installed 32bit Hardy over my 64 bit install - at least I can now install the drivers and have detected a network - alhough i can't connect - seperate issues.

---

