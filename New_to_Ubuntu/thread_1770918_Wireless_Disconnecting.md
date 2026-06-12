---
title: "Wireless Disconnecting"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by MarkTrent on 2011-05-29
Hi,

I have a problem with my wireless disconnecting every so often, it can happen anywhere from 5 minutes to 5 hours. Network manager says the connection is still active, but disconnecting and reconnecting doesn't solve the problem. The only way to get wireless back is by unplugging the usb dongle and putting it back in.

I tried switching to wicd but I couldn't connect to the network using that.

I'm using Ubuntu 11.04, 2.6.35-28 Kernel, and the wireless driver is RTL8192SU.

Thanks for any help,

Mark

---

### Post by jtarin on 2011-05-29
Post your results from the command "lspci" (without quotes).
Where do you get your signal from when this is happening?

---

### Post by MarkTrent on 2011-05-29
Doesn't look like the wireless usb dongle is listed here?

```

mark@HTPC:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:01.0 PCI bridge: Hewlett-Packard Company Device 9602
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (rev 40)
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:16.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5723 Gigabit Ethernet PCIe (rev 10)

```

Signal is from a wireless router, other computers are still connected to the router fine. When I plug the dongle back into my Ubuntu box the wireless connection connects again automatically.

---

### Post by jtarin on 2011-05-29
My bad.....wrong command. "lsusb".

---

### Post by MarkTrent on 2011-05-29
```

mark@HTPC:~$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 06a3:8021 Saitek PLC Eclipse II Keyboard
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 1532:0016 Razer USA, Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 0781:540e SanDisk Corp. Cruzer Contour Flash Drive
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0bda:8171 Realtek Semiconductor Corp. RTL8188SU 802.11n WLAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by jtarin on 2011-05-29
Okay I see "Realtek Semiconductor Corp. RTL8188SU 802.11n WLAN Adapter".
Now the command "lsmod".....let's see if the correct module is loaded.

---

### Post by MarkTrent on 2011-05-29
```

mark@HTPC:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           4657  1 
nls_cp437               6375  1 
vfat                   10954  1 
fat                    56244  1 vfat
arc4                    1497  2 
binfmt_misc             7984  1 
nfsd                  306088  11 
lockd                  75956  1 nfsd
nfs_acl                 2701  1 nfsd
auth_rpcgss            44898  1 nfsd
sunrpc                229477  12 nfsd,lockd,nfs_acl,auth_rpcgss
exportfs                4226  1 nfsd
parport_pc             30086  0 
ppdev                   6804  0 
nls_utf8                1453  0 
ufsd                  474262  7 
fglrx                2731504  37 
r8192s_usb            317763  0 
eeprom_93cx6            1789  1 r8192s_usb
amd64_edac_mod         24459  0 
edac_core              46822  3 amd64_edac_mod
edac_mce_amd            9387  1 amd64_edac_mod
k10temp                 3535  0 
i2c_piix4              10047  0 
lp                     10201  0 
shpchp                 34910  0 
parport                37032  3 parport_pc,ppdev,lp
usb_storage            50436  2 
usbhid                 42030  0 
hid                    84710  1 usbhid
tg3                   135768  0 
ahci                   22210  5 
pata_atiixp             4405  3 
libahci                26148  1 ahci

```

---

### Post by jtarin on 2011-05-29
Common problem......the fix is [here]("http://ubuntuforums.org/showthread.php?t=1705004&highlight=RTL8188su").

---

### Post by MarkTrent on 2011-05-29
Hi, thanks for the help but that's not the fix to this problem. I had to do that fix months ago to actually get the wireless to work in the first place.

---

### Post by jtarin on 2011-05-29
Then it would be helpful to all, if you would post what you have tried or at least link to a thread that you have posted this problem previously.

---

### Post by MarkTrent on 2011-05-29
I haven't posted a thread about this problem before. The post you linked to is about a problem where you can't connect to wireless at all, the best explanation for that is [here]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html").

My problem is different, that the wireless connection will disconnect randomly and is only fixable by reinserting the usb dongle.

---

### Post by jtarin on 2011-05-29
Well that link you gave me states:"Anyway this discussion it is not relevant for 11.04 since the driver r8912s_usb 
(RTL8192SU) will be replaced by RTL8172U:" so from this I am assuming the module r8912 should probably be blacklisted and the module r8172 should be loaded????

---

### Post by MarkTrent on 2011-05-29
I tried loading that new driver included with 11.04 but then the wireless dongle wasn't detected anymore. I think it's because that driver is for a newer kernel that I'm not using.

---

### Post by jtarin on 2011-05-29
Well you didn't state your version. Why not upgrade your kernel then?

---

### Post by MarkTrent on 2011-05-29
I'm using a filesystem driver that's not compatible with the newest kernel yet :(

---

### Post by jtarin on 2011-05-29
There was a suggestion about disabling security on the router or at least the level.
I just recently updated the firmware on my router and am well pleased with my connectivity.

---

### Post by jtarin on 2011-05-29
> **MarkTrent said:**
> I'm using a filesystem driver that's not compatible with the newest kernel yet :(What filesystem?

---

### Post by MarkTrent on 2011-05-30
Damn, I switched to the latest kernel this morning to use the latest wireless driver included and it hasn't disconnected once…

But I'm stuck, I can't compile the filesystem driver I need (Paragon NTFS&HFS for Linux 8.1 Express) under *2.6.**38***:

```
Building driver to kernel 2.6.38-8-generic
make -C /lib/modules/2.6.38-8-generic/build SUBDIRS=/home/mark/Downloads/ntfs O=/lib/modules/2.6.38-8-generic/build V=1 modules 2>&1
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
make -C /usr/src/linux-headers-2.6.38-8-generic \
	KBUILD_SRC=/usr/src/linux-headers-2.6.38-8-generic \
	KBUILD_EXTMOD="/home/mark/Downloads/ntfs" -f /usr/src/linux-headers-2.6.38-8-generic/Makefile \
	modules
