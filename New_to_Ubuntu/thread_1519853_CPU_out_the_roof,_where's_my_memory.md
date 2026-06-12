---
title: "CPU out the roof, where's my memory??"
date: 2010-06-28
forum: New to Ubuntu
---

### Post by Xinu38 on 2010-06-28
hi, so i been trying to do this forever now, found some threads how to delete the drivers, and reinstall new drivers, still didnt work.

for some reason, my computer will NOT use my graphics card correctly is what im figuring out. heres a few pics of my computer just IDLE, and another pic of streaming a video line on live stream. 

this was after a restart, no programs open, been idle for about 10 minutes and i was in awe of how active the CPU bounces.

[IMG]http://i2.photobucket.com/albums/y41/Xinu38/cpucrap.png[/IMG]


at this point i tried to put in the better drivers. but it would never download or install any of em, well i finally got it to work today.

[IMG]http://i2.photobucket.com/albums/y41/Xinu38/driverview.png[/IMG]

but this still didnt seem to do anything at all. my memory is still untouched and my cpu is screaming. heres my computer trying to do a stream video. 

[IMG]http://i2.photobucket.com/albums/y41/Xinu38/crapcpuagain.png[/IMG]

as i said up top, i did find a tut on how to delete the drivers in terminal, but for some reason, at the end of the deletion it asked are you sure y/n and whenever i typed y or yes it always went no and ended the terminal. every restart it says something about the nvidia card i have isnt supported.

before on windows, i could run warcraft, half life 2, black and white 2 etc all on the computer. but now, i tried to play starcraft brood war and it lags like a bitch. 

i have 2 gigs of ram or so. i need help to get this corrected cause nothing i have tried for the past few months have helped. thanks in advanced.

---

### Post by mikewhatever on 2010-06-28
Can you post your computer specs. What's the graphics card model?
In the precesses tab, can you check which process users CPU the most (or run top and post the output).

---

### Post by Xinu38 on 2010-06-28
> **mikewhatever said:**
> Can you post your computer specs. What's the graphics card model?
In the precesses tab, can you check which process users CPU the most (or run top and post the output).

ya ya, ubuntu 10.4, comp specs is older specs, pent 3 age, but 2 gig ram with nvidia 7600 card. 200gig hd, and the only thing that is killing the CPU on the process tab that i saw with just idle is gnome system monitor and XORG, compiz is on there but only uses like 1 or 2% same for rhythmbox. dont know what other info you want exactly, hope i said enough.

o and btw, i dont normally post anything on forums cause i normally always find an answer somewhere, so i feel kind of shameful i gotta actually post something. so i appreciate all the help i can have on this issue. cause i am just plain lost.

---

### Post by QIII on 2010-06-29
Could you install htop

```
sudo apt-get install htop
```

then 

```
htop
```

and cut and paste the results?

---

### Post by robert shearer on 2010-06-29
> comp specs is older specs, pent 3 age
Would help if this was accurate so....

In a terminal type 

```
sudo lshw
```

and report your cpu.

lshw = **l**i**s**t **h**ard**w**are
and is  comprehensive.

---

### Post by mikewhatever on 2010-06-29
The gnome-system-monitor itself tends to be on the cpu intensive side of processes with constant refreshing of graphs and data that it does. As suggested by QIII above, run htop instead, it is much lighter. In case the cpu usage is still too high, turn of compiz.
Last but not least, nothing seems to be wrong with the memory.

---

### Post by Xinu38 on 2010-06-29
> **QIII said:**
> Could you install htop

```
sudo apt-get install htop
```

then 

```
htop
```

and cut and paste the results?

```

  1  [||||||||||||||||||||||||                                                                               21.0%]     Tasks: 242 total, 1 running
  2  [|||||||||||                                                                                             9.1%]     Load average: 0.93 1.07 1.21 
  Mem[||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||774/2012MB]     Uptime: 1 day, 01:06:25
  Swp[                                                                                                    0/5890MB]

  PID USER     PRI  NI  VIRT   RES   SHR S CPU% MEM%   TIME+  Command
 1062 root      20   0  177M 51972 14012 S  7.0  2.5 26:37.15 /usr/bin/X :0 -nr -verbose -auth /var/run/gdm/auth-for-gdm-H28nji/database -nolisten tcp vt7
 1618 brad      20   0  114M 94476 15248 S  7.0  4.6 10:44.39 compiz
 7323 brad      21   1  308M 81724 34896 S  5.0  4.0  2:20.25 rhythmbox
 7723 brad      39  19  2720  1404   972 R  3.0  0.1  0:00.72 htop
 7613 brad      20   0 45816 12972  9616 S  3.0  0.6  0:06.39 gnome-terminal
 2024 brad      20   0  308M 81724 34896 S  1.0  4.0 10:27.70 rhythmbox
 7225 brad      20   0  139M 24180 16448 S  1.0  1.2  1:04.11 /opt/google/chrome/chrome --type=plugin --plugin-path=/usr/lib/adobe-flashplugin/libflashplayer.so --lang=en-US --plugin-data-dir=/home/brad/.config/google-chrome/Default --ch
 7060 brad      20   0  308M 81724 34896 S  1.0  4.0  0:23.45 rhythmbox
 1773 brad      20   0 19776  9764  7764 S  1.0  0.5  0:06.53 /usr/bin/gtk-window-decorator
 7075 brad      20   0  196M 56480 23272 S  1.0  2.7  0:00.08 /opt/google/chrome/google-chrome
 1651 brad      -6   0  157M 10724  9472 S  0.0  0.5  9:09.15 /usr/bin/pulseaudio --start --log-target=syslog
 7059 brad      20   0  308M 81724 34896 S  0.0  4.0  0:47.84 rhythmbox
 1644 brad      20   0 48640 22720 11820 S  0.0  1.1  0:09.19 gnome-panel
 1629 brad       9 -11  157M 10724  9472 S  0.0  0.5  6:44.41 /usr/bin/pulseaudio --start --log-target=syslog
 1590 brad      20   0  3384  1632   664 S  0.0  0.1  0:51.82 /bin/dbus-daemon --fork --print-pid 5 --print-address 9 --session
 7078 brad      20   0  196M 56480 23272 S  0.0  2.7  0:09.61 /opt/google/chrome/google-chrome
    1 root      20   0  2800  1608  1164 S  0.0  0.1  0:00.56 /sbin/init
  395 root      20   0  2312   912   648 S  0.0  0.0  0:00.08 upstart-udev-bridge --daemon
  418 root      16  -4  2568   972   316 S  0.0  0.0  0:00.06 udevd --daemon
  690 root      18  -2  2776  1100   344 S  0.0  0.1  0:00.02 udevd --daemon
  766 syslog    20   0 34536  1496  1020 S  0.0  0.1  0:00.28 rsyslogd -c4
  799 syslog    20   0 34536  1496  1020 S  0.0  0.1  0:00.04 rsyslogd -c4
  800 syslog    20   0 34536  1496  1020 S  0.0  0.1  0:00.00 rsyslogd -c4
 7720 syslog    20   0 34536  1496  1020 S  0.0  0.1  0:00.00 rsyslogd -c4
  853 messageb  20   0  3364  1628   760 S  0.0  0.1  0:07.37 dbus-daemon --system --fork
  867 avahi     20   0  2924  1528  1260 S  0.0  0.1  0:00.28 avahi-daemon: running [Stoke.local]
  868 avahi     20   0  2924   544   320 S  0.0  0.0  0:00.00 avahi-daemon: chroot helper
  884 root      20   0 18432  3088  2552 S  0.0  0.1  0:00.08 gdm-binary
 1046 root      20   0 18432  3088  2552 S  0.0  0.1  0:00.00 gdm-binary
  893 root      20   0 18552  3780  3164 S  0.0  0.2  0:00.08 NetworkManager
  999 root      20   0 18552  3780  3164 S  0.0  0.2  0:00.00 NetworkManager
  895 root      20   0  4164  2260  1828 S  0.0  0.1  0:00.02 /usr/sbin/modem-manager
  910 root      20   0  4824  1712  1440 S  0.0  0.1  0:00.00 /sbin/wpa_supplicant -u -s
  914 root      20   0 20652  3232  2356 S  0.0  0.2  0:00.09 /usr/sbin/console-kit-daemon --no-daemon
  919 root      20   0 20652  3232  2356 S  0.0  0.2  0:00.00 /usr/sbin/console-kit-daemon --no-daemon
  921 root      20   0 20652  3232  2356 S  0.0  0.2  0:00.00 /usr/sbin/console-kit-daemon --no-daemon
  922 root      20   0 20652  3232  2356 S  0.0  0.2  0:00.00 /usr/sbin/console-kit-daemon --no-daemon
  923 root      20   0 20652  3232  2356 S  0.0  0.2  0:00.00 /usr/sbin/console-kit-daemon --no-daemon
  924 root      20   0 20652  3232  2356 S  0.0  0.2  0:00.00 /usr/sbin/console-kit-daemon --no-daemon
  925 root      20   0 20652  3232  2356 S  0.0  0.2  0:00.00 /usr/sbin/console-kit-daemon --no-daemon
  927 root      20   0 20652  3232  2356 S  0.0  0.2  0:00.00 /usr/sbin/console-kit-daemon --no-daemon
  928 root      20   0 20652  3232  2356 S  0.0  0.2  0:00.00 /usr/sbin/console-kit-daemon --no-daemon
  929 root      20   0 20652  3232  2356 S  0.0  0.2  0:00.00 /usr/sbin/console-kit-daemon --no-daemon
  930 root      20   0 20652  3232  2356 S  0.0  0.2  0:00.00 /usr/sbin/console-kit-daemon --no-daemon
  931 root      20   0 20652  3232  2356 S  0.0  0.2  0:00.00 /usr/sbin/console-kit-daemon --no-daemon
  932 root      20   0 20652  3232  2356 S  0.0  0.2  0:00.00 /usr/sbin/console-kit-daemon --no-daemon
  933 root      20   0 20652  3232  2356 S  0.0  0.2  0:00.00 /usr/sbin/console-kit-daemon --no-daemon
  934 root      20   0 20652  3232  2356 S  0.0  0.2  0:00.00 /usr/sbin/console-kit-daemon --no-daemon
F1Help  F2Setup F3SearchF4InvertF5Tree  F6SortByF7Nice -F8Nice +F9Kill  F10Quit

```

