---
title: "Creating separate IP address for bridge"
date: 2022-01-13
forum: Networking &amp; Wireless
---

### Post by smbunn on 2022-01-13
I have an ethernet connection to my Ubuntu 20.04 installation.  It used to use 192.168.1.38 as an IP address assigned via DHCP from my router.  The router has the mac address in its table of pre-assigned IP addresses.

Inside the Ubuntu machine I am running KVM and one of my KVM VMs has a virtual NIC which uses BR0, my pre-created bridge.  This was setup in /etc/netplan/01-network-manager-all.yaml

I want the KVM VM to use 192.168.1.22.  I have also set this up in my router as a static IP address linked to the MAC address of the VM NIC.

I have netplan, and the renderer was networkd.  However I recently moved my router to 192.168.1.1 (it was .2) and now my KVM VM no longer sees the Internet.  I assume this is because the gateway is still set as 192.168.1.2 and hence it has no access and no DNS lookup.

I decided to change netplan to use NetworkManager and changed that one line and applied.  The result is I have lost 192.168.1.38 (the ubuntu server) but can still see and access .22, but still have no internet access.
I assume I am going to have to physically plug in a keyboard, mouse and monitor to fix this.

I also have no idea how I use networkmanager.  Any easy guide on how to have a bridge to my physical nic on the host, where the bridge has its own separate IP address?

thanks

Simon

---

### Post by Tadaen_Sylvermane on 2022-01-14
You will need local access if you have no remote.

You do not need the bridge to have it's own ip. Consider.

```
network:
 version: 2
 renderer: networkd
 ethernets:
  eth0:
   dhcp4: false
 bridges:
  br0:
   dhcp4: true
   interfaces: [eth0]
```

Assuming the ip assignment is done from your dhcp server then that is the ip you access the host at. Any vm connected to said bridge will effectively just be another machine on the lan. No special config needed. If you want the dhcp server to give them static ip's then put vm mac on dhcp server like any other machine.
*EDIT* For the record you are likely best served by assigning the static ip to the host / bridge manually in the netplan file rather than the dhcp. If the dhcp is down then you've got nothing.

---

