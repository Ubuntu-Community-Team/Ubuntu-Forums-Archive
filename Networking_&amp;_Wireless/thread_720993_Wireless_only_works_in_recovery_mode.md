---
title: "Wireless only works in recovery mode"
date: 2008-03-10
forum: Networking &amp; Wireless
---

### Post by vikram on 2008-03-10
Weird problem - I am using a Trendnet TEW-424UB usb network card using ndiswrapper. This never works using a normal mode but works perfectly fine in recovery mode.
```

root@vikram-desktop:/data/software# uname -r
2.6.22-14-generic
root@vikram-desktop:/data/software# ndiswrapper -l
sis163u : driver installed
        device (0457:0163) present
root@vikram-desktop:/data/software# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"1234"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1E:C7:88:AA:69
          Bit Rate=54 Mb/s   Tx-Power:17 dBm   Sensitivity=0/3
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:57/100  Signal level:-59 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2522  Invalid misc:51379   Missed beacon:0

root@vikram-desktop:/data/software# cat /etc/network/interfaces
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
#iface eth0 inet dhcp

auto eth1
#iface eth1 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp


#iface wlan0 inet dhcp


iface wlan0 inet dhcp
wireless-essid 1234
wireless-channel 6
wireless-mode managed

auto wlan0

```

I have currently  turned off encryption. Any idea how I can work in regular mode so that I dont have to work as root ?

if this helps unless I am in recovery mode commands like ifconfig, iwconfig and even sudo su hang and never return. The machine doesnt shutdown and I have to do SysRq REISUB to reboot.

This card used to work with Opensuse using ndiswrapper

Thanks in advance for your help

---

### Post by rustybronco on 2008-03-12
> **vikram said:**
> Weird problem - I am using a Trendnet TEW-424UB usb network card using ndiswrapper. This never works using a normal mode but works perfectly fine in recovery mode.
```

root@vikram-desktop:/data/software# ndiswrapper -l
[b]sis163u : driver installed
        device (0457:0163) present[/b]
root@vikram-desktop:/data/software# iwconfig

wlan0     IEEE 802.11g  ESSID:"1234"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1E:C7:88:AA:69
          Bit Rate=54 Mb/s   Tx-Power:17 dBm   Sensitivity=0/3
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:57/100  Signal level:-59 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          **Tx excessive retries:2522  Invalid misc:51379**   Missed beacon:0

```

I have currently  turned off encryption. Any idea how I can work in regular mode so that I dont have to work as root ?

if this helps unless I am in recovery mode commands like ifconfig, iwconfig and even sudo su hang and never return. The machine doesnt shutdown and I have to do SysRq REISUB to reboot.

This card used to work with Opensuse using ndiswrapper

Thanks in advance for your helpNo answer to this problem?
was this a fresh install or did it work at some time with this adapter?
my gut feeling if it is a fresh install, either the 7.10 install or ndiswrapper install  is corrupt or possibly the wrong driver is being used as shown by the high invalid misc (other things could be causing it also ).
if 7.10 does/did work with another adapter then try removing and re-installing ndiswrapper.

***edit*** although it does look like the correct driver is installed for your device i.d.

---

### Post by vikram on 2008-03-12
> **rustybronco said:**
> No answer to this problem?
was this a fresh install or did it work at some time with this adapter?
my gut feeling if it is a fresh install, either the 7.10 install or ndiswrapper install  is corrupt or possibly the wrong driver is being used as shown by the high invalid misc (other things could be causing it also ).
if 7.10 does/did work with another adapter then try removing and re-installing ndiswrapper.

***edit*** although it does look like the correct driver is installed for your device i.d.

Thanks for responding rustybronco

I'm having trouble reproducing this error. Sometimes it works and sometimes it doesn't.  I will try reinstalling ndiswrapper from the repos this evening.

This is not a fresh install - I've been using Kubuntu for almost 2 years. Due to some unrelated network changes at home I had to shift from wired to wirless networking. This particular wirless adaptor worked with ndiswrapper when I was using openSuse in 2005.  Since I couldnt get to the network to install ndiswrapper wrapper from the repos I  downloaded it fromt the source forge site using my work laptop (thankfully the proprietary os on the laptop didnt crash for a few hours) and installed the latestest stable version.

---

### Post by rustybronco on 2008-03-12
just another meaningless thought, be sure to remove ndiswrapper completely first, then if possible cable to the router, download and install it.
anything in the log's ?

---

### Post by vikram on 2008-03-17
> **rustybronco said:**
> just another meaningless thought, be sure to remove ndiswrapper completely first, then if possible cable to the router, download and install it.
anything in the log's ?

I finally got to this over the weekend. Installed and reinstalled ndiswrapper repeatedly from the repos. Also unplugged the cable. It ***seems* **to work after repeated 
make uninstall  and installs. I say seems because sometimes it does and sometimes it doesn't. I'm going to make sure it works over the next few days. will update this soon.

---

### Post by vikram on 2008-03-20
I tested this repeatedly and it works almost every other time which makes it hard to trouble shoot :(

if it helps I get this message on dmesg

ndiswrapper (iw_get_network_type:258): getting network type failed: C0000001

---

### Post by vikram on 2008-03-23
bump.

somebody  help ?

---