that is what came  up.

---

### Post by Xinu38 on 2010-06-29
> **robert shearer said:**
> Would help if this was accurate so....

In a terminal type 

```
sudo lshw
```

and report your cpu.

lshw = **l**i**s**t **h**ard**w**are
and is  comprehensive.

kk, heres this one.

```
    bus info: cpu@1
          version: 15.3.2
          slot: Socket 939
          size: 1GHz
          capacity: 3700MHz
          clock: 199MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: c
             slot: L1 Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: e
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back unified
     *-memory:0
          description: System Memory
          physical id: 35
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR 400 MHz (2.5 ns)
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 512MiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: DIMM DDR 400 MHz (2.5 ns)
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 512MiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:2
             description: DIMM DDR 400 MHz (2.5 ns)
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
             size: 1GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:3
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A3
             width: 64 bits
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 3
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 0
          vendor: nVidia Corporation
          physical id: 0.1
          bus info: pci@0000:00:00.1
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:3 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 1
          vendor: nVidia Corporation
          physical id: 0.2
          bus info: pci@0000:00:00.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:4 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 5
          vendor: nVidia Corporation
          physical id: 0.3
          bus info: pci@0000:00:00.3
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:5 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 4
          vendor: nVidia Corporation
          physical id: 0.4
          bus info: pci@0000:00:00.4
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master
          configuration: latency=0
     *-memory:6 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 0.5
          bus info: pci@0000:00:00.5
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-memory:7 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 3
          vendor: nVidia Corporation
          physical id: 0.6
          bus info: pci@0000:00:00.6
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:8 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 2
          vendor: nVidia Corporation
          physical id: 0.7
          bus info: pci@0000:00:00.7
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-pci:0
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport
          resources: irq:24 ioport:e000(size=4096) memory:fdb00000-fdbfffff ioport:fdc00000(size=1048576)
     *-pci:1
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport
          resources: irq:25 ioport:c000(size=4096) memory:fa000000-fcffffff ioport:e0000000(size=268435456)
        *-display
             description: VGA compatible controller
             product: G73 [GeForce 7600 GT]
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@0000:02:00.0
             version: a1
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list rom
             configuration: driver=nvidia latency=0
             resources: irq:16 memory:fa000000-faffffff memory:e0000000-efffffff(prefetchable) memory:fb000000-fbffffff ioport:cf00(size=128) memory:fcfe0000-fcffffff(prefetchable)
     *-memory:9 UNCLAIMED
          description: RAM memory
          product: MCP51 Host Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP51 LPC Bridge
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP51 SMBus
          vendor: nVidia Corporation
          physical id: a.1
          bus info: pci@0000:00:0a.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:255 ioport:4c00(size=64) ioport:4c40(size=64)
     *-memory:10 UNCLAIMED
          description: RAM memory
          product: MCP51 Memory Controller 0
          vendor: nVidia Corporation
          physical id: a.2
          bus info: pci@0000:00:0a.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:20 memory:fe02f000-fe02ffff
     *-usb:1
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b.1
          bus info: pci@0000:00:0b.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:21 memory:fe02e000-fe02e0ff
     *-ide:0
          description: IDE interface
          product: MCP51 IDE
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          logical name: scsi1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fd00(size=16)
        *-cdrom
             description: DVD writer
             product: CD/DVDW TS-H552L
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             logical name: /media/cdrom0
             version: 0614
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,utf8 state=mounted status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom
                logical name: /media/cdrom0
                capabilities: partitioned partitioned:mac
                configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,utf8 state=mounted
              *-volume:0 UNCLAIMED
                   description: Apple partition map
                   physical id: 1
                   capacity: 1KiB
              *-volume:1 UNCLAIMED
                   description: Apple HFS
                   physical id: 2
                   size: 556MiB
                   capacity: 556MiB
                   capabilities: hfs initialized
                   configuration: created=1999-08-01 12:37:49 filesystem=hfs label=Brood War CD modified=1999-08-03 15:55:44 state=clean
     *-ide:1
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          logical name: scsi2
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:f800(size=16) memory:fe02d000-fe02dfff
        *-disk
             description: ATA Disk
             product: ST3250823AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: 3.03
             serial: 3ND2PEVH
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=cab10bee
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: d9d68dc8-1ea0-4e81-9774-e88a02108462
                size: 227GiB
                capacity: 227GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2009-12-12 12:46:52 filesystem=ext4 lastmountpoint=/&#65533;&#65533;\t&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;~&#65533;&#65533;u^ &#65533;U/&#65533;&#65533;~&#65533;&#65533;~!&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;~&#65533;&#65533;~&#65533;&#65533;a modified=2010-06-20 01:30:34 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-06-28 19:11:18 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 5891MiB
                capacity: 5891MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 5890MiB
                   capabilities: nofs
     *-ide:2
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: f
          bus info: pci@0000:00:0f.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:22 ioport:9e0(size=8) ioport:be0(size=4) ioport:960(size=8) ioport:b60(size=4) ioport:f300(size=16) memory:fe02c000-fe02cfff
     *-pci:2
          description: PCI bridge
          product: MCP51 PCI Bridge
          vendor: nVidia Corporation
          physical id: 10
          bus info: pci@0000:00:10.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht bus_master cap_list
          resources: ioport:d000(size=4096) memory:fde00000-fdefffff memory:fdd00000-fddfffff(prefetchable)
        *-firewire
             description: FireWire (IEEE 1394)
             product: FW322/323
             vendor: Agere Systems
             physical id: 5
             bus info: pci@0000:03:05.0
             version: 61
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci1394 latency=32 maxlatency=24 mingnt=12
             resources: irq:19 memory:fdeff000-fdefffff
        *-network
             description: Ethernet interface
             product: NC100 Network Everywhere Fast Ethernet 10/100
             vendor: ADMtek
             physical id: a
             bus info: pci@0000:03:0a.0
             logical name: eth0
             version: 11
             serial: 00:18:f8:0b:a8:bd
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom ethernet physical
             configuration: broadcast=yes driver=tulip driverversion=1.1.15 ip=192.168.1.5 latency=32 maxlatency=128 mingnt=64 multicast=yes
             resources: irq:18 ioport:de00(size=256) memory:fdefe000-fdefe3ff memory:fdd00000-fdd1ffff(prefetchable)
     *-multimedia
          description: Audio device
          product: MCP51 High Definition Audio
          vendor: nVidia Corporation
          physical id: 10.1
          bus info: pci@0000:00:10.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
          resources: irq:22 memory:fe024000-fe027fff
     *-bridge
          description: Ethernet interface
          product: MCP51 Ethernet Controller
          vendor: nVidia Corporation
          physical id: 14
          bus info: pci@0000:00:14.0
          logical name: eth1
          version: a1
          serial: 00:17:31:05:da:99
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
          resources: irq:23 memory:fe02b000-fe02bfff ioport:f200(size=8)
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi
          physical id: 4
          bus info: usb@2:8
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@6:0.0.1
             logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@6:0.0.2
             logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@6:0.0.3
             logical name: /dev/sde

```

---

### Post by Xinu38 on 2010-06-29
> **mikewhatever said:**
> The gnome-system-monitor itself tends to be on the cpu intensive side of processes with constant refreshing of graphs and data that it does. As suggested by QIII above, run htop instead, it is much lighter. In case the cpu usage is still too high, turn of compiz.
Last but not least, nothing seems to be wrong with the memory.

well the memory never budges, stays at 700mbs constantly no matter what i do, thought hte memory should cushion the the cpu usage. or am i wrong here...

---

### Post by robert shearer on 2010-06-29
You missed the 4 lines **before**...
>  bus info: cpu@0 that identify the cpu. 

here,by way of example,are mine...
 *-cpu
          description: CPU
          product: AMD Athlon(tm) XP 2600+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0



Further down your post lists.
> description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz

So that would seem to indicate an AMD cpu (in a Gigabyte/nvidia board ?)
and a bit more advanced than a P3 too.

Look at the top of the lshw output for the motherboard.
Also, which windows were you running and was it 32 or 64 bit ?

---

### Post by Xinu38 on 2010-06-29
> **robert shearer said:**
> You missed the 4 lines **before**...
 that identify the cpu. 

here,by way of example,are mine...
 *-cpu
          description: CPU
          product: AMD Athlon(tm) XP 2600+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0



Further down your 
So that would seem to indicate an AMD cpu (in a Gigabyte/nvidia board ?)
and a bit more advanced than a P3 too.

Look at the top of the lshw output for the motherboard.
Also, which windows were you running and was it 32 or 64 bit ?

weird, didnt show anything above, i didnt think it was all the info, ill look again.


```
     *-cpu:1
          description: CPU
          vendor: AMD
          physical id: 5
          bus info: cpu@1
          version: 15.3.2
          slot: Socket 939
          size: 1GHz
          capacity: 3700MHz
          clock: 199MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: c
             slot: L1 Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: e
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back unified

```

did it again. and i was running xp media center.

---

### Post by robert shearer on 2010-06-29
Somethings weird here.
The reported cpu is only 1000MHz yet the board can accommodate one at 3700MHz.
The cpu has no model identifier and the clock speed is only 199MHz.

Possibly it is crippled to suit a form factor (media centre) and minimal power supply so that fan noise is low...?  Thinking aloud here.

Or its not a genuine AMD ?? Did it ship with the board or have you replaced the original  ?.

Can you run this command and post the output here..
```
cat /proc/cpuinfo
```



