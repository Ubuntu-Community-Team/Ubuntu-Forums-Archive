---
title: "eth1 interface shows as Ethernet"
date: 2005-04-17
forum: Networking &amp; Wireless
---

### Post by nageshtv on 2005-04-17
hi all,

I have recently installed Ubuntu (hoary hedgedog) and my laptop has an intel pro wireless 2100 driver. The device is detected and configured to use the network interface "eth1". However, I am not able to use wireless because the device type shows as "Ethernet". I checked this in the "System->Administration->Device Manager" interface.

 net.media string Ethernet

I have not been able to find any place to change that "Ethernet" to "Wireless". I would appreciate any help in this regard.

Is there a way I can un-install the ipw2100 module and re-install it ? I need to use wireless. 

My /etc/network/interfaces file has the following information:

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth1

iface eth1 inet dhcp
        wireless_essid Ensemble
        wireless_key 1DCF4AD62A

auto eth1

iface eth0 inet dhcp

auto eth0

Thanks
Nagesh

---

### Post by soul_rebel on 2005-04-18
I suppose that wireless interfaces need to be wlan* not eth*... maybe this is the problem

---

### Post by nageshtv on 2005-04-18
The wireless interface would be wlan* if ndiswrapper is used. The 5.04 version has the intel linux driver (ipw2100) for my wireless card and this configures eth1 instead of wlan*

I was able to use the wireless interface when I first installed ubuntu. But, once I connected thru Ethernet, my wireless doesnot work anymore bcos eth1 has changed to be of type "Ethernet". I dont know how to change the device type setting. 

In Fedora, the "Network Device Control" would let me configure a device (eth0,eth1,wlan*)  as wired/wireless and associate with the right adapter (Alternatively, using /etc/network-scripts/ifcfg-eth1). I do not see a way to do this in ubuntu.

Need to have wireless working please. 

Nagesh

---

