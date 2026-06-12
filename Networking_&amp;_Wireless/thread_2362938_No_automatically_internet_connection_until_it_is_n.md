---
title: "No automatically internet connection until it is not started manually"
date: 2017-06-04
forum: Networking &amp; Wireless
---

### Post by Xpdin on 2017-06-04
Every time Linux boots I have to manually use the beyond two commands in order to have an working internet connection. 


```
ethtool -s eth0 autoneg off speed 100 duplex full

```
```
dhclient eth0

```


I am looking for a method so the internet connection will start automatically when Lubuntu boots up.




/etc/network/interfaces: 


    ```
# This file describes the network interfaces available on your system
    # and how to activate them. For more information, see interfaces(5).
    
    source /etc/network/interfaces.d/*
    
    # The loopback network interface
    auto lo
    iface lo inet loopback
    
    # The primary network interface
    #auto eth0
    iface eth0 inet dhcp
    
    ethtool -s eth0 autoneg off speed 100 duplex full
    allow-hotplug eth0
    
    #iface wlan0 inet manual
    #wpa-roam /etc/wpa_supplicant/wpa_supplicant.conf
```


/etc/rc.local: 


  


     ```
 #!/bin/sh -e
        #
        # rc.local
        #
        # This script is executed at the end of each multiuser runlevel.
        # Make sure that the script will "exit 0" on success or any other
        # value on error.
        #
        # In order to enable or disable this script just change the execution
        # bits.
        #
        # By default this script does nothing.
        
        echo 500 > /sys/class/backlight/intel_backlight/brightness
        xrandr -s 960x540
        rfkill block bluetooth
        rfkill block wifi
        ethtool -s eth0 autoneg off speed 100 duplex full
        ip link set eth0 up
        ifup eth0
        dhcpcd eth0
        
        exit 0
```




    ```
systemctl status rc-local: 
    globalisation@WindowsXP:~$ systemctl status rc-local
    &#9679; rc-local.service - /etc/rc.local Compatibility
       Loaded: loaded (/lib/systemd/system/rc-local.service; static; vendor preset: 
      Drop-In: /lib/systemd/system/rc-local.service.d
               &#9492;&#9472;debian.conf
       Active: failed (Result: exit-code) since Sun 2017-06-04 00:31:28 CEST; 15min 
      Process: 636 ExecStart=/etc/rc.local start (code=exited, status=1/FAILURE)
    
    Jun 04 00:31:27 WindowsXP systemd[1]: Starting /etc/rc.local Compatibility...
    Jun 04 00:31:28 WindowsXP rc.local[636]: Can't open display
    Jun 04 00:31:28 WindowsXP systemd[1]: rc-local.service: Control process exited, 
    Jun 04 00:31:28 WindowsXP systemd[1]: Failed to start /etc/rc.local Compatibilit
    Jun 04 00:31:28 WindowsXP systemd[1]: rc-local.service: Unit entered failed stat
    Jun 04 00:31:28 WindowsXP systemd[1]: rc-local.service: Failed with result 'exit
    
    globalisation@WindowsXP:~$ 

```


When Lubuntu boots it appears these errors:
```

Failed to start LSB: IPV4 DHCP client with IPV4ALL support. 
See 'systemctl status dhcpcd.service' for details 
16.780656 usb 1-1.4.3: device descriptor read/64, error -110 
```


/etc/sysctl.conf: 


    ```
#
    # /etc/sysctl.conf - Configuration file for setting system variables
    # See /etc/sysctl.d/ for additional system variables.
    # See sysctl.conf (5) for information.
    #
    
    #kernel.domainname = example.com
    
    # Uncomment the following to stop low-level messages on console
    #kernel.printk = 3 4 1 3
    
    ##############################################################3
    # Functions previously found in netbase
    #
    
    # Uncomment the next two lines to enable Spoof protection (reverse-path filter)
    # Turn on Source Address Verification in all interfaces to
    # prevent some spoofing attacks
    #net.ipv4.conf.default.rp_filter=1
    #net.ipv4.conf.all.rp_filter=1
    
    # Uncomment the next line to enable TCP/IP SYN cookies
    # See http://lwn.net/Articles/277146/
    # Note: This may impact IPv6 TCP sessions too
    #net.ipv4.tcp_syncookies=1
    
    # Uncomment the next line to enable packet forwarding for IPv4
    #net.ipv4.ip_forward=1
    
    # Uncomment the next line to enable packet forwarding for IPv6
    #  Enabling this option disables Stateless Address Autoconfiguration
    #  based on Router Advertisements for this host
    #net.ipv6.conf.all.forwarding=1
    
    
    ###################################################################
    # Additional settings - these settings can improve the network
    # security of the host and prevent against some network attacks
    # including spoofing attacks and man in the middle attacks through
    # redirection. Some network environments, however, require that these
    # settings are disabled so review and enable them as needed.
    #
    # Do not accept ICMP redirects (prevent MITM attacks)
    #net.ipv4.conf.all.accept_redirects = 0
    #net.ipv6.conf.all.accept_redirects = 0
    # _or_
    # Accept ICMP redirects only for gateways listed in our default
    # gateway list (enabled by default)
    # net.ipv4.conf.all.secure_redirects = 1
    #
    # Do not send ICMP redirects (we are not a router)
    #net.ipv4.conf.all.send_redirects = 0
    #
    # Do not accept IP source route packets (we are not a router)
    #net.ipv4.conf.all.accept_source_route = 0
    #net.ipv6.conf.all.accept_source_route = 0
    #
    # Log Martian Packets
    #net.ipv4.conf.all.log_martians = 1
    #
    
    net.ipv6.conf.all.disable_ipv6 = 1
    net.ipv6.conf.default.disable_ipv6 = 1
    net.ipv6.conf.lo.disable_ipv6 = 1

```


 Thank you.

