---
title: "IBM X30 Prism Wireless not working - Dapper Drake and Feisty Fawn"
date: 2007-05-25
forum: Networking &amp; Wireless
---

### Post by jzerocsk on 2007-05-25
I've tried a whole lot of things that I found both here and elsewhere, but so far I have not been able to get my IBM X30's Prism2.5 wireless card to do a thing.  After reading about some wireless issues in Feisty, I decided to try Dapper after reading that the Prism cards may work more easily, but I'm not having any luck.

Currently I'm running Dapper Drake, although if someone can give me some hot leads for Feisty Fawn, I can easily reload that.

Ideally I want to connect to a network that uses PEAP authentication, but I am currently trying to connect to a non-encrypted network.  The only restriction on this network is that the SSID is not being broadcast.  

I have installed network-manager in Dapper, but it does not give me the ability to connect to a wireless network, even if I unplug the wire and reboot.  Also, if I go into the network control panel (Administration->Networking), even if I just cancel and make no changes, suddenly iwconfig shows no wireless extensions for any interface and iwlist scan shows no scanning support available for any interface.  

Anyway, here is some relevant information....

Result of *lspci*:```

0000:01:02.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
```

Result of *lsmod*:
```
hostap_pci             56848  0
hostap                119428  1 hostap_pci
...
orinoco_pci             7168  0
orinoco                43156  1 orinoco_pci
hermes                  7808  2 orinoco_pci,orinoco
```
 
Result of *iwconfig*:
```
lo        no wireless extensions.

irda0     no wireless extensions.

eth0      no wireless extensions.

wifi0     IEEE 802.11-DS  Mode:Managed

wlan0     no wireless extensions.

sit0      no wireless extensions.
```

Result of *iwlist scan*:
```
lo        Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning : Network is down

wlan0     Interface doesn't support scanning.

sit0      Interface doesn't support scanning.
```


Result of *lshw -C network*:
```
  *-network:0 DISABLED
       description: Ethernet interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 2
       bus info: pci@01:02.0
       logical name: wifi0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list logical ethernet physical
       configuration: broadcast=yes driver=hostap_pci multicast=yes
       resources: iomemory:f8000000-f8000fff irq:11
```

Contents of /etc/network/interfaces:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

I appreciate any suggestions!  I am already running linux full time at home...success in this endeavor will allow me to also use linux at work!
Thanks!

---

### Post by matoxxx on 2007-05-25
```
blacklist hostap 
blacklist hostap_pci
blacklist prism2
blacklist prism2pci
```

add this into yours **/etc/modprobe.d/blacklist file**

it works i have conection after setting up network, but with issues on feisty, network manager isnt working for me ...

---

### Post by chili555 on 2007-05-25
I believe it is *prism2_pci* and not *prism2pci.* As well, I think it will work fine with only prism2_pci blacklisted.

---

### Post by jzerocsk on 2007-05-29
> **chili555 said:**
> I believe it is *prism2_pci* and not *prism2pci.* As well, I think it will work fine with only prism2_pci blacklisted.

Blacklisting prism2 and prism2_pci did not seem to help in Feisty Fawn.  

I did not bother blacklisting them in Dapper since they did not appear at all when running lsmod, but I will give it a whirl later today.  I had to switch back to Windows so that I could get some work done.

I tried alternately blacklisting the hostap drivers and the orinoco drivers in Dapper.  When I blacklist orinoco, the wifi0/wlan0 items disappear completely from network-manager.  When I blacklist hostap, it appears to work the same as not blacklisting anything.

If there are other suggestions in the meantime....I'm all ears.

Thanks!

---

### Post by chili555 on 2007-05-30
> *-network:0 DISABLEDFrom *lshw.* Wonder what this means. Is there a switch or key combination that is supposed to turn the wireless onn and off? You might also have a look at:```
sudo cat /var/log/messages | grep -i Kill
```

---

### Post by russgalleywood on 2007-05-30
Hi Guys,

i don't know whether this is of any help but am so pleased at finally getting my Wireless card to work with Ubuntu that I thought I'd share it with others who might need it!

I have a Prism GT card and although it was flashing away it would not connect on Dapper Drake! I thought it was on eth1 but when I looked in /etc/network/interfaces there was no entry for eth1! So, i just added;

[B]auto eth1
iface eth1 inet dhcp[/B]

Then I typed in **sudo ifup eth1** at the CLI and the Network connection bar at the top right turned green for the first time ever!

