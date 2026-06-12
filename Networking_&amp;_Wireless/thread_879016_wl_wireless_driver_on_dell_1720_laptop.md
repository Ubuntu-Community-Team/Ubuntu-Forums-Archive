---
title: "wl wireless driver on dell 1720 laptop"
date: 2008-08-03
forum: Networking &amp; Wireless
---

### Post by Alexander Dreyzen on 2008-08-03
Hi everybody,

I installed 8.04 on Inspiron 1720. Everything works great except wireless. The wl driver is shown in system->administration-hwdrivers as checked enabled and in use. 

lshw -C network
  *-network               
       description: Wireless interface 
       product: BCM4310 USB Controller 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:0c:00.0 
       logical name: eth1 
       version: 01 
       serial: 00:16:44:c5:6d:c8 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11bg 

sudo iwlist scan
          Cell 03 - Address: 00:14:6C:DB:69:D0 
                    ESSID:"NETGEAR" 
                    Mode:Managed 
                    Frequency:2.462 GHz (Channel 11) 
                    Quality:5/5  Signal level:-44 dBm  Noise level:-15 dBm 
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s 
                              48 Mb/s; 54 Mb/s 
sudo iwconfig


I setup the system->administration->network (ESSID:NETGEAR, WEP(HEX):key, auto(DHCP))

sudo iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

eth1      IEEE 802.11bg  ESSID:"NETGEAR"  Nickname:"" 
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 5E:5D:7A:DC:5D:C7   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality=5/5  Signal level=-57 dBm  Noise level=-92 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

Everything seems to be recognized, but no wireless (no internet when disconnect from the wire).

Here are wireless relevant lines from syslog on boot:

Aug  3 11:34:21 inspiron-1720 kernel: [   23.125343] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.18.0

Aug  3 11:34:46 inspiron-1720 avahi-daemon[5164]: Registering new address record for fe80::216:44ff:fec5:6dc8 on eth1.*.

Aug  3 11:34:49 inspiron-1720 hcid[5432]: Default passkey agent (:1.22, /org/bluez/passkey) registered

Aug  3 11:34:49 inspiron-1720 hcid[5432]: Default authorization agent (:1.22, /org/bluez/auth) registered

Aug  3 11:34:50 inspiron-1720 NetworkManager: <info>  Updating allowed wireless network lists.

Aug  3 11:34:50 inspiron-1720 NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored..

Aug  3 11:34:55 inspiron-1720 kernel: [   47.193727] eth1: no IPv6 routers present

Aug  3 11:39:26 inspiron-1720 anacron[5549]: Job `cron.daily' started

Aug  3 11:39:26 inspiron-1720 anacron[6210]: Updated timestamp for job `cron.daily' to 2008-08-03


I don't want ndiswrapper suggestions. I want the native wl driver to work. It's a shame that so many people have to waste so much time to get the wireless to work on Linux. 

Thanks for your help,

---

### Post by Alexander Dreyzen on 2008-08-03
Just noticed iwconfig lists eth1 as Ad-hoc, when I 

sudo iwconfig eth1 mode Managed

I get:

Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Invalid argument.

---

### Post by isendel123 on 2009-03-11
OMG. I have spent so much time trying to get this wireless from my 1720 to work. I have both OS's (Vista and Ubuntu) installed. I don't have physical access to the router (ethernet cable). I need a simple and "noobish" proccedure to get my wireless NIC to work. I am not familiar with any of this Ubuntu or Linux. I need a step by step way to get this working. I only have internet access when booting windows thx to the fact that IT DOES recognize the WNIC and makes things easy. It's a pitty that things like these make ppl not want to get into Linux. What a pitty. I simply hate windows and that is why I wanna try this. But I think I won't have other options if it's going to be like this for every single driver.  :(

---

