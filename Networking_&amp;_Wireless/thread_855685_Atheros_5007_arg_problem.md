---
title: "Atheros 5007 arg problem"
date: 2008-07-10
forum: Networking &amp; Wireless
---

### Post by libertas on 2008-07-10
ive tried a number of solutions each which have worked for a bit before either an update screwed them up or they just stopped working

ive tried

sudo aptitude update && sudo aptitude -y install build-essential linux-headers-$(uname -r)
cd ~
wget -O driver.tar.gz [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)
tar xf driver.tar.gz
cd madwifi-*
make
sudo make install
echo ath_pci | sudo tee -a /etc/modules
sudo modprobe ath_pci

and the official one from the administrators which looks similar to this

they each have worked before but won't work now
the wireless card does not even see wirless networks any longer, there was a bit where it would see them but could not access them and then a bit where it asked for the wirless WPA password again and again and then finally it just didn't see anything

this is what i get when i run iwconfig in the terminal

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


I can't understand all of it but it looks bad to me, any ideas?

also this is what i get when i run "sudo lshw -C network" in the terminal

 *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:1b:24:43:f6:bf
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=192.168.1.101 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:19:7e:84:5e:40
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g


please help, i really need my wireless internet :( :)

---

### Post by libertas on 2008-07-10
those :O or :o i don't really know faces in the middle are actually :  O

---

