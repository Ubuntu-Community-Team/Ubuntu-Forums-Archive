---
title: "VirtIO netplan force speed and duplex"
date: 2024-02-12
forum: Networking &amp; Wireless
---

### Post by tl5k5 on 2024-02-12
[COLOR=#141618][FONT=&amp]Hello,[/FONT][/COLOR]
[COLOR=#141618][FONT=&amp]I'm working through an issue with VirtIO NIC drivers on a Ubuntu 22.04 VM in Proxmox.[/FONT][/COLOR]
[COLOR=#141618][FONT=&amp]I need ethtools to recognize the VirtIO NIC speed of 10000 and duplex as Full instead of "Unknown!" :
[/FONT][/COLOR]```
# ethtool ens18Settings for ens18:
        Supported ports: [  ]
        Supported link modes:   Not reported
        Supported pause frame use: No
        Supports auto-negotiation: No
        Supported FEC modes: Not reported
        Advertised link modes:  Not reported
        Advertised pause frame use: No
        Advertised auto-negotiation: No
        Advertised FEC modes: Not reported
        Speed: Unknown!
        Duplex: Unknown! (255)
        Auto-negotiation: off
        Port: Other
        PHYAD: 0
        Transceiver: internal

        Link detected: yes
```[COLOR=#141618][FONT=&amp]

[/FONT][/COLOR][COLOR=#141618][FONT=&amp]Of course, when I manually edit with ethtool the change works until I reboot:
[/FONT][/COLOR]```
[COLOR=#141618][FONT=inherit]ethtool -s enp0s18 speed 10000 duplex full autoneg off[/FONT][/COLOR]
```[COLOR=#141618][FONT=&amp]

[/FONT][/COLOR][COLOR=#141618][FONT=&amp]**Is there a way to add speed and duplex to Ubuntu's netplan yaml?** Google is not revealing an answer.[/FONT][/COLOR]
[COLOR=#141618][FONT=&amp]Thanks![/FONT][/COLOR]
[COLOR=#141618][FONT=&amp]

[/FONT][/COLOR]

---

### Post by TheFu on 2024-02-12
Actually, I don't think there's a way to force a speed with virtio drivers.  They connect to shared resources which can have wildly different performance.  My virtio NICs range from 20Gbps to 46Gbps testing using iperf3.  Same VMs, different days == different performance.

If you need a specific speed, don't use virtio.  Specify a supported real-world NIC to emulate with the speed you want.

---

### Post by tl5k5 on 2024-02-13
Hold up.
When I force the speed/duplex, ethtools shows speed/duplex correctly (see below).  So are you sure your statement of "[COLOR=#000000]I don't think there's a way to force a speed with virtio drivers." is correct?  I just need a way for these to stick after a reboot.
[/COLOR]Also, it's my understanding that only the VirtiO (paravirtualized) option will work greater than 1Gb within Proxmox.

```

# ethtool -s enp0s18 speed 10000 duplex full autoneg off
# ethtool enp0s18
Settings for ens18:
        Supported ports: [  ]
        Supported link modes:   Not reported
        Supported pause frame use: No
        Supports auto-negotiation: No
        Supported FEC modes: Not reported
        Advertised link modes:  Not reported
        Advertised pause frame use: No
        Advertised auto-negotiation: No
        Advertised FEC modes: Not reported
**        Speed: 10000Mb/s**
**        Duplex: Full**
        Auto-negotiation: off
        Port: Other
        PHYAD: 0
        Transceiver: internal
        Link detected: yes
```

---

### Post by TheFu on 2024-02-14
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1581132](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1581132) says they added the "feature" to set/get link speed in kernel 4.4.x.

I've seen where others on proxmox and serverfault discussions say it isn't useful, except for simulators. The virtio driver will go as fast as it can, since it is really just a memory contents move between a VM and some RAM either in a VM or the host, as no real networking hardware is involved.  That makes me wonder if the set/get isn't actually enforced, but just a place for those properties to be held inside the virtio driver, but otherwise ignored.  

After all, the real ethernet NICs are shared resources that cannot go faster than their standards allow, but paravirtual drivers are designed to be shared resources across 1- 3000+ VMs.

---

### Post by tl5k5 on 2024-02-15
Interesting.
I'm trying to use Proxmox to connect a Ubuntu VM to a proprietary storage using the the manufactures client connection software.  They do not qualify Proxmox/VirtIO, but I've found it connects correctly if I manually set the speed and duplex parameters before installing their client software.  After a reboot and the manual bit go away, it no longer works.  So...I'm just trying to find a workaround to get these parameters to stick.
Thanks for the insight!

---

### Post by TheFu on 2024-02-15
I'd create a setting list a post-up command in the netplan sytemd unit file. [https://askubuntu.com/questions/1032153/how-to-execute-post-up-scripts-with-netplan](https://askubuntu.com/questions/1032153/how-to-execute-post-up-scripts-with-netplan) explains.  Read all the comments for caveats.

---

### Post by tl5k5 on 2024-02-20
I've reviewed the links and tried a few things, but I'm not a script writer or programmer by any stretch.
The following does not work, but am I going in the right direction?
/etc/networkd-dispatcher/no-carrier.d/50-pre-up-hooks
```
#!/bash/sh
ethtool -s enp0s18 speed 10000 duplex full autoneg off
done
exit 0
```

FYI...
-rw------- 1 root root   78 Feb 20 17:25 50-pre-up-hooks

Thanks!

---