Still wouldn't connect though but suddenly my Access Point appeared in Wifi Radar. So I went into the Networking tool in the Administration section and simply enabled the Wireless connection which was turned off in there. I then put in the details of my AP and suddenly it connected! I am now on the Internet and it survived a reboot!

This might all seem complete nonsense but I thought I'd post it just in case it helps anyone else.

---

### Post by jzerocsk on 2007-05-30
> **chili555 said:**
> From *lshw.* Wonder what this means. Is there a switch or key combination that is supposed to turn the wireless onn and off?
I thought that was weird, too.  There was another thread I was reading where someone had a similar problem.  You were actually helping him out, then he suddenly came back and had it working, but didn't really indicate what he did.  

I did double-check that there isn't a way to disable the wireless either by a switch or a key combo and I confirmed that my X30 has no such mechanism, so at least that possiblity can be ruled out.

> You might also have a look at:```
sudo cat /var/log/messages | grep -i Kill
```

Thanks for the tip...I'll give that a whirl tomorrow.  Unfortunately "real" work has prevented me from doing any further experimentation since last week. :(

---

### Post by jzerocsk on 2007-06-04
OK After reaching many dead ends, I decided to try using ndiswrapper over the native drivers.

I am currently using Feisty Fawn.

I was able to successfully load my Win32 drivers:

sudo ndiswrapper -l:
```
imwebn51.sys : driver installed
        device (1260:3873) present (alternate driver: orinoco_pci)

```

lsmod |grep ndiswrapper:
```

ndiswrapper           194608  0 
usbcore               134280  3 ndiswrapper,uhci_hcd

```

That usbcore bit may be part of the problem.  AFAIK it's hooked to the PCI bus.

iwconfig:
```

wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=11 Mb/s   
          Power Management min timeout:0us  mode:All packets received
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

sudo iwlist wlan0 scan:
```
wlan0     No scan results
```
This seems sensible - I do not believe there are any APs in range of my office that broadcast their SSIDs.

But, when I try to connect to the unsecured network using network-manager, it times out.
The messages that appear in the logs are:
```
Jun  4 17:37:46 peasantry-lx dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Jun  4 17:37:46 peasantry-lx kernel: [ 2220.824000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  4 17:37:46 peasantry-lx kernel: [ 2221.000000] ndiswrapper (iw_set_ap_address:650): setting AP mac address failed (C00000BB)
Jun  4 17:38:46 peasantry-lx kernel: [ 2281.056000] ndiswrapper (iw_set_ap_address:650): setting AP mac address failed (C00000BB)
Jun  4 17:38:46 peasantry-lx kernel: [ 2281.088000] ndiswrapper (iw_set_ap_address:650): setting AP mac address failed (C00000BB)

```

The first error message is kind of odd, no?

As always, I appreciate any suggestions!

---

### Post by z_diver on 2007-06-08
Big excitement!  **I got my prism 2.5 working**.  I'll list all the steps I did as I'm not sure exactly what did it as it didn't come up in network manager or anything else until a reboot.

For the record I have a IBM R31 but *lspci* listed it the same as on jzerocsk's original post and all the rest of my printouts came out very similar.

1) blacklisted in **/etc/modprobe.d/blacklist file**```
blacklist hostap 
blacklist hostap_pci
blacklist prism2
blacklist prism2pci
blacklist prism2_pci
```2. added this to **/etc/network/interfaces** because only had eth0 and eth2```

# wireless entry for the prism 2.5 card
auto wlan0 
iface wlan0 inet dhcp
```3.  At that point I tried to bring up the interface using *sudo ifup wlan0* which didn't work so I decided to reboot with the blacklisted modules and everything worked as normal.  I saw 4 networks in Network Manager and with just my password it connected.  No key was necessary due to the fact I had it working in Dapper.

Good luck everyone.

---

### Post by z_diver on 2007-06-08
I just noticed that my prism is listed as **eth1** and not **wlan0** when I run [I]**sudo lshw -C network**[B].

[/B][/I]Therefore I question my addition to **/etc/network/interfaces** in the post above but I don't know where Network Manager pulls it's devices from if not there.  Maybe someone reading this will.

---

### Post by matoxxx on 2007-06-16
[http://ubuntuforums.org/showthread.php?t=475753](http://ubuntuforums.org/showthread.php?t=475753)

i wrote small how to, might interrest Prism card owners

---

