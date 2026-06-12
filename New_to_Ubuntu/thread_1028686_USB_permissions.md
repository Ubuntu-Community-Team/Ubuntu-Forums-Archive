---
title: "USB permissions"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by jcats on 2009-01-02
I recently got an external HD, to use as a backup. It came formatted in NTFS. So first, I plugged it into XP and used the safely remove, and then it worked in both XP and Ubuntu. While I could not mount it, I could read and write to it. It worked fine for about 3 times, then I got the small screen that says I am not privileged to mount the drive. And I couldn't access it at all. After running around Google and the forums here, I can now mount, read and write and unmount it from the terminal.
Now my USB mp3 player is giving me the same "not privileged" screen. And this has never given me trouble, through plenty of mountings and unmountings.
:confused:
Ultimately, I'd like to get any USB device to auto mount. But I have no idea why the sudden problems.
I have done the Administration-Authorization, and given me permission to mount and unmount.
What ever I plug in always shows in "Places"
I'm running 8.04
I'd appreciate any ideas as to why, and maybe a fix?
Thanks;
jcats

---

### Post by ubrox on 2009-01-03
First off check "dmesg" output to see if there is any relevant information there. Run the command after plugging in your USB disk/player & then last few lines will be relevant. 

If there is a problem with disk, you maybe able to see it there.

Next, open a console and try mounting the disk manually using sudo. If it works, mounting and USB disk are fine. 

You have to check your privileges. System->Administration->Authorizations

Check the following tree:
org->freedesktop->hal->storage->mount file systems from removable drives.

Try granting this provilege to your account.

---

### Post by roscal on 2009-01-03
Not expert advice here, but I have had problems mounting usb devices lately too. Now, I have to plug the device in and run the command:

lsusb

Usually the device will then pop up on the desktop.

---

### Post by Michael.Godawski on 2009-01-03
hi,

let's see what we can do concerning your usb devices.

Please post the output of this terminal command:
```

sudo fdisk -l
```

Then check also this:

> **User Privileges**

 If your usb device doesn't appear on your desktop, you should check that your user has the correct privileges.  Go to **System->Administration->User and Groups**, choose the user, click on "Properties", then go to the "User Privileges" tab. You should have the "Access external storage devices automatically" option checked. 


---

### Post by jcats on 2009-01-03
Thank you ,everyone
I have gone through the authorizations, and I have privileges. And have been to users and groups, every box is checked in permissions. Still no change.

I tried the lsusb, the HD isn't listed

fdisk -l
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd51bd51b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10352    83152408+   7  HPFS/NTFS
/dev/sda2           10353       19080    70107660   83  Linux
/dev/sda3           19081       19457     3028252+   5  Extended
/dev/sda5           19081       19457     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa331b283

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS
```

I don't know how to read the dmesg, but here are the last lines

```
[  871.010925] usb-storage: device scan complete
[  871.011542] scsi 2:0:0:0: Direct-Access     Generic  External         2.10 PQ: 0 ANSI: 4
[  871.020388] sd 2:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[  871.021763] sd 2:0:0:0: [sdb] Write Protect is off
[  871.021771] sd 2:0:0:0: [sdb] Mode Sense: 21 00 00 00
[  871.021774] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  871.023253] sd 2:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[  871.024386] sd 2:0:0:0: [sdb] Write Protect is off
[  871.024392] sd 2:0:0:0: [sdb] Mode Sense: 21 00 00 00
[  871.024395] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  871.024400]  sdb: sdb1
[  871.046339] sd 2:0:0:0: [sdb] Attached SCSI disk
[  871.046387] sd 2:0:0:0: Attached scsi generic sg3 type 0
[ 1149.477217] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0d:56:64:04:dd:08:00 SRC=192.168.1.104 DST=192.168.1.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=56310 PROTO=UDP SPT=138 DPT=138 LEN=209 
[ 1422.848044] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0d:56:64:04:dd:08:00 SRC=192.168.1.104 DST=192.168.1.255 LEN=237 TOS=0x00 PREC=0x00 TTL=128 ID=56312 PROTO=UDP SPT=138 DPT=138 LEN=217 
[ 1870.253174] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0d:56:64:04:dd:08:00 SRC=192.168.1.104 DST=192.168.1.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=56314 PROTO=UDP SPT=138 DPT=138 LEN=209
```

Thank you for your efforts
jcats

---

### Post by mkvnmtr on 2009-01-03
I have started having the same problems with external hard drives and usb sticks. It began when I started reformating everything to work on both my Ubuntu and my Mac. I am sure it is something I have done but I have just got used to typing in the command. The good part is I can now read and write in both.

---

### Post by albinootje on 2009-01-03
> **jcats said:**
> 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS[/code]


```

sudo mkdir /media/sdb1
sudo ntfs-3g /dev/sdb1 /media/sdb1 -o force,umask=000,uid=1000,gid=1000

