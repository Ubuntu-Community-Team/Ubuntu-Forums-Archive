---
title: "configuring madwifi for atheros AR5005G on egdy"
date: 2006-12-13
forum: Networking &amp; Wireless
---

### Post by shadowfax on 2006-12-13
having absolutely no luck configuring my wireless card on ubuntu. while on breezy earlier, it just wouldnt work. after installing edgy it worked for exactly one day and then back to square one. quite a newbie, so have tried most suggestions, with no luck at all. 
**lshw** gives: 
```
-network:1 UNCLAIMED
             description: Ethernet controller
             product: AR5005G 802.11abg NIC
             vendor: Atheros Communications, Inc.
             physical id: b
             bus info: pci@00:0b.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             resources: iomemory:e2010000-e201ffff irq:225
```

restricted modules are installed of course. and i just removed and reinstalled it again. 
**lsmod** gives
```
ath_pci                97184  0 
ath_rate_sample        15488  1 ath_pci
wlan                  203996  2 ath_pci,ath_rate_sample
ath_hal               192080  2 ath_pci,ath_rate_sample
```

i suppose the driver is not bound to the device? did modprobe ath_pci but still
```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.
```

did **dmesg |less** and got 
```
 ath_hal: 0.9.17.2 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[17179600.964000] wlan: 0.8.4.2 (0.9.2.1)
[17179600.972000] ath_rate_sample: 1.2 (0.9.2.1)
[17179600.996000] ath_pci: 0.9.4.5 (0.9.2)
[17179600.996000] PCI: Enabling device 0000:00:0b.0 (0010 -> 0012)
[17179600.996000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 17 (level, low) -> IRQ 225
[17179600.996000] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
```

isnt 0.9.2.1 the latest version of madwifi-ng?

having no luck, on a suggestion i tried following instructions on []("http://www.ubuntuforums.org/showthread.php?t=113405&highlight=MADWIFI")
to reinstall madwifi without breaking restricted modules. but that stalls at step 7 as **ah_osdep.o** and **hal.o** dont exist in the new madwifi directory. 

any ideas? getting so psyched with this :evil: not even sure if i followed the right steps. anyway, i´ll post any more info you may need. many thanks

---

### Post by FrodoB on 2006-12-13
Take a look here. This device is not supported in the HAL yet per this information, I don't know if this is still true or not.

[http://madwifi.org/wiki/Compatibility#AtherosAR5005G](http://madwifi.org/wiki/Compatibility#AtherosAR5005G)


[http://ubuntuforums.org/showthread.php?t=309333](http://ubuntuforums.org/showthread.php?t=309333)


[http://rik.rikva.nl/?q=node/10](http://rik.rikva.nl/?q=node/10)

---

### Post by shadowfax on 2006-12-13
thanks for your reply. i suppose that settles it for madwifi. i had tried using ndiswrapper ages ago and it never worked. but i retried with the lates version and yay, it atleast it shows up in iwconfig:
```
wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Encryption key:off
          Power Management:off
          Link Quality:4/100  Signal level:-93 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

but i still can´t connect. 
```
iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Operation not supported


```

why is that? i´m sure its worked earlier.

---

### Post by FrodoB on 2006-12-13
If you are not using the very latest ndiswrapper, I would try that.  It is up to at least version 1.31 and it works better with newer hardware.

---

### Post by shadowfax on 2006-12-14
yes i am using the latest version of ndiswrapper

---

### Post by FrodoB on 2006-12-14
Have you tried this recommended driver?

[ftp://ftp.support.acer-euro.com/notebook/travelmate_2410/driver/Wireless%20Lan%2080211bg.zip](ftp://ftp.support.acer-euro.com/notebook/travelmate_2410/driver/Wireless%20Lan%2080211bg.zip)

---

### Post by tturrisi on 2006-12-14
> **FrodoB said:**
> Have you tried this recommended driver?

[ftp://ftp.support.acer-euro.com/notebook/travelmate_2410/driver/Wireless%20Lan%2080211bg.zip](ftp://ftp.support.acer-euro.com/notebook/travelmate_2410/driver/Wireless%20Lan%2080211bg.zip)

That's a broadcom driver for broadcom chipsets,  it won't work with atheros chipsets.

---

### Post by FrodoB on 2006-12-14
Actually it is a zipped file that contains both. There is the Broadcom driver along with a Foxconn driver for the AR5005G devices, so it is the right archive to get.  Once you have the Foxconn driver you will have to get into it with unshield which you need to install with atp-get:

sudo apt-get update
sudo apt-get install unshield

Unzip the thing and inside the Foxconn section you need to unshield x data2.cab and look inside Driver_Files_NDIS5 

Give it a try. This is what some folks are saying works on the ndiswrapper list.

Good luck.

---

### Post by FrodoB on 2006-12-14
Well actually it is both in one zip archive, see instructions.

> **tturrisi said:**
> That's a broadcom driver for broadcom chipsets,  it won't work with atheros chipsets.

---

### Post by FrodoB on 2006-12-14
Also search for AR5005G in this page:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

There are a lot of success reports.

---

### Post by spacetree on 2007-02-12
here ive got the same problem: My laptop is an acer aspire 5100-5325 (64x2 turion, ati radeon x1100... and the ATHEROS 802.11 b/g wireless.

The thing is, that it worked perfectly on DAPPER, and when i switched to edgy  and downloade the network manager, IT SHOWS ME THE NETWORKS, but it can connect. I supposedly installed both the acer_acpi and madwifi drivers, but loading the drivers just dont  do anything. Here i post some outputs that i think that may be usefull:


saul@saul-laptop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:16:CF:87:8C:25  
          inet6 addr: fe80::216:cfff:fe87:8c25/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:16:D4:57:4B:2A  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:50 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-16-CF-87-8C-25-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20207 errors:0 dropped:0 overruns:0 frame:56985
          TX packets:870 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:1986665 (1.8 MiB)  TX bytes:40088 (39.1 KiB)
          Interrupt:233 Memory:ffffc20000060000-ffffc20000070000 

saul@saul-laptop:~$ dmesg | grep acer
[  287.379828] acer_acpi: Acer Laptop ACPI Extras version 0.3
[  287.379841] acer_acpi: No WMI interface, unable to load.
saul@saul-laptop:~$ 



saul@saul-laptop:~$ dmesg | grep ath
[  119.864048] ath0: no IPv6 routers present
[  531.847830] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[  536.948184] ath0: no IPv6 routers present
[  574.128081] ath0: no IPv6 routers present
[ 1652.832041] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[ 1657.993889] ath0: no IPv6 routers present
[ 1695.979853] ath0: no IPv6 routers present
[ 1726.907050] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[ 1733.310616] ath0: no IPv6 routers present
[ 1770.054215] ath0: no IPv6 routers present

ANY help will be apreciated

---

