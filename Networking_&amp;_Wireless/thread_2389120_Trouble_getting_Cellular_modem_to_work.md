---
title: "Trouble getting Cellular modem to work"
date: 2018-04-11
forum: Networking &amp; Wireless
---

### Post by zlb323 on 2018-04-11
Hello everyone,

I am working on a fitlet2 trying to get a SimTech 7100A cell modem to give me internet access and I am having a bit of trouble and hoping someone could help me.

First off I want to thank anyone for any help in advance. 

OK, so I have tried getting this modem configured with Network Manager and I cannot seem to get anything working on it. Most of the time the modem itself is unavailable to the Network Manager:

```

$ nmcli d
DEVICE    TYPE      STATE        CONNECTION
enp2s0    ethernet  connected    enp2s0
enp3s0    ethernet  connected    Wired connection 1
tap0      tun       connected    tap0
wlp1s0    wifi      connected    MSI WiFi 2.4Ghz
cdc-wdm1  gsm       unavailable  --
lo        loopback  unmanaged    --

```

The device seems to have the correct driver installed as it creates the cdc-wdm1 device as well as 5 ttyUSBs. I have the following configuration for the connection:

```

=============================================================================== 
                      Connection profile details (vzw)
===============================================================================
connection.id:                          vzw
connection.uuid:                        a1b6e4cf-8799-4367-8784-1cee2ef1f05f
connection.interface-name:              cdc-wdm1
connection.type:                        gsm
connection.autoconnect:                 yes
connection.autoconnect-priority:        0
connection.timestamp:                   1523458603
connection.read-only:                   no
connection.permissions:
connection.zone:                        --
connection.master:                      --
connection.slave-type:                  --
connection.autoconnect-slaves:          -1 (default)
connection.secondaries:
connection.gateway-ping-timeout:        0
connection.metered:                     unknown
connection.lldp:                        -1 (default)
-------------------------------------------------------------------------------
ipv4.method:                            auto
ipv4.dns:
ipv4.dns-search:
ipv4.dns-options:                       (default)
ipv4.dns-priority:                      0
ipv4.addresses:
ipv4.gateway:                           --
ipv4.routes:
ipv4.route-metric:                      -1
ipv4.ignore-auto-routes:                no
ipv4.ignore-auto-dns:                   no
ipv4.dhcp-client-id:                    --
ipv4.dhcp-timeout:                      0
ipv4.dhcp-send-hostname:                yes
ipv4.dhcp-hostname:                     --
ipv4.dhcp-fqdn:                         --
ipv4.never-default:                     no
ipv4.may-fail:                          yes
ipv4.dad-timeout:                       -1 (default)
-------------------------------------------------------------------------------
ipv6.method:                            auto
ipv6.dns:
ipv6.dns-search:
ipv6.dns-options:                       (default)
ipv6.dns-priority:                      0
ipv6.addresses:
ipv6.gateway:                           --
ipv6.routes:
ipv6.route-metric:                      -1
ipv6.ignore-auto-routes:                no
ipv6.ignore-auto-dns:                   no
ipv6.never-default:                     no
ipv6.may-fail:                          yes
ipv6.ip6-privacy:                       0 (disabled)
ipv6.addr-gen-mode:                     stable-privacy
ipv6.dhcp-send-hostname:                yes
ipv6.dhcp-hostname:                     --
-------------------------------------------------------------------------------
gsm.number:                             *99#
gsm.username:                           1
gsm.password:                           <hidden>
gsm.password-flags:                     0 (none)
gsm.apn:                                vzwinternet
gsm.network-id:                         --
gsm.pin:                                <hidden>
gsm.pin-flags:                          0 (none)
gsm.home-only:                          no
gsm.device-id:                          --
gsm.sim-id:                             --
gsm.sim-operator-id:                    --
-------------------------------------------------------------------------------



```

But trying to connect gives the following:

```

$ nmcli con up vzw
Error: Connection activation failed: No suitable device found for this connection.



$ nmcli device connect cdc-wdm1
Error: Failed to add/activate new connection: gsm: GSM mobile broadband connection requires a 'gsm' setting

```

I assume this is because of the device being unavailable. I cannot figure out what to do to bring the device up and configured with Network Manager. This is the output of lshw: 

```

*-usb:1
                      description: Generic USB device
                      product: SimTech, Incorporated
                      vendor: SimTech, Incorporated
                      physical id: 2
                      bus info: usb@1:8.2
                      version: 2.32
                      serial: 0123456789ABCDEF
                      capabilities: usb-2.00
                      configuration: driver=qmi_wwan maxpower=500mA speed=480Mbit/s



```