According to lshw you should have a K8 in a 939 socket and i can't find a listing for one less than 2000MHz.
[http://www.cpu-world.com/CPUs/K8/TYPE-Athlon%2064.html](http://www.cpu-world.com/CPUs/K8/TYPE-Athlon%2064.html)

Unless you are running cpu-frequency scaling for low power use/heat output.
This could explain why the cpu is being used so intensively and only reports at 1000MHz.

Right click in a space on the top panel and select 'add to panel'
From the box that opens scroll down to 'cpu frequency scaling monitor'.
Select it and 'Add' (if it says that your cpu doesnt support frequency scaling report back.

Now try some thing cpu intensive and see what the applet does. Right click it and see what power mode it is set to.
Report back.


This is a desktop right  ? not a lappy ?

---

### Post by mikewhatever on 2010-06-30
> **Xinu38 said:**
> well the memory never budges, stays at 700mbs constantly no matter what i do, thought hte memory should cushion the the cpu usage. or am i wrong here...

No data is swapped in your case, and if you want to call it cushioning, well, it's working.

---

### Post by robert shearer on 2010-06-30
One other simple possibility that has affected me in the past is a dying cmos battery.

One morning my Athlon xp1800+ became a Duron 1600 and it took ages to figure out.
Replacing the rather old cmos battery fixed it.

I don't think this is the problem in your case but **if all else** fails the following **may** be worth a try. 

Before you do anything, access the bios and use a camera to record each screen (and/or manually write down) then check that the captured settings are readable.

That way when you replace the battery and the bios is reset to default you will be able to reconfigure it using the camera captures.

Have a ps2 plug keyboard at hand, you may need it to access the bios after battery replacement as some defaults do not recognise usb input.

---

### Post by cascade9 on 2010-06-30
Socket 939 is a lot faster than any of the P3s (even the last 1400MHz 512k versions). 

I've found gnome-system-monitor is a resource pig, htop is a lot better (as you can see yourself from the difference between them). Compiz and xorg are eating a fair chuck on CPU as well....

Also, though its very hard to know 100% for sure, but in most of the socket 939 motherboards are  dual-channel RAM capable, but normally you need the paired sticks in bank 0+1, or 2+3. our RAM is in banks 1+2, so its probably in singlwe channel mode...not that should affect the CPU much, if at all.   

> **Xinu38 said:**
> well the memory never budges, stays at 700mbs constantly no matter what i do, thought hte memory should cushion the the cpu usage. or am i wrong here...

RAM is RAM, CPU is CPU, and one cant substitute for the other.  

> **robert shearer said:**
> Somethings weird here.
The reported cpu is only 1000MHz yet the board can accommodate one at 3700MHz.
The cpu has no model identifier and the clock speed is only 199MHz.

Possibly it is crippled to suit a form factor (media centre) and minimal power supply so that fan noise is low...?  Thinking aloud here.

Or its not a genuine AMD ?? Did it ship with the board or have you replaced the original  ?.

Can you run this command and post the output here..
```
cat /proc/cpuinfo
```

I would guess that its a Athlon 64 X2 3800+ (2000MHz, 512k) with cpufreq running, and lshw is reporting it wrong, which I've seen before, like here -

> I double-checked to be sure what I remembered was correct - it's got 512 of level 2 cache - hence an Athlon 64. It's interesting that it shows the speed at 2200mhz but also shows it capable of 3000mhz[http://ubuntuforums.org/showthread.php?t=1518630&page=3](http://ubuntuforums.org/showthread.php?t=1518630&page=3)

BTW, 'sudo lshw' shows more info than plain lshw.  

> **robert shearer said:**
> 
According to lshw you should have a K8 in a 939 socket and i can't find a listing for one less than 2000MHz.
[http://www.cpu-world.com/CPUs/K8/TYPE-Athlon%2064.html](http://www.cpu-world.com/CPUs/K8/TYPE-Athlon%2064.html)



You missed one, the 3000+. Single core anyway, the CPU Xinu38 is runnign is a dualie. ;) 

[U][http://www.cpu-world.com/CPUs/K8/AMD-Athlon%2064%203000%2B%20-%20ADA3000DIK4BI%20%28ADA3000BIBOX%29.html](http://www.cpu-world.com/CPUs/K8/AMD-Athlon%2064%203000%2B%20-%20ADA3000DIK4BI%20%28ADA3000BIBOX%29.html)

[/U]Edit- bah, linked the wrong CPU. fixed now ;)

---

### Post by robert shearer on 2010-06-30
Yeah, the command run was sudo lshw  I was shorthanding.

> You missed one, the 3000+. good find Sherlock. :)

>  Single core anyway, the CPU Xinu38 is running is a dualie.   How do you figure that ?? :confused:

---

### Post by cascade9 on 2010-06-30
> **robert shearer said:**
> Yeah, the command run was sudo lshw  I was shorthanding.

  How do you figure that ?? :confused:


My apologies, I was saying the sudo lshw thing more for Xinu38s benefit. For all I know, he did run the command, removed the 1st bit, as I get the motherboard model, etc at the beginning of output on my main box, and the computer I'm sitting in front of right now (and I'm pretty sure that I get that info even on the awful compaq P3 I use as a media boxxen)

As for the dualie, well, what looks like 2 lines in the gnome-system-monitor output, and the clincher is CPU 1+2 on htop

---

### Post by robert shearer on 2010-06-30
> **cascade9 said:**
> the clincher is CPU 1+2 on htop

Ahhhhh, missed that, thanks for the enlightenment. :)

---

### Post by Xinu38 on 2010-06-30
> **robert shearer said:**
> Somethings weird here.
The reported cpu is only 1000MHz yet the board can accommodate one at 3700MHz.
The cpu has no model identifier and the clock speed is only 199MHz.

Possibly it is crippled to suit a form factor (media centre) and minimal power supply so that fan noise is low...?  Thinking aloud here.

Or its not a genuine AMD ?? Did it ship with the board or have you replaced the original  ?.

Can you run this command and post the output here..
```
cat /proc/cpuinfo
```



According to lshw you should have a K8 in a 939 socket and i can't find a listing for one less than 2000MHz.
[http://www.cpu-world.com/CPUs/K8/TYPE-Athlon%2064.html](http://www.cpu-world.com/CPUs/K8/TYPE-Athlon%2064.html)

Unless you are running cpu-frequency scaling for low power use/heat output.
This could explain why the cpu is being used so intensively and only reports at 1000MHz.

Right click in a space on the top panel and select 'add to panel'
From the box that opens scroll down to 'cpu frequency scaling monitor'.
Select it and 'Add' (if it says that your cpu doesnt support frequency scaling report back.

Now try some thing cpu intensive and see what the applet does. Right click it and see what power mode it is set to.
Report back.


This is a desktop right  ? not a lappy ?

```
brad@Stoke:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 35
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping	: 2
cpu MHz		: 1000.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy
bogomips	: 2004.34
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 35
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping	: 2
cpu MHz		: 1000.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy
bogomips	: 2004.34
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

```

theres the cpu info, ya its a desktop and ive replaced the graphics card and added ram from i believe an original 1.5gig (2 sticks) and added a 500mb stick to make it 2 gigs. those are the only things i changed. 

as far as i remember, was never like this with windows, but when i switched, ubuntu 9.10 was lightning fast, i was actually stunned, but still video streams lagged, etc.

---

### Post by Kazade on 2010-06-30
> 
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
cpu MHz		: 1000.000


That's almost certainly not right. Add the CPU Frequency Scaling applet and see if you can disable frequency scaling from there (as mentioned above).

---

### Post by sandy8925 on 2010-06-30
the low speed is probably due to cpu frequency scaling as others have said. nothing to worry about. if you want good performance use the cpu frequency applet to set the frequency to max and it should work well.

also to check if drivers are working properly run lsmod|grep nvidia and post the results here. if nothing comes up try lsmod|grep noveau.

---

### Post by ibuclaw on 2010-06-30
> **Kazade said:**
> That's almost certainly not right. Add the CPU Frequency Scaling applet and see if you can disable frequency scaling from there (as mentioned above).

I looks perfectly all right to me. :)

The X2 3800+ works at a clockrate of 2000 MHz. That is 1000MHz for each core, and there are x2 of them.

Trying to veer this topic back to the scope of the original question.

@Xinu38 - You say that video **streaming** - as in Flash Videos - is lagging? I would have suspected the GPU, or the driver that is installed for it - rather than the CPU  - to be the problem here.

The simplest thing you can try is:
[LIST=1]
[*]Turn off Visual Effects.
Don't use overblown Compiz effects when you need the GPU to process something else.
[*]Try switching to another Browser - ie: Chromium, and see if the problem follows.
[/LIST]
Regards

---

### Post by Xinu38 on 2010-06-30
> **ibuclaw said:**
> I looks perfectly all right to me. :)

The X2 3800+ works at a clockrate of 2000 MHz. That is 1000MHz for each core, and there are x2 of them.

Trying to veer this topic back to the scope of the original question.

@Xinu38 - You say that video **streaming** - as in Flash Videos - is lagging? I would have suspected the GPU, or the driver that is installed for it - rather than the CPU  - to be the problem here.

The simplest thing you can try is:
[LIST=1]
[*]Turn off Visual Effects.
Don't use overblown Compiz effects when you need the GPU to process something else.
[*]Try switching to another Browser - ie: Chromium, and see if the problem follows.
[/LIST]
Regards
 
well thats where i noticed it for an online aspect, i cant run starcraft brood war (which if you dont know was made back in the late 90's) i cant run brood war smoothly, cpu maxes out playing a 12 year old computer game. it literally blows. livestream.com, youtube in hd, hulu, almost anything will spike my cpu usage, i just got home from work, imma try some things here that was posted to see what i get.

i have a friend that has linux and he was saying for some reason the graphics card wasnt being used, or not used properly with ubuntu. i downloaded new drivers etc to try to get it fixed, but im guessing since i have an older graphics card it isnt supported by ubuntu? ill restart my comp to see what it tells me in the beginning word for word.

---

### Post by Xinu38 on 2010-06-30
> **sandy8925 said:**
> the low speed is probably due to cpu frequency scaling as others have said. nothing to worry about. if you want good performance use the cpu frequency applet to set the frequency to max and it should work well.

also to check if drivers are working properly run lsmod|grep nvidia and post the results here. if nothing comes up try lsmod|grep noveau.

imma dl the app, but heres the results

```
lsmod|grep nvidia
nvidia               9961216  38 
agpgart                31724  1 nvidia

```

also here is a before and after shot of the usage since i dled htop, still doesnt run as smooth as i want it with programs, but it is improved :)

