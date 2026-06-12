---
title: "no wireless in 6.10"
date: 2007-03-21
forum: Networking &amp; Wireless
---

### Post by kpjoyce on 2007-03-21
My wireless card does not work under 6.10.  It worked on the liveCD for 6.06, but not on my installation of Edgy.  The connection shows up in gnome in my list of network devices, but cannot be activated.

output from lshw:
> 
           *-network:1 DISABLED
                description: Wireless interface
                product: AR5211 802.11ab NIC
                vendor: Atheros Communications, Inc.
                physical id: a
                bus info: pci@02:0a.0
                logical name: wifi0
                version: 01
                serial: 00:90:96:3d:73:6a
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath_pci multicast=yes wireless=IEEE 802.11b
                resources: iomemory:fcee0000-fceeffff irq:11

output from iwconfig:
> 
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11b  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:0 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


trying to scan for networks:

> kpjoyce@kpjoyce-laptop:~$ iwlist wifi0 scan
wifi0     Interface doesn't support scanning.

kpjoyce@kpjoyce-laptop:~$ iwlist ath0 scan
ath0      No scan results

There seems to be disagreement about the name of my wireless card.  lshw thinks it is wifi0, and iwconfig thinks it is ath0.  When things work in 6.06, everyone agrees that the name is ath0.

What can I do next to try and get things working?  Thank you.

---

### Post by spd106 on 2007-03-21
[QUOTE=kpjoyce]output from lshw:> *-network:1 DISABLED[/QUOTE]The interface hasn't been activated. Try running this command```
sudo ifconfig ath0 up
```

There may be a line missing from your /etc/network/interfaces file, it should contain auto ath0, which ensures that the card is activated at boot.

---

### Post by kpjoyce on 2007-03-21
Great!  thank you for your reply.  Your suggestions helped, but I'm not there yet.

after your ifconfig command, the device no longer was disabled, and I could scan for networks.  The network connection still does not work, however.

my /etc/network/interfaces file:

> auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto wlan0
iface wlan0 inet dhcp




auto eth0

iface ath0 inet dhcp
wireless-essid Robbins Network

auto ath0

'Robbins Network' is a network that is typically available here, but is not one I intend to use.

---

### Post by stchman on 2007-03-21
> **kpjoyce said:**
> My wireless card does not work under 6.10.  It worked on the liveCD for 6.06, but not on my installation of Edgy.  The connection shows up in gnome in my list of network devices, but cannot be activated.

output from lshw:


output from iwconfig:


trying to scan for networks:



There seems to be disagreement about the name of my wireless card.  lshw thinks it is wifi0, and iwconfig thinks it is ath0.  When things work in 6.06, everyone agrees that the name is ath0.

What can I do next to try and get things working?  Thank you.


Go to the Synaptic Package Manager and install the restricted module.  Type Atheros in the search box.  This will give you results and you can install a new kernel 2.6.17-11-i386 I believe it is.  This kernel supports Atheros (somewhat) wireless cards.

That kernel supports my plug in 5005G but not the built in 5006EG card.  I am waiting for Feisty as it supports the built in wireless OOB.

Hope this helps.

---

### Post by kpjoyce on 2007-03-21
thank you for your help.

I think that I may have a chicken-and-egg problem with installing packages and getting my wireless network up.

And could it be a matter of kernel compatibility when ubuntu 6.06 runs my wireless card just fine?

thanks again.

---

### Post by stchman on 2007-03-21
> **kpjoyce said:**
> thank you for your help.

I think that I may have a chicken-and-egg problem with installing packages and getting my wireless network up.

And could it be a matter of kernel compatibility when ubuntu 6.06 runs my wireless card just fine?

thanks again.

What kernel is your 6.06 using?  Type uname -a in terminal.

I personally am waiting for Feisty.

---

### Post by spd106 on 2007-03-21
> could it be a matter of kernel compatibility when ubuntu 6.06 runs my wireless card just fine?

You have all of the right packages installed or you wouldn't have been able to get this far. It's more likely that you need to either change the ssid to another network or add an encryption key. The network-admin capplet will be able to assist in this, unless you need WPA, then Network Manager would be a better choice. Perhaps look at this wiki page [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager).

Please bear in mind that in the transition to Edgy the madwifi driver was changed to madwifi-ng, this is where the wifi0 interface comes from. The side effect of this was that adhoc/monitor/master modes are not available anymore (without extra tools).

One more thing, make sure that you have the linux-restricted-modules-generic package installed in order to make future updates run smoothly.

---

### Post by kpjoyce on 2007-03-21
To  be clear: this was not an update from 6.06 to 6.10.  This is a fresh install of 6.10 from the cd.  I was playing around with running 6.06 from the liveCD, which is how I know that it works.  the kernel on the 6.06 liveCD is 2.6.15.24.

I'm pretty confident that network security and encryption are not the issue.  I have been able to use this wireless network without it.

How would I force the wireless adapter's logical name to be ath0 and not wifi0?  I'd like to try that. Or is this not an issue, just the result of the driver change you mentioned?

I'm also tempted to just install the working 6.06, and then try the update to 6.10.

Again, thanks for working with me on this.

---

### Post by spd106 on 2007-03-21
Assuming you are trying to connect to the Robbins Network, you cannot have spaces in the ssid in the interfaces file. Instead you must wrap it in quotes (I'm not sure whether single or double). 
It's a known bug [https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/50386](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/50386)

---