```
This assumes that you're logged in with the username you've chosen during the Ubuntu installatie.

After that check out the content of /media/sdb1/
Please post any errors.

---

### Post by jcats on 2009-01-03
Thanks albinootje;
I used the code you sent, and the USB HD showed up. But I cannot unmount it, as it says it is not mounted.
I only have 1 log in, so yes, I am logged in as the name I created on install.
I don't know how to check out the content of /media/sdb1/ :???:

I just plugged in my MP3 player, and it now mounts and unmounts, so I'm part way home ;)
Thanks again for your help.
jcats

---

### Post by albinootje on 2009-01-03
> **jcats said:**
> Thanks albinootje;
I used the code you sent, and the USB HD showed up. But I cannot unmount it, as it says it is not mounted.
I only have 1 log in, so yes, I am logged in as the name I created on install.
I don't know how to check out the content of /media/sdb1/ :???:

I just plugged in my MP3 player, and it now mounts and unmounts, so I'm part way home ;)


Can you do the following :
Go to "Places" -> Home Folder -> File System (at the left panel) -> Media -> sdb1
Is there something in there or not at all ?
Can you please post the output of :
```

mount
dmesg

```
Thanks.

---

### Post by jcats on 2009-01-03
There is nothing in sdb1. 
(Maybe this will help?)-while in media, I also saw "Backup" which is the name I gave the external HD (also empty), and " NewVolume" which is the original name of the HD. And in that folder is all the contents of the HD.

mount:
```
/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
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
nfsd on /proc/fs/nfsd type nfsd (rw)
gvfs-fuse-daemon on /home/jcats/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jcats)
```

dmesg:
```
[    0.404025] ACPI: EC: Look up EC in DSDT
[    0.412556] ACPI: Interpreter enabled
[    0.412561] ACPI: (supports S0 S1 S4 S5)
[    0.412578] ACPI: Using IOAPIC for interrupt routing
[    0.426145] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.426234] PCI: 0000:00:00.0 reg 10 32bit mmio: [e0000000, e3ffffff]
[    0.426255] pci 0000:00:00.0: nForce2 C1 Halt Disconnect fixup
[    0.426433] PCI: 0000:00:01.1 reg 10 io port: [e000, e01f]
[    0.426466] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.426471] pci 0000:00:01.1: PME# disabled
[    0.426499] PCI: 0000:00:02.0 reg 10 32bit mmio: [e8080000, e8080fff]
[    0.426532] pci 0000:00:02.0: supports D1
[    0.426534] pci 0000:00:02.0: supports D2
[    0.426536] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.426541] pci 0000:00:02.0: PME# disabled
[    0.426562] PCI: 0000:00:02.1 reg 10 32bit mmio: [e8083000, e8083fff]
[    0.426595] pci 0000:00:02.1: supports D1
[    0.426597] pci 0000:00:02.1: supports D2
[    0.426599] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.426604] pci 0000:00:02.1: PME# disabled
[    0.426632] PCI: 0000:00:02.2 reg 10 32bit mmio: [e8086000, e80860ff]
[    0.426669] pci 0000:00:02.2: supports D1
[    0.426671] pci 0000:00:02.2: supports D2
[    0.426673] pci 0000:00:02.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.426678] pci 0000:00:02.2: PME# disabled
[    0.426705] PCI: 0000:00:04.0 reg 10 32bit mmio: [e8087000, e8087fff]
[    0.426712] PCI: 0000:00:04.0 reg 14 io port: [e400, e407]
[    0.426741] pci 0000:00:04.0: supports D1
[    0.426743] pci 0000:00:04.0: supports D2
[    0.426745] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.426749] pci 0000:00:04.0: PME# disabled
[    0.426771] PCI: 0000:00:05.0 reg 10 32bit mmio: [e8000000, e807ffff]
[    0.426804] pci 0000:00:05.0: supports D1
[    0.426806] pci 0000:00:05.0: supports D2
[    0.426827] PCI: 0000:00:06.0 reg 10 io port: [d000, d0ff]
[    0.426834] PCI: 0000:00:06.0 reg 14 io port: [d400, d47f]
[    0.426840] PCI: 0000:00:06.0 reg 18 32bit mmio: [e8081000, e8081fff]
[    0.426866] pci 0000:00:06.0: supports D1
[    0.426868] pci 0000:00:06.0: supports D2
[    0.426925] PCI: 0000:00:09.0 reg 20 io port: [f000, f00f]
[    0.426967] PCI: 0000:00:0d.0 reg 10 32bit mmio: [e8084000, e80847ff]
[    0.426974] PCI: 0000:00:0d.0 reg 14 32bit mmio: [e8085000, e808503f]
[    0.427003] pci 0000:00:0d.0: supports D1
[    0.427005] pci 0000:00:0d.0: supports D2
[    0.427008] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.427012] pci 0000:00:0d.0: PME# disabled
[    0.427096] PCI: bridge 0000:00:08.0 io port: [a000, bfff]
[    0.427101] PCI: bridge 0000:00:08.0 32bit mmio: [e6000000, e7ffffff]
[    0.427136] PCI: 0000:02:00.0 reg 10 32bit mmio: [d0000000, d7ffffff]
[    0.427142] PCI: 0000:02:00.0 reg 14 io port: [c000, c0ff]
[    0.427149] PCI: 0000:02:00.0 reg 18 32bit mmio: [e5000000, e500ffff]
[    0.427166] PCI: 0000:02:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.427181] pci 0000:02:00.0: supports D1
[    0.427183] pci 0000:02:00.0: supports D2
[    0.427205] PCI: 0000:02:00.1 reg 10 32bit mmio: [d8000000, dfffffff]
[    0.427211] PCI: 0000:02:00.1 reg 14 32bit mmio: [e5010000, e501ffff]
[    0.427241] pci 0000:02:00.1: supports D1
[    0.427243] pci 0000:02:00.1: supports D2
[    0.427280] PCI: bridge 0000:00:1e.0 io port: [c000, cfff]
[    0.427284] PCI: bridge 0000:00:1e.0 32bit mmio: [e4000000, e5ffffff]
[    0.427289] PCI: bridge 0000:00:1e.0 32bit mmio pref: [d0000000, dfffffff]
[    0.427299] bus 00 -> node 0
[    0.427308] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.427578] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.427964] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[    0.500994] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.501244] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.501492] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.501742] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.501989] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.502238] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.502486] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.502733] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.502981] ACPI: PCI Interrupt Link [LAPU] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.503232] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.503478] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.503727] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.503975] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.504244] ACPI: PCI Interrupt Link [LFIR] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.504495] ACPI: PCI Interrupt Link [L3CM] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.504743] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.504955] ACPI: PCI Interrupt Link [APC1] (IRQs *16), disabled.
[    0.505156] ACPI: PCI Interrupt Link [APC2] (IRQs *17), disabled.
[    0.505348] ACPI: PCI Interrupt Link [APC3] (IRQs *18), disabled.
[    0.505540] ACPI: PCI Interrupt Link [APC4] (IRQs *19)
[    0.505731] ACPI: PCI Interrupt Link [APCE] (IRQs *16), disabled.
[    0.506008] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0
[    0.506284] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0
[    0.506558] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0
[    0.506833] ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22) *0
[    0.507106] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0
[    0.507380] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled.
[    0.507574] ACPI: PCI Interrupt Link [APCS] (IRQs *23)
[    0.507846] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0
[    0.508133] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0
[    0.508411] ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0, disabled.
[    0.508688] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
[    0.508911] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.508960] pnp: PnP ACPI init
[    0.508970] ACPI: bus type pnp registered
[    0.515847] pnp: PnP ACPI: found 14 devices
[    0.515850] ACPI: ACPI bus type pnp unregistered
[    0.515854] PnPBIOS: Disabled by ACPI PNP
[    0.516354] PCI: Using ACPI for IRQ routing
[    0.516491] NET: Registered protocol family 8
[    0.516491] NET: Registered protocol family 20
[    0.516491] NetLabel: Initializing
[    0.516491] NetLabel:  domain hash size = 128
[    0.516491] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.516491] NetLabel:  unlabeled traffic allowed by default
[    0.516491] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.516491]    actual entries 65620
[    0.516640] AppArmor: AppArmor Filesystem Enabled
[    0.516665] ACPI: RTC can wake from S4
[    0.516674] system 00:00: ioport range 0x4000-0x407f has been reserved
[    0.516674] system 00:00: ioport range 0x4080-0x40ff has been reserved
[    0.516674] system 00:00: ioport range 0x4400-0x447f has been reserved
[    0.516674] system 00:00: ioport range 0x4480-0x44ff has been reserved
[    0.516674] system 00:00: ioport range 0x4200-0x427f has been reserved
[    0.516674] system 00:00: ioport range 0x4280-0x42ff has been reserved
[    0.516674] system 00:01: ioport range 0x5000-0x503f has been reserved
[    0.516674] system 00:01: ioport range 0x5100-0x513f has been reserved
[    0.516674] system 00:02: iomem range 0xf0000-0xf3fff could not be reserved
[    0.516674] system 00:02: iomem range 0xf4000-0xf7fff could not be reserved
[    0.516674] system 00:02: iomem range 0xf8000-0xfbfff could not be reserved
[    0.516674] system 00:02: iomem range 0xfc000-0xfffff could not be reserved
[    0.516674] system 00:02: iomem range 0x5fff0000-0x5fffffff could not be reserved
[    0.516674] system 00:02: iomem range 0xffff0000-0xffffffff could not be reserved
[    0.516674] system 00:02: iomem range 0x0-0x9ffff could not be reserved
[    0.516674] system 00:02: iomem range 0x100000-0x5ffeffff could not be reserved
[    0.516674] system 00:02: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.516674] system 00:02: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.516674] system 00:04: ioport range 0xb78-0xb7b has been reserved
[    0.516674] system 00:04: ioport range 0xf78-0xf7b has been reserved
[    0.516674] system 00:04: ioport range 0xa78-0xa7b has been reserved
[    0.516674] system 00:04: ioport range 0xe78-0xe7b has been reserved
[    0.516674] system 00:04: ioport range 0xbbc-0xbbf has been reserved
[    0.516674] system 00:04: ioport range 0xfbc-0xfbf has been reserved
[    0.516674] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.516674] system 00:04: ioport range 0x294-0x297 has been reserved
[    0.552504] pci 0000:00:08.0: PCI bridge, secondary bus 0000:01
[    0.552508] pci 0000:00:08.0:   IO window: 0xa000-0xbfff
[    0.552515] pci 0000:00:08.0:   MEM window: 0xe6000000-0xe7ffffff
[    0.552519] pci 0000:00:08.0:   PREFETCH window: disabled
[    0.552529] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.552532] pci 0000:00:1e.0:   IO window: 0xc000-0xcfff
[    0.552537] pci 0000:00:1e.0:   MEM window: 0xe4000000-0xe5ffffff
[    0.552542] pci 0000:00:1e.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.552557] pci 0000:00:08.0: setting latency timer to 64
[    0.552564] bus: 00 index 0 io port: [0, ffff]
[    0.552567] bus: 00 index 1 mmio: [0, ffffffff]
[    0.552569] bus: 01 index 0 io port: [a000, bfff]
[    0.552572] bus: 01 index 1 mmio: [e6000000, e7ffffff]
[    0.552574] bus: 01 index 2 mmio: [0, 0]
[    0.552576] bus: 01 index 3 mmio: [0, 0]
[    0.552578] bus: 02 index 0 io port: [c000, cfff]
[    0.552581] bus: 02 index 1 mmio: [e4000000, e5ffffff]
[    0.552583] bus: 02 index 2 mmio: [d0000000, dfffffff]
[    0.552585] bus: 02 index 3 mmio: [0, 0]
[    0.552597] NET: Registered protocol family 2
[    0.552740] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.553106] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.554542] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.555247] TCP: Hash tables configured (established 131072 bind 65536)
[    0.555251] TCP reno registered
[    0.555385] NET: Registered protocol family 1
[    0.555540] checking if image is initramfs... it is
[    1.056095] Switched to high resolution mode on CPU 0
[    1.268070] Freeing initrd memory: 7931k freed
[    1.269085] audit: initializing netlink socket (disabled)
[    1.269106] type=2000 audit(1230986473.268:1): initialized
[    1.274954] highmem bounce pool size: 64 pages
[    1.274962] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.277913] VFS: Disk quotas dquot_6.5.1
[    1.278018] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.278143] msgmni has been set to 1752
[    1.278296] io scheduler noop registered
[    1.278299] io scheduler anticipatory registered
[    1.278302] io scheduler deadline registered
[    1.278315] io scheduler cfq registered (default)
[    1.336092] pci 0000:02:00.0: Boot video device
[    1.336533] isapnp: Scanning for PnP cards...
[    1.690764] isapnp: No Plug & Play device found
[    1.741516] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.741677] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.741867] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.742659] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.743037] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.745353] brd: module loaded
[    1.745450] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.745602] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.745605] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.746224] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.746861] mice: PS/2 mouse device common for all mice
[    1.747052] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.747076] rtc0: alarms up to one year, y3k
[    1.747239] EISA: Probing bus 0 at eisa.0
[    1.747262] Cannot allocate resource for EISA slot 4
[    1.747265] Cannot allocate resource for EISA slot 5
[    1.747281] EISA: Detected 0 cards.
[    1.747285] cpuidle: using governor ladder
[    1.747288] cpuidle: using governor menu
[    1.747870] TCP cubic registered
[    1.747903] Using IPI No-Shortcut mode
[    1.748179] registered taskstats version 1
[    1.748303]   Magic number: 9:596:682
[    1.748512] rtc_cmos 00:06: setting system clock to 2009-01-03 12:41:14 UTC (1230986474)
[    1.748517] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.748519] EDD information not available.
[    1.748992] Freeing unused kernel memory: 424k freed
[    1.749053] Write protecting the kernel text: 2576k
[    1.749089] Write protecting the kernel read-only data: 936k
[    1.777010] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.004921] fuse init (API version 7.9)
[    2.238625] fan PNP0C0B:00: registered as cooling_device0
[    2.238634] ACPI: Fan [FAN] (on)
[    2.292959] processor ACPI0007:00: registered as cooling_device1
[    2.332274] thermal LNXTHERM:01: registered as thermal_zone0
[    2.337093] ACPI: Thermal Zone [THRM] (33 C)
[    3.848461] usbcore: registered new interface driver usbfs
[    3.848494] usbcore: registered new interface driver hub
[    3.864785] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    3.865257] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
[    3.865267] forcedeth 0000:00:04.0: PCI INT A -> Link[APCH] -> GSI 22 (level, high) -> IRQ 22
[    3.865274] forcedeth 0000:00:04.0: setting latency timer to 64
[    3.865310] nv_probe: set workaround bit for reversed mac addr
[    3.884082] usbcore: registered new device driver usb
[    3.891123] No dock devices found.
[    3.903818] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.968213] SCSI subsystem initialized
[    4.073168] libata version 3.00 loaded.
[    4.384696] forcedeth 0000:00:04.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:50:8d:f9:fe:c3
[    4.384702] forcedeth 0000:00:04.0: timirq lnktim desc-v1
[    4.385680] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
[    4.385690] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 21 (level, high) -> IRQ 21
[    4.385705] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    4.385709] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    4.385762] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[    4.385791] ohci_hcd 0000:00:02.0: irq 21, io mem 0xe8080000
[    4.442256] usb usb1: configuration #1 chosen from 1 choice
[    4.442292] hub 1-0:1.0: USB hub found
[    4.442307] hub 1-0:1.0: 3 ports detected
[    4.648824] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 20
[    4.648837] ohci_hcd 0000:00:02.1: PCI INT B -> Link[APCG] -> GSI 20 (level, high) -> IRQ 20
[    4.648855] ohci_hcd 0000:00:02.1: setting latency timer to 64
[    4.648860] ohci_hcd 0000:00:02.1: OHCI Host Controller
[    4.648907] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[    4.648935] ohci_hcd 0000:00:02.1: irq 20, io mem 0xe8083000
[    4.706333] usb usb2: configuration #1 chosen from 1 choice
[    4.706368] hub 2-0:1.0: USB hub found
[    4.706382] hub 2-0:1.0: 3 ports detected
[    4.808797] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[    4.808805] ehci_hcd 0000:00:02.2: PCI INT C -> Link[APCL] -> GSI 22 (level, high) -> IRQ 22
[    4.808822] ehci_hcd 0000:00:02.2: setting latency timer to 64
[    4.808827] ehci_hcd 0000:00:02.2: EHCI Host Controller
[    4.808857] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
[    4.808894] ehci_hcd 0000:00:02.2: debug port 1
[    4.808900] ehci_hcd 0000:00:02.2: cache line size of 64 is not supported
[    4.808919] ehci_hcd 0000:00:02.2: irq 22, io mem 0xe8086000
[    4.824069] usb 1-1: new full speed USB device using ohci_hcd and address 2
[    4.836035] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.836278] usb usb3: configuration #1 chosen from 1 choice
[    4.836317] hub 3-0:1.0: USB hub found
[    4.836330] hub 3-0:1.0: 6 ports detected
[    4.892146] hub 1-0:1.0: unable to enumerate USB device on port 1
[    5.044365] pata_amd 0000:00:09.0: version 0.3.10
[    5.044437] pata_amd 0000:00:09.0: setting latency timer to 64
[    5.044918] scsi0 : pata_amd
[    5.045754] scsi1 : pata_amd
[    5.046873] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    5.046878] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    5.242126] ata1.00: ATA-7: ST3160812A, 3.AAJ, max UDMA/100
[    5.242132] ata1.00: 312581808 sectors, multi 16: LBA48 
[    5.242147] ata1: nv_mode_filter: 0x3f39f&0x3f01f->0x3f01f, BIOS=0x3f000 (0xc600c5c0) ACPI=0x3f01f (20:600:0x13)
[    5.308678] ata1.00: configured for UDMA/100
[    5.620015] usb 1-1: new full speed USB device using ohci_hcd and address 3
[    5.688340] ata2.00: ATAPI: ATAPI   DVD A  DH20A4P, 9P57, max UDMA/66
[    5.688359] ata2.01: ATAPI: ATAPI   DVD D  DH16D2P, HP57, max UDMA/33
[    5.688373] ata2: nv_mode_filter: 0x1f39f&0x1f01f->0x1f01f, BIOS=0x1f000 (0xc600c5c0) ACPI=0x1f01f (30:60:0x1f)
[    5.688379] ata2: nv_mode_filter: 0x739f&0x701f->0x701f, BIOS=0x7000 (0xc600c5c0) ACPI=0x701f (30:60:0x1f)
[    5.720265] ata2.00: configured for UDMA/66
[    5.760270] ata2.01: configured for UDMA/33
[    5.760397] scsi 0:0:0:0: Direct-Access     ATA      ST3160812A       3.AA PQ: 0 ANSI: 5
[    5.761684] scsi 1:0:0:0: CD-ROM            ATAPI    DVD A  DH20A4P   9P57 PQ: 0 ANSI: 5
[    5.763008] scsi 1:0:1:0: CD-ROM            ATAPI    DVD D  DH16D2P   HP57 PQ: 0 ANSI: 5
[    5.763566] ACPI: PCI Interrupt Link [APCM] enabled at IRQ 21
[    5.763572] ohci1394 0000:00:0d.0: PCI INT A -> Link[APCM] -> GSI 21 (level, high) -> IRQ 21
[    5.763579] ohci1394 0000:00:0d.0: setting latency timer to 64
[    5.815326] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[e8084000-e80847ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    5.872421] usb 1-1: configuration #1 chosen from 1 choice
[    5.895386] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    5.895446] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    5.895495] scsi 1:0:1:0: Attached scsi generic sg2 type 5
[    5.935562] Driver 'sd' needs updating - please use bus_type methods
[    5.935702] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    5.935727] sd 0:0:0:0: [sda] Write Protect is off
[    5.935731] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.935766] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.935851] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    5.935871] sd 0:0:0:0: [sda] Write Protect is off
[    5.935874] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.935909] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.935915]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    5.955598]  sda1 sda2 sda3 < sda5 >
[    5.981880] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.990611] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.990618] Uniform CD-ROM driver Revision: 3.20
[    5.990735] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.996624] sr1: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[    5.996751] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    6.188023] usb 1-2: new low speed USB device using ohci_hcd and address 4
[    6.406395] usb 1-2: configuration #1 chosen from 1 choice
[    6.408585] usbcore: registered new interface driver hiddev
[    6.418505] hiddev96hidraw0: USB HID v1.00 Device [Lexmark  2500 Series] on usb-0000:00:02.0-1
[    6.428758] input: Logitech USB RECEIVER as /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.0/input/input2
[    6.429137] input,hidraw1: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0000:00:02.0-2
[    6.429163] usbcore: registered new interface driver usbhid
[    6.429168] usbhid: v2.6:USB HID core driver
[    6.490750] PM: Starting manual resume from disk
[    6.490755] PM: Resume from partition 8:5
[    6.490757] PM: Checking hibernation image.
[    6.490935] PM: Resume from disk failed.
[    6.560718] kjournald starting.  Commit interval 5 seconds
[    6.560733] EXT3-fs: mounted filesystem with ordered data mode.
[    6.930439] ohci1394: fw-host0: SelfID received outside of bus reset sequence
[    7.200161] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000000508df8fec3]
[   13.403588] ip_tables: (C) 2000-2006 Netfilter Core Team
[   13.484664] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   13.484845] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Plase use
[   13.484848] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   13.484851] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   13.685193] udevd version 124 started
[   14.386606] Linux agpgart interface v0.103
[   14.436668] agpgart: Detected NVIDIA nForce2 chipset
[   14.440879] agpgart-nvidia 0000:00:00.0: AGP aperture is 64M @ 0xe0000000
[   14.678468] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x5000
[   14.678531] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x5100
[   14.730356] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   14.740035] ACPI: Power Button (FF) [PWRF]
[   14.740200] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   14.756040] ACPI: Power Button (CM) [PWRB]
[   15.422974] parport_pc 00:0c: reported by Plug and Play ACPI
[   15.423092] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   17.087925] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   17.131306] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.408919] usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x043D pid 0x010B
[   17.408950] usbcore: registered new interface driver usblp
[   17.539163] usbcore: registered new interface driver lmpcm_usb
[   17.543053] lmpcm_usb: v0.5.5:USB Logitech MediaPlay Cordless Mouse driver
[   17.924375] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 20
[   17.924383] Intel ICH 0000:00:06.0: PCI INT A -> Link[APCJ] -> GSI 20 (level, high) -> IRQ 20
[   17.924410] Intel ICH 0000:00:06.0: setting latency timer to 64
[   18.209606] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   18.248034] intel8x0_measure_ac97_clock: measured 52728 usecs
[   18.248039] intel8x0: clocking to 47455
[   21.226731] lp0: using parport0 (interrupt-driven).
[   21.283231] w83627hf: Found W83627HF chip at 0x290
[   21.469976] Adding 3028212k swap on /dev/sda5.  Priority:-1 extents:1 across:3028212k
[   22.031408] EXT3 FS on sda2, internal journal
[   23.239549] type=1505 audit(1231004496.141:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4124
[   23.478723] type=1505 audit(1231004496.381:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4129
[   23.479058] type=1505 audit(1231004496.381:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4129
[   24.812358] NET: Registered protocol family 17
[   30.530099] NET: Registered protocol family 10
[   30.530723] lo: Disabled Privacy Extensions
[   31.537387] warning: `ntpd' uses 32-bit capabilities (legacy support in use)
[   32.257856] ACPI: WMI: Mapper loaded
[   32.581940] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
[   32.585532] powernow: Trying ACPI perflib
[   32.586813] powernow: ACPI perflib can not be used in this platform
[   32.586820] powernow: ACPI and legacy methods failed
[   32.586823] powernow: See http://www.codemonkey.org.uk/projects/cpufreq/powernow-k7.html
[   33.535217] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   33.535226] apm: overridden by ACPI.
[   33.822823] ppdev: user-space parallel port driver
[   34.924842] RPC: Registered udp transport module.
[   34.924851] RPC: Registered tcp transport module.
[   34.986297] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   35.086380] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   35.095762] NFSD: starting 90-second grace period
[   38.006287] Bluetooth: Core ver 2.13
[   38.009750] NET: Registered protocol family 31
[   38.009760] Bluetooth: HCI device and connection manager initialized
[   38.009766] Bluetooth: HCI socket layer initialized
[   38.161163] Bluetooth: L2CAP ver 2.11
[   38.161170] Bluetooth: L2CAP socket layer initialized
[   38.190331] Bluetooth: RFCOMM socket layer initialized
[   38.191154] Bluetooth: RFCOMM TTY layer initialized
[   38.191161] Bluetooth: RFCOMM ver 1.10
[   38.244182] Bluetooth: SCO (Voice Link) ver 0.6
[   38.244192] Bluetooth: SCO socket layer initialized
[   38.284687] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   38.284695] Bluetooth: BNEP filters: protocol multicast
[   38.361125] Bridge firewalling registered
[   38.362799] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   40.728011] eth0: no IPv6 routers present
[  132.564311] ppdev0: registered pardevice
[  132.612240] ppdev0: unregistered pardevice
[  134.888095] ppdev0: registered pardevice
[  134.936021] ppdev0: unregistered pardevice
[  135.620310] ppdev0: registered pardevice
[  135.668153] ppdev0: unregistered pardevice
[  245.744020] usb 3-5: new high speed USB device using ehci_hcd and address 4
[  245.897970] usb 3-5: configuration #1 chosen from 1 choice
[  246.016234] usbcore: registered new interface driver libusual
[  246.041362] Initializing USB Mass Storage driver...
[  246.043640] scsi2 : SCSI emulation for USB Mass Storage devices
[  246.046064] usbcore: registered new interface driver usb-storage
[  246.046075] USB Mass Storage support registered.
[  246.047818] usb-storage: device found at 4
[  246.047824] usb-storage: waiting for device to settle before scanning
[  251.044167] usb-storage: device scan complete
[  251.045513] scsi 2:0:0:0: Direct-Access     Generic  External         2.10 PQ: 0 ANSI: 4
[  251.093850] sd 2:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[  251.099021] sd 2:0:0:0: [sdb] Write Protect is off
[  251.099031] sd 2:0:0:0: [sdb] Mode Sense: 21 00 00 00
[  251.099034] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  251.100872] sd 2:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[  251.102330] sd 2:0:0:0: [sdb] Write Protect is off
[  251.102340] sd 2:0:0:0: [sdb] Mode Sense: 21 00 00 00
[  251.102343] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  251.103016]  sdb: sdb1
[  251.123388] sd 2:0:0:0: [sdb] Attached SCSI disk
[  251.123735] sd 2:0:0:0: Attached scsi generic sg3 type 0
[  530.956015] usb 2-3: new full speed USB device using ohci_hcd and address 2
[  534.183235] usb 2-3: configuration #1 chosen from 1 choice
[  534.206493] scsi3 : SCSI emulation for USB Mass Storage devices
[  534.210169] usb-storage: device found at 2
[  534.210175] usb-storage: waiting for device to settle before scanning
[  539.209198] usb-storage: device scan complete
[  539.216173] scsi 3:0:0:0: Direct-Access     CREATIVE MuVo V100        1023 PQ: 0 ANSI: 4
[  539.230389] sd 3:0:0:0: [sdc] 1011584 2048-byte hardware sectors (2072 MB)
[  539.244365] sd 3:0:0:0: [sdc] Write Protect is off
[  539.244375] sd 3:0:0:0: [sdc] Mode Sense: 38 00 00 00
[  539.244379] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[  539.265184] sd 3:0:0:0: [sdc] 1011584 2048-byte hardware sectors (2072 MB)
[  539.272251] sd 3:0:0:0: [sdc] Write Protect is off
[  539.272261] sd 3:0:0:0: [sdc] Mode Sense: 38 00 00 00
[  539.272265] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[  539.272802]  sdc: sdc1
[  539.286371] sd 3:0:0:0: [sdc] Attached SCSI removable disk
[  539.286849] sd 3:0:0:0: Attached scsi generic sg4 type 0
[  550.337104] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0d:56:64:04:dd:08:00 SRC=192.168.1.104 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=128 ID=56650 PROTO=UDP SPT=68 DPT=67 LEN=308 
[  559.336359] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0d:56:64:04:dd:08:00 SRC=192.168.1.104 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=128 ID=56651 PROTO=UDP SPT=68 DPT=67 LEN=308 
[  567.736083] usb 2-3: USB disconnect, address 2
[  685.112346] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0d:56:64:04:dd:08:00 SRC=192.168.1.104 DST=192.168.1.255 LEN=237 TOS=0x00 PREC=0x00 TTL=128 ID=56652 PROTO=UDP SPT=138 DPT=138 LEN=217
```

Thank you,albinootje, for hanging in with me
jcats

---

### Post by albinootje on 2009-01-03
Thanks for posting this.
It's a little weird, because there are no errors, and your usb disk is not mounted :(

Did you get any errors when you typed in that mount command for /dev/sdb1 ?

---

### Post by jcats on 2009-01-03
No, I got no error, any time, except when trying to mount or unmount.
I did shut down (power) to the HD and unplugged it. When I plugged it back in again, I still coudln't see it. I ran your code again and it appeared on the desk top. I can read and write to the files.
If your confused, then I'm completely lost:-k

ok, maybe I spoke to soon-I tried this, in terminal:

jcats@PurpleUbuntu:~$ mount /dev/sdb1
mount: according to mtab, /dev/sdb1 is mounted on /media/sdb1
mount failed

so then I tried:

jcats@PurpleUbuntu:~$ sudo mount /dev/sdb1

 and it immediately returned to jcats@PurpleUbuntu:~$, so I tried to unmount it at the desktop and got the little screen that says I am not privileged to unmount "Backup"

---

### Post by albinootje on 2009-01-03
> **jcats said:**
> 
jcats@PurpleUbuntu:~$ mount /dev/sdb1
mount: according to mtab, /dev/sdb1 is mounted on /media/sdb1

OK, interesting, can you please do the following, and post the output :
```

sudo mount
sudo ls /media/sdb1/

```

---

### Post by jcats on 2009-01-03
Here you go:

```
jcats@PurpleUbuntu:~$ sudo mount
[sudo] password for jcats: 
/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
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
nfsd on /proc/fs/nfsd type nfsd (rw)
gvfs-fuse-daemon on /home/jcats/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jcats)
/dev/sdb1 on /media/sdb1 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb1 on /media/desktop type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
jcats@PurpleUbuntu:~$ sudo ls /media/sdb1/
2008-12-21_20.35.38.764649.PurpleUbuntu.ful  Ubuntu system backup
2008-12-30_16.42.44.934430.jcatslaptop.inc   XP Documents
RECYCLER				     XP Downloads
System Volume Information		     XP Games
Ubuntu Documents			     XP music
Ubuntu Music				     XP saved parts
Ubuntu Pictures
```

---

### Post by albinootje on 2009-01-03
> **jcats said:**
> 
/dev/sdb1 on /media/sdb1 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb1 on /media/desktop type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

jcats@PurpleUbuntu:~$ sudo ls /media/sdb1/
2008-12-21_20.35.38.764649.PurpleUbuntu.ful  Ubuntu system backup
2008-12-30_16.42.44.934430.jcatslaptop.inc   XP Documents
RECYCLER				     XP Downloads
System Volume Information		     XP Games
Ubuntu Documents			     XP music
Ubuntu Music				     XP saved parts
Ubuntu Pictures[/code]

Looks good, isn't it ?

---

### Post by jcats on 2009-01-03
> **albinootje said:**
> Looks good, isn't it ?

I have no idea :confused:
I assume your talking about the dmesg output, but I don't know how to read it(sorry NOOB alert)
yes, the ls/media/sdb1 is correct

Again, thank you for all your efforts, I am learning as we go

---

### Post by albinootje on 2009-01-03
> **jcats said:**
> I have no idea :confused:

I assume you can recognize some of the folder names, no ? :)

> 
I assume your talking about the dmesg output, but I don't know how to read it(sorry NOOB alert)
yes, the ls/media/sdb1 is correct

Again, thank you for all your efforts, I am learning as we go

You're welcome.

Can you go to -> Places ?
Is it there, or not ?
If not, go to -> Places -> Home Folder -> File System (at the left panel)
then to Media, then to sdb1

---

### Post by jcats on 2009-01-03
OK, now I'm really confused.
I shut down and unplugged the USB from my computer. It left an icon on the desktop, which will not go away. I replugged in and turned on the HD, and rebooted. Now "Places" sees 2 "Backup". Click on 1, and it says there is no device, click on the other and it shows the files. And I can unmount it.
And anything I plug in is now auto mounting, and unmounting.

While I'm happy it's seems to be working correctly, I wish I knew why.

1 last question-how do I get rid of the useless icon on my desktop?

albinootje-thank you very much for all your efforts =D>

---

### Post by albinootje on 2009-01-03
> **jcats said:**
> OK, now I'm really confused.
I shut down and unplugged the USB from my computer. It left an icon on the desktop, which will not go away. I replugged in and turned on the HD, and rebooted. Now "Places" sees 2 "Backup". Click on 1, and it says there is no device, click on the other and it shows the files. And I can unmount it.
And anything I plug in is now auto mounting, and unmounting.

While I'm happy it's seems to be working correctly, I wish I knew why.

Can you post the output of this (again ?) to see whether there's something in there which shouldn't be in there :
```

cat /etc/fstab

```

> 

1 last question-how do I get rid of the useless icon on my desktop?

Is it completely empty ?

You can do this :
```

gksu nautilus

```
Then browse to -> File System -> Home -> your_username -> Desktop
and carefully remove that folder.

(where "your_username" is your own username)

> 
albinootje-thank you very much for all your efforts =D>

My pleasure.

---

### Post by jcats on 2009-01-03
#  -- This file has been automaticly generated by ntfs-config --
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda2 :
UUID=13e67b20-b14a-49cb-ac6e-05dd47a1d7f7 / ext3 defaults,errors=remount-ro,relatime 0 1
# Entry for /dev/sda5 :
UUID=37aeb614-6f13-4604-b47a-3f32f4dea1b4 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/hdc /media/cdrom1 udf,iso9660 user,noauto,exec 0 0
#/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0
/dev/sdb1 /media/desktop ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdb1 /media/60gigdrive ntfs-3g defaults,locale=en_US.UTF-8 0 0

OK, here's another strange one. I followed your directions to delete the desktop icon. It showed in the left panel in Nautilus. Clicked on it, it said it couldn't show it, but the icon went away and the 60gig hd took it's place. Clicked on that, it said it couldn't show it and it disappeared.
(The 60gig hd was an internal HD that I was using for back up. I took it out when I got the external one). How they are getting confused is beyond me

---

### Post by albinootje on 2009-01-03
> **jcats said:**
> 
/dev/sdb1 /media/desktop ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdb1 /media/60gigdrive ntfs-3g defaults,locale=en_US.UTF-8 0 0

OK, you have duplicate entries in /etc/fstab, probably done by ntfs-config.
Do you want to remove them ?
> 
OK, here's another strange one. I followed your directions to delete the desktop icon. It showed in the left panel in Nautilus. Clicked on it, it said it couldn't show it, but the icon went away and the 60gig hd took it's place. Clicked on that, it said it couldn't show it and it disappeared.
(The 60gig hd was an internal HD that I was using for back up. I took it out when I got the external one). How they are getting confused is beyond me

Hmmm.. I'm getting confused too :| :(
Time for some food and fresh air :)

---

### Post by jcats on 2009-01-03
Hey, it all works, and that's what I was after. And I learned a few things.
I did go to fstab, and commented out the 60 gig HD.
Thanks again,
jcats

---

