---
title: "Setting up wireless via ndswrapper problem"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by tadcan on 2009-03-06
I am following this guide

[http://www.cyberciti.biz/faq/marvell-88w8335-chipset-netgear-wg311-pcicard-driver/](http://www.cyberciti.biz/faq/marvell-88w8335-chipset-netgear-wg311-pcicard-driver/)

I am currently stuck on step 5

iwconfig reads

```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

when I run the next step again I get

```
tadcan@Quad:~$  sudo modprobe ndiswrapper
tadcan@Quad:~$ 

```

So I presume it installed the first time?

```
tadcan@Quad:~$ sudo apt-get install wpasupplicant
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wpasupplicant is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

This seems fine as well.
I get a text pad when I run this
```
tadcan@Quad:~$ gksudo gedit /etc/wpa_supplicant.conf
```

I put this in 
> network={
        ssid="off/any"
        proto=WPA
        key_mgmt=WPA-PSK
        pairwise=TKIP
        group=TKIP
        psk="*******"
}

The 'off/any' I get from the wlan0 in iwconfig

So then I run the next bit 
```
tadcan@Quad:~$ sudo apt-get install wpasupplicant
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wpasupplicant is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
tadcan@Quad:~$ gksudo gedit /etc/wpa_supplicant.conf
tadcan@Quad:~$ sudo wpa_supplicant -Bw -c/etc/wpa_supplicant.conf -iwlan0
wpa_supplicant: invalid option -- 'w'
wpa_supplicant v0.6.4
Copyright (c) 2003-2008, Jouni Malinen <j@w1.fi> and contributors

This program is free software. You can distribute it and/or modify it
under the terms of the GNU General Public License version 2.

Alternatively, this software may be distributed under the terms of the
BSD license. See README and COPYING for more details.

This product includes software developed by the OpenSSL Project
for use in the OpenSSL Toolkit (http://www.openssl.org/)

usage:
  wpa_supplicant [-BddhKLqqtuvW] [-P<pid file>] [-g<global ctrl>] \
        -i<ifname> -c<config file> [-C<ctrl>] [-D<driver>] [-p<driver_param>] \
        [-b<br_ifname>] [-f<debug file>] \
        [-N -i<ifname> -c<conf> [-C<ctrl>] [-D<driver>] \
        [-p<driver_param>] [-b<br_ifname>] ...]

drivers:
  wext = Linux wireless extensions (generic)
  atmel = ATMEL AT76C5XXx (USB, PCMCIA)
  wired = wpa_supplicant wired Ethernet driver
options:
  -b = optional bridge interface name
  -B = run daemon in the background
  -c = Configuration file
  -C = ctrl_interface parameter (only used if -c is not)
  -i = interface name
  -d = increase debugging verbosity (-dd even more)
  -D = driver name
  -f = log output to debug file instead of stdout
  -g = global ctrl_interface
  -K = include keys (passwords, etc.) in debug output
  -t = include timestamp in debug messages
  -h = show this help text
  -L = show license (GPL and BSD)
  -p = driver parameters
  -P = PID file
  -q = decrease debugging verbosity (-qq even less)
  -u = enable DBus control interface
  -v = show version
  -W = wait for a control interface monitor before starting
  -N = start describing new interface
example:
  wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
```

When I run this I get
```
tadcan@Quad:~$ sudo ifconfig wlan0 up
tadcan@Quad:~$ 
```

When I should get 

> Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
 

What am I doing wrong?

---

### Post by carml on 2009-03-06
If you install the package ndisgtk you'll get a graphical interface for the ndiswrapper installer.After the installation you'll find it under System->Administration->Windows wireless driver.

---

### Post by tadcan on 2009-03-06
I did that and it showed me the driver was installed.

I checked the network manager and it saw the network from the router. 

Now it works! 

Now just curious why I have a low percentage of connectivity (from 29-58%) The router is about two metres away.

---

### Post by carml on 2009-03-06
> **tadcan said:**
> I did that and it showed me the driver was installed.

I checked the network manager and it saw the network from the router. 

Now it works! 

Now just curious why I have a low percentage of connectivity (from 29-58%) The router is about two metres away.

I'm glad you solved your problem, but I don't have an answer for your low connectivity.

---

### Post by tadcan on 2009-03-06
I didn't finish the list. There is an extra part to have the driver load at start-up. Back to not seeing the wireless card. Have to start again, I dont know what triggered it the last time.

When I use the graphical tool and press 'configure network', I am told 'Cannot find network configuration tool'

---

### Post by tadcan on 2009-03-07
At the moment I dont see my wireless card when I start the computer.

I need to run sudo modprobe ndiswrapper to start the wireless

I tried the script to run the driver from start up, but must have made a mistake somewhere. I used the default script, do I need to make changes and what do I need to change.

If you run ping in the terminal how do you stop it.

---

### Post by iamkrazee on 2009-03-07
put the module in /etc/modules and restart.

---

### Post by iamkrazee on 2009-03-07
For ping, you can break it by ctrl+c

or

```
ping -c 50 192.168.1.1
```

Replace 50 by no. of times you want the destination to be pinged.

Replace 192.168.1.1 by the destination IP.

---

### Post by tadcan on 2009-03-07
> **iamkrazee said:**
> put the module in /etc/modules and restart.

I need more information then that, like how do I find the module and where do I find /etc/module

---

### Post by anewguy on 2009-03-07
In a terminal window, do the following:

cd /etc

gksudo gedit modules

this calls up the editor and opens the file modules.  This file contains the additional kernal modules you want loaded at boot.  Ndiswrapper must be added to this file:

scroll to the end of the file

create a blank line at the end of the file

type:

ndiswrapper

in that blank line.

Save the file, exit, and reboot.


dave :)

---

### Post by tadcan on 2009-03-08
Thanks that worked.

Solved!

---