before
[IMG]http://i2.photobucket.com/albums/y41/Xinu38/cpucrap.png[/IMG]

after
[IMG]http://i2.photobucket.com/albums/y41/Xinu38/newcpu.png[/IMG]

i thank you guys so much for all the help and time.

---

### Post by ibuclaw on 2010-06-30
Don't look at the graph, the graph lies (sort of). :)

Have a look at the processes tab, and deduct the usage the monitor uses itself from the total usage.

For me, the system monitor uses more than all other processes combined ... 
It's a known bug and shouldn't be trusted. ;)

Regards

---

### Post by Xinu38 on 2010-06-30
i tried installing a applet for the cpu scaling, gave me this message.

> Reguires installation of untrusted packages

The action would require the installation of packages from no authenticated sources.

---

### Post by Xinu38 on 2010-06-30
> **ibuclaw said:**
> Don't look at the graph, the graph lies (sort of). :)

Have a look at the processes tab, and deduct the usage the monitor uses itself from the total usage.

For me, the system monitor uses more than all other processes combined ... 
It's a known bug and shouldn't be trusted. ;)

Regards

tru, this is what mine does, XORG would sometimes be at 2 or 4, but would spike all the time. idk what that is...

[IMG]http://i2.photobucket.com/albums/y41/Xinu38/processes.png[/IMG]

---

### Post by Xinu38 on 2010-06-30
dont know if it means anything, but when i start up, looks like a terminal code telling me that nforce2 blah blah probing error. 

than it gives me a message about monitor configuration.

---

### Post by spydeyrch on 2010-06-30
> **ibuclaw said:**
> I looks perfectly all right to me. :)

The X2 3800+ works at a clock rate of 2000 MHz. That is 1000MHz for each core, and there are x2 of them.


sorry to be the sore thumb, but.........

That actually is not correct.  :confused: you can't take the frequency of the cores and multiply it by the number of cores to get the cpu frequency. i.e. 2 cores x 1GHz/per core = 2GHz. It doesn't work like that. If that was the case, then my quad core would be a 12.8GHz cpu! because each core runs at 3.2GHz.

When dealing with multi-core cpus, each core runs at the specified cpu frequency. Hence, each core runs at 2GHz. Or in my case, each of my four cores runs at 3.2GHz. That is how CPU frequencies work with multi-core tech. You can't take the frequency and divide it by the number of cores to get each cores frequency. They all run at the same frequency (unless personally customized otherwise).

Perhaps that doesn't help with the actual issue but at least it clarifies the previous statement. I will go over the other posts to see if there is anything that I can do to help. 

:lolflag:

-Spydey :guitar:

---

### Post by ibuclaw on 2010-06-30
> **Xinu38 said:**
> dont know if it means anything, but when i start up, looks like a terminal code telling me that nforce2 blah blah probing error. 

than it gives me a message about monitor configuration.

That may be the start of something. Can you obtain a copy of Xorg and dmesg logs? They are in /var/log in the filesystem, but the quick terminal way would be running:

```
dmesg
```
```
cat /var/log/Xorg.0.log
```

Regards

---

### Post by ibuclaw on 2010-06-30
> **spydeyrch said:**
> sorry to be the sore thumb, but.........

That actually is not correct.  :confused: you can't take the frequency of the cores and multiply it by the number of cores to get the cpu frequency. i.e. 2 cores x 1GHz/per core = 2GHz. It doesn't work like that. If that was the case, then my quad core would be a 12.8GHz cpu! because each core runs at 3.2GHz.

Actually, it's adding ... but same thing. ;)
> **spydeyrch said:**
> 
When dealing with multi-core cpus, each core runs at the specified cpu frequency. Hence, each core runs at 2GHz. Or in my case, each of my four cores runs at 3.2GHz. That is how CPU frequencies work with multi-core tech. You can't take the frequency and divide it by the number of cores to get each cores frequency. They all run at the same frequency (unless personally customized otherwise).

Tell that to my 1.6GHz atom processor.
```

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU N270   @ 1.60GHz
stepping	: 2
cpu MHz		: 800.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 xtpr pdcm movbe lahf_lm
bogomips	: 3192.07
clflush size	: 64
cache_alignment	: 64
address sizes	: 32 bits physical, 32 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU N270   @ 1.60GHz
stepping	: 2
cpu MHz		: 800.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 xtpr pdcm movbe lahf_lm
bogomips	: 3191.92
clflush size	: 64
cache_alignment	: 64
address sizes	: 32 bits physical, 32 bits virtual
power management:

```
Maybe that's the hyper-threading talking though...

---

### Post by Xinu38 on 2010-06-30
> **spydeyrch said:**
> sorry to be the sore thumb, but.........

That actually is not correct.  :confused: you can't take the frequency of the cores and multiply it by the number of cores to get the cpu frequency. i.e. 2 cores x 1GHz/per core = 2GHz. It doesn't work like that. If that was the case, then my quad core would be a 12.8GHz cpu! because each core runs at 3.2GHz.

When dealing with multi-core cpus, each core runs at the specified cpu frequency. Hence, each core runs at 2GHz. Or in my case, each of my four cores runs at 3.2GHz. That is how CPU frequencies work with multi-core tech. You can't take the frequency and divide it by the number of cores to get each cores frequency. They all run at the same frequency (unless personally customized otherwise).

Perhaps that doesn't help with the actual issue but at least it clarifies the previous statement. I will go over the other posts to see if there is anything that I can do to help. 

:lolflag:

-Spydey :guitar:

:bow:

> **ibuclaw said:**
> That may be the start of something. Can you obtain a copy of Xorg and dmesg logs? They are in /var/log in the filesystem, but the quick terminal way would be running:

```
dmesg
```
```
cat /var/log/Xorg.0.log
```

Regards

for some reason it doesnt look like its giving me the full dmesg....

