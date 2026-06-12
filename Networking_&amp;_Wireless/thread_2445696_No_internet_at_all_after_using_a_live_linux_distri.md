---
title: "No internet at all after using a live linux distribution (Tail)"
date: 2020-06-18
forum: Networking &amp; Wireless
---

### Post by gerardsix on 2020-06-18
I have used Tail booting a USB key. When I have start again my PC, Windows 10 works correctly (connecting the internet normaly) but no more internet connection (nor wired nor wifi) on Lubuntu!


How to fix that?


Thank you for your help.

---

### Post by TheFu on 2020-06-18
What have you tried so far?  
Which forum posts did you follow already?

We can't read your mind.  What is "Tail"?  Could you mean "Tails" or is "Tail" a new adult-centered distro? ;)

If you need steps for troubleshooting, ... [https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking) has some, in order, to figure out where the issue may be.  Often the internet is fine and only DNS has been broken. Troubleshooting the wrong thing wastes time.

---

### Post by sudodus on 2020-06-18
Lubuntu *should not* be affected by what you do with a live linux system.

I am not a networking expert, and I think you need help from such a person, who might know what setting or blacklisting, that might affect you after using Tails.

In the meantime, while waiting for an answer, you can check, if a *live Lubuntu* session can connect (at least via wired internet).

---

### Post by gerardsix on 2020-06-18
I have tried the live Lubuntu 20.04 on a usb key : it can connnect to the internet.

Here is commands I have typed :

```
(base) gerard@gerard-HP-Laptop-15-db0xxx:~$ sudo ip link set enp2s0 down
[sudo] Mot de passe de gerard : 
Cannot find device "enp2s0"


(base) gerard@gerard-HP-Laptop-15-db0xxx:~$ ifconfig
lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Boucle locale)
        RX packets 14154  bytes 1439249 (1.4 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 14154  bytes 1439249 (1.4 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


(base) gerard@gerard-HP-Laptop-15-db0xxx:~$ uname -a
Linux gerard-HP-Laptop-15-db0xxx 4.15.0-106-generic #107-Ubuntu SMP Thu Jun 4 11:27:52 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux


(base) gerard@gerard-HP-Laptop-15-db0xxx:~$ lspci -k -nn | grep -A 3 -i net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:84ac]
    Kernel modules: r8168
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:d723]
    Subsystem: Hewlett-Packard Company Device [103c:8319]
    Kernel modules: rtl8723de


(base) gerard@gerard-HP-Laptop-15-db0xxx:~$ ifconfig -a
lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Boucle locale)
        RX packets 42465  bytes 4727783 (4.7 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 42465  bytes 4727783 (4.7 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0



```

---

### Post by TheFu on 2020-06-18
Why?
```
sudo ip link set enp2s0 down
```
that turns off the NIC. No networking will happen. That assumes **enp2s0** is the correct device. That certainly wasn't in the link provided.

Assuming you've booted the OS instance you want to troubleshoot, connect it to a wired ethernet and follow the steps outlined in my link above.  Report back with the actual commands AND the output.

If you can't ping your local router using a LAN IP address, we'll head in a different direction than if you can ping 8.8.8.8.  But we need facts to decide stuff.

Please.

---

### Post by gerardsix on 2020-06-19
@TheFu : Thank you for help.

1) As you can see : [COLOR=#000000][FONT=&amp]sudo ip link set enp2s0 down is followed by [/FONT][/COLOR][COLOR=#000000][FONT=&amp]Cannot find device "enp2s0", I did't really know what I was doing.

[/FONT][/COLOR]2) I can't connect it to a wired ethernet on the system I want to troubleshoot.

I've tried many things (from your link)

