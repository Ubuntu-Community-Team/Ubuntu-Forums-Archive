---
title: "No wireless connections after sleep/suspend"
date: 2017-12-01
forum: Networking &amp; Wireless
---

### Post by makem2 on 2017-12-01
As the title says. There is a thread dated 2012 but the solution does not work for me. Recovery is only by restarting.


I am attempting to use Teamviewer to wake my sleeping/suspended (what is the difference if any?) remote laptop whilst I travel. It works fine if the computer is left on but if I set it to sleep/suspend, via the logout menu, on resuming the wifi is down. Until I can solve that I am unable to continue with researching WoL with wifi.


```

sudo lshw -C network
[sudo] password for makem: 
  *-network               
       description: Wireless interface
       product: Wireless 3160
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlp7s0
       version: cb
       serial: 34:e6:ad:ba:1f:d0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.10.0-40-generic firmware=17.459231.0 ip=192.168.2.33 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:55 memory:b6300000-b6301fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: enp8s0
       version: 0c
       serial: 2c:60:0c:8a:6e:27
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:50 ioport:4000(size=256) memory:b6200000-b6200fff memory:b6000000-b6003fff
makem@ssdTOSH:~$

```


Driver = iwlwifi


Previous solution:


[https://ubuntuforums.org/showthread.php?t=2004690](https://ubuntuforums.org/showthread.php?t=2004690)


```

sudo gedit /etc/pm/config.d/config

```


Add line:


```

SUSPEND_MODULES="iwlwifi"
```


 /etc/pm/config.d/config does not exist and making that file with the relevant line does not do the trick.


```

makem@ssdTOSH:/$ lsb_release -a
LSB Version:    core-9.20160110ubuntu0.2-amd64:core-9.20160110ubuntu0.2-noarch:security-9.20160110ubuntu0.2-amd64:security-9.20160110ubuntu0.2-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial
makem@ssdTOSH:/$

```

---

### Post by ajgreeny on 2017-12-01
I am not on my Xubuntu machine at the moment, but I originally had the same problem as you have.

I can not remember the details and will find them for you tomorrow, but it requires a new file in the power management area of the file system which simply restarts networking after a wake from suspend.

EDIT:
[https://ubuntuforums.org/showthread.php?t=2366041&p=13665563&viewfull=1#post13665563](https://ubuntuforums.org/showthread.php?t=2366041&p=13665563&viewfull=1#post13665563)
This post of mine may help you; you may have to play around with the sleep time in the command but I find 4 or 5 seconds works every time on my old netbook.

Further info still to come as I see this is not my final solution.

Good luck!

---

### Post by makem2 on 2017-12-01
> **ajgreeny said:**
> I am not on my Xubuntu machine at the moment, but I originally had the same problem as you have.

I can not remember the details and will find them for you tomorrow, but it requires a new file in the power management area of the file system which simply restarts networking after a wake from suspend.

EDIT:
[https://ubuntuforums.org/showthread.php?t=2366041&p=13665563&viewfull=1#post13665563](https://ubuntuforums.org/showthread.php?t=2366041&p=13665563&viewfull=1#post13665563)
This post of mine may help you; you may have to play around with the sleep time in the command but I find 4 or 5 seconds works every time on my old netbook.

Further info still to come as I see this is not my final solution.

Good luck!

```

makem@ssdTOSH:~$ sudo lshw -class network
[sudo] password for makem: 
  *-network               
       description: Wireless interface
       product: Wireless 3160
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlp7s0
       version: cb
       serial: 34:e6:ad:ba:1f:d0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.10.0-40-generic firmware=17.459231.0 ip=192.168.2.33 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:55 memory:b6300000-b6301fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: enp8s0
       version: 0c
       serial: 2c:60:0c:8a:6e:27
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:50 ioport:4000(size=256) memory:b6200000-b6200fff memory:b6000000-b6003fff
makem@ssdTOSH:~$

```

From that maybe the model is RTL8111 or RTL8111/8168/8411

I am rather loath to try them so will wait for further comment please. Is 'N' the time you refer to?

---

### Post by makem2 on 2017-12-01
> **ajgreeny said:**
> I am not on my Xubuntu machine at the moment, but I originally had the same problem as you have.

I can not remember the details and will find them for you tomorrow, but it requires a new file in the power management area of the file system which simply restarts networking after a wake from suspend.

EDIT:
[https://ubuntuforums.org/showthread.php?t=2366041&p=13665563&viewfull=1#post13665563](https://ubuntuforums.org/showthread.php?t=2366041&p=13665563&viewfull=1#post13665563)
This post of mine may help you; you may have to play around with the sleep time in the command but I find 4 or 5 seconds works every time on my old netbook.

Further info still to come as I see this is not my final solution.

Good luck!

```

makem@ssdTOSH:~$ sudo lshw -class network
[sudo] password for makem: 
  *-network               
       description: Wireless interface
       product: Wireless 3160
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlp7s0
       version: cb
       serial: 34:e6:ad:ba:1f:d0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.10.0-40-generic firmware=17.459231.0 ip=192.168.2.33 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:55 memory:b6300000-b6301fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: enp8s0
       version: 0c
       serial: 2c:60:0c:8a:6e:27
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:50 ioport:4000(size=256) memory:b6200000-b6200fff memory:b6000000-b6003fff
makem@ssdTOSH:~$

```

From that maybe the model is RTL8111 or RTL8111/8168/8411 (Ethernet Inteface)

I am rather loath to try them so will wait for further comment please. Is 'N' the time you refer to?

I am referring to Wireless Interface, are you?

For convenience I wanted WoL on WiFi.

EDIT: Restarting the network-manager allows internet access.

```

makem@ssdTOSH:~$ sudo service network-manager restart
[sudo] password for makem: 
makem@ssdTOSH:~$

```

---

### Post by makem2 on 2017-12-01
The following worked for me:

[https://askubuntu.com/questions/766718/script-to-restart-network-manager-after-resume-from-sleep](https://askubuntu.com/questions/766718/script-to-restart-network-manager-after-resume-from-sleep)

```

makem@ssdTOSH:/lib/systemd/system-sleep$ sudo nano network-restart


```

Script for network-restart:

```

#!/bin/sh
set -e

if [ "$2" = "suspend" ] || [ "$2" = "hybrid-sleep" ]; then
    case "$1" in
        post) sleep 10 ; systemctl restart network-manager ;;
    esac
fi
```

Save & exit nano. Make executable:

```

makem@ssdTOSH:/lib/systemd/system-sleep$ sudo chmod +x network-restart



```

Suspend via menu and resume using power button. (Where is the 'suspend' button?)

It took about 12 seconds to have the internet access back.

EDIT: Now maybe I can use an always on Raspberry pi (Or wake it up) to wake up my wifi connected suspended laptop :-)

[http://www.instructables.com/id/Raspberry-Pi-As-Wake-on-LAN-Server/](http://www.instructables.com/id/Raspberry-Pi-As-Wake-on-LAN-Server/)

---

### Post by ajgreeny on 2017-12-02
Here is the script I I mentioned above which I have now found and which has worked faultlessly for me on Lubuntu 16.04 on an old netbook.

Just copy all the text as shown below and, as root, save it as 
**/lib/systemd/system-sleep/NetworkManagerRestartWorkaroundForBug1380480.sh** 
exactly as mentioned in the script itself.  
I found that my netbook needed the 4 or 5 seconds sleep (the next to bottom line of the script) to get the system up and running properly when coming out of suspend; yours may be much quicker or slower.
```
#!/bin/bash
# Created by Hans Deragon (hans@deragon.biz), 2015-05-14 07:31:11 EDT

# INSTALLATION
#
#   - Move this script under: /lib/systemd/system-sleep
#   - chmod +x /lib/systemd/system-sleep/NetworkManagerRestartWorkaroundForBug1380480.sh

# DESCRIPTION
#
#   Restarting the NetworkManager as a workaround for the following bug:
# 
#   &#8729; https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1380480


# 3 seconds delay is necessary apparently; may be shorter or longer so needs to be
# tested.  But if no delay is implemented, nm-applet crashes.  Seems that we
# need to leave the system to resume completely before attempting a restart of
# NetworkManager.
(sleep 3; systemctl restart NetworkManager.service) &
disown

```
Here is the bug itself which you may find has other useful information.
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1380480](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1380480)

---

### Post by makem2 on 2017-12-02
[COLOR=#000000][FONT=&amp]Thank you for finding that. It worked for me even after a shutdown.

I will give it a few days then if it survives, mark it solved/

[/FONT][/COLOR]

---