I can connect to the device via minicom and I will see stuff like this:

```

NO CARRIER

+PPPD: DISCONNECTED


SMS DONE

```

So even though I haven't done a usb-modeswitch I don't think I need to. I have been able to get this sim card to work on a different board so I don't think that it has anything to do with that. 

I have tried using wvdial also but that doesn't seem to be any more promising:

```


--> WvDial: Internet dialer version 1.61
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Modem initialized.
--> Sending: atdt*99#
--> Waiting for carrier.
atdt*99#
CONNECT 115200
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Wed Apr 11 14:36:33 2018
--> Pid of pppd: 2680
--> Using interface ppp0
--> Disconnecting at Wed Apr 11 14:36:33 2018
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds



```

the syslog I get when I run wvdial: 

```

Apr 11 14:33:33 development-fitlet2 ModemManager[810]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: 3GPP Registration state changed (unknown -> idle)
Apr 11 14:36:33 development-fitlet2 pppd[2680]: pppd 2.4.7 started by development, uid 0
Apr 11 14:36:33 development-fitlet2 pppd[2680]: speed 1152000000 not supported
Apr 11 14:36:33 development-fitlet2 pppd[2680]: using channel 7
Apr 11 14:36:33 development-fitlet2 pppd[2680]: Using interface ppp0
Apr 11 14:36:33 development-fitlet2 NetworkManager[854]: nm_device_get_device_type: assertion 'NM_IS_DEVICE (self)' failed
Apr 11 14:36:33 development-fitlet2 pppd[2680]: Connect: ppp0 <--> /dev/ttyUSB3
Apr 11 14:36:33 development-fitlet2 pppd[2680]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xee7c1e4d> <pcomp>]
Apr 11 14:36:33 development-fitlet2 NetworkManager[854]: <info>  [1523478993.1522] manager: (ppp0): new Generic device (/org/freedesktop/NetworkManager/Devices/12)
Apr 11 14:36:33 development-fitlet2 pppd[2680]: rcvd [LCP ConfReq id=0x18 <asyncmap 0x0> <auth chap MD5> <magic 0x6945e080> <pcomp> <accomp>]
Apr 11 14:36:33 development-fitlet2 pppd[2680]: sent [LCP ConfRej id=0x18 <accomp>]
Apr 11 14:36:33 development-fitlet2 pppd[2680]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0xee7c1e4d> <pcomp>]
Apr 11 14:36:33 development-fitlet2 pppd[2680]: rcvd [LCP ConfReq id=0x19 <asyncmap 0x0> <auth chap MD5> <magic 0x6945e080> <pcomp>]
Apr 11 14:36:33 development-fitlet2 pppd[2680]: sent [LCP ConfNak id=0x19 <auth chap MS-v2>]
Apr 11 14:36:33 development-fitlet2 pppd[2680]: rcvd [LCP ConfReq id=0x1a <asyncmap 0x0> <auth chap MD5> <magic 0x6945e080> <pcomp>]
Apr 11 14:36:33 development-fitlet2 pppd[2680]: sent [LCP ConfNak id=0x1a <auth chap MS-v2>]
Apr 11 14:36:33 development-fitlet2 pppd[2680]: rcvd [LCP ConfReq id=0x1b <asyncmap 0x0> <auth chap MD5> <magic 0x6945e080> <pcomp>]
Apr 11 14:36:33 development-fitlet2 pppd[2680]: sent [LCP ConfNak id=0x1b <auth chap MS-v2>]
Apr 11 14:36:33 development-fitlet2 pppd[2680]: rcvd [LCP ConfReq id=0x1c <asyncmap 0x0> <auth chap MD5> <magic 0x6945e080> <pcomp>]
Apr 11 14:36:33 development-fitlet2 pppd[2680]: sent [LCP ConfNak id=0x1c <auth chap MS-v2>]
Apr 11 14:36:33 development-fitlet2 NetworkManager[854]: <info>  [1523478993.1619] devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Apr 11 14:36:33 development-fitlet2 NetworkManager[854]: <info>  [1523478993.1620] device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Apr 11 14:36:33 development-fitlet2 pppd[2680]: rcvd [LCP ConfReq id=0x1d <asyncmap 0x0> <auth chap MD5> <magic 0x6945e080> <pcomp>]
Apr 11 14:36:33 development-fitlet2 pppd[2680]: sent [LCP ConfNak id=0x1d <auth chap MS-v2>]
Apr 11 14:36:33 development-fitlet2 pppd[2680]: rcvd [LCP ConfReq id=0x1e <asyncmap 0x0> <auth chap MD5> <magic 0x6945e080> <pcomp>]
Apr 11 14:36:33 development-fitlet2 pppd[2680]: sent [LCP ConfRej id=0x1e <auth chap MD5>]
Apr 11 14:36:33 development-fitlet2 pppd[2680]: rcvd [LCP ConfReq id=0x1f <asyncmap 0x0> <magic 0x6945e080> <pcomp>]
Apr 11 14:36:33 development-fitlet2 pppd[2680]: sent [LCP ConfAck id=0x1f <asyncmap 0x0> <magic 0x6945e080> <pcomp>]
Apr 11 14:36:33 development-fitlet2 pppd[2680]: sent [LCP EchoReq id=0x0 magic=0xee7c1e4d]
Apr 11 14:36:33 development-fitlet2 pppd[2680]: sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Apr 11 14:36:33 development-fitlet2 pppd[2680]: rcvd [LCP DiscReq id=0x20 magic=0x6945e080]
Apr 11 14:36:33 development-fitlet2 pppd[2680]: rcvd [LCP EchoRep id=0x0 magic=0x6945e080 ee 7c 1e 4d]
Apr 11 14:36:33 development-fitlet2 pppd[2680]: Modem hangup
Apr 11 14:36:33 development-fitlet2 pppd[2680]: Connection terminated.
Apr 11 14:36:33 development-fitlet2 NetworkManager[854]: <error> [1523478993.1935] platform-linux: do-change-link[13]: failure changing link: failure 19 (No such device)
Apr 11 14:36:33 development-fitlet2 NetworkManager[854]: <warn>  [1523478993.1936] device (ppp0): failed to disable userspace IPv6LL address handling
Apr 11 14:36:33 development-fitlet2 NetworkManager[854]: <info>  [1523478993.1987] devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Apr 11 14:36:33 development-fitlet2 pppd[2680]: Exit.

```