```
[    0.218603] pci 0000:00:0e.0: reg 18 io port: [0x970-0x977]
[    0.218608] pci 0000:00:0e.0: reg 1c io port: [0xb70-0xb73]
[    0.218614] pci 0000:00:0e.0: reg 20 io port: [0xf800-0xf80f]
[    0.218620] pci 0000:00:0e.0: reg 24 32bit mmio: [0xfe02d000-0xfe02dfff]
[    0.218668] pci 0000:00:0f.0: reg 10 io port: [0x9e0-0x9e7]
[    0.218674] pci 0000:00:0f.0: reg 14 io port: [0xbe0-0xbe3]
[    0.218680] pci 0000:00:0f.0: reg 18 io port: [0x960-0x967]
[    0.218685] pci 0000:00:0f.0: reg 1c io port: [0xb60-0xb63]
[    0.218691] pci 0000:00:0f.0: reg 20 io port: [0xf300-0xf30f]
[    0.218697] pci 0000:00:0f.0: reg 24 32bit mmio: [0xfe02c000-0xfe02cfff]
[    0.218788] pci 0000:00:10.1: reg 10 32bit mmio: [0xfe024000-0xfe027fff]
[    0.218824] pci 0000:00:10.1: PME# supported from D3hot D3cold
[    0.218828] pci 0000:00:10.1: PME# disabled
[    0.218862] pci 0000:00:14.0: reg 10 32bit mmio: [0xfe02b000-0xfe02bfff]
[    0.218868] pci 0000:00:14.0: reg 14 io port: [0xf200-0xf207]
[    0.218892] pci 0000:00:14.0: supports D1 D2
[    0.218895] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.218899] pci 0000:00:14.0: PME# disabled
[    0.219016] pci 0000:00:02.0: bridge io port: [0xe000-0xefff]
[    0.219020] pci 0000:00:02.0: bridge 32bit mmio: [0xfdb00000-0xfdbfffff]
[    0.219025] pci 0000:00:02.0: bridge 64bit mmio pref: [0xfdc00000-0xfdcfffff]
[    0.219049] pci 0000:02:00.0: reg 10 32bit mmio: [0xfa000000-0xfaffffff]
[    0.219058] pci 0000:02:00.0: reg 14 64bit mmio pref: [0xe0000000-0xefffffff]
[    0.219066] pci 0000:02:00.0: reg 1c 64bit mmio: [0xfb000000-0xfbffffff]
[    0.219072] pci 0000:02:00.0: reg 24 io port: [0xcf00-0xcf7f]
[    0.219077] pci 0000:02:00.0: reg 30 32bit mmio pref: [0xfcfe0000-0xfcffffff]
[    0.219132] pci 0000:00:04.0: bridge io port: [0xc000-0xcfff]
[    0.219136] pci 0000:00:04.0: bridge 32bit mmio: [0xfa000000-0xfcffffff]
[    0.219141] pci 0000:00:04.0: bridge 64bit mmio pref: [0xe0000000-0xefffffff]
[    0.219175] pci 0000:03:05.0: reg 10 32bit mmio: [0xfdeff000-0xfdefffff]
[    0.219213] pci 0000:03:05.0: supports D1 D2
[    0.219215] pci 0000:03:05.0: PME# supported from D0 D1 D2 D3hot
[    0.219220] pci 0000:03:05.0: PME# disabled
[    0.219252] pci 0000:03:0a.0: reg 10 io port: [0xde00-0xdeff]
[    0.219260] pci 0000:03:0a.0: reg 14 32bit mmio: [0xfdefe000-0xfdefe3ff]
[    0.219282] pci 0000:03:0a.0: reg 30 32bit mmio pref: [0xfdec0000-0xfdedffff]
[    0.219298] pci 0000:03:0a.0: supports D1 D2
[    0.219301] pci 0000:03:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.219305] pci 0000:03:0a.0: PME# disabled
[    0.219332] pci 0000:00:10.0: transparent bridge
[    0.219336] pci 0000:00:10.0: bridge io port: [0xd000-0xdfff]
[    0.219340] pci 0000:00:10.0: bridge 32bit mmio: [0xfde00000-0xfdefffff]
[    0.219345] pci 0000:00:10.0: bridge 32bit mmio pref: [0xfdd00000-0xfddfffff]
[    0.219354] pci_bus 0000:00: on NUMA node 0
[    0.219360] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.219629] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.324314] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.324505] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.324692] ACPI: PCI Interrupt Link [LNK3] (IRQs *5 7 9 10 11 14 15)
[    0.324874] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.325060] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 *7 9 10 11 14 15)
[    0.325243] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.325428] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.325613] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.325797] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.325986] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.326172] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)
[    0.326359] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.326545] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)
[    0.326733] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.326921] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.327106] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.327290] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.327474] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.327660] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[    0.327845] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 *10 11 14 15)
[    0.328082] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.328309] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.328530] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
[    0.328751] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[    0.328977] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0
[    0.329199] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[    0.329423] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[    0.329645] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[    0.329868] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
[    0.330093] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[    0.330317] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[    0.330541] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[    0.330765] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[    0.330990] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[    0.331213] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[    0.331437] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
[    0.331665] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
[    0.331888] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[    0.332124] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.332357] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[    0.332581] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[    0.332752] vgaarb: device added: PCI:0000:02:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.332756] vgaarb: loaded
[    0.332885] SCSI subsystem initialized
[    0.333002] libata version 3.00 loaded.
[    0.333086] usbcore: registered new interface driver usbfs
[    0.333100] usbcore: registered new interface driver hub
[    0.333128] usbcore: registered new device driver usb
[    0.333274] ACPI: WMI: Mapper loaded
[    0.333276] PCI: Using ACPI for IRQ routing
[    0.333459] NetLabel: Initializing
[    0.333461] NetLabel:  domain hash size = 128
[    0.333463] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.333479] NetLabel:  unlabeled traffic allowed by default
[    0.335511] AppArmor: AppArmor Filesystem Enabled
[    0.335533] pnp: PnP ACPI init
[    0.335551] ACPI: bus type pnp registered
[    0.340823] pnp: PnP ACPI: found 9 devices
[    0.340825] ACPI: ACPI bus type pnp unregistered
[    0.340829] PnPBIOS: Disabled by ACPI PNP
[    0.340842] system 00:01: ioport range 0x4000-0x407f has been reserved
[    0.340845] system 00:01: ioport range 0x4080-0x40ff has been reserved
[    0.340849] system 00:01: ioport range 0x4400-0x447f has been reserved
[    0.340852] system 00:01: ioport range 0x4480-0x44ff has been reserved
[    0.340855] system 00:01: ioport range 0x4800-0x487f has been reserved
[    0.340858] system 00:01: ioport range 0x4880-0x48ff has been reserved
[    0.340861] system 00:01: ioport range 0x2000-0x207f has been reserved
[    0.340864] system 00:01: ioport range 0x2080-0x20ff has been reserved
[    0.340870] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.340874] system 00:02: ioport range 0x800-0x87f has been reserved
[    0.340881] system 00:07: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.340887] system 00:08: iomem range 0xf0000-0xf3fff could not be reserved
[    0.340891] system 00:08: iomem range 0xf4000-0xf7fff could not be reserved
[    0.340894] system 00:08: iomem range 0xf8000-0xfbfff could not be reserved
[    0.340897] system 00:08: iomem range 0xfc000-0xfffff could not be reserved
[    0.340901] system 00:08: iomem range 0x7fef0000-0x7fefffff could not be reserved
[    0.340904] system 00:08: iomem range 0xffff0000-0xffffffff has been reserved
[    0.340908] system 00:08: iomem range 0x0-0x9ffff could not be reserved
[    0.340911] system 00:08: iomem range 0x100000-0x7feeffff could not be reserved
[    0.340915] system 00:08: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.340918] system 00:08: iomem range 0xfee00000-0xfeefffff has been reserved
[    0.340921] system 00:08: iomem range 0xfefff000-0xfeffffff has been reserved
[    0.340929] system 00:08: iomem range 0xfff80000-0xfff80fff has been reserved
[    0.340932] system 00:08: iomem range 0xfff90000-0xfffbffff has been reserved
[    0.340936] system 00:08: iomem range 0xfffed000-0xfffeffff has been reserved
[    0.375623] Switching to clocksource acpi_pm
[    0.375971] pci 0000:03:0a.0: BAR 6: address space collision on of device [0xfdec0000-0xfdedffff]
[    0.375971] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.375971] pci 0000:00:02.0:   IO window: 0xe000-0xefff
[    0.375971] pci 0000:00:02.0:   MEM window: 0xfdb00000-0xfdbfffff
[    0.375971] pci 0000:00:02.0:   PREFETCH window: 0x000000fdc00000-0x000000fdcfffff
[    0.375971] pci 0000:00:04.0: PCI bridge, secondary bus 0000:02
[    0.375971] pci 0000:00:04.0:   IO window: 0xc000-0xcfff
[    0.375971] pci 0000:00:04.0:   MEM window: 0xfa000000-0xfcffffff
[    0.375971] pci 0000:00:04.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
[    0.375971] pci 0000:00:10.0: PCI bridge, secondary bus 0000:03
[    0.375971] pci 0000:00:10.0:   IO window: 0xd000-0xdfff
[    0.375971] pci 0000:00:10.0:   MEM window: 0xfde00000-0xfdefffff
[    0.375971] pci 0000:00:10.0:   PREFETCH window: 0xfdd00000-0xfddfffff
[    0.375971] pci 0000:00:02.0: setting latency timer to 64
[    0.375971] pci 0000:00:04.0: setting latency timer to 64
[    0.375971] pci 0000:00:10.0: setting latency timer to 64
[    0.375971] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.375971] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.375971] pci_bus 0000:01: resource 0 io:  [0xe000-0xefff]
[    0.375971] pci_bus 0000:01: resource 1 mem: [0xfdb00000-0xfdbfffff]
[    0.375971] pci_bus 0000:01: resource 2 pref mem [0xfdc00000-0xfdcfffff]
[    0.375971] pci_bus 0000:02: resource 0 io:  [0xc000-0xcfff]
[    0.375971] pci_bus 0000:02: resource 1 mem: [0xfa000000-0xfcffffff]
[    0.375971] pci_bus 0000:02: resource 2 pref mem [0xe0000000-0xefffffff]
[    0.375971] pci_bus 0000:03: resource 0 io:  [0xd000-0xdfff]
[    0.375971] pci_bus 0000:03: resource 1 mem: [0xfde00000-0xfdefffff]
[    0.375971] pci_bus 0000:03: resource 2 pref mem [0xfdd00000-0xfddfffff]
[    0.375971] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.375971] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    0.375971] NET: Registered protocol family 2
[    0.375971] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.375971] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.375971] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.375971] TCP: Hash tables configured (established 131072 bind 65536)
[    0.375971] TCP reno registered
[    0.375971] NET: Registered protocol family 1
[    0.375971] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.375971] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.412072] pci 0000:00:09.0: Found disabled HT MSI Mapping
[    0.412080] pci 0000:00:0e.0: Enabling HT MSI Mapping
[    0.412138] pci 0000:00:09.0: Found disabled HT MSI Mapping
[    0.412146] pci 0000:00:0f.0: Enabling HT MSI Mapping
[    0.412206] pci 0000:00:09.0: Found disabled HT MSI Mapping
[    0.412212] pci 0000:00:10.0: Enabling HT MSI Mapping
[    0.412275] pci 0000:00:09.0: Found disabled HT MSI Mapping
[    0.412284] pci 0000:00:10.1: Enabling HT MSI Mapping
[    0.412304] pci 0000:02:00.0: Boot video device
[    0.412541] cpufreq-nforce2: No nForce2 chipset.
[    0.412569] Scanning for low memory corruption every 60 seconds
[    0.412689] audit: initializing netlink socket (disabled)
[    0.412700] type=2000 audit(1277934984.409:1): initialized
[    0.422955] highmem bounce pool size: 64 pages
[    0.422963] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.423320] Freeing initrd memory: 7782k freed
[    0.424798] VFS: Disk quotas dquot_6.5.2
[    0.424879] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.425691] fuse init (API version 7.13)
[    0.425806] msgmni has been set to 1695
[    0.426205] alg: No test for stdrng (krng)
[    0.426288] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.426294] io scheduler noop registered
[    0.426297] io scheduler anticipatory registered
[    0.426299] io scheduler deadline registered
[    0.426366] io scheduler cfq registered (default)
[    0.426623]   alloc irq_desc for 24 on node -1
[    0.426627]   alloc kstat_irqs on node -1
[    0.426648] pcieport 0000:00:02.0: irq 24 for MSI/MSI-X
[    0.426658] pcieport 0000:00:02.0: setting latency timer to 64
[    0.426765]   alloc irq_desc for 25 on node -1
[    0.426768]   alloc kstat_irqs on node -1
[    0.426773] pcieport 0000:00:04.0: irq 25 for MSI/MSI-X
[    0.426778] pcieport 0000:00:04.0: setting latency timer to 64
[    0.426846] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.426887] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.427140] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.427151] ACPI: Power Button [PWRB]
[    0.427252] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.427256] ACPI: Power Button [PWRF]
[    0.427336] fan PNP0C0B:00: registered as cooling_device0
[    0.427343] ACPI: Fan [FAN] (on)
[    0.428156] processor LNXCPU:00: registered as cooling_device1
[    0.428196] processor LNXCPU:01: registered as cooling_device2
[    0.435469] thermal LNXTHERM:01: registered as thermal_zone0
[    0.435477] ACPI: Thermal Zone [THRM] (40 C)
[    0.435615] isapnp: Scanning for PnP cards...
[    0.437021] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.438361] brd: module loaded
[    0.438877] loop: module loaded
[    0.438968] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.439173] pata_acpi 0000:00:0d.0: setting latency timer to 64
[    0.439620] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[    0.439626]   alloc irq_desc for 23 on node -1
[    0.439628]   alloc kstat_irqs on node -1
[    0.439641] pata_acpi 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    0.439659] pata_acpi 0000:00:0e.0: setting latency timer to 64
[    0.439667] pata_acpi 0000:00:0e.0: PCI INT A disabled
[    0.440073] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22
[    0.440076]   alloc irq_desc for 22 on node -1
[    0.440078]   alloc kstat_irqs on node -1
[    0.440086] pata_acpi 0000:00:0f.0: PCI INT A -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
[    0.440104] pata_acpi 0000:00:0f.0: setting latency timer to 64
[    0.440112] pata_acpi 0000:00:0f.0: PCI INT A disabled
[    0.440444] Fixed MDIO Bus: probed
[    0.440480] PPP generic driver version 2.4.2
[    0.440524] tun: Universal TUN/TAP device driver, 1.6
[    0.440526] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.440613] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.440981] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21
[    0.440984]   alloc irq_desc for 21 on node -1
[    0.440986]   alloc kstat_irqs on node -1
[    0.440994] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[APCL] -> GSI 21 (level, low) -> IRQ 21
[    0.441012] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    0.441016] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    0.441065] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    0.441093] ehci_hcd 0000:00:0b.1: debug port 1
[    0.441101] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported
[    0.441126] ehci_hcd 0000:00:0b.1: irq 21, io mem 0xfe02e000
[    0.456025] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    0.456125] usb usb1: configuration #1 chosen from 1 choice
[    0.456156] hub 1-0:1.0: USB hub found
[    0.456166] hub 1-0:1.0: 8 ports detected
[    0.456232] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.456598] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 20
[    0.456601]   alloc irq_desc for 20 on node -1
[    0.456603]   alloc kstat_irqs on node -1
[    0.456612] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[APCF] -> GSI 20 (level, low) -> IRQ 20
[    0.456620] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    0.456623] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    0.456656] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    0.456683] ohci_hcd 0000:00:0b.0: irq 20, io mem 0xfe02f000
[    0.514079] usb usb2: configuration #1 chosen from 1 choice
[    0.514106] hub 2-0:1.0: USB hub found
[    0.514116] hub 2-0:1.0: 8 ports detected
[    0.514177] uhci_hcd: USB Universal Host Controller Interface driver
[    0.514266] PNP: No PS/2 controller found. Probing ports directly.
[    0.516985] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.516994] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.517118] mice: PS/2 mouse device common for all mice
[    0.517248] rtc_cmos 00:04: RTC can wake from S4
[    0.517291] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.517325] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    0.517436] device-mapper: uevent: version 1.0.3
[    0.517563] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.517638] device-mapper: multipath: version 1.1.0 loaded
[    0.517641] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.517769] EISA: Probing bus 0 at eisa.0
[    0.517779] Cannot allocate resource for EISA slot 2
[    0.517784] Cannot allocate resource for EISA slot 4
[    0.517797] EISA: Detected 0 cards.
[    0.517882] cpuidle: using governor ladder
[    0.517884] cpuidle: using governor menu
[    0.518337] TCP cubic registered
[    0.518506] NET: Registered protocol family 10
[    0.518974] lo: Disabled Privacy Extensions
[    0.519300] NET: Registered protocol family 17
[    0.519341] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ processors (2 cpu cores) (version 2.20.00)
[    0.519388] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x8
[    0.519392] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0xa
[    0.519395] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12
[    0.519440] Using IPI No-Shortcut mode
[    0.519523] PM: Resume from disk failed.
[    0.519537] registered taskstats version 1
[    0.519883]   Magic number: 14:374:956
[    0.519933] pcieport 0000:00:04.0: hash matches
[    0.520028] rtc_cmos 00:04: setting system clock to 2010-06-30 21:56:25 UTC (1277934985)
[    0.520033] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.520035] EDD information not available.
[    0.788600] isapnp: No Plug & Play device found
[    0.788630] Freeing unused kernel memory: 656k freed
[    0.789199] Write protecting the kernel text: 4676k
[    0.789241] Write protecting the kernel read-only data: 1840k
[    0.809426] udev: starting version 151
[    0.911488] sata_nv 0000:00:0e.0: version 3.5
[    0.911511] sata_nv 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    0.911515] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    0.911587] sata_nv 0000:00:0e.0: setting latency timer to 64
[    0.921794] scsi0 : sata_nv
[    0.937642] scsi1 : sata_nv
[    0.937911] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xf800 irq 23
[    0.937915] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xf808 irq 23
[    0.937977] pata_amd 0000:00:0d.0: version 0.4.1
[    0.938030] pata_amd 0000:00:0d.0: setting latency timer to 64
[    0.956131] scsi2 : pata_amd
[    0.959371] scsi3 : pata_amd
[    0.960255] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfd00 irq 14
[    0.960259] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfd08 irq 15
[    0.960386] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    0.960760] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[    0.960766] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
[    0.960772] forcedeth 0000:00:14.0: setting latency timer to 64
[    0.960826] nv_probe: set workaround bit for reversed mac addr
[    0.969662] Linux Tulip driver version 1.1.15 (Feb 27, 2007)
[    0.970124] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[    0.970130]   alloc irq_desc for 18 on node -1
[    0.970133]   alloc kstat_irqs on node -1
[    0.970145] tulip 0000:03:0a.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[    0.970772] tulip0:  MII transceiver #1 config 1000 status 786d advertising 05e1.
[    0.977476] eth0: ADMtek Comet rev 17 at Port 0xde00, 00:18:f8:0b:a8:bd, IRQ 18.
[    1.184042] usb 2-3: new low speed USB device using ohci_hcd and address 2
[    1.404047] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.412196] ata1.00: ATA-7: ST3250823AS, 3.03, max UDMA/100
[    1.412201] ata1.00: 488397168 sectors, multi 1: LBA48 
[    1.420144] usb 2-3: configuration #1 chosen from 1 choice
[    1.420217] ata1.00: configured for UDMA/100
[    1.420347] scsi 0:0:0:0: Direct-Access     ATA      ST3250823AS      3.03 PQ: 0 ANSI: 5
[    1.420565] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.420600] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.420687] sd 0:0:0:0: [sda] Write Protect is off
[    1.420690] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.420712] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.420857]  sda:
[    1.435270] usbcore: registered new interface driver hiddev
[    1.442020]  sda1 sda2 <
[    1.449363] input: Chicony Saitek Eclipse Keyboard as /devices/pci0000:00/0000:00:0b.0/usb2/2-3/2-3:1.0/input/input3
[    1.449465] generic-usb 0003:06A3:8020.0001: input,hidraw0: USB HID v1.11 Keyboard [Chicony Saitek Eclipse Keyboard] on usb-0000:00:0b.0-3/input0
[    1.463915]  sda5 >
[    1.464257] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.480105] input: Chicony Saitek Eclipse Keyboard as /devices/pci0000:00/0000:00:0b.0/usb2/2-3/2-3:1.1/input/input4
[    1.480226] generic-usb 0003:06A3:8020.0002: input,hiddev96,hidraw1: USB HID v1.11 Device [Chicony Saitek Eclipse Keyboard] on usb-0000:00:0b.0-3/input1
[    1.480259] usbcore: registered new interface driver usbhid
[    1.480262] usbhid: v2.6:USB HID core driver
[    1.485147] forcedeth 0000:00:14.0: ifname eth1, PHY OUI 0x732 @ 13, addr 00:17:31:05:da:99
[    1.485152] forcedeth 0000:00:14.0: highdma pwrctl lnktim desc-v3
[    1.485202] sata_nv 0000:00:0f.0: PCI INT A -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
[    1.485210] sata_nv 0000:00:0f.0: Using SWNCQ mode
[    1.485285] sata_nv 0000:00:0f.0: setting latency timer to 64
[    1.485481] scsi4 : sata_nv
[    1.485595] scsi5 : sata_nv
[    1.485822] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xf300 irq 22
[    1.485826] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xf308 irq 22
[    1.724023] usb 2-5: new low speed USB device using ohci_hcd and address 3
[    1.742495] ata2: SATA link down (SStatus 0 SControl 300)
[    1.810497] ata5: SATA link down (SStatus 0 SControl 300)
[    1.920330] ata4.00: ATAPI: TSSTcorpCD/DVDW TS-H552L, 0614, max UDMA/33
[    1.920359] ata4: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc000) ACPI=0x701f (60:600:0x13)
[    1.942148] usb 2-5: configuration #1 chosen from 1 choice
[    1.952303] ata4.00: configured for UDMA/33
[    1.953149] scsi 3:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-H552L 0614 PQ: 0 ANSI: 5
[    1.956119] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    1.956123] Uniform CD-ROM driver Revision: 3.20
[    1.956248] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.956316] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    1.957393] input: Logitech USB RECEIVER as /devices/pci0000:00/0000:00:0b.0/usb2/2-5/2-5:1.0/input/input5
[    1.957479] generic-usb 0003:046D:C50E.0003: input,hidraw2: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0000:00:0b.0-5/input0
[    2.260020] usb 2-8: new full speed USB device using ohci_hcd and address 4
[    2.278496] ata6: SATA link down (SStatus 0 SControl 300)
[    2.285034] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[    2.285043]   alloc irq_desc for 19 on node -1
[    2.285045]   alloc kstat_irqs on node -1
[    2.285059] ohci1394 0000:03:05.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
[    2.342054] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[fdeff000-fdeff7ff]  Max Packet=[1024]  IR/IT contexts=[8/8]
[    2.476169] usb 2-8: configuration #1 chosen from 1 choice
[    2.486139] Initializing USB Mass Storage driver...
[    2.486317] scsi6 : SCSI emulation for USB Mass Storage devices
[    2.486424] usbcore: registered new interface driver usb-storage
[    2.486428] USB Mass Storage support registered.
[    2.486545] usb-storage: device found at 4
[    2.486548] usb-storage: waiting for device to settle before scanning
[    2.527754] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    3.620152] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d800009d6d24]
[    7.486176] usb-storage: device scan complete
[    7.493074] scsi 6:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    7.500063] scsi 6:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    7.507062] scsi 6:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[    7.514062] scsi 6:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[    7.514531] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    7.514667] sd 6:0:0:1: Attached scsi generic sg3 type 0
[    7.514821] sd 6:0:0:2: Attached scsi generic sg4 type 0
[    7.514976] sd 6:0:0:3: Attached scsi generic sg5 type 0
[    7.558058] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    7.569063] sd 6:0:0:1: [sdc] Attached SCSI removable disk
[    7.591061] sd 6:0:0:2: [sdd] Attached SCSI removable disk
[    7.602062] sd 6:0:0:3: [sde] Attached SCSI removable disk
[   17.449958] udev: starting version 151
[   17.467652] Adding 6032368k swap on /dev/sda5.  Priority:-1 extents:1 across:6032368k 
[   17.583593] ACPI: resource nForce2_smbus [0x4c00-0x4c3f] conflicts with ACPI region SM00 [0x4c00-0x4c05]
[   17.583599] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   17.583602] nForce2_smbus 0000:00:0a.1: Error probing SMB1.
[   17.583697] i2c i2c-0: nForce2 SMBus adapter at 0x4c40
[   17.665495] lp: driver loaded but no devices found
[   17.702621] Linux agpgart interface v0.103
[   17.864661] type=1505 audit(1277935002.844:2):  operation="profile_load" pid=726 name="/sbin/dhclient3"
[   17.865014] type=1505 audit(1277935002.844:3):  operation="profile_load" pid=726 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   17.865192] type=1505 audit(1277935002.844:4):  operation="profile_load" pid=726 name="/usr/lib/connman/scripts/dhclient-script"
[   17.923298] nvidia: module license 'NVIDIA' taints kernel.
[   17.923303] Disabling lock debugging due to kernel taint
[   18.325594] eth1: no link during initialization.
[   18.329540] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   19.133486] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
[   19.133494] HDA Intel 0000:00:10.1: PCI INT B -> Link[AAZA] -> GSI 22 (level, low) -> IRQ 22
[   19.133498] hda_intel: Disable MSI for Nvidia chipset
[   19.133528] HDA Intel 0000:00:10.1: setting latency timer to 64
[   19.286578] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
[   19.286587]   alloc irq_desc for 16 on node -1
[   19.286589]   alloc kstat_irqs on node -1
[   19.286602] nvidia 0000:02:00.0: PCI INT A -> Link[APC5] -> GSI 16 (level, low) -> IRQ 16
[   19.286611] nvidia 0000:02:00.0: setting latency timer to 64
[   19.286617] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   19.286969] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.24  Thu Apr 22 09:18:20 PDT 2010
[   19.685035] hda_codec: ALC883: BIOS auto-probing.
[   20.000110] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:10.1/input/input6
[   21.317803] 0000:03:0a.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
[   21.317814] eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
[   25.831351] UDF-fs: No VRS found
[   25.831357] UDF-fs: No partition found (1)
[   28.369018] eth0: no IPv6 routers present

```

