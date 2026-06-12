---
title: "no internet connection"
date: 2011-05-24
forum: New to Ubuntu
---

### Post by ornothaloapq on 2011-05-24
i recently upgraded to 11.04 and now i my computer wont connect wirelessly. i do not think it is my computer i think it is the internet service provider or the router i am using. is there a terminal command to see what the problem is?

---

### Post by beew on 2011-05-24
> **ornothaloapq said:**
> i recently upgraded to 11.04 and now i my computer wont connect wirelessly. i do not think it is my computer i think it is the internet service provider or the router i am using. is there a terminal command to see what the problem is?

```
lshw -c network
```

Just to find out what your graphic card is.

Alternatively run Additional Drivers and see if it recommends any wireless driver to be installed.

---

### Post by duke.tim on 2011-05-24
#1
First check to see if you need to enable some drivers

System-> Administration -> Additional Drivers

#2 If you still can't get access:

If you have a LAN cable plug your computer directly into the router to see if you can get internet access.

::::

If your drivers are enabled/LAN works but wireless doesn't, post the output of the following* (I've included the terminal commands below the Network tools program)

System -> Administration -> Network Tools

Ping will tell you if you are able to send and receive information from google


Ping [www.google.com](www.google.com) 
Post the results, do the packets go through?

Traceroute shows where the data is routed to get to google (a.k.a via router to isp to google)

Traceroute [www.google.com](www.google.com)
Does it get stopped before reaching google?

It is likely you just need to install the drivers :)
///\\\Terminal///\\\
```
ping -c 5 www.google.com
```

If that doesn't work you might want to install traceroute

```
sudo apt-get install traceroute
```

then run the program

```
traceroute www.google.com
```

---

### Post by 5149.5 on 2011-05-24
Entering nm-tool will show the wireless networks that your wireless adapter can see.

---

### Post by ornothaloapq on 2011-05-25
when i type in the code from the first response posted i get the following: ```
 DX4300:~$ sudo lshw -C network [sudo] password for joel:  PCI (sysfs)     *-network                       description: Ethernet interface        product: 88E8071 PCI-E Gigabit Ethernet Controller        vendor: Marvell Technology Group Ltd.        physical id: 0        bus info: pci@0000:04:00.0        logical name: eth1        version: 16        serial: 00:22:68:68:93:11        capacity: 1Gbit/s        width: 64 bits        clock: 33MHz        capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation        configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair        resources: irq:44 memory:fe9fc000-fe9fffff ioport:d800(size=256) memory:fe9c0000-fe9dffff   *-network        description: Wireless interface        product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller        vendor: Realtek Semiconductor Co., Ltd.        physical id: 5        bus info: pci@0000:06:05.0        logical name: wlan1        version: 20        serial: 00:06:4f:81:b7:25        width: 32 bits        clock: 33MHz        capabilities: pm bus_master cap_list ethernet physical wireless        configuration: broadcast=yes driver=rtl8180 driverversion=2.6.38-8-generic firmware=N/A latency=64 link=no maxlatency=64 mingnt=32 multicast=yes wireless=IEEE 802.11bg        resources: irq:20 ioport:e800(size=256) memory:febffc00-febffdff
``` from the second response i dont have a lan cable connection but from the terminal i got this: ```
 -DX4300:~$ sudo ping -C www.google.com  [sudo] password for joel:   ping: invalid option -- 'C'  Usage: ping [-LRUbdfnqrvVaAD] [-c count] [-i interval] [-w deadline]              [-p pattern] [-s packetsize] [-t ttl] [-I interface]              [-M pmtudisc-hint] [-m mark] [-S sndbuf]              [-T tstamp-options] [-Q tos] [hop1 ...] destination  joel@joel-DX4300:~$ sudo apt-get install traceroute  Reading package lists... Done  Building dependency tree         Reading state information... Done  Package traceroute is not available, but is referred to by another package.  This may mean that the package is missing, has been obsoleted, or  is only available from another source    E: Package 'traceroute' has no installation candidate 
```   and when i put nm-tool into the terminal i got this : ```
 -DX4300:~$ nm-tool    NetworkManager Tool    State: disconnected    - Device: eth1 -----------------------------------------------------------------    Type:              Wired    Driver:            sky2    State:             unavailable    Default:           no    HW Address:        00:22:68:68:93:11      Capabilities:      Carrier Detect:  yes      Wired Properties      Carrier:         off      - Device: wlan1 ----------------------------------------------------------------    Type:              802.11 WiFi    Driver:            rtl8180    State:             disconnected    Default:           no    HW Address:        00:06:4F:81:B7:25      Capabilities:      Wireless Properties      WEP Encryption:  yes      WPA Encryption:  yes      WPA2 Encryption: yes      Wireless Access Points    
```      im sorry i could not put all of this into a different font or into one of those squares made for code. i hope this gets posted in a readable way and not jumbled together.  im sorry, for some reason my code pasted from the terminal is in one line like that. i have had that problem before and i never learned how to fix that.

---

### Post by ornothaloapq on 2011-05-25
i am using a lan cable now and everything works. i checked the additional drivers and there isnt anything there about a wireless card.

---

### Post by duke.tim on 2011-05-25
Looks like you have your realtek driver installed

I think I misunderstood your question :( is it that:

# You connect, but can not access the internet.
# Can see the nearby wifi networks but you can not connect to yours.
# No wireless on your computer.

Try using the quote tags instead of the code tags because it is rather difficult to read some of the terminal output

(to get the commands to work)

using the wireless connection with out the Lan cable try ping again
but make sure you use a lowercase c and you don't need sudo :) [besides the fact that I forgot the count number]

```
ping -c 5 www.google.com
```

To install traceroute you will need to be connected to the internet, I should have mentioned that...

You don't need to use sudo for all your commands
General information about Sudo:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