I do have refuse-chap, local, and noauth configured in the /etc/ppp/options file. This here is the wvdial.conf I am using:

```


[Dialer Defaults]
Init1 = ATZ
Stupid Mode = 1
Dial Command = atdt
Carrier Check = no
New PPPD = yes


[ Dialer Verizon ]
Inherits = Dialer Defaults
Modem = /dev/ttyUSB3
Baud = 1152000000
Phone = *99#
Username = 1
Password = 1



```

Any help anyone could give me would be great as I have been stuck on this way longer than I care to admit.

---

### Post by Autodave on 2018-04-13
What version of Linux are you running?

What kind of PC are you running it on?

---

### Post by zlb323 on 2018-04-18
Hello sorry for the delay getting back to you. I am running Ubuntu 16.04 on a compulab fitlet2

---

### Post by vladimir-loshchin on 2018-08-06
Have the same issue with Huawei E1550 after Ubunty 17.10 -> 18.04 update. 

> 
$ nmcli device
DEVICE   TYPE      STATE         CONNECTION
enp4s0   ethernet  disconnected  --
wlp3s0   wifi      disconnected  --
ttyUSB2  gsm       unavailable   --
lo       loopback  unmanaged     --


> 
$ nmcli device show ttyUSB2 
GENERAL.DEVICE:                         ttyUSB2                  
GENERAL.TYPE:                           gsm                  
GENERAL.HWADDR:                         (unknown)                                                      
GENERAL.MTU:                            0                      
GENERAL.STATE:                          20 (unavailable)            
GENERAL.CONNECTION:                     --                 
GENERAL.CON-PATH:                       --              


> 
$ nmcli device connect ttyUSB2
Error: Failed to add/activate new connection: gsm: GSM mobile broadband connection requires a 'gsm' setting


Did you find any solution?

---

### Post by vladimir-loshchin on 2018-08-06
I found a solution for my situation. 
I just switch my GPRS stick to "modem only" mode.
For my *Huawei E1550* it could be done by command **AT^U2DIAG=0**.

---

### Post by zlb323 on 2018-08-06
The problem I was having had to do with the modem not being registered on my carriers network. I finally had to switch to a different modem in order to solve my problem. It doesn't sound like the same problem that you are having sorry I can't be more help

---

### Post by huso113 on 2018-08-08
Hi,
fitlet2 has wiki about cellular connection, possibly it can help
[http://fit-pc.com/wiki/index.php/Linux_Mint:_Mobile_broadband](http://fit-pc.com/wiki/index.php/Linux_Mint:_Mobile_broadband)

---

