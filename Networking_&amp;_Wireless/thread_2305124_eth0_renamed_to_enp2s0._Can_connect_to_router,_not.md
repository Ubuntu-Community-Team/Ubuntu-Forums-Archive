---
title: "eth0 renamed to enp2s0. Can connect to router, not to google"
date: 2015-12-02
forum: Networking &amp; Wireless
---

### Post by mikybee93 on 2015-12-02
Hey all. I'm currently running Ubuntu Dekstop 15.10. I had to do a reboot earlier after installing xubuntu to replace the default appearance. After the reboot I was entirely unable to connect to the internet, and upon running ifconfig I discovered that 'eth0' no longer existed, and was replaced by 'enp2s0'. Here's the ifconfig:

```

enp2s0    Link encap:Ethernet  HWaddr  10:78....
             inet6 addr: fe80::1278... Scope:Link
             UP BROADCAST RUNNING MULITCAST  MTU:1500 Metric:1
             RX packets:0...
             TX packets:63... (0 errors etc)
             collisions:0 txqueuelen:1000
             RX bytes:0  TX bytes:11307

```

Here is my /etc/network/interfaces file:

```

auto lo eth0
iface lo inet loopback
iface eth0 inet static
        address 192.168.1.144
        netmast 255.255.255.0
        gateway 192.168.1.1
        dns-nameservers 8.8.8.8 192.168.1.1

```

I changed the interfaces file so that all instances of 'eth0' were replaced by 'enp2s0' and it allowed me to connect to my router at 192.168.1.1 in firefox, but not to connect to the internet or ping google.

I was able to rename enp2s0 to eth0 earlier by creating a file, I believe it was /etc/udev/rules.d/10-network.rules, but I reverted those changes because they got me nowhere.

I checked to make sure that the drivers existed and they do, as does the network card. Any help? Thanks ahead of time.

---

### Post by Bucky Ball on 2015-12-03
The name change is a new thing and apparently normal from the new 15.10. Disregard and move on.

If you are also using Network Manager tweaking the /interfaces file is going to screw things up. Your interfaces file should look like this:

```
# The loopback network interface
auto lo
iface lo inet loopback
```

That's it. Try reverting to that, reboot, and see if you can get it going by setting up or tweaking the connection in Network Manager. Set IPv6 tab in Network Manager to 'Ignore'. Does everything else there look as it should? Let us know if you're not sure. Also, give us the output of:

```
sudo lshw -C network
```

---

### Post by mikybee93 on 2015-12-03
So I woke up this morning and my wifi was down. I unplugged my router and plugged it back in... and everything was working perfectly... I went ahead and changed the file to what you had suggested anyhow. Works great!

My last question for you, I'm trying to use a static IP so that I can use port forwarding reliably on my router. Do I not need to edit the /interfaces file to achieve that?

---

### Post by steeldriver on 2015-12-03
Not if you're using network-manager (which it appears that you are, based on the fact that you get connectivity with only lo defined in /etc/network/interfaces)

With network-manager, you simply use the GUI applet and change the IP setting from 'Automatic' to 'Manual'. Then fill in the desired static IP address / netmask and DNS settings in the boxes provided.

---

### Post by Bucky Ball on 2015-12-03
> **steeldriver said:**
> Not if you're using network-manager (which it appears that you are, based on the fact that you get connectivity with only lo defined in /etc/network/interfaces)

With network-manager, you simply use the GUI applet and change the IP setting from 'Automatic' to 'Manual'. Then fill in the desired static IP address / netmask and DNS settings in the boxes provided.

+1. :)

Leave /interfaces as it is now. Good luck. If you need any help with the static IP, let us know.

PS: If you're expecting guests who will be wanting to simply log on to the network wirelessy without much fuss then you can set up the router to use DHCP to serve IPs to a range of addresses outside where you set your static IPs, but that comes later. :)

---

