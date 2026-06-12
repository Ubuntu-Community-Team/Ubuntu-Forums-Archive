---
title: "Card Reader not working"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by adikobi on 2009-05-10
I cannot use the built in card reader on my laptop (Toshiba Protege). Please help noob.

---

### Post by benj1 on 2009-05-10
what kind is it ?

post the output of 'lspci' if you don't know

---

### Post by gandaran on 2009-05-10
try installing these packages;
libssl0.9.8, libpcsclite1, libjasper1, pcscd, libccid and libpcsclite-dev 
these packages are necessary for some cards reader, maybe one or two of them will make your card reader work.

---

### Post by adikobi on 2009-05-10
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 21)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 21)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200 32M/64M] (rev a1)
02:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
02:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 33)
02:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 05)

Thanks but still not working.

---

### Post by adikobi on 2009-05-14
Please help card reader is not working (Toshiba Protege) Ubuntu 9.4

---

### Post by coffeeaddict22 on 2009-05-14
Hi,
A bit more info would be good.
By "not working", what do you mean?  When you put a card in, does anything happen at all?
Are you the only user of the machine?
Did it work previously; if so, what did you install around the time it stopped?
In addition, if you put a card in, what is the output of ```
dmesg |tail
``` a few seconds later?
finally, what is the output of ```
mount -l
``` when the card is inserted?

---

### Post by adikobi on 2009-05-15
When I put the card in it is not mounting so I cannot read or write to the card

dmesg |tail
[   14.185564] type=1505 audit(1242345604.445:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1925
[   14.224612] type=1505 audit(1242345604.485:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1929
[   17.117414] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.117418] Bluetooth: BNEP filters: protocol multicast
[   17.151851] Bridge firewalling registered
[   18.509566] ppdev: user-space parallel port driver
[   21.758015] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   32.736035] eth1: no IPv6 routers present
[   74.820561] ieee80211_crypt: registered algorithm 'TKIP'
[   81.112049] Clocksource tsc unstable (delta = -299903508 ns)

mount -l
/dev/sda2 on / type ext4 (rw,relatime,errors=remount-ro) []
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/cecee/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=cexex)

---

### Post by coffeeaddict22 on 2009-05-15
If you go into System/Users and Groups/ and unlock it, then look at hte properties of your username.  Do you have permissions to access external devices automatically?

---

### Post by adikobi on 2009-05-15
yes

---

### Post by coffeeaddict22 on 2009-05-15
What sort of card are you putting in?  And I'm assuming it's built in?  
Open a terminal, and (after putting the card in) type in ```
lspci -v
```; if it's an external (USB) card reader, do "lsusb" instead.
post the results back; that should tell us something about your card reader.

---

### Post by adikobi on 2009-05-15
In internal...

00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 21)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, fast devsel, latency 0
    Memory at e0000000 (32-bit, prefetchable) [size=256M]
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 21)
    Flags: bus master, 66MHz, fast devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
    Memory behind bridge: fd000000-fdffffff
    Prefetchable memory behind bridge: d0000000-dfffffff
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, medium devsel, latency 0, IRQ 11
    I/O ports at efe0 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, medium devsel, latency 0, IRQ 11
    I/O ports at ef80 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, medium devsel, latency 0, IRQ 11
    I/O ports at 18c0 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) (prog-if 20)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, medium devsel, latency 0, IRQ 11
    Memory at 64000000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=04, sec-latency=64
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fce00000-fcefffff
    Prefetchable memory behind bridge: 60000000-63ffffff
    Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
    Flags: bus master, medium devsel, latency 0
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, medium devsel, latency 0, IRQ 11
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at bfa0 [size=16]
    Memory at 64000400 (32-bit, non-prefetchable) [size=1K]
    Kernel driver in use: ata_piix

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
    Subsystem: Toshiba America Info Systems Device 02c5
    Flags: bus master, medium devsel, latency 0, IRQ 11
    I/O ports at 1000 [size=256]
    I/O ports at 1880 [size=64]
    Memory at 64000800 (32-bit, non-prefetchable) [size=512]
    Memory at 64000a00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: medium devsel, IRQ 11
    I/O ports at 1400 [size=256]
    I/O ports at 1800 [size=128]
    Capabilities: <access denied>
    Kernel modules: snd-intel8x0m

01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200 32M/64M] (rev a1)
    Subsystem: Toshiba America Info Systems Device 0010
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 10
    Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidiafb

02:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
    Subsystem: Intel Corporation Device 2741
    Flags: bus master, medium devsel, latency 64, IRQ 11
    Memory at fceff000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ipw2200
    Kernel modules: ipw2200

02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, medium devsel, latency 64, IRQ 11
    Memory at fcefe000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at cf40 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: e100
    Kernel modules: e100, eepro100

02:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 33)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, slow devsel, latency 168, IRQ 11
    Memory at fce00000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=02, secondary=03, subordinate=03, sec-latency=0
    Memory window 0: 60000000-63fff000 (prefetchable)
    Memory window 1: 68000000-6bfff000
    I/O window 0: 0000c000-0000c0ff
    I/O window 1: 0000c400-0000c4ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

02:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 05)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: medium devsel, IRQ 255
    Memory at fce01000 (32-bit, non-prefetchable) [disabled] [size=512]
    Capabilities: <access denied>

---

### Post by anewguy on 2009-05-15
Does it show if you do:

sudo mount -l with the card in?

Does anything show in /dev when you insert the card?  How about if you look but using su priviledges?

Dave :)

---

### Post by adikobi on 2009-05-16
No it is still not showing.

---

### Post by coffeeaddict22 on 2009-05-16
Sorry if it seems like a whole lot of dumb questions.  What sort of card are you trying to read?  
The output of lspci -v shows the card reader is being seen- it's the last 5 or so lines.  The access denied simply means you'll get more info if you do ```
sudo lspci -v |grep SD -A10
``` and that'd be a good thing to try now... the |grep bit just selects only the stuff you're interested in, so the output should be a bit shorter :-)

---

### Post by ceecee10 on 2009-05-23
[FONT=monospace]02:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 05)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: medium devsel, IRQ 255
    Memory at fce01000 (32-bit, non-prefetchable) [disabled] [size=512]
    Capabilities: [80] Power Management version 2
[/FONT]

---

### Post by coffeeaddict22 on 2009-05-23
Sorry to be the bearer of bad news.  Have a look [here]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/88863") - basically, Toshiba haven't released a driver, and no-one's managed yet to reverse engineer it, although according to that thread there is a driver at testing stage, and they're looking for volunteers- have a read of it.

---

### Post by adikobi on 2009-05-24
Thanks

---

