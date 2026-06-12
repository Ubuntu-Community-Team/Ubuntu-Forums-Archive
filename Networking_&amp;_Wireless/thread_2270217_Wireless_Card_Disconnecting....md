---
title: "Wireless Card Disconnecting..."
date: 2015-03-21
forum: Networking &amp; Wireless
---

### Post by b14speedfreak on 2015-03-21
Hi Guys, 

I started off this off on the AskUbuntu forum.  However only one person made any suggestions, and ended up with suggesting that I file a bug report:

[http://askubuntu.com/questions/597168/wireless-card-disconecting?noredirect=1#comment832600_597168](http://askubuntu.com/questions/597168/wireless-card-disconecting?noredirect=1#comment832600_597168)

My system is as follows:

**Hardware:**
GIGABIT LAN & WIRELESS 802.11N CARD INC. BLUETOOTH 3.0 - laptop custom built by pcspecialist.co.uk

lshw displays the following:

```
mark-w54-55su1-suw
description: Computer
width: 64 bits
capabilities: vsyscall32
*-core
   description: Motherboard
   physical id: 0
 *-memory
      description: System memory
      physical id: 0
      size: 7901MiB
 *-cpu
      product: Intel(R) Core(TM) i7-4712MQ CPU @ 2.30GHz
      vendor: Intel Corp.
      physical id: 1
      bus info: cpu@0
      size: 800MHz
      capacity: 800MHz
      width: 64 bits
      capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 fma cx16 xtpr pdcm pcid sse4_1 sse4_2 movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid cpufreq
 *-pci
      description: Host bridge
      product: Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller
      vendor: Intel Corporation
      physical id: 100
      bus info: pci@0000:00:00.0
      version: 06
      width: 32 bits
      clock: 33MHz
    *-display
         description: VGA compatible controller
         product: 4th Gen Core Processor Integrated Graphics Controller
         vendor: Intel Corporation
         physical id: 2
         bus info: pci@0000:00:02.0
         version: 06
         width: 64 bits
         clock: 33MHz
         capabilities: vga_controller bus_master cap_list rom
         configuration: driver=i915 latency=0
         resources: irq:44 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)
    *-multimedia:0
         description: Audio device
         product: Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
         vendor: Intel Corporation
         physical id: 3
         bus info: pci@0000:00:03.0
         version: 06
         width: 64 bits
         clock: 33MHz
         capabilities: bus_master cap_list
         configuration: driver=snd_hda_intel latency=0
         resources: irq:47 memory:f7e14000-f7e17fff
    *-usb:0
         description: USB controller
         product: 8 Series/C220 Series Chipset Family USB xHCI
         vendor: Intel Corporation
         physical id: 14
         bus info: pci@0000:00:14.0
         version: 05
         width: 64 bits
         clock: 33MHz
         capabilities: xhci bus_master cap_list
         configuration: driver=xhci_hcd latency=0
         resources: irq:40 memory:f7e00000-f7e0ffff
    *-communication
         description: Communication controller
         product: 8 Series/C220 Series Chipset Family MEI Controller #1
         vendor: Intel Corporation
         physical id: 16
         bus info: pci@0000:00:16.0
         version: 04
         width: 64 bits
         clock: 33MHz
         capabilities: bus_master cap_list
         configuration: driver=mei_me latency=0
         resources: irq:45 memory:f7e1e000-f7e1e00f
    *-usb:1
         description: USB controller
         product: 8 Series/C220 Series Chipset Family USB EHCI #2
         vendor: Intel Corporation
         physical id: 1a
         bus info: pci@0000:00:1a.0
         version: 05
         width: 32 bits
         clock: 33MHz
         capabilities: ehci bus_master cap_list
         configuration: driver=ehci-pci latency=0
         resources: irq:16 memory:f7e1c000-f7e1c3ff
    *-multimedia:1
         description: Audio device
         product: 8 Series/C220 Series Chipset High Definition Audio Controller
         vendor: Intel Corporation
         physical id: 1b
         bus info: pci@0000:00:1b.0
         version: 05
         width: 64 bits
         clock: 33MHz
         capabilities: bus_master cap_list
         configuration: driver=snd_hda_intel latency=0
         resources: irq:46 memory:f7e10000-f7e13fff
    *-pci:0
         description: PCI bridge
         product: 8 Series/C220 Series Chipset Family PCI Express Root Port #1
         vendor: Intel Corporation
         physical id: 1c
         bus info: pci@0000:00:1c.0
         version: d5
         width: 32 bits
         clock: 33MHz
         capabilities: pci normal_decode bus_master cap_list
         configuration: driver=pcieport
         resources: irq:16 ioport:2000(size=4096) memory:df200000-df3fffff ioport:df400000(size=2097152)
    *-pci:1
         description: PCI bridge
         product: 8 Series/C220 Series Chipset Family PCI Express Root Port #3
         vendor: Intel Corporation
         physical id: 1c.2
         bus info: pci@0000:00:1c.2
         version: d5
         width: 32 bits
         clock: 33MHz
         capabilities: pci normal_decode bus_master cap_list
         configuration: driver=pcieport
         resources: irq:18 ioport:e000(size=4096) memory:f7d00000-f7dfffff
       *-network
            description: Wireless interface
            product: RTL8723BE PCIe Wireless Network Adapter
            vendor: Realtek Semiconductor Co., Ltd.
            physical id: 0
            bus info: pci@0000:02:00.0
            logical name: wlan0
            version: 00
            serial: 30:10:b3:b3:1f:ec
            width: 64 bits
            clock: 33MHz
            capabilities: bus_master cap_list ethernet physical wireless
            configuration: broadcast=yes driver=rtl8723be driverversion=3.13.0-46-generic firmware=N/A ip=192.168.0.6 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
            resources: irq:18 ioport:e000(size=256) memory:f7d00000-f7d03fff
    *-pci:2
         description: PCI bridge
         product: 8 Series/C220 Series Chipset Family PCI Express Root Port #4
         vendor: Intel Corporation
         physical id: 1c.3
         bus info: pci@0000:00:1c.3
         version: d5
         width: 32 bits
         clock: 33MHz
         capabilities: pci normal_decode bus_master cap_list
         configuration: driver=pcieport
         resources: irq:19 ioport:d000(size=4096) memory:f7c00000-f7cfffff
       *-generic
            description: Unassigned class
            product: Realtek Semiconductor Co., Ltd.
            vendor: Realtek Semiconductor Co., Ltd.
            physical id: 0
            bus info: pci@0000:03:00.0
            version: 01
            width: 32 bits
            clock: 33MHz
            capabilities: bus_master cap_list rom
            configuration: driver=rtsx_pci latency=0
            resources: irq:42 memory:f7c15000-f7c15fff memory:f7c00000-f7c0ffff
       *-network
            description: Ethernet interface
            product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
            vendor: Realtek Semiconductor Co., Ltd.
            physical id: 0.1
            bus info: pci@0000:03:00.1
            logical name: eth0
            version: 12
            serial: 80:fa:5b:0c:3f:ac
            size: 10Mbit/s
            capacity: 1Gbit/s
            width: 64 bits
            clock: 33MHz
            capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
            configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8411-2_0.0.1 07/08/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
            resources: irq:41 ioport:d000(size=256) memory:f7c14000-f7c14fff memory:f7c10000-f7c13fff
    *-usb:2
         description: USB controller
         product: 8 Series/C220 Series Chipset Family USB EHCI #1
         vendor: Intel Corporation
         physical id: 1d
         bus info: pci@0000:00:1d.0
         version: 05
         width: 32 bits
         clock: 33MHz
         capabilities: ehci bus_master cap_list
         configuration: driver=ehci-pci latency=0
         resources: irq:23 memory:f7e1b000-f7e1b3ff
    *-isa
         description: ISA bridge
         product: HM86 Express LPC Controller
         vendor: Intel Corporation
         physical id: 1f
         bus info: pci@0000:00:1f.0
         version: 05
         width: 32 bits
         clock: 33MHz
         capabilities: isa bus_master cap_list
         configuration: driver=lpc_ich latency=0
         resources: irq:0
    *-storage
         description: SATA controller
         product: 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode]
         vendor: Intel Corporation
         physical id: 1f.2
         bus info: pci@0000:00:1f.2
         version: 05
         width: 32 bits
         clock: 66MHz
         capabilities: storage ahci_1.0 bus_master cap_list
         configuration: driver=ahci latency=0
         resources: irq:43 ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f090(size=8) ioport:f080(size=4) ioport:f060(size=32) memory:f7e1a000-f7e1a7ff
    *-serial UNCLAIMED
         description: SMBus
         product: 8 Series/C220 Series Chipset Family SMBus Controller
         vendor: Intel Corporation
         physical id: 1f.3
         bus info: pci@0000:00:1f.3
         version: 05
         width: 64 bits
         clock: 33MHz
         configuration: latency=0
         resources: memory:f7e19000-f7e190ff ioport:f040(size=32)
 *-scsi
      physical id: 2
      logical name: scsi0
      capabilities: emulated
    *-cdrom
         description: DVD-RAM writer
         product: CDDVDW SU-208FB
         vendor: TSSTcorp
         physical id: 0.0.0
         bus info: scsi@0:0.0.0
         logical name: /dev/cdrom
         logical name: /dev/sr0
         version: TC00
         capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
         configuration: ansiversion=5 status=nodisc
```

iwconfig show the following:

```

mark@mark-W54-55SU1-SUW:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"NETGEARPUR"  
      Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1E:2A:1F:80:14   
      Bit Rate=1 Mb/s   Tx-Power=20 dBm   
      Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
      Power Management:off
      Link Quality=56/70  Signal level=-54 dBm  
      Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
      Tx excessive retries:0  Invalid misc:17   Missed beacon:0

```

uname -a shows the followed the following before I backported it:
```

uname -a
 Linux mark-W54-55SU1-SUW 3.13.0-46-generic #79-Ubuntu SMP Tue Mar 10 20:06:50 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```

But now shows:

```

mark@mark-W54-55SU1-SUW:~$ uname -a 
Linux mark-W54-55SU1-SUW 3.13.0-46-generic #79-Ubuntu SMP Tue Mar 10 20:06:50 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```

I had a look at the syslog (/var/log) and [pasted]("http://paste.ubuntu.com/10612311/") up the log around the time frame that connection fails.  I have also removed all the firewalls, and ensured that "all users may connect to this network" is ticked for this connection on the network-manager gui for the main connection I use.

Has anyone got any ideas or should I just file this as a bug report?

Thanks in advance for any posts,

Mark.

---

### Post by b14speedfreak on 2015-03-21
So I looked at my syslog again, as the network-manager locked up again.  I found the following quite relevant:

```


Mar 21 12:38:19 mark-W54-55SU1-SUW NetworkManager[4706]: <warn> Connection disconnected (reason 15)
Mar 21 12:38:19 mark-W54-55SU1-SUW kernel: [ 5647.018495] cfg80211: Calling CRDA to update world regulatory domain
Mar 21 12:38:28 mark-W54-55SU1-SUW wpa_supplicant[1097]: wlan0: CTRL-EVENT-SCAN-STARTED 
Mar 21 12:38:28 mark-W54-55SU1-SUW NetworkManager[4706]: <info> (wlan0): supplicant interface state: 4-way handshake -> disconnected
Mar 21 12:38:28 mark-W54-55SU1-SUW NetworkManager[4706]: <info> Activation (wlan0/wireless): disconnected during association, asking for new key.
Mar 21 12:38:28 mark-W54-55SU1-SUW NetworkManager[4706]: <info> (wlan0): device state change: config -> need-auth (reason 'supplicant-disconnect') [50 60 8]
Mar 21 12:38:28 mark-W54-55SU1-SUW kernel: [ 5656.621049] cfg80211: World regulatory domain updated:
Mar 21 12:38:28 mark-W54-55SU1-SUW kernel: [ 5656.621055] cfg80211:  DFS Master region: unset
Mar 21 12:38:28 mark-W54-55SU1-SUW kernel: [ 5656.621056] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Mar 21 12:38:28 mark-W54-55SU1-SUW kernel: [ 5656.621060] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Mar 21 12:38:28 mark-W54-55SU1-SUW kernel: [ 5656.621062] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Mar 21 12:38:28 mark-W54-55SU1-SUW kernel: [ 5656.621064] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
Mar 21 12:38:28 mark-W54-55SU1-SUW kernel: [ 5656.621066] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Mar 21 12:38:28 mark-W54-55SU1-SUW kernel: [ 5656.621067] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Mar 21 12:38:28 mark-W54-55SU1-SUW dbus[580]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Mar 21 12:38:29 mark-W54-55SU1-SUW dbus[580]: [system] Successfully activated service 'org.freedesktop.hostname1'
Mar 21 12:38:29 mark-W54-55SU1-SUW kernel: [ 5656.957853] systemd-hostnamed[4731]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!

```

I looked up nss-myhostname via google and found the [following]("http://askubuntu.com/questions/453072/what-is-nss-myhostname-and-why-is-it-not-installable").  I forgot to mention that I have a LAMP stack installed in order to make use of Drupal development.  I did alter the /etc/hosts file as I was trying to setup virtual hosting.  So I commented out the alterations I made...I hope this sorts it out!  But any other ideas welcomed.

---

### Post by jeremy31 on 2015-03-21
It might be worth trying the backports to see if it will fix
```
sudo apt-get install build-essential linux-headers-generic
```
```
wget https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.19-rc1/backports-3.19-rc1-1.tar.gz
```
```
tar -zxvf backports-3.19-rc1-1.tar.gz
```
```
cd backports-3.19-rc1-1
```
```
make defconfig-rtlwifi
```
```
make
```
```
sudo make install
```

And this might help also ```
[COLOR=#222222]echo "options rtl8723be fwlps=N ips=N" | sudo tee /etc/modprobe.d/rtl8723be.conf
```
Reboot[/COLOR]

---

### Post by b14speedfreak on 2015-04-05
Hey sorry for the delay in response.  But I guess this seemed to sort things out a bit.  I have had a few instances where my connection has needed to be reset, but its no where near as bad as it once was.  Instead of every 5 mins its more like once a week or so!  So thanks again for your posts and help :)

---

### Post by praseodym on 2015-04-05
If the card gets too hot, you can try additionally:

```
echo 'KERNEL=="wlan0", RUN+="/sbin/iwconfig wlan0 txpower [COLOR="#FF0000"]15[/COLOR]"' | sudo tee -a /etc/udev/rules.d/70-persistent-net.rules
```
You can also try: 15dBm is ~31mW, 18dBm is ~63mW of the allowed 100 mW (which is 20 dBm)

---

