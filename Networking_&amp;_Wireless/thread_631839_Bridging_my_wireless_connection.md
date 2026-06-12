---
title: "Bridging my wireless connection"
date: 2007-12-04
forum: Networking &amp; Wireless
---

### Post by jckdnk111 on 2007-12-04
I'd like to run qemu or virtualbox to have a copy of windows running inside my Ubuntu Gutsy Gibbon host. The reason for running windows is to be able to run a proprietary vpn client which only supports windows (won't install with wine).

The vpn client needs various tcp / udp ports and ipsec support which I'm unable to get working in qemu's usermode environment or virtualbox's nat environment. My only other option is creating a tap interface and then bridging my wireless connection with the tap interface as I understand it.

I'm having a difficult time understanding the bridging / getting it to work.

My wireless card is called eth2 and requires an essid / wep key to grab an ip via dhcp.
So here is what I've done so far:

1) sudo ifconfig eth2 0.0.0.0
2) sudo brctl addbr br0
3) sudo brctl addif br0 eth2
4) sudo ifup br0

My /etc/network/interfaces file looks like this:
auto br0
iface br0 inet static
address 192.168.1.1      # I have no idea why I'm assigning this ip (or any ip)?
network 192.168.1.0
netmask 255.255.255.0
broadcast 192.168.1.255
bridge_ports eth2
up /sbin/iwconfig eth2 essid my_ess_id_here && /sbin/iwconfig eth2 key my_wep_key_here

Everything come up OK, but I can't get out to the internet after creating the bridge?
I can't connect to the internet on the guest OS or the host OS?
My lan ip for eth2 normally looks something like 10.0.0.8.
I have an Intel 3945abg wireless card and I've read it supports promiscuous mode (it doesn't throw and error when I add 'promisc' to step 1 above)
I don't understand how the bridge is supposed to use eth2 to get out to the internet?

Any help would be greatly appreciated.

---

### Post by jckdnk111 on 2007-12-07
No takers ah?
Well  I don't blame you ... I never could figure this out. Perhaps it's not possible with my hardware.

I've heard that wireless cards based on the Prism chipset are good candidates for this type of setup. I'm sure most people do this as an afterthought though, not when they're buying their laptop.

---

### Post by GuySmily on 2007-12-24
I'm trying to do the same thing and cannot for the life of me figure it out.

I'm trying to follow the guide [here](http://ubuntuforums.org/showthread.php?t=346185) but have not been successful.

```
sudo tunctl -t tap0 -u guysmily  # use your Ubuntu login
sudo chmod 666 /dev/net/tun

sudo ifconfig eth1 0.0.0.0 promisc  # use your wireless card for eth1
sudo brctl addbr br0
sudo brctl addif br0 eth1
sudo dhclient br0
```

At this point, dhclient usually fails to get an IP.  It has succeeded a couple of times, but I'm still unable to connect to the internet or ping my wireless router.

It was SO easy with windows.. Select two connections, right click, bridge connections.  Done!

Can someone lend us a hand?

---

### Post by GuySmily on 2007-12-24
Found a solution!  This worked for my needs, though I don't know if it'll work for what you're doing.

These 3 commands replace the ENTIRE Step 2 (Setup Ubuntu Networking)
 
> **sythem said:**
> An alternative to the networking would to be use port forwarding and Nat. Disable the built in remote desktop option and then use these 3 commands with the virtual machine off.

```
VBoxManage setextradata "NameOfTheVirtualMachine" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/remotedesk/Protocol" TCP

VBoxManage setextradata "NameOfTheVirtualMachine" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/remotedesk/GuestPort" 3389

VBoxManage setextradata "NameOfTheVirtualMachine" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/remotedesk/HostPort" <whateverportyouwanttouse>

```

This works with Nat networking and doesn't require any other linux networking configuration. Hope it's helpful.

---