and heres the Xorg log.

```
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux Stoke 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=d9d68dc8-1ea0-4e81-9774-e88a02108462 ro quiet splash
Build Date: 09 June 2010  10:55:28AM
xorg-server 2:1.7.6-2ubuntu7.1 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Jun 30 17:56:46 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:2:0:0) 10de:0391:1682:2220 nVidia Corporation G73 [GeForce 7600 GT] rev 161, Mem @ 0xfa000000/16777216, 0xe0000000/268435456, 0xfb000000/16777216, I/O @ 0x0000cf00/128, BIOS @ 0x????????/131072
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.24  Thu Apr 22 10:38:29 PDT 2010
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  195.36.24  Thu Apr 22 09:34:29 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "1920x1080 +0+0; 1024x768 +0+0; 800x600 +0+0; 1280x720_60 +0+0"
(**) Jun 30 17:56:46 NVIDIA(0): Enabling RENDER acceleration
(II) Jun 30 17:56:46 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Jun 30 17:56:46 NVIDIA(0):     enabled.
(II) Jun 30 17:56:47 NVIDIA(0): NVIDIA GPU GeForce 7600 GT (G73) at PCI:2:0:0 (GPU-0)
(--) Jun 30 17:56:47 NVIDIA(0): Memory: 262144 kBytes
(--) Jun 30 17:56:47 NVIDIA(0): VideoBIOS: 05.73.22.15.05
(II) Jun 30 17:56:47 NVIDIA(0): Detected PCI Express Link width: 16X
(--) Jun 30 17:56:47 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Jun 30 17:56:47 NVIDIA(0): Connected display device(s) on GeForce 7600 GT at PCI:2:0:0:
(--) Jun 30 17:56:47 NVIDIA(0):     ACI VW246 (DFP-0)
(--) Jun 30 17:56:47 NVIDIA(0): ACI VW246 (DFP-0): 330.0 MHz maximum pixel clock
(--) Jun 30 17:56:47 NVIDIA(0): ACI VW246 (DFP-0): Internal Dual Link TMDS
(II) Jun 30 17:56:47 NVIDIA(0): Assigned Display Device: DFP-0
(WW) Jun 30 17:56:47 NVIDIA(0): No valid modes for "1280x720_60+0+0"; removing.
(II) Jun 30 17:56:47 NVIDIA(0): Validated modes:
(II) Jun 30 17:56:47 NVIDIA(0):     "1920x1080+0+0"
(II) Jun 30 17:56:47 NVIDIA(0):     "1024x768+0+0"
(II) Jun 30 17:56:47 NVIDIA(0):     "800x600+0+0"
(II) Jun 30 17:56:47 NVIDIA(0): Virtual screen size determined to be 1920 x 1080
(--) Jun 30 17:56:47 NVIDIA(0): DPI set to (92, 91); computed from "UseEdidDpi" X config
(--) Jun 30 17:56:47 NVIDIA(0):     option
(==) Jun 30 17:56:47 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) Jun 30 17:56:47 NVIDIA(0): Initialized GPU GART.
(II) Jun 30 17:56:47 NVIDIA(0): ACPI: failed to connect to the ACPI event daemon; the daemon
(II) Jun 30 17:56:47 NVIDIA(0):     may not be running or the "AcpidSocketPath" X
(II) Jun 30 17:56:47 NVIDIA(0):     configuration option may not be set correctly.  When the
(II) Jun 30 17:56:47 NVIDIA(0):     ACPI event daemon is available, the NVIDIA X driver will
(II) Jun 30 17:56:47 NVIDIA(0):     try to use it to receive ACPI event notifications.  For
(II) Jun 30 17:56:47 NVIDIA(0):     details, please see the "ConnectToAcpid" and
(II) Jun 30 17:56:47 NVIDIA(0):     "AcpidSocketPath" X configuration options in Appendix B: X
(II) Jun 30 17:56:47 NVIDIA(0):     Config Options in the README.
(II) Jun 30 17:56:47 NVIDIA(0): Setting mode "1920x1080+0+0"
(II) Loading extension NV-GLX
(II) Jun 30 17:56:48 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Jun 30 17:56:48 NVIDIA(0): Initialized X Rendering Acceleration
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Chicony Saitek Eclipse Keyboard (/dev/input/event3)
(**) Chicony Saitek Eclipse Keyboard: Applying InputClass "evdev keyboard catchall"
(**) Chicony Saitek Eclipse Keyboard: always reports core events
(**) Chicony Saitek Eclipse Keyboard: Device: "/dev/input/event3"
(II) Chicony Saitek Eclipse Keyboard: Found keys
(II) Chicony Saitek Eclipse Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Chicony Saitek Eclipse Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Chicony Saitek Eclipse Keyboard (/dev/input/event4)
(**) Chicony Saitek Eclipse Keyboard: Applying InputClass "evdev keyboard catchall"
(**) Chicony Saitek Eclipse Keyboard: always reports core events
(**) Chicony Saitek Eclipse Keyboard: Device: "/dev/input/event4"
(II) Chicony Saitek Eclipse Keyboard: Found keys
(II) Chicony Saitek Eclipse Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Chicony Saitek Eclipse Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Logitech USB RECEIVER (/dev/input/event5)
(**) Logitech USB RECEIVER: Applying InputClass "evdev pointer catchall"
(**) Logitech USB RECEIVER: always reports core events
(**) Logitech USB RECEIVER: Device: "/dev/input/event5"
(II) Logitech USB RECEIVER: Found 20 mouse buttons
(II) Logitech USB RECEIVER: Found scroll wheel(s)
(II) Logitech USB RECEIVER: Found relative axes
(II) Logitech USB RECEIVER: Found x and y relative axes
(II) Logitech USB RECEIVER: Configuring as mouse
(**) Logitech USB RECEIVER: YAxisMapping: buttons 4 and 5
(**) Logitech USB RECEIVER: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB RECEIVER" (type: MOUSE)
(II) Logitech USB RECEIVER: initialized for relative axes.
(II) config/udev: Adding input device Logitech USB RECEIVER (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event6)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)

```

