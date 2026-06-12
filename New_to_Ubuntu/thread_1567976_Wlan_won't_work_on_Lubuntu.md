---
title: "Wlan won't work on Lubuntu"
date: 2010-09-04
forum: New to Ubuntu
---

### Post by Tumetsu on 2010-09-04
So I tried today to install Lubuntu for my new netbook and ran it from USB as a live. Everything works fine now, except wlan. Looks like Lubuntu can't detect wlan or probably even the wlan card. Here is some information of the setup

> 
ubuntu@ubuntu:~$ sudo -C network
sudo: the argument to -C must be at least 3
usage: sudo -h | -K | -k | -L | -V
usage: sudo -v [-AknS] [-p prompt]
usage: sudo -l[l] [-AknS] [-g groupname|#gid] [-p prompt] [-U username] [-u
            username|#uid] [-g groupname|#gid] [command]
usage: sudo [-AbEHknPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] file ...
ubuntu@ubuntu:~$ sudo lshw /C  network
Hardware Lister (lshw) - B.02.14
usage: lshw [-format] [-options ...]
       lshw -version

    -version        print program version (B.02.14)

format can be
    -html           output hardware tree as HTML
    -xml            output hardware tree as XML
    -short          output hardware paths
    -businfo        output bus information

options can be
    -class CLASS    only show a certain class of hardware
    -C CLASS        same as '-class CLASS'
    -c CLASS        same as '-class CLASS'
    -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
    -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
    -quiet          don't display status
    -sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
    -numeric        output numeric IDs (for PCI, USB, etc.)Computer

Asus eeePc R101

Wlan card: Atheros AR8132 PCI-E Fast Ethernet Controller (10/100MBit), Atheros AR2427 Wireless Network Adapter (bg)


Oh and how I can change keyboard settings in Lubuntu_ I would like to change my keyboard layout from english to finish since my netbook has finnish keyboard.

Thanks for help. I hope I can soon actually install lubuntu for my netbook :)

---

### Post by Old_Grey_Wolf on 2010-09-04
Rather than posting the output of "sudo -C network" command which doesn't work, try posting the output of the command "ifconfig". :)

---

### Post by halitech on 2010-09-04
to get your hardware info it would be
```
sudo lshw -C network
```

for ifconfig, you probably need to run it as sudo ifconfig

---

### Post by Tumetsu on 2010-09-04
Oh sorry guys. It was command I found from one topic regarding wlan issues here so I thought it would be the needed one. Here is the output of the sudo lshw -C network:

> *-network UNCLAIMED     
       description: Network controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:fbff0000-fbffffff
  *-network
       description: Ethernet interface
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: 48:5b:39:87:3b:d6
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI duplex=full firmware=N/A ip=192.168.11.4 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:29 memory:f7fc0000-f7ffffff ioport:ec00(size=128)
tuomas@Tuomas-netbook:~$ 


And sudo ifconfig:
> sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 48:5b:39:87:3b:d6  
          inet addr:192.168.11.4  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::4a5b:39ff:fe87:3bd6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26494 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16207 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:39191522 (39.1 MB)  TX bytes:1410831 (1.4 MB)
          Interrupt:29 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:168 errors:0 dropped:0 overruns:0 frame:0
          TX packets:168 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11972 (11.9 KB)  TX bytes:11972 (11.9 KB)


---

### Post by jeight on 2010-09-04
Try 'sudo ifconfig wlan0 up'.

---

### Post by Tumetsu on 2010-09-05
> **jeight said:**
> Try 'sudo ifconfig wlan0 up'.
DIdn't work. Got this:

> wlan0: ERROR while getting interface flags: There is not device("there is not device" were rough translation from finnish so it may not be exactly same as it would return in english setup.

EDIT: Solved with these instructions: [http://ubuntuforums.org/showthread.php?t=1461138](http://ubuntuforums.org/showthread.php?t=1461138)

---

