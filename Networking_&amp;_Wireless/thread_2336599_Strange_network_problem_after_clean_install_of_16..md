---
title: "Strange network problem after clean install of 16.04.1"
date: 2016-09-09
forum: Networking &amp; Wireless
---

### Post by JKyleOKC on 2016-09-09
I attempted an on-line distro upgrade from 14.04.4 to 16.04.1, which froze solid around the halfway point forcing me to do a power-down and of course that destroyed the system. Fortunately I was able to copy the /home directory to an external HD, via the Live CD. I then did a clean install of 16.04.1 -- which in itself was a bit of a hoot since the box in question has an EFI motherboard and my first effort used the wrong boot selection  but I did eventually get a successful installation that is able to boot.

Unfortunately, this installation's network interface appears to be seriously borked. For some reason, during the boot process the systemd code renames "eth0" to something else. From that box, I can ping my other machine (on which I'm typing this). However it is unable to reach past that point. And from the current machine, any attempt to ping the problem system gets "network unreachable."

Can anyone offer troubleshooting suggestions? The /var/log/syslog file is so cluttered up with systemd entries that I can't find anything there that looks useful....

---

### Post by JKyleOKC on 2016-09-10
bump -- this is becoming extremely frustrating!

---

### Post by wildmanne39 on 2016-09-10
*Thread moved to **Networking & Wireless**.*

eth0 is renamed because that is a feature of 16.04, is your issue with a wired connection?

---

### Post by JKyleOKC on 2016-09-10
Yes, it's a wired connection, that is able to ping my "router box" (on which I'm typing this reply) but is unable to ping any other address, nor does it have access to my DNS server located on the "router box" although all of this worked properly before the clean install of 16.04.1.

Because of problems in the earlier installation, I had completely uninstalled Network Manager and reverted to the /etc/network/interfaces method, and after this problem appeared I manually added the necessary stanza to the interfaces file, including the dns-server line. The Network Manager applet now shows "network not managed" and after a few ping tests, the output of "ifconfig -a" shows a reasonable number of packets received -- and a much larger number transmitted because of the "Destination host unreachable" reports when I attempt to ping anything beyond the router box.

Since I made no changes at all to the physical components and it had been working before the upgrade, I'm assuming that something is mis-configured due to the upgrade but I'm unable to determine just what it is. The "route" command fails to show any default rule immediately after powering up, but adding one from the command line has no effect whatsoever on the problem. Since this is my first contact with the massive changes introduced by systemd, I'm a bit lost and growing more frustrated by the hour!

Thanks for moving the thread; hopefully it will get more response here.

---

### Post by wildmanne39 on 2016-09-10
I work with wireless issues and really have not done much work with wired so hopefully someone will stop by and take a look.

When you reinstalled after the failed upgrade did you reformat your drive so no left over configuration files were present?

---

### Post by JKyleOKC on 2016-09-10
> **Wild Man said:**
> I work with wireless issues and really have not done much work with wired so hopefully someone will stop by and take a look.

When you reinstalled after the failed upgrade did you reformat your drive so no left over configuration files were present?I simply checked the option to "Use entire disk" on the Live CD. However I've (at long last) found the problem and it's now working again. In my interfaces file, I had mis-spelled the dns-server line; it should have been dns-nameservers. The root problem was apparently the misconfigured route table, and I still don't have it corrected properly. My workaround is to add two lines to /etc /rc.local to first, install the default gateway rule correctly, then "ip route flush scope link" to get rid of the two lines apparently created by systemd that were shutting me down.

Hopefully someone with more systemd experience will be able to show me how to make things work as well as they did before this "improvement" came onto the scene <grin>. Meanwhile the workaround seems to suffice, now that I corrected the problem in the interfaces file.

---

### Post by King of Heart 4711 on 2016-09-11
> **Wild Man said:**
> *Thread moved to **Networking & Wireless**.*

eth0 is renamed because that is a feature of 16.04, is your issue with a wired connection?

Please note: This is not a new feature of Ubuntu itself, but is a result  of Canonical falling in line with Debian and other distributions in moving to the systemd init system from upstart and SysV. The network changes specificly is the result of a systemd feature called [Predictable Network Interfaces]("https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/") - all distributions that have moved to systemd will have network names like this:

 
[LIST=1]
[*]Names incorporating Firmware/BIOS provided index numbers for on-board devices (example: eno1) 
[*]Names incorporating Firmware/BIOS provided PCI Express hotplug slot index numbers (example: ens1) 
[*]Names incorporating physical/geographical location of the connector of the hardware (example: enp2s0)  [ most distros that I have used are doing it this way ] 
[*]Names incorporating the interfaces's MAC address (example: enx78e7d1ea46da) 
[*]Classic, unpredictable kernel-native ethX naming (example: eth0) 
[/LIST]

