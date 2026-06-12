---
title: "Netgear WPN311"
date: 2006-09-16
forum: Networking &amp; Wireless
---

### Post by benwad on 2006-09-16
Hi - I'm new to Ubuntu, and generally to Linux as well. Here's my dilemma:

I have a Netgear WPN311 wireless card in my computer, but Ubuntu is not recognising it - the light it on to indicate that it's receiving power but Ubuntu doesn't know it's there. I understand that this is normal - I've heard of something called MadWiFi that could make Ubuntu support this card, however I have no way of connecting to the Internet on this computer so I won't be able to use apt-get. I've got a computer running Mac OS X and a digital camera that can serve as a way to transport data between my Mac and my Ubuntu PC, but I don't know how I can download the necessary things to get MadWiFi to work

Thanks for reading,

Ben

---

### Post by pwall on 2006-11-28
I am running  6.06 and I installed a WPN311 wireless card. Whilst  Ubuntu seems to recognise the card fine.. it can not connect to the   router. The Router is a rangemax WPN824. What is interesting is that the  card connects OK when I boot into windows....
I have configured WEP and the SSID etc .. although even when I turn that off... Ubuntu sees the card but doesnt see the wireless network at all.

I tried the upgrade (AMD64 alternate CD) to 6.10 and it also saw the card but cant see the wireless network
One of the interesting thing I note in windows (which I note again works fine) is that the netgear software says the signal is 50% but the windows ICON says the signal is very weak so Im wondering if the issue is these things need some special propietry program running (Just a guess - I really have no idea !)

Any suggestions appreciated !

---

### Post by FrodoB on 2006-11-28
Publish the following outputs:

lspci

iwconfig

Report which version of Ubuntu you have and which install CD you used: Regular Install CD or Alternate CD.

---

### Post by pwall on 2006-11-30
I installed using AMD64 bit alternate CD 6.10.
It actually connected during the install (well the dhcp bit says it succeeded) 
The wifi card is the netgear WPN311
ifconfig only shows  lo - looback
iwconfig only lists lo, eth0 and eth1 noting for all
"no wireless extensions"
ath0 is not shown

The interfaces file has the entry 
auto atho
iface ath0 inet dhcp 
      wireless-mode managed
      wireless-essid XXXXXX
      wireless-key1 xxxxxxxxx
(im happy to turn wep of initially but not sure HOW to - until I get this fixed I only have command line access)

lspci | grep controller shows
05:07.0 Ethernet contoller: Atheros Communications, Inc. AR5215 802.11abg NIC (rev 01)


*-network:0 UNCLAIMED
    description:Ethernet controller
    product: AR5215 802.11abg NIC
    vendor: Atheros Communications
    physical id:7
     bus info: pci@05:07.0
    version:01
    width: 32 bits
    clock: 33 MHz
    capabilities: bus_master cap_list
    resources: iomemory: d4000000-d400ffff irq:3

attempt to run 
sudo /etc/init.d/networking restart shows
* Reconfiguring network interfaces
Error for wireless request "Set Mode" (8B06) :
  Set failed on device ath0 ; No such device.
Error for wireless request "Set Encode" (8B2A) :
  Set failed on device ath0 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
  Set failed on device ath0 ; No such device.

There is already a pid file /var/run/dhclient.ath0.pid with pid 5798864

Internet Systems consortium DHCO Client V3.0.4
Copyright.....
All rights
For info....

SIOCSIFADDR: No such device
ath0: Error while getting interface flags: No such device
ath0: Error while getting interface flags: No such device
Bind soclet to interface: no such device
failed to bring up ath0

---

### Post by FrodoB on 2006-11-30
For starters try this:

1) Have the install CD ready for use.

2) Open a terminal command prompt and type the following:

$ sudo apt-get install linux-restricted-modules-`uname -r`

The system should present a prompt asking you to insert the install CD, put it in the CD driver that you used for installation and then press enter. 

Apt will find the .deb archives and install them for you. A reboot should result in a system that now sees the cards that worked during the install.

---

### Post by benwad on 2007-05-06
Hi

I'm back from a long time away to have another stab at getting this card to work with Ubuntu

That command for linux-restricted-modules didn't work to get the modules off the CD (6.06 LTS) but I found a directory with the same name on the CD in ~/pool/restricted/l/linux-restricted-modules/ and there was a file called "avm-fritz-firmware-2.6.15-23_3.11+2.6.15.11-1_i386.deb". Should I install that? Or is there something else?

---

### Post by khughitt on 2007-12-20
Anyone able to get this working on Gusty? I have it plugged it, but it isn't being detected.
I'm getting ready to try NDISWRAPPER, but I haven't been able to fine the driver .inf files either.

Any suggestions?

Thanks,

---