---

### Post by spydeyrch on 2010-06-30
> **ibuclaw said:**
> Actually, it's adding ... but same thing. ;)

Tell that to my 1.6GHz atom processor.
```

processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 28
model name    : Intel(R) Atom(TM) CPU N270   @ 1.60GHz
stepping    : 2
cpu MHz        : 800.000
cache size    : 512 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 1
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 xtpr pdcm movbe lahf_lm
bogomips    : 3192.07
clflush size    : 64
cache_alignment    : 64
address sizes    : 32 bits physical, 32 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 28
model name    : Intel(R) Atom(TM) CPU N270   @ 1.60GHz
stepping    : 2
cpu MHz        : 800.000
cache size    : 512 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 1
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 xtpr pdcm movbe lahf_lm
bogomips    : 3191.92
clflush size    : 64
cache_alignment    : 64
address sizes    : 32 bits physical, 32 bits virtual
power management:

```Maybe that's the hyper-threading talking though...


Actually, what I think is happening, is that your CPU is down clocking itself based upon cpu usage, to save energy. My AMD cpu does it all the time. I have a quad-core Phenom 9950 oc'd to 3.2GHz, and when I am not using it's full potential, it will down clock itself to 800Mhz. An if I run cpu-z in win7, it will show that the capability of the CPU is 3.2Ghz, but that currently it is clocked to 800Mhz, on each core.