test -e include/generated/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /home/mark/Downloads/ntfs/.tmp_versions ; rm -f /home/mark/Downloads/ntfs/.tmp_versions/*
make -f /usr/src/linux-headers-2.6.38-8-generic/scripts/Makefile.build obj=/home/mark/Downloads/ntfs
  gcc -Wp,-MD,/home/mark/Downloads/ntfs/ifslinux/.ufsdvfs.o.d  -nostdinc -isystem /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/include -I/usr/src/linux-headers-lbm- -I/usr/src/linux-headers-2.6.38-8-generic/arch/x86/include -Iinclude  -I/usr/src/linux-headers-2.6.38-8-generic/include -include include/generated/autoconf.h -Iubuntu/include -I/usr/src/linux-headers-2.6.38-8-generic/ubuntu/include   -I/home/mark/Downloads/ntfs -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -include /home/mark/Downloads/ntfs/ifslinux/fs_conf.h -DUFSD_DEVICE=ufsd -DUFSD_USE_ASM_DIV64 -DNDEBUG -g0  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(ufsdvfs)"  -D"KBUILD_MODNAME=KBUILD_STR(ufsd)" -c -o /home/mark/Downloads/ntfs/ifslinux/.tmp_ufsdvfs.o /home/mark/Downloads/ntfs//ifslinux/ufsdvfs.c
/home/mark/Downloads/ntfs//ifslinux/ufsdvfs.c:2254:15: error: \u2018file_fsync\u2019 undeclared here (not in a function)
/home/mark/Downloads/ntfs//ifslinux/ufsdvfs.c:2258:3: error: unknown field \u2018ioctl\u2019 specified in initializer
/home/mark/Downloads/ntfs//ifslinux/ufsdvfs.c:2258:3: warning: initialization from incompatible pointer type
/home/mark/Downloads/ntfs//ifslinux/ufsdvfs.c:2309:3: warning: initialization from incompatible pointer type
/home/mark/Downloads/ntfs//ifslinux/ufsdvfs.c:2310:3: warning: initialization from incompatible pointer type
/home/mark/Downloads/ntfs//ifslinux/ufsdvfs.c: In function \u2018ufsd_setattr\u2019:
/home/mark/Downloads/ntfs//ifslinux/ufsdvfs.c:2734:5: error: implicit declaration of function \u2018inode_setattr\u2019
/home/mark/Downloads/ntfs//ifslinux/ufsdvfs.c: In function \u2018ufsd_permission\u2019:
/home/mark/Downloads/ntfs//ifslinux/ufsdvfs.c:3412:3: warning: passing argument 3 of \u2018generic_permission\u2019 makes integer from pointer without a cast
include/linux/fs.h:2184:12: note: expected \u2018unsigned int\u2019 but argument is of type \u2018int (*)(struct inode *, int)\u2019
/home/mark/Downloads/ntfs//ifslinux/ufsdvfs.c:3412:3: error: too few arguments to function \u2018generic_permission\u2019
include/linux/fs.h:2184:12: note: declared here
/home/mark/Downloads/ntfs//ifslinux/ufsdvfs.c: At top level:
/home/mark/Downloads/ntfs//ifslinux/ufsdvfs.c:4552:3: warning: initialization from incompatible pointer type
/home/mark/Downloads/ntfs//ifslinux/ufsdvfs.c:5050:3: error: unknown field \u2018ioctl\u2019 specified in initializer
/home/mark/Downloads/ntfs//ifslinux/ufsdvfs.c:5050:3: warning: initialization from incompatible pointer type
/home/mark/Downloads/ntfs//ifslinux/ufsdvfs.c:5066:3: warning: initialization from incompatible pointer type
/home/mark/Downloads/ntfs//ifslinux/ufsdvfs.c: In function \u2018ufsd_write_begin\u2019:
/home/mark/Downloads/ntfs//ifslinux/ufsdvfs.c:5899:28: warning: passing argument 1 of \u2018block_write_begin\u2019 from incompatible pointer type
include/linux/buffer_head.h:204:5: note: expected \u2018struct address_space *\u2019 but argument is of type \u2018struct file *\u2019
/home/mark/Downloads/ntfs//ifslinux/ufsdvfs.c:5899:28: warning: passing argument 2 of \u2018block_write_begin\u2019 makes integer from pointer without a cast
include/linux/buffer_head.h:204:5: note: expected \u2018loff_t\u2019 but argument is of type \u2018struct address_space *\u2019
/home/mark/Downloads/ntfs//ifslinux/ufsdvfs.c:5899:28: warning: passing argument 5 of \u2018block_write_begin\u2019 makes pointer from integer without a cast
include/linux/buffer_head.h:204:5: note: expected \u2018struct page **\u2019 but argument is of type \u2018unsigned int\u2019
/home/mark/Downloads/ntfs//ifslinux/ufsdvfs.c:5899:28: warning: passing argument 6 of \u2018block_write_begin\u2019 from incompatible pointer type
include/linux/buffer_head.h:204:5: note: expected \u2018int (*)(struct inode *, sector_t,  struct buffer_head *, int)\u2019 but argument is of type \u2018struct page **\u2019
/home/mark/Downloads/ntfs//ifslinux/ufsdvfs.c:5899:28: error: too many arguments to function \u2018block_write_begin\u2019
include/linux/buffer_head.h:204:5: note: declared here
/home/mark/Downloads/ntfs//ifslinux/ufsdvfs.c: At top level:
/home/mark/Downloads/ntfs//ifslinux/ufsdvfs.c:7435:3: warning: initialization from incompatible pointer type
/home/mark/Downloads/ntfs//ifslinux/ufsdvfs.c:7436:3: error: unknown field \u2018clear_inode\u2019 specified in initializer
/home/mark/Downloads/ntfs//ifslinux/ufsdvfs.c:7436:3: warning: initialization from incompatible pointer type
/home/mark/Downloads/ntfs//ifslinux/ufsdvfs.c: In function \u2018ufsd_read_super\u2019:
/home/mark/Downloads/ntfs//ifslinux/ufsdvfs.c:8299:21: warning: assignment from incompatible pointer type
make[3]: *** [/home/mark/Downloads/ntfs/ifslinux/ufsdvfs.o] Error 1
make[2]: *** [_module_/home/mark/Downloads/ntfs] Error 2
make[1]: *** [sub-make] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [ufsd.ko] Error 2
Can't build driver

```

but those two 'missing' files are in that location.

So instead I compiled the latest wireless driver I need (rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401) under *2.6.**35***, and loaded the module into the kernel. When I insert the usb dongle it does load the module, but the wireless doesn't work.

So I either need to get the filesystem driver to compile under *2.6.38*
or
Get the latest wireless driver to work under *2.6.35*

Any ideas?

---

### Post by jtarin on 2011-05-30
Why do you need this file system driver?

---

### Post by MarkTrent on 2011-05-30
It's the only ntfs driver I've found that gives good write speeds (80mb/s instead of 15mb/s from ntfs-3g) and handles full disk compression. The drives in my Ubuntu box are full of data so can't be reformatted in a unix filesystem, and it also allows me to switch easily if I go back to using Windows again in the future. It works flawlessly under 2.6.35 so looks like I'll just have to wait a while until it's updated or whatever.

---

### Post by jtarin on 2011-05-30
> **MarkTrent said:**
> It's the only ntfs driver I've found that gives good write speeds (80mb/s instead of 15mb/s from ntfs-3g) and handles full disk compression. The drives in my Ubuntu box are full of data so can't be reformatted in a unix filesystem, and it also allows me to switch easily if I go back to using Windows again in the future. It works flawlessly under 2.6.35 so looks like I'll just have to wait a while until it's updated or whatever.You can revert to a usable kernel or possibly examine the device path you are using to r/w to and from, for bottlenecks occurring with the native driver.

---