You can revert back by adding this to your /etc/default/grub:

```
GRUB_CMDLINE_LINUX_DEFAULT="net.ifnames=0 biosdevname=0"
```

Run update-grub and reboot. Your interface names will then use the legacy ethX/wlanX names. 

I did this on a few systems so I didn't need to rewrite a bunch of bash scripts :smile:

A great location to find information in systemd is [here]("https://www.freedesktop.org/wiki/Software/systemd/") and [here]("https://wiki.archlinux.org/index.php/Systemd").  Most of the examples are using Fedora or Arch, but are exactly the same  for Ubuntu - which is the point of systemd to have a unified init  system across distributions.

---

### Post by wildmanne39 on 2016-09-11
I miss spoke I guess I should have said eth0 is renamed because that is how it is done in 16.04 yes I knew it is called Predictable Network Interfaces, but I am trying to help a lot of people and figured that short explanation would suffice. You did a real nice job of explaining it.
Thank you!

---

### Post by JKyleOKC on 2016-09-11
Thanks very much for the added information. Since this seems to be the wave of the future, i need to learn all i can about it. Nos if someone would chime in with some ideas about why the routing table isn't usable after a reboot, with no "default" rule and two "scope link" rules that make all internet access impossible until the table is repaired!

---

### Post by King of Heart 4711 on 2016-09-11
> **JKyleOKC said:**
> Thanks very much for the added information. Since this seems to be the wave of the future, i need to learn all i can about it. Nos if someone would chime in with some ideas about why the routing table isn't usable after a reboot, with no "default" rule and two "scope link" rules that make all internet access impossible until the table is repaired!

I haven't had any issues with Network Manager on my "normal" installs (however my experience in with Network *Mangler* in my production environment at work is a different story :-| )

When Network Manager sees that your interfaces (other than lo) have been configured with /etc/network/interfaces it will display "network not managed", so that's normal. What's definitely weird is that it should "*just work*" if you are letting it be auto configured as default. Just to clarify, your are not having any issues with other boxes on your network right?? 

I'm not sure if your issue is exactly a systemd issue or an Ubuntu issue (there are issues with wireless not coming back online after suspend on some systems caused by Network Mangler not starting back up properly with 16.04)

As far as using /etc/network/interfaces, I only use that on servers. But should also just work if properly configured. Below are a few example configurations I have used in the past:

DHCP Configuration:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto ${INTERFACENAME}
iface ${INTERFACENAME} inet dhcp
```

Static configuration:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto ${INTERFACENAME}
iface ${INTERFACENAME} inet static
    address $HostIP
    netmask 255.255.255.0   # Change to your network configuration, but it's probably this...
    network $NetworkIP
    broadcast $BroadcastIP
    gateway $GatewayIP       # Probably your router's IP
    # dns-* options are implemented by the resolvconf package, if installed
    dns-nameservers 8.8.8.8 8.8.4.4 #list of name servers, also could be the router's IP
```


You can also use the ifconfig[deprecated] and ip commands to configure the interfaces, but that's getting a little fancy (and it's not persistent)...

---

### Post by JKyleOKC on 2016-09-11
No other network issues at all, and I've been using the /etc/network/interfaces approach exclusively for several months after Network Mangler reassigned the default gateway on my other box to the LAN rather than to the router that provides my LAN. My network is currently just two boxes; one serves as the LAN router and is equipped with two NICs. The other connects only to the first. Back in April, the default gateway switch shut me down for a couple of days. I solved it by disabling Network Mangler on the "router box" and replacing it with the interfaces file, and all was well.

When I had to clean-install 16.04.1, I accepted Network Mangler as the default but it was unable to obtain any response using DHCP. I then edited the connection to assign a static IP, but the change of interface name led me down a blind alley for a while, during which time I rewrote the interfaces file here to take the place of NM. Once I had full connection capability back, I discovered the route table problem. I then did "systemctl disable" to take NM out of the picture entirely.

My current solution to the route table is to add these three lines to /etc/rc.local (the IP address is the LAN router box):
```
# correct route table - 9-10-2016 jk
ip route add default via 192.168.0.2 dev enp4s0
ip route flush scope link
```However I definitely would prefer to have it set automatically during the boot process!

---

