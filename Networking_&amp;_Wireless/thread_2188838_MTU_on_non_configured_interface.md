---
title: "MTU on non configured interface"
date: 2013-11-19
forum: Networking &amp; Wireless
---

### Post by alessandro-macuz on 2013-11-19
Is tehre a way to move this post to the [Networking & Wireless]("http://ubuntuforums.org/forumdisplay.php?f=336") [COLOR=#000000]Forum?
[/COLOR]
I realized later there was a better place.

Sorry for the mistake.

-----------------------------------

Hi all,

I configured sub-interfaces (802.1q) on eth1 interface and assigned IPv4 addresses to them. However I need the interface be able to treat Jumbo frames.
Once the system is up I'm able to perform that via ifconfig but not through /etc/network/interface. Here below the relevant part

[CUT]

# The secondary network interface, carrying VLAN 1 (native) and 32
auto eth1
iface eth1 inet static


#       address 10.42.1.5
#       netmask 255.255.255.0
#       broadcast 10.42.1.255
        mtu 9000


auto eth1.32
iface eth1.32 inet static
        address 10.42.32.5
        netmask 255.255.240.0
        broadcast 10.42.47.255
        vlan-raw-device eth1

How can this be configured?

Thanks,

Alex

---

### Post by varunendra on 2013-11-20
Welcome to the forums Alex!

> **alessandro-macuz said:**
> Is tehre a way to move this post to the [Networking & Wireless]("http://ubuntuforums.org/forumdisplay.php?f=336") [COLOR=#000000]Forum?
[/COLOR]
You can use the "Report Post" button at the bottom of any post to report it to the mods/admins. It can be used for anything that needs a mod action. I'm going to do that for your post now. And by the way, that is not really a mistake that you need to apologize for. :)

> **alessandro-macuz said:**
> .. I need the interface be able to treat Jumbo frames.
Once the system is up I'm able to perform that via ifconfig but not through /etc/network/interface. Here below the relevant part

[CUT]

# The secondary network interface, carrying VLAN 1 (native) and 32
auto **[COLOR="#FF0000"]eth1[/COLOR]**
iface eth1 inet static


#       address 10.42.1.5
#       netmask 255.255.255.0
#       broadcast 10.42.1.255
        **[COLOR="#800000"]mtu 9000[/COLOR]**


auto **[COLOR="#FF0000"]eth1.32[/COLOR]**
iface eth1.32 inet static
        address 10.42.32.5
        netmask 255.255.240.0
        broadcast 10.42.47.255
        vlan-raw-device eth1
From "man interfaces", it seems the above should work as you expect, but I'm not knowledgeable enough to say confidently if its format is entirely correct.
But do you really have two different interfaces with the above highlighted logical names (eth1 and **eth1[COLOR="#FF0000"].32[/COLOR]**)?
Have you manually assigned one of the interfaces that name? How (not that it matters much, just curious about how and why)?

Anyway, another way to set MTU for an interface is to add/edit its udev rule : [https://wiki.archlinux.org/index.php/Network_Configuration#Set_device_MTU_and_queue_Length](https://wiki.archlinux.org/index.php/Network_Configuration#Set_device_MTU_and_queue_Length)

---

### Post by alessandro-macuz on 2013-11-21
Hi Varun,

> **varunendra said:**
> Welcome to the forums Alex!

From "man interfaces", it seems the above should work as you expect, but I'm not knowledgeable enough to say confidently if its format is entirely correct.
But do you really have two different interfaces with the above highlighted logical names (eth1 and **eth1[COLOR=#FF0000].32[/COLOR]**)?
Have you manually assigned one of the interfaces that name? How (not that it matters much, just curious about how and why)?

No, I haven't assigned any name and I rely on the old school ethX, I suspect it might be unappropriated if interfaces come up in a different order one day, but so far I didn't have any problem.

In which way names may help in having the non-configured interface get the correct mtu?

eth1.32 is a sub-interface of eth1 where no traffic must flow on the native vlan, hence no need for the address. However mtu is a property of the physical interface and not of the sub-interface.

I may consider to use names but I wonder if scripts relying on old names fail in case.

> **varunendra said:**
> 

Anyway, another way to set MTU for an interface is to add/edit its udev rule : [https://wiki.archlinux.org/index.php/Network_Configuration#Set_device_MTU_and_queue_Length](https://wiki.archlinux.org/index.php/Network_Configuration#Set_device_MTU_and_queue_Length)

This is totally new to me.

Thing is that I have to apply all of above to a production server very far from me, and I hope you understand :-)

Thanks,

Alex

---

