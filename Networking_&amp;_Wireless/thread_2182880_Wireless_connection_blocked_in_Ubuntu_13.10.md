---
title: "Wireless connection blocked in Ubuntu 13.10"
date: 2013-10-22
forum: Networking &amp; Wireless
---

### Post by JQ6MRWt on 2013-10-22
Hi everybody,

I've just installed Ubuntu 13.10 but I manage to connect only with wired connection; if I click on the menu which should show the available connections I can see only the wired ones, while the wireless connections don't appear; in addition, the option "Enable Wi-Fi" is disabled and blocked (I can't tick it, practically).
Then, I can add that is not an issue of 'manually' blocked hardware, because I've tried more times to push *fn+F2* in order to enable the wireless connection, but without results...

Therefore I post here the outputs of some commands which should help the more expert ones to understand where is the problem.


_*lshw -C network*_
```

  *-network DISABLED      
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 6c:71:d9:97:aa:f1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.11.0-12-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f7900000-f797ffff memory:f7980000-f798ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.2
       bus info: pci@0000:04:00.2
       logical name: eth0
       version: 0a
       serial: 74:d0:2b:d8:76:a9
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8411-1_0.0.3 06/18/12 ip=10.36.232.58 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:46 ioport:d000(size=256) memory:f2104000-f2104fff memory:f2100000-f2103fff

```
_*rfkill list *_
```
0: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: yes
2: asus-wlan: Wireless LAN
        Soft blocked: no
        Hard blocked: no
3: asus-bluetooth: Bluetooth
        Soft blocked: no
        Hard blocked: no

```
_*ifconfig*_
```
eth0      Link encap:Ethernet  IndirizzoHW 74:d0:2b:d8:76:a9  
          indirizzo inet:10.36.232.58  Bcast:10.36.232.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::76d0:2bff:fed8:76a9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:164826 errors:0 dropped:1 overruns:0 frame:0
          TX packets:89245 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:194831176 (194.8 MB)  Byte TX:7862658 (7.8 MB)


lo        Link encap:Loopback locale  
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4894 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4894 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:385002 (385.0 KB)  Byte TX:385002 (385.0 KB)

```
_*iwconfig*_
```
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

```

---

### Post by JQ6MRWt on 2013-10-23
Update: things have changed a little bit, now the wireless connection works!
But unfortunately it doesn't work always!! And the worst thing is that I can't control it with the button: for instance, I start the pc and it doesn't work, then I reboot it and everything's fine (or not, it seems not to have any rule!)

What should I do ??

---

### Post by varunendra on 2013-10-24
> **JQ6MRWt said:**
> Update: things have changed a little bit, now the wireless connection works!
But unfortunately it doesn't work always!! And the worst thing is that I can't control it with the button: for instance, I start the pc and it doesn't work, then I reboot it and everything's fine (or not, it seems not to have any rule!)

What should I do ??

For now, just do as suggested here : [http://ubuntuforums.org/showthread.php?t=2181558](http://ubuntuforums.org/showthread.php?t=2181558)

Post #1 is a fix for hard blocked state, and post #2 is a workaround for the Fn+F2 function.

---

### Post by JQ6MRWt on 2013-10-25
Thank you, it solved perfectly!!

I mark the thread as [SOLVE]

---

### Post by varunendra on 2013-10-25
You're welcome! :)

If you have a launchpad account, please consider reporting the bug as you are one of those who are directly affected.

---