[COLOR=#000000][FONT=&amp]

[/FONT][/COLOR]```
(base) gerard@gerard-HP-Laptop-15-db0xxx:~$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
(base) gerard@gerard-HP-Laptop-15-db0xxx:~$ route -n
Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic Metric Ref    Use Iface
(base) gerard@gerard-HP-Laptop-15-db0xxx:~$ dmesg |grep eth[0-9]
(base) gerard@gerard-HP-Laptop-15-db0xxx:~$ sudo lshw -C network
[sudo] Mot de passe de gerard : 
  *-network NON-RÉCLAMÉ     
       description: Ethernet controller
       produit: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       fabriquant: Realtek Semiconductor Co., Ltd.
       identifiant matériel: 0
       information bus: pci@0000:02:00.0
       version: 15
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
       ressources: portE/S:3000(taille=256) mémoire:f0b04000-f0b04fff mémoire:f0b00000-f0b03fff
  *-network NON-RÉCLAMÉ
       description: Network controller
       produit: Realtek Semiconductor Co., Ltd.
       fabriquant: Realtek Semiconductor Co., Ltd.
       identifiant matériel: 0
       information bus: pci@0000:03:00.0
       version: 00
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: pm msi pciexpress cap_list
       configuration: latency=0
       ressources: portE/S:2000(taille=256) mémoire:f0a00000-f0a0ffff
(base) gerard@gerard-HP-Laptop-15-db0xxx:~$ ifconfig -a
lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Boucle locale)
        RX packets 2410  bytes 233255 (233.2 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2410  bytes 233255 (233.2 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


(base) gerard@gerard-HP-Laptop-15-db0xxx:~$ more /etc/resolv.conf
# Generated by NetworkManager
nameserver 127.0.0.53
(base) gerard@gerard-HP-Laptop-15-db0xxx:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.4 LTS
Release:    18.04
Codename:    bionic



```[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]

---

### Post by CelticWarrior on 2020-06-19
"NON-RÉCLAMÉ" means "UNCLAIMED".

Somehow your installed system lost the drivers for both devices.

---

### Post by gerardsix on 2020-06-19
I also think that in a certain way system has lost drivers. But how to reinstall these drivers?

---

### Post by TheFu on 2020-06-19
When running Tails, did you manually go and delete stuff?
Assuming you rebooted the system and that didn't fix anything?

_Realtek Semiconductor Co., Ltd. RTL8111/8168/8411_ is the driver you need to locate.
It is usually automatically loaded as either r8169.ko or r8168.ko and both are included with the kernel.  The card revision seems to dictate which of the 68 or 69 driver is needed. Here's mine:
```
$ sudo lspci -vk |perl -lne 'print if /Ethernet|Network/ .. /^[\w]*$/' 
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. **RTL8111/8168/8411** PCI Express Gigabit Ethernet Controller (**rev 0c**)
        Subsystem: Gigabyte Technology Co., Ltd Onboard Ethernet
        Flags: bus master, fast devsel, latency 0, IRQ 26
        I/O ports at e000 [size=256]
        Memory at f7e00000 (64-bit, non-prefetchable) [size=4K]
        Memory at f0000000 (64-bit, prefetchable) [size=16K]
        Capabilities: [40] Power Management version 3
        Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Capabilities: [70] Express Endpoint, MSI 01
        Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
        Capabilities: [d0] Vital Product Data
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [140] Virtual Channel
        Capabilities: [160] Device Serial Number 01-00-00-00-68-7c-00-00
        Capabilities: [170] Latency Tolerance Reporting
        Kernel driver in use: **r8169**
        Kernel modules: r8169
```
Note the revision, 0C. Yours says revision "15", so using r8169 would be my best guess. If the r8168 driver tries to load (check dmesg), you may need to blacklist it in the /etc/modprobe.d/blacklist.local file.  There are lots of blacklisting examples in that directory.

The fact that those have gone missing means there is a bigger problem with your storage. Check the disk for failures.  Drivers included with the kernel don't just "disappear."

_My mistake - Update: command is modprobe_
You could try doing a **sudo modprob_e_ r8169** and seeing if that loads the driver. Check that with the **lspci** command (get the device name), then bring that network interface up.

Some realtek NICs need to have custom built drivers.  If you google *RTL8111/8168/8411 rev 15 ubuntu XX.YY*, you should find any specific instructions. [https://ubuntuforums.org/showthread.php?t=2415415](https://ubuntuforums.org/showthread.php?t=2415415) is for 18.10.  I used 18.04 for "XX.YY" in my search.

---

### Post by gerardsix on 2020-06-19
Here is what I get :


```
(base) gerard@gerard-HP-Laptop-15-db0xxx:~$ sudo modprob r8169[sudo] Mot de passe de gerard : 
sudo: modprob : commande introuvable
```


and 
```
(base) gerard@gerard-HP-Laptop-15-db0xxx:~$ lspci -k -nn | grep -A 3 -i net02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
	Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:84ac]
	Kernel modules: r8168
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:d723]
	Subsystem: Hewlett-Packard Company Device [103c:8319]
	Kernel modules: rtl8723de
```

---

### Post by spjackson on 2020-06-19
Typo. It should be modprobe not modprob.

---

### Post by TheFu on 2020-06-19
Sorry, i use *tab completion* for all commands and files.  The system would have filled in the 'e' at the end of **modprobe**.
i don't really memorize commands since tab-completion has worked the last 25 yrs.

So, if the r8168 driver is getting loaded. Bring the interface up and go back to my first link. **Follow those steps in-order** and post each, please.  BTW, thanks for the code tags. Appreciated.

---

### Post by gerardsix on 2020-06-19
Not better :

```
(base) gerard@gerard-HP-Laptop-15-db0xxx:~$ sudo modprobe r8169
[sudo] Mot de passe de gerard : 
(base) gerard@gerard-HP-Laptop-15-db0xxx:~$ 
```

---

### Post by Autodave on 2020-06-19
(copied from DistroWatch)


The Amnesic Incognito Live System (Tails) is a Debian-based live DVD/USB  with the goal of providing complete Internet anonymity for the user.  The product ships with several Internet applications, including web  browser, IRC client, mail client and instant messenger, all  pre-configured with security in mind and with all traffic anonymised. To  achieve this, Incognito uses the Tor network to make Internet traffic  very hard to trace.

---

### Post by TheFu on 2020-06-19
The r8168 driver is already loaded.  One or the other is needed.  
> So, if the r8168 driver is getting loaded. Bring the interface up and go back to my first link. Follow those steps in-order and post each, please.

---

### Post by gerardsix on 2020-06-19
Ok. So how do I b[COLOR=#000000]*ring the interface up ?*[/COLOR]

---

### Post by TheFu on 2020-06-19
> **gerardsix said:**
> Ok. So how do I b[COLOR=#000000]*ring the interface up ?*[/COLOR]
[LIST=1]
[*]Determine the name for the interface. ```
dmesg |grep eth
```
[*]Use the **ip** command to bring that interface "up" - you already showed a "down" command above.  Use "up" instead, but with the correct interface name.
[/LIST]

---

### Post by gerardsix on 2020-06-21
It seems that ther is no ethernet interface :
```


(base) gerard@gerard-HP-Laptop-15-db0xxx:~$ dmesg | grep eth
               Initialized Local Variables for Method [_STA]:
[    0.257777] No Arguments are initialized for method [_STA]
[    0.257779] ACPI Error: Method parse/execution failed \_SB.WLBU._STA, AE_NOT_FOUND (20170831/psparse-550)
               Initialized Local Variables for Method [_STA]:
[    0.257872] No Arguments are initialized for method [_STA]
[    0.257874] ACPI Error: Method parse/execution failed \_SB.WLBU._STA, AE_NOT_FOUND (20170831/psparse-550)
               Initialized Local Variables for Method [_STA]:
[    0.358200] No Arguments are initialized for method [_STA]
[    0.358201] ACPI Error: Method parse/execution failed \_SB.WLBU._STA, AE_NOT_FOUND (20170831/psparse-550)
               Initialized Local Variables for Method [_STA]:
[    0.441741] No Arguments are initialized for method [_STA]
[    0.441743] ACPI Error: Method parse/execution failed \_SB.WLBU._STA, AE_NOT_FOUND (20170831/psparse-550)
[   19.828791] wmi_bus wmi_bus-PNP0C14:00: WQBJ data block query control method not found
```

---

### Post by TheFu on 2020-06-21
The NIC could be dead/dying.

All the ways I know to see network devices:
```
ip addr
lspci -vk |egrep --after-context=8 'Ethernet|Network'
lspci -vk |perl -lne 'print if /Ethernet|Network/ .. /^[\w]*$/' 
sudo lsusb -v  |egrep 'Ether|Network'
lsmod |grep usbnet

**sudo lshw -C network**
```

These usually require a driver for the device to load, however.  The **lshw** one is the best. It shows important details. The lspci often don't show the device names, so they are of little use.  

The **lsusb** command is for usb-based networking that won't show up any other way.

We're looking for something like this:
```
$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       **logical name: eth0**
       version: 0c
       serial: fc:aa:14:a7:06:51
       **size: 10Mbit/s**
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes **driver=r8169 driverversion=2.3LK-NAPI** duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:18 ioport:e000(size=256) memory:f7e00000-f7e00fff memory:f
  *-network
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 1
       bus info: pci@0000:04:01.0
       **logical name: eth1**
       version: 12
       serial: 00:04:ee:ff:ee:ea
       **size: 1Gbit/s**
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes **driver=skge driverversion=1.14** duplex=full latency=32 link=yes maxlatency=31 mingnt=23 multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:16 memory:f7d00000-f7d03fff ioport:d000(size=256)
```
Want the logical name, size and driver info.  Note how the Marvell is 1Gbit/s size but the Realtek is 10Mbit/s sized?  That's because that system doesn't use the Realtek.  Just to be clear, that Marvell NIC is really bad, but still better than the Realtek.  Intel makes the most compatible, fastest, least CPU overhead NICs, that "just work" out of the box.

But it feels like we are going in circles, yes?  Perhaps someone else can step in and help?

---

### Post by gerardsix on 2020-06-22
Here are the results of the commands :
```
(base) gerard@gerard-HP-Laptop-15-db0xxx:~$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
(base) gerard@gerard-HP-Laptop-15-db0xxx:~$ lspci -vk |egrep --after-context=8 'Ethernet|Network'
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
    Flags: bus master, fast devsel, latency 0, IRQ 255
    I/O ports at 3000 [size=256]
    Memory at f0b04000 (64-bit, non-prefetchable) [size=4K]
    Memory at f0b00000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: r8168


03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device d723
    Subsystem: Hewlett-Packard Company Device 8319
    Flags: fast devsel, IRQ 255
    I/O ports at 2000 [size=256]
    Memory at f0a00000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel modules: rtl8723de


(base) gerard@gerard-HP-Laptop-15-db0xxx:~$ lspci -vk |perl -lne 'print if /Ethernet|Network/ .. /^[\w]*$/' 
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
    Flags: bus master, fast devsel, latency 0, IRQ 255
    I/O ports at 3000 [size=256]
    Memory at f0b04000 (64-bit, non-prefetchable) [size=4K]
    Memory at f0b00000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: r8168


03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device d723
    Subsystem: Hewlett-Packard Company Device 8319
    Flags: fast devsel, IRQ 255
    I/O ports at 2000 [size=256]
    Memory at f0a00000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel modules: rtl8723de


(base) gerard@gerard-HP-Laptop-15-db0xxx:~$ sudo lsusb -v  |egrep 'Ether|Network'
[sudo] Mot de passe de gerard : 
(base) gerard@gerard-HP-Laptop-15-db0xxx:~$ lsmod |grep usbnet
(base) gerard@gerard-HP-Laptop-15-db0xxx:~$ sudo lshw -C network
  *-network NON-RÉCLAMÉ     
       description: Ethernet controller
       produit: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       fabriquant: Realtek Semiconductor Co., Ltd.
       identifiant matériel: 0
       information bus: pci@0000:02:00.0
       version: 15
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
       ressources: portE/S:3000(taille=256) mémoire:f0b04000-f0b04fff mémoire:f0b00000-f0b03fff
  *-network NON-RÉCLAMÉ
       description: Network controller
       produit: Realtek Semiconductor Co., Ltd.
       fabriquant: Realtek Semiconductor Co., Ltd.
       identifiant matériel: 0
       information bus: pci@0000:03:00.0
       version: 00
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: pm msi pciexpress cap_list
       configuration: latency=0
       ressources: portE/S:2000(taille=256) mémoire:f0a00000-f0a0ffff
(base) gerard@gerard-HP-Laptop-15-db0xxx:~$ 
```

Does it help?

---

### Post by TheFu on 2020-06-22
**lshw** doesn't show the driver, but **lspci** does. We are beyond my skill.

Here's what I would do.
[LIST=1]
[*]Get the correct driver to load and show up in both methods. Use **lsmod** to check that it was loaded.
[*]Figure out the interface name from lshw or lspci or dmesg or any other command you like
[*]Bring the interface up, if it isn't already up.  That can be done using **network-manager**, **nmcli**, terminal commands. Doesn't matter. Whatever works.
[*]Try to ping your local router by IP.
[*]Try to **ping 1.1.1.1** 
[*]Try to **ping google.com**
[/LIST]
Do those in order. Stop when the first one fails, since everything after is useless. If you can't ping your local router, but the interface is up, stop. Post the **ip addr** and **route -n** output.

It is quite possible that the r8168 is wrong and the r8169 is needed.
It is quite possible that both of those installed with the kernel aren't the version that your device needs, so you may need to get the correct version online, build the driver following those instructions, install it as a, manually load the module using modprobe or insmod, then try again from the top.

After all of this, it is still possible that the NIC is failing and nothing can get it working. A $25 Intel PRO/1000 NIC can make this all go away in 15 minutes. At least for the wired ethernet. Those are plug-in-play cards almost always and extremely well supported across all OSes.

Still hoping others will chime in with better ideas for a solution.

---

