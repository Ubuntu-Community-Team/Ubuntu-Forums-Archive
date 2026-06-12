---
title: "VirtualBox Networking"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by cold_fu5ion on 2008-05-09
Hi,

I was having some problems getting the internet working with VirtualBox after upgrading to 8.04, so I followed some instruction (which I can no longer find but are similar to [https://help.ubuntu.com/community/VirtualBox#head-ac88c03223e773c78dbb46b4b13c109de1143a03](https://help.ubuntu.com/community/VirtualBox#head-ac88c03223e773c78dbb46b4b13c109de1143a03)
 ) which basically said how to set up a tap and to run a script each time VirtualBox is run.

So it worked (I'm posting them from an XP virtual machine), but now my internet no longer works on my host machine which is rather annoying. So my question is rather vague, but how can I get my networking in Ubuntu again? I know that more information will be needed to diagnose this but I have no idea what is needed.

Any help or advice would be great,

Thanks

---

### Post by revderek on 2008-05-09
Bizarre.

Check that the route still shows correctly for your gateway (route -n should show a default route to the gateway) and that the gateway is accessible.
Check that the DNS server(s) are available (/etc/resolv.conf) and try pinging out onto the internet.

I don't use TAP but NAT as that requires no changes to the underlying network - it does mean that the virtual machines change IP address.

I have not had this issue even running a multiple virtual machine network.

:-) Derek

---

### Post by superprash2003 on 2008-05-09
as mentioned above.. try pinging to your router and say google.com also post ifconfig output

---

### Post by cold_fu5ion on 2008-05-10
Hi,

I can ping any computer and any router on my network but no computer can ping me. Pinging google gives "unknown host"

Th output for ifconfig is:

```
br0       Link encap:Ethernet  HWaddr 00:13:d4:e3:1c:f5  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d4ff:fee3:1cf5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:508 errors:0 dropped:0 overruns:0 frame:0
          TX packets:234 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:116405 (113.6 KB)  TX bytes:29299 (28.6 KB)

eth0      Link encap:Ethernet  HWaddr 00:13:d4:e3:1c:f5  
          inet6 addr: fe80::213:d4ff:fee3:1cf5/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:4176 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3767 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3840366 (3.6 MB)  TX bytes:661381 (645.8 KB)
          Interrupt:21 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3826 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3826 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:197868 (193.2 KB)  TX bytes:197868 (193.2 KB)

tap1      Link encap:Ethernet  HWaddr 00:ff:dc:97:a0:d4  
          inet6 addr: fe80::2ff:dcff:fe97:a0d4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3500 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4074 errors:0 dropped:5 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:611725 (597.3 KB)  TX bytes:3805924 (3.6 MB)

vbox0     Link encap:Ethernet  HWaddr 00:ff:1f:8a:ae:eb  
          inet6 addr: fe80::2ff:1fff:fe8a:aeeb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:522 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

And the script I have to run to get virtualbox networking to work:

```
USERNAME=james           # login name of HOST system
DHCP=1      # set to 1 to use dynamic ip for bridge
IP_ADDRESS=192.168.1.1    # static ip address of bridge (only used if DHCP set to 0)

tunctl -t tap1 -u $USERNAME
brctl addbr br0
ifconfig eth0 0.0.0.0 promisc
brctl addif br0 eth0

if [ DHCP = 1 ]; then
 dhclient br0
else
 ifconfig br0 $IP_ADDRESS
fi 

brctl addif br0 tap1
ifconfig tap1 up
chmod 0666 /dev/net/tun

```

If I don't run that script then my virtual machine doesn't start.

---