So I think that is what is happening with your Atom CPU. They are a somewhat newer architecture and if I remember correctly, Intel started to really implement down clocking to save energy around the time period that Atom started to come out. Especially being as it was originally intended for netbooks, mobile devices, laptops, etc. They wanted to save on the battery life.

I could be wrong, wouldn't be the first nor the last time, but I think that is what is happening with your atom cpu.

):P

-Spydey

---

### Post by ibuclaw on 2010-06-30
> **Xinu38 said:**
> 
for some reason it doesnt look like its giving me the full dmesg....

No worries - I only need to see the bits I need to see. ;)

Next question, is ACPID installed? The NViDIA driver seems to be disabling shared memory pixmaps - possibly because it can't connect to the ACPI of your system.
```
sudo apt-get install acpid
```
Reboot your computer after installing, and run:
```
status acpid
```
and
```
ls /var/run/acpid.socket
```

Regards

---

### Post by ibuclaw on 2010-06-30
> **spydeyrch said:**
> Actually, what I think is happening, is that your CPU is down clocking itself based upon cpu usage, to save energy. My AMD cpu does it all the time. I have a quad-core Phenom 9950 oc'd to 3.2GHz, and when I am not using it's full potential, it will down clock itself to 800Mhz. An if I run cpu-z in win7, it will show that the capability of the CPU is 3.2Ghz, but that currently it is clocked to 800Mhz, on each core.

I am pretty certain that /proc/cpuinfo is read-only, and remains static throughout the system's live state. But, am learning here as much as I am teaching; so I'd love to be proved wrong. ;)

---

### Post by mikewhatever on 2010-06-30
The following value does change in /proc/cpuinfo when going from idle to under load:
```
cpu MHz		: 800.000

```
```
cpu MHz		: 1600.000

```
the CPU info
```
cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU Z530   @ 1.60GHz
stepping	: 2
cpu MHz		: 1600.000
cache size	: 512 KB

```

---

### Post by Xinu38 on 2010-06-30
> **ibuclaw said:**
> No worries - I only need to see the bits I need to see. ;)

Next question, is ACPID installed? The NViDIA driver seems to be disabling shared memory pixmaps - possibly because it can't connect to the ACPI of your system.
```
sudo apt-get install acpid
```
Reboot your computer after installing, and run:
```
status acpid
```
and
```
ls /var/run/acpid.socket
```

Regards

will try and post results my good man, thank you.

---

### Post by Xinu38 on 2010-06-30
> **ibuclaw said:**
> No worries - I only need to see the bits I need to see. ;)

Next question, is ACPID installed? The NViDIA driver seems to be disabling shared memory pixmaps - possibly because it can't connect to the ACPI of your system.
```
sudo apt-get install acpid
```
Reboot your computer after installing, and run:
```
status acpid
```
and
```
ls /var/run/acpid.socket
```

Regards

info seems scarce....

```
brad@Stoke:~$ sudo apt-get install acpid
Reading package lists... Done
Building dependency tree       
Reading state information... Done
acpid is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
brad@Stoke:~$ status acpid
acpid stop/waiting
brad@Stoke:~$ ls /var/run/acpid.socket
ls: cannot access /var/run/acpid.socket: No such file or directory

```

---

### Post by anewguy on 2010-06-30
> **ibuclaw said:**
> No worries - I only need to see the bits I need to see. ;)

Next question, is ACPID installed? The NViDIA driver seems to be disabling shared memory pixmaps - possibly because it can't connect to the ACPI of your system.
```
sudo apt-get install acpid
```
Reboot your computer after installing, and run:
```
status acpid
```
and
```
ls /var/run/acpid.socket
```

Regards

Looka like that is failing:

> 
(II) Jun 30 17:56:47 NVIDIA(0): Initialized GPU GART.
(II) Jun 30 17:56:47 NVIDIA(0): ACPI: failed to connect to the ACPI event daemon; the daemon
(II) Jun 30 17:56:47 NVIDIA(0):     may not be running or the "AcpidSocketPath" X
(II) Jun 30 17:56:47 NVIDIA(0):     configuration option may not be set correctly.  When the
(II) Jun 30 17:56:47 NVIDIA(0):     ACPI event daemon is available, the NVIDIA X driver will
(II) Jun 30 17:56:47 NVIDIA(0):     try to use it to receive ACPI event notifications.  For
(II) Jun 30 17:56:47 NVIDIA(0):     details, please see the "ConnectToAcpid" and
(II) Jun 30 17:56:47 NVIDIA(0):     "AcpidSocketPath" X configuration options in Appendix B: X
(II) Jun 30 17:56:47 NVIDIA(0):     Config Options in the README

dave

---

### Post by ibuclaw on 2010-07-01
You could edit grub config:
```
gksu gedit /etc/default/grub
```
And on the **GRUB_CMDLINE_LINUX_DEFAULT** line, add:
```
acpi=force
```
inside the "quotation marks".

Save, quit, and update grub
```
sudo update-grub
```
and reboot.

That may invoke behaviours, or do absolutely nothing - (or make things worse in the unfortunate case). Your mileage may vary. :)

Regards

---

### Post by nishant.singh28 on 2010-07-01
> **ibuclaw said:**
> You could edit grub config:
```
gksu gedit /etc/default/grub
```
And on the **GRUB_CMDLINE_LINUX_DEFAULT** line, add:
```
acpi=force
```
inside the "quotation marks".

Save, quit, and update grub
```
sudo update-grub
```
and reboot.

That may invoke behaviours, or do absolutely nothing - (or make things worse in the unfortunate case). Your mileage may vary. :)

Regards
Or you could try a temporary boot with that option by pressing e at the grub screen and adding the option so it stays for one boot.

And if it's flash that's causing the blowout....rest assured. You don't have a problem. It's flash that doesn't like Linux machines. You can't do much about that except wait for the next flash plugin version.

---

### Post by cascade9 on 2010-07-01
> **ibuclaw said:**
> I am pretty certain that /proc/cpuinfo is read-only, and remains static throughout the system's live state. But, am learning here as much as I am teaching; so I'd love to be proved wrong. ;)

This doesnt really 'prove' you wrong, but AFAIK, cat /proc/cpuinfo will report the current state of the CPU, and isnt static. Here is the output from that command on 1 system, with cpufreq working- 

```
cat /proc/cpuinfo
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 4
model name    : AMD Phenom(tm) II X2 550 Processor
stepping    : 3
cpu MHz        : 800.000
cache size    : 512 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt npt lbrv svm_lock nrip_save
bogomips    : 6228.23
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

```And the output from a fairly similar setup, with no cpufreq working- 


```
cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 107
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4800+
stepping        : 2
cpu MHz         : 2499.901
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
apicid          : 0
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch lbrv
bogomips        : 4999.80
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

```If you really want I can poke at the 2nd machine and get cpufreq working, which is a bit closer to 'proof' ;)

@ Xinu38- you can always check in your BIOS to see if your CPU is being detected right.

---

### Post by Xinu38 on 2010-07-01
> **ibuclaw said:**
> You could edit grub config:
```
gksu gedit /etc/default/grub
```
And on the **GRUB_CMDLINE_LINUX_DEFAULT** line, add:
```
acpi=force
```
inside the "quotation marks".

Save, quit, and update grub
```
sudo update-grub
```
and reboot.

That may invoke behaviours, or do absolutely nothing - (or make things worse in the unfortunate case). Your mileage may vary. :)

Regards

lol alright, thank you for continuing to help me out on this, as what youre seeing so far, this is a configuration issue, not a hardware issue right? and ill try these steps when i get home from work and post results.

---

### Post by Xinu38 on 2010-07-01
ok it said "quiet splash" on that line, input acpi=force in place, restarting now, see what happens :crossfingers:

---

### Post by Xinu38 on 2010-07-01
doesnt seem to have done anything.......im beginning to think this may just be a computer issue if everything seems to be working fine. i just dont understand why the ubuntu os cant handle starcraft when my computer is set up to run counterstrike and other high distributing games smoothly before ubuntu. 

gotta be something thats missing here...](*,)

---

### Post by ibuclaw on 2010-07-01
> **Xinu38 said:**
> doesnt seem to have done anything.......im beginning to think this may just be a computer issue if everything seems to be working fine. i just dont understand why the ubuntu os cant handle starcraft when my computer is set up to run counterstrike and other high distributing games smoothly before ubuntu. 

gotta be something thats missing here...](*,)

And
```
ls /var/run/acpid.socket
```
still returns that the file doesn't exist?

If you haven't done already, you can remove that option you added from /etc/default grub.

It probably boils down to a badly manufactured system board. Sadly is not uncommon in the PC world.


edit:
An old NViDIA performance boost used to be putting:
```

Option "PixmapCacheSize" "1000000"
Option "AllowSHMPixmaps" "0"

```
In the "Device" section of xorg.conf. Though is largely deprecated on cards newer than GeForce 8.

---

### Post by Xinu38 on 2010-07-01
i havnt been to xorg.config since i got the os. i know its gksu gedit etc/X11/xorg.conf

but.............i dont remember it being blank.

---

### Post by 98cwitr on 2010-07-07
crsx bump

---

### Post by anewguy on 2010-07-13
> **Xinu38 said:**
> i havnt been to xorg.config since i got the os. i know its gksu gedit etc/X11/xorg.conf

but.............i dont remember it being blank.

I believe it started with 9.10, but at any rate there is no xorg.conf file by default anymore.  The system now tries to configure everything automatically, which doesn't always work.  I don't remember the command off hand, but there is supposedly a way to create this file (something like sudo dpkg-reconfigure xorg-'something').  You may want to do a search using no xorg-config as the search string.

Dave ;)

EDIT:  I think it may be sudo dpkg-reconfigure xserver-xorg

---

