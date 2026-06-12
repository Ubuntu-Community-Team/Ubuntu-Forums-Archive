---
title: "Ubuntu 13.10 networking starts late"
date: 2014-03-30
forum: Networking &amp; Wireless
---

### Post by martijn6 on 2014-03-30
Good evening everyone!

I'm a regular Ubuntu user and have learnt at least some of its wicked ways :D. But I'm by no means an expert which is why I come to you for help. And something has been bothering for quite a while now.

You see, I used 10.04 up to quite recently because of a dodgy old NVidia card and an, eh, frugal nature. It had a CIFS share (on a NAS) and a 2nd HDD added to fstab working flawlessly.

Now I treated myself to a SSD and figured I better start using an updated OS too. So I did, and configured as decribed on [this Easy Linux page]("https://sites.google.com/site/easylinuxtipsproject/ssd"). Both Ubuntu and Mint 16 Petra version, actually, and both displayed the same issue. Also I started using gufw instead of firestarter. However, disabling the firewall makes no difference. 

What happens is that networing is started late (my eth0 gets no IP?), about 3-4 seconds after booting finishes and Unity is visible. It then pops a message telling me it started wired networking, which by the way works absolutely fine afterwards. Same with wire*less*, really. Searching Google got me nowhere and my (limited?) *nix knowledge has just ended.

Hopefully you know the answer.

Thanks in advance!

Martijn

Some output:

**uname -a**
```
Linux blackbox 3.11.0-18-generic #32-Ubuntu SMP Tue Feb 18 21:11:14 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

**sudo lshw -C network**
```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 40:61:86:78:90:57
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-1.fw ip=192.168.178.21 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:43 ioport:d800(size=256) memory:f6fff000-f6ffffff memory:f6ff8000-f6ffbfff memory:fbee0000-fbefffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       bus info: usb@2:1.4.2
       logical name: wlan0
       serial: 1c:4b:d6:47:9a:4a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u multicast=yes wireless=unassociated
```

**ifconfig eth0**
```
eth0      Link encap:Ethernet  HWaddr 40:61:86:78:90:57  
          inet addr:192.168.178.21  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fd00::4261:86ff:fe78:9057/64 Scope:Global
          inet6 addr: fe80::4261:86ff:fe78:9057/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:243050 errors:0 dropped:0 overruns:0 frame:0
          TX packets:194671 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:255911120 (255.9 MB)  TX bytes:22131217 (22.1 MB)

```

**/etc/fstab**
```
# 2e HDD
/dev/sdb1  /home/mdctr/Mounts/Intern2/              ext4      defaults            0       0
#
# Netwerk
//192.168.178.23/mdctr /home/mdctr/Mounts/Whitebox/ cifs username=*****,password=*****,uid=1000,iocharset=utf8 0 0
```


**sudo ufw status numbered**
```
Status: actief

     Naar                       Actie       Van
     ----                       -----       ---
[ 1] 5353/udp                   DENY IN     Anywhere
[ 2] 5900/tcp                   DENY IN     Anywhere
[ 3] 22                         DENY IN     Anywhere
[ 4] 25/tcp                     DENY IN     Anywhere
[ 5] 135,139,445/tcp            DENY IN     Anywhere
[ 6] 137,138/udp                DENY IN     Anywhere
[ 7] 110                        DENY IN     Anywhere
[ 8] 2049                       DENY IN     Anywhere
[ 9] 143                        DENY IN     Anywhere
[10] 21/tcp                     DENY IN     Anywhere
[11] 1:19/tcp                   DENY OUT    Anywhere (out)
[12] 1:19/udp                   DENY OUT    Anywhere (out)
[13] 22:52/tcp                  DENY OUT    Anywhere (out)
[14] 22:52/udp                  DENY OUT    Anywhere (out)
[15] 54:79/tcp                  DENY OUT    Anywhere (out)
[16] 54:79/udp                  DENY OUT    Anywhere (out)
[17] 81:122/tcp                 DENY OUT    Anywhere (out)
[18] 81:122/udp                 DENY OUT    Anywhere (out)
[19] 124:442/tcp                DENY OUT    Anywhere (out)
[20] 124:442/udp                DENY OUT    Anywhere (out)
[21] 444:65535/tcp              DENY OUT    Anywhere (out)
[22] 444:65535/udp              DENY OUT    Anywhere (out)
[23] 5353/udp                   DENY IN     Anywhere (v6)
[24] 5900/tcp                   DENY IN     Anywhere (v6)
[25] 22                         DENY IN     Anywhere (v6)
[26] 25/tcp                     DENY IN     Anywhere (v6)
[27] 135,139,445/tcp            DENY IN     Anywhere (v6)
[28] 137,138/udp                DENY IN     Anywhere (v6)
[29] 110                        DENY IN     Anywhere (v6)
[30] 2049                       DENY IN     Anywhere (v6)
[31] 143                        DENY IN     Anywhere (v6)
[32] 21/tcp                     DENY IN     Anywhere (v6)
[33] 1:19/tcp                   DENY OUT    Anywhere (v6) (out)
[34] 1:19/udp                   DENY OUT    Anywhere (v6) (out)
[35] 22:52/tcp                  DENY OUT    Anywhere (v6) (out)
[36] 22:52/udp                  DENY OUT    Anywhere (v6) (out)
[37] 54:79/tcp                  DENY OUT    Anywhere (v6) (out)
[38] 54:79/udp                  DENY OUT    Anywhere (v6) (out)
[39] 81:122/tcp                 DENY OUT    Anywhere (v6) (out)
[40] 81:122/udp                 DENY OUT    Anywhere (v6) (out)
[41] 124:442/tcp                DENY OUT    Anywhere (v6) (out)
[42] 124:442/udp                DENY OUT    Anywhere (v6) (out)
[43] 444:65535/tcp              DENY OUT    Anywhere (v6) (out)
[44] 444:65535/udp              DENY OUT    Anywhere (v6) (out)
```

---

