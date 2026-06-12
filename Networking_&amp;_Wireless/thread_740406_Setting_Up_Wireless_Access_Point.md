---
title: "Setting Up Wireless Access Point"
date: 2008-03-30
forum: Networking &amp; Wireless
---

### Post by downsideup16 on 2008-03-30
I've tried following the two community documents [WifiDocs/WirelessAccessPoint]("https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint") and [Router]("https://help.ubuntu.com/community/Router") as well as a couple pages I found with google and I still can't get an access point running. When searching for a wireless connection with another computer it finds a BRCM_TEST_SSID that I'm unable to connect to. I installed the firmware for the wireless card with the restricted device manager and it says Broadcom 43xx chipset. The output from lspci is ```
02:0b.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
```


eth0 is my wired connection to the broadband and eth1 is the wireless card. 
Here's the different file configurations I have and hopefully someone can point out what I'm doing wrong.

/etc/network/interfaces
```
# Set up the local loopback interface 
auto lo
iface lo inet loopback

# Set up the external interface
#
# Don't forget to change eth0 to the proper name of the external
# interface if applicable.
#
auto eth0
iface eth0 inet dhcp


# Set up the internal wireless network 
#
# Don't forget to change wlan0 to the proper name of the internal
# wireless network interface if applicable.
#
# If you would like to use WEP, uncomment the line 'wireless-key'
# and replace '<key goes here>' with a WEP key.
# 
# You may also change the network essid and channel.
#
auto eth1
iface eth1 inet static
    wireless-mode master
    wireless-essid UbuntuWireless
    wireless-channel 1
    wireless-key  6bbc6ea50ac4107e874913a5d7
    address 10.1.1.1
    network 10.1.1.0
    netmask 255.255.255.0
    broadcast 10.1.1.255

```

iwconfig output
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"UbuntuWireless"  Nickname:"Broadcom 4306"
          Mode:Master  Frequency=2.472 GHz  Access Point: Invalid
          Bit Rate=1 Mb/s   Tx-Power=19 dBm
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by pseudo-random on 2008-03-30
Careful you don't post your IP there. I believe thats classed as personal info.

---

### Post by dstew on 2008-03-30
Just a few things I see. First, you need to set up your domain-name servers. You have left the default values only:> # option definitions common to all supported networks...
option domain-name "example.org";
option domain-name-servers ns1.example.org, ns2.example.org;
If this is the real DHCP server, you need to make it authoritative. It is not:```
# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
#authoritative;
```Do you possibly have another competing DHCP server on your network? If your DSL modem serves addresses, you need to disable it. Also, if you put the domain-name servers address up top, I think you can eliminate this line in your DHCP subnet definition:```
option domain-name-servers 10.1.1.1;
```I don't think that could possibly be a correct domain-name server address. It is your router address.

---

### Post by downsideup16 on 2008-03-30
My wired connection is to a DHCP router. I made the changes to the dhcpd.conf it didn't change anything.

---

### Post by downsideup16 on 2008-03-31
So I figured out that my card is broadcasting a signal but its not the one i configured. It shows as BRCM_TEST_SSID and i'm unable to connect to it. Is this a driver problem? I have the Broadcom 43xx chipset firmware installed through the restricted drivers manager.

---

