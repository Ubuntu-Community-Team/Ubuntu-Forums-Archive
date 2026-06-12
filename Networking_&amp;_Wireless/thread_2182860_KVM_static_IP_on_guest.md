---
title: "KVM static IP on guest"
date: 2013-10-22
forum: Networking &amp; Wireless
---

### Post by darkapec on 2013-10-22
I am sure this question has been asked a thousand times. However I have  been unable to locate any relevant info via google or ubuntu forums.

My setup is as follows;```


[B]Host
(/etc/network/interfaces)[/B]


# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet static

address 192.168.1.150
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
dns-nameservers 192.168.1.1

[B]Guest
(/etc/network/interfaces)[/B]

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static

address 192.168.1.145
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
dns-nameservers 192.168.1.1

```

With the above code the host has no problems connecting to the internet /  local network. However the guest is unable to reach local or internet.  If I change the guest OS to DHCP like so; 

```

# The primary network interface
auto eth0
iface eth0 inet dhcp

```

Everything works fine on the host and guest. Am I missing something? 

Thanks

---

### Post by darkapec on 2013-10-22
I changed the host to;

```


# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto br0
iface br0 inet static
        address 192.168.1.150
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        bridge_ports eth1
        bridge_stp off
        bridge_maxwait 5
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.1.1

```

The host still works fine, however the guest is not working in DHCP or static now

---

### Post by darkapec on 2013-10-22
Another update,

further investigation shows that when using DHCP on the guest OS the ip is in the 192.168.122.XXX range. Does anyone know how to change this to a 192.168.1.XXX range?

---

### Post by houstonbofh on 2013-10-22
You are binding the guest to the virtual network device, and you need to bind it to the bridge.  How are you managing your guests?

---

### Post by darkapec on 2013-10-23
Hi thanks for the reply,

I am managing my guest with virt-manager. It appears to be an issue with the iptables / virbr0 address range. I am currently googling to see how to change virbr0 address range.

---

### Post by darkapec on 2013-10-23
well, that did no seem to work either. I found out I could edit virbr0 by accessing "virsh net-edit  default" however after I edited that file the virbr0 will not start because it is in the same range as br0. So I guess I am back to square one. How can something so simple be such a pain?? If anyone has some configs of a working guest static IP i would like to reference them.

---

### Post by darkapec on 2013-10-23
ok this was way easier then I thought. If anyone else has the above problem the solution is actually quite simple. 

setup the host as I have above 
```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto br0
iface br0 inet static
        address 192.168.1.150
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        bridge_ports eth1
        bridge_stp off
        bridge_maxwait 5
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.1.1

```

After creating the bridge on the host restart the machine. Verify you still have internet / intranet after the reboot. 

Run the following to verify the ip address is now binded to br0 instead of eth0 / eth1
```

ifconfig

```

Then open virt-manager, shutdown the guest OS if it is still running. Then go to "edit" and select "virtual machine details" then select the blue icon "virtual machine hardware details". On the left side click "NIC" change "source device" to "specify shared device name." Then type br0 in the text box.

Upon starting the guest host, I am now within the range I would like to be and able to specify a static ip by editing /etc/network/interfaces.

---

