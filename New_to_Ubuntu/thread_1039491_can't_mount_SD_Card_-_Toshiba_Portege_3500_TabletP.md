---
title: "can't mount SD Card - Toshiba Portege 3500 TabletPC"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by aBitLater on 2009-01-14
Hello, I can't get my SD Card to mount.  The card is an HP 1GB card, and the slot is an internal slot, built in to the Toshiba.  I'm not sure what to do, and if anyone can help, it is much appreciated.

Here is the output of some terminal commands, most of the output doesn't make sense to me, but I've seen reference to these commands in other posts.

I am also using a Toshiba external pcmcia DVD ROM drive and a USB Logitech mouse.

The SD Card was in the slot when these commands were run.

Thanks again!

sudo lspcmcia
```
Socket 0 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:00:10.0)
Socket 0 Device 0:	[orinoco_cs]		(bus ID: 0.0)
Socket 1 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:00:11.0)
  CardBus card -- see "lspci" for more information
Socket 2 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:00:11.1)
brian@machine3:~$ sudo lspcmcia
Socket 0 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:00:10.0)
Socket 0 Device 0:	[orinoco_cs]		(bus ID: 0.0)
Socket 1 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:00:11.0)
  CardBus card -- see "lspci" for more information
Socket 2 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:00:11.1)

```


After I take it out of the slot, and re-insert, /var/log/syslog shows nothing

```
Jan 14 07:04:01 machine3 syslogd 1.5.0#2ubuntu6: restart.
Jan 14 07:04:01 machine3 anacron[4920]: Job `cron.daily' terminated
Jan 14 07:04:01 machine3 anacron[4920]: Normal exit (1 job run)
Jan 14 07:16:02 machine3 -- MARK --
Jan 14 07:17:01 machine3 /USR/SBIN/CRON[8106]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

```

sudo lspci 
```
00:00.0 Host bridge: ALi Corporation M1644/M1644T Northbridge+Trident (rev 01)
00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller
00:04.0 IDE interface: ALi Corporation M5229 IDE (rev c3)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 01)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:0a.0 Ethernet controller: Intel Corporation 82551QM Ethernet Controller (rev 10)
00:0c.0 USB Controller: NEC Corporation USB (rev 41)
00:0c.1 USB Controller: NEC Corporation USB (rev 41)
00:0c.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
00:10.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
00:11.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
00:11.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
00:12.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade XPAi1 (rev 82)
06:00.0 Mass storage controller: Device 1691:0001 (rev 01)

```

sudo lsusb
```
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c03d Logitech, Inc. M-BT69a Pilot Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

sudo fdisk -l
```
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffefffef

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4682    37608133+  83  Linux
/dev/sda2            4683        4864     1461915    5  Extended
/dev/sda5            4683        4864     1461883+  82  Linux swap / Solaris
```

sudo pccardctl info
```
PRODID_1="TOSHIBA"
PRODID_2="Wireless LAN Card"
PRODID_3="Version 01.01"
PRODID_4=""
MANFID=0156,0002
FUNCID=6
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

```

sudo pccardctl status
```
Socket 0:
  3.3V 16-bit PC Card
  Subdevice 0 (function 0) bound to driver "orinoco_cs"
Socket 1:
  3.3V 32-bit PC Card
Socket 2:
  no card

```

---

### Post by newbee70 on 2009-01-14
with the card in the slot what are the outputs of

fisk -l 

and 

 mount

---

### Post by aBitLater on 2009-01-14
fdisk -l 

```
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffefffef

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4682    37608133+  83  Linux
/dev/sda2            4683        4864     1461915    5  Extended
/dev/sda5            4683        4864     1461883+  82  Linux swap / Solaris
```

sudo mount
```
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/me/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=me)
```

---

### Post by aBitLater on 2009-01-16
anyone?

---

### Post by aBitLater on 2009-01-31
bump

---

### Post by prplwiredwizard on 2010-05-28
Was any one able to come up with an answer to this? Ubuntu is not seeing my sd card reader at all? any  advice?

---

