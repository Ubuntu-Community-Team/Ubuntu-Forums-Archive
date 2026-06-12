---
title: "Xen DomU NFS boot for migration"
date: 2007-07-27
forum: Networking &amp; Wireless
---

### Post by m_atif on 2007-07-27
Hi 
I am trying to boot Xen 3.1.0 guests using NFS for migration purpose and have tried to follow [http://www.debian-administration.org/articles/505](http://www.debian-administration.org/articles/505). This includes compiling the guest domain (domU) kernel with CONFIG_ROOT_NFS support inside the kernel, as i have ubuntu distribution. I am not sure if that is compiled inside or not, but Config files suggests that CONFIG_ROOT_NFS=y and all other necessary things are build inside. Some of the information is as under:
=============================
CONFIG_NFS_FS=y
CONFIG_NFS_V3=y
CONFIG_NFS_V3_ACL=y
CONFIG_NFS_V4=y
CONFIG_NFS_DIRECTIO=y
CONFIG_NFSD=m
CONFIG_NFSD_V2_ACL=y
CONFIG_NFSD_V3=y
CONFIG_NFSD_V3_ACL=y
CONFIG_NFSD_V4=y
CONFIG_NFSD_TCP=y
CONFIG_ROOT_NFS=y
...
===============================
Similarly I have already compiled the drivers of my NIC, although i dont see any point as i am using xenBr0. Now once i try to boot the virtual machine (vm), it waits for root file system and then drops to the initramfs shell. 

Upon a closer look i saw that kernel boot data command line is not correct i.e.
Bootdata ok (command line is ip=x.x.x.x:y.y.y.y::255.255.255.0:mvp1:eth0: off nfsroot=y.y.y.y:nfs/xen-mig/vp101 ). I think it is missing root=/dev/nfs for whatever reason, although i have it in mvp1.cfg file. NFS server (y.y.y.y) is exporting the file /nfs/xen-mig/vp101 and is visible. Once in the init shell I am able to mount the nfs/xen-mig/vp to /root but not /. 

Upon forcing root=/dev/nfs with extra (in the mvp1.cfg), i get 'connect: No route to host', shown as last attachment (paste) i.e. I am not dropped to shell.

The config file of virtual machine mvp1.cfg is as follows.
====================================
#  Kernel + memory size
kernel = '/boot/domu/vmlinuz-2.6.18-xen'
ramdisk = '/boot/domu/initrd.img-2.6.18-xen'
memory  = '128'
#  Hostname
name    = 'mvp1'
hostname = 'mvp1'
#  Networking
#dhcp = 'dhcp'
vif  = [ 'bridge=xenbr0' ]
#vif = ['']
ip = '192.168.0.213'
netmask = '255.255.255.0'
broadcast = '192.168.0.255'
gateway = '192.168.0.2'
#NFS options
nfs_server='192.168.0.10'
nfs_root='/nfs/xen-mig/vp'
root='/dev/nfs'
#i had to do this because of the reason in 2-3 paras.
extra='root=/dev/nfs'  
#  Behaviour
on_poweroff = 'destroy'
on_reboot   = 'restart'
on_crash    = 'restart'
=======================================

upon creation of domain following messages come up

Started domain mvp1
                   Bootdata ok (command line is ip=192.168.0.213:192.168.0.10:192.168.0
.2:255.255.255.0:mvp1:eth0:off nfsroot=192.168.0.10:/nfs/xen-mig/vp101 root=/dev/nfs)
Linux version 2.6.18-xen (root@vorpalblade2) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
) #4 SMP Fri Jul 27 05:36:28 EST 2007
BIOS-provided physical RAM map:
 Xen: 0000000000000000 - 0000000008800000 (usable)
No mptable found.
Built 1 zonelists.  Total pages: 34816
Kernel command line: ip=192.168.0.213:192.168.0.10:192.168.0.2:255.255.255.0:mvp1:eth0:
off nfsroot=192.168.0.10:/nfs/xen-mig/vp101 root=/dev/nfs
Initializing CPU#0
PID hash table entries: 1024 (order: 10, 8192 bytes)
Xen reported: 2204.996 MHz processor.
Console: colour dummy device 80x25
Dentry cache hash table entries: 32768 (order: 6, 262144 bytes)
Inode-cache hash table entries: 16384 (order: 5, 131072 bytes)
Software IO TLB disabled
Memory: 106632k/139264k available (2371k kernel code, 24284k reserved, 1032k data, 180k
 init)