---

### Post by Bucky Ball on 2017-06-04
Are you using Network Manager as well as trying to tweak the /interfaces file? Have you manually made changes to the /interfaces file? If so, where did you get the code for how to change it?

Generally, if you are using Network Manager, you would leave the /interfaces file as it is. The two do not play together.

---

### Post by Xpdin on 2017-06-04
Thank you Bucky Ball,

I am not using Network Manager.
I try to be as minimal as possible, it is a Lubuntu mini.iso with no desktop environment, with only fvwm window manager.

The /interfaces file config has been edited during the time, took those lines from different sources.

Regarding this issue, trying to resolve it, in the last hours I have been trying these "versions" of /interfaces:

[URL="https://paste.debian.net/hidden/ad54b052/"]https://paste.debian.net/hidden/ad54b052/
[/URL][URL="https://paste.debian.net/hidden/33ce3a40/"]https://paste.debian.net/hidden/33ce3a40/
[/URL] [https://paste.debian.net/hidden/3e0f8e2b/](https://paste.debian.net/hidden/3e0f8e2b/)

Regards.

It also seams that the second command ```
dhclient eth0
``` after using the MANDATORY ONE ```
ethtool -s eth0 autoneg off speed 100 duplex full
``` (still all the commands take effects only manually) could be replaced with  ```
ifup eth0
``` in order for the internet to work.


Maybe an important part of the next log is ```
Link detected: no
``` After boot if immediately the first command is ```
ethtool eth0
``` the output is:


```
:~$ sudo ethtool eth0
[sudo] password for globalisation: 
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised pause frame use: Symmetric Receive-only
	Advertised auto-negotiation: Yes
	Speed: 10Mb/s
	Duplex: Half
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
			       drv probe ifdown ifup
	Link detected: no

```


I would like to add that the same Linux machine in discussion always receives internet connection instantly/directly, even after reboot, shutdown, with no others supplementary manual commands, or any other actions, if I only change the cable from "the problematic in discussion internet connection" to the "non problematic" completely different DSL router connection(another ISP, BUT STILL THE SAME ETHERNET CABLE) 


The problematic connection dependent on the manual commands "in discussion" which has internet only after the manually commands, is from another ISP and is a coaxial/tv cable modem.


Regards.

---

### Post by Xpdin on 2017-06-04
Coud it be problems with onboard NIC?


This exactly same machine with this exactly system with  "in discussion", THE SAME ETHERNET CABLE, takes/keeps internet directly/immediately even after reboot/shutdown or whatever I would do, without any manual commands, ONLY MOVING THE ETHERNET CABLE from this "in discussion" problematic router to another router connected to completely another internet connection on another ISP.




The same port on the router the same cable, even from in discussion PROBLEMATIC ROUTER  also Windows 7 and Windows 10 connect to the internet instantly/directly without any clicks supplementary clicks, only changing the cable from the Linux machine to the Windows machine.

---

### Post by Xpdin on 2017-06-04
If you have please any ideas how this could happen, I have just remembered that  this in discussion same machine + same OS(Linux no changed configurations) + same Ethernet cable always "received and kept"  the internet automatically (no extra manual commands) from all the 3 different models of routers. 


All 3 connections and routers were from the same ISP, other than this forth problematic connection and router. 


Best wishes.

---

### Post by Xpdin on 2017-06-05
It seams that the final result, in order to have internet access automatically after reboot/shutdown/sleep with no more manual commands:


/etc/network/interfaces


```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


source /etc/network/interfaces.d/*


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
iface eth0 inet dhcp
    pre-up ethtool -s eth0 autoneg off speed 100 duplex full


allow-hotplug eth0



```


/etc/rc.local


```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.


echo 70 > /sys/class/backlight/intel_backlight/brightness
rfkill block bluetooth
rfkill block wifi
ethtool -s eth0 autoneg off speed 100 duplex full
ip link set eth0 up


exit 0

```

---

### Post by Bucky Ball on 2017-06-05
So it works?

---

### Post by Xpdin on 2017-06-05
At least for the moment, it seams that yes, indeed it works :)

---

### Post by Bucky Ball on 2017-06-05
Excellent work! Perhaps you could mark thread as solved to help others and save them time. See Thread Tools at the top right of the page.

Enjoy. ;)

---

### Post by Xpdin on 2017-06-05
Thanks Bucky Ball,

Maybe still it seams that because the IP are dynamically provided automatically by ISP, it seams that sometimes the IP are changed automatically by ISP even without me to restart, reset the router. 
In that moment the connection is lost so it seams that only ```
ethtool -s eth0 autoneg off speed 100 duplex full
``` should be used again manually in order to have again internet connection, after the IP is changed...

Has anyone any idea about it please?

Regards.

---

### Post by Bucky Ball on 2017-06-05
You are connected directly to the internet and not through a modem/router/access point? If you are, are you sure it is not the DHCP server on this device serving you a new IP (and that will happen every time your reboot your machine)? Not sure if you're talking about the IP on the router being reset everytime or the one on your machine.

If the one on your machine, simply set a static IP. I know how to do this in Network Manager, not a terminal in the /interfaces file, sorry.

---

### Post by Xpdin on 2017-06-06
Thanks Bucky Ball, it seams that this behavior is normal...

Regards.

---