Calibrating delay using timer specific routine.. 4411.16 BogoMIPS (lpj=22055839)
Security Framework v1.0.0 initialized
Capability LSM initialized
Mount-cache hash table entries: 256
CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
CPU: L2 Cache: 1024K (64 bytes/line)
CPU: Physical Processor ID: 1
CPU: Processor Core ID: 1
SMP alternatives: switching to UP code
Freeing SMP alternatives: 28k freed
Brought up 1 CPUs
migration_cost=0
checking if image is initramfs... it is
Freeing initrd memory: 16952k freed
NET: Registered protocol family 16
Brought up 1 CPUs
PCI: setting up Xen PCI frontend stub
ACPI: Interpreter disabled.
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI: disabled
xen_mem: Initialising balloon driver.
PCI: System does not support PCI
PCI: System does not support PCI
NET: Registered protocol family 2
pcifront pci-0: Installing PCI frontend
pcifront pci-0: Creating PCI Frontend Bus 0000:03
IP route cache hash table entries: 2048 (order: 2, 16384 bytes)
TCP established hash table entries: 8192 (order: 5, 131072 bytes)
TCP bind hash table entries: 4096 (order: 4, 65536 bytes)
TCP: Hash tables configured (established 8192 bind 4096)
TCP reno registered
IA-32 Microcode Update Driver: v1.14a-xen <tigran@veritas.com>
audit: initializing netlink socket (disabled)
audit(1185485687.380:1): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Initializing Cryptographic API
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered (default)
rtc: IRQ 8 is not free.
Non-volatile memory driver v1.2
RAMDISK driver initialized: 16 RAM disks of 16384K size 1024 blocksize
loop: loaded (max 8 devices)
Intel(R) PRO/1000 Network Driver - version 7.1.9-k4-NAPI
Copyright (c) 1999-2006 Intel Corporation.
e100: Intel(R) PRO/100 Network Driver, 3.5.10-k2-NAPI
e100: Copyright(c) 1999-2005 Intel Corporation
Xen virtual console successfully installed as tty1
Event-channel device installed.
netfront: Initialising virtual ethernet driver.
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 50MHz system bus speed for PIO modes; override with idebus=xx
PNP: No PS/2 controller found. Probing ports directly.
i8042.c: No controller found.
mice: PS/2 mouse device common for all mice
md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
md: bitmap version 4.39
NET: Registered protocol family 1
NET: Registered protocol family 17
netfront: device eth0 has copying receive path.
XENBUS: Device with no driver: device/console/0
IP-Config: Complete:
      device=eth0, addr=192.168.0.213, mask=255.255.255.0, gw=192.168.0.2,
     host=mvp1, domain=, nis-domain=(none),
     bootserver=192.168.0.10, rootserver=192.168.0.10, rootpath=
Freeing unused kernel memory: 180k freed
Loading, please wait...
Couldnt get a file descriptor referring to the console
Couldnt get a file descriptor referring to the console
Couldnt get a file descriptor referring to the console
Couldnt get a file descriptor referring to the console
Couldnt get a file descriptor referring to the console
Couldnt get a file descriptor referring to the console
Begin: Loading essential drivers... ...
device-mapper: ioctl: 4.7.0-ioctl (2006-06-24) initialised: [email]dm-devel@redhat.com[/email]
Done.
Begin: Running /scripts/init-premount ...
Done.
Begin: Mounting root file system... ...
Begin: Running /scripts/nfs-top ...
Done.
IP-Config: eth0 hardware address 00:16:3e:37:7a:3e mtu 1500
IP-Config: eth0 guessed broadcast address 192.168.0.255
IP-Config: eth0 guessed nameserver address 192.168.0.10
IP-Config: eth0 complete (from 192.168.0.10):
 address: 192.168.0.213    broadcast: 192.168.0.255    netmask: 255.255.255.0
 gateway: 192.168.0.2      dns0     : 192.168.0.10     dns1   : 0.0.0.0
 host   : mvp1
 rootserver: 192.168.0.10 rootpath:
 filename  :
Begin: Running /scripts/nfs-premount ...
Done.
connect: No route to host

My kernel version is 2.6.18 (Xen) and NFS server is running on 2.6.16.13. Can anyone help me. I apologize if i have missed out on details and am reposting it (initially posted at beginner talk).

I think it must be due to some stupid configuration/networking error on my side. Just a side note, without NFS, the domUs are up and running.
My hardware is AMD x64 with no vmx option.

---

