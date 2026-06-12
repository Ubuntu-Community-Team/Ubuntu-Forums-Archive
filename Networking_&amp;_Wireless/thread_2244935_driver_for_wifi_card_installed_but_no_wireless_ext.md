---
title: "driver for wifi card installed but no wireless extension found"
date: 2014-09-19
forum: Networking &amp; Wireless
---

### Post by Ben1649 on 2014-09-19
Hello everybody!
I've just started using ubundu (14.04. lts) and have problems setting up a wifi connection.
I'll try to give the relevant informations:

Network controller: Broadcom corporation BCM43227 802.11b/g/n
Driver: (I used Software&Updates "center") Broadcom-802.11-Linux-STA-Wireless-Driver from bcmwl-kernel-source (proprietary)


The responce to "iwconfig":
eth0   no wireless extensions.
lo   no wireless extentions.

It appears to me that ubuntu does not find the wifi card (roughly speaking).

Can anybody help? I really would appreciate some comments as I do not get how to proceed.
Thank you very much in advance!

---

### Post by varunendra on 2014-09-20
Welcome to the forums Ben1649!

Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by Ben1649 on 2014-09-21
Hi,
I downloaded and run the script.

```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

PC-Benedikt 3.13.0-32-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Core(TM) i5-2450M CPU @ 2.50GHz
Memory : 7838 MB
Uptime : 12:02:06 up 12 min,  1 user,  load average: 0,00, 0,17, 0,22


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:0504]
    Kernel driver in use: tg3
--
03:00.0 Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [14e4:4358]
    Subsystem: Foxconn International, Inc. Device [105b:e040]
    Kernel driver in use: bcma-pci-bridge


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 009: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 1bcf:288a Sunplus Innovation Technology Inc. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                 Soft blocked  Hard blocked
0: acer-wireless: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

bcma                   52096  0 
acer_wmi               32522  0 
mxm_wmi                13021  1 nouveau
sparse_keymap          13948  1 acer_wmi
wmi                    19177  3 acer_wmi,mxm_wmi,nouveau
video                  19476  3 i915,acer_wmi,nouveau


module parameters ~~~~~~~~~~~~~~~~~~

acer_wmi      (5): brightness=-1 | ec_raw_mode=N | force_series=0 | mailled=-1 | threeg=-1
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
================o=======o========o===========o====  =====o===========o==============o===========
 Interface & ID | Type  | Driver | State     | Default | Speed     | Support      | HW Addr   
================o=======o========o===========o====  =====o===========o==============o===========
 eth0           | Wired | tg3    | unmanaged | no      |           |              | <MAC eth0>
----------------+-------+--------+-----------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~
 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

auto eth0
    iface eth0 inet static
    address 193.136.222.247
    netmask 255.255.255.0
    gateway 193.136.222.254
    network 193.136.222.0
    broadcast 193.136.222.255
    dns-nameservers 193.136.221.1
 

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 193.136.221.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         193.136.222.254 0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
193.136.222.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0

--- 193.136.222.254 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2016ms
pipe 3

--- 193.136.221.1 ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 1000ms



iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : de_DE.UTF-8)
country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN, NO-IBSS
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

           - 


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

No way to aquire root rights found.


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[bcma]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/bcma/bcma.ko
srcversion:     E41B811D88783DD5BC38565
depends:        

[acer_wmi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/acer-wmi.ko
srcversion:     15371DC0E403E93954B38E5
depends:        wmi,sparse-keymap,video
parm:           mailled:Set initial state of Mail LED (int)
parm:           brightness:Set initial LCD backlight brightness (int)
parm:           threeg:Set initial state of 3G hardware (int)
parm:           force_series:Force a different laptop series (int)
parm:           ec_raw_mode:Enable EC raw mode (bool)

[mxm_wmi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/mxm-wmi.ko
srcversion:     62CBD37DE87DF0C4CD7FBA3
depends:        wmi

[wmi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)

[video]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/acpi/video.ko
srcversion:     274A2250DEAB415D412A67C
depends:        
parm:           brightness_switch_enabled:bool
parm:           allow_duplicates:bool
parm:           use_native_backlight:int


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x14e4:0x16b5 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/vmlinuz-3.13.0-32-generic root=/dev/mapper/ubuntu--vg-root ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.828700] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.828987] audit: initializing netlink socket (disabled)
[    2.360350] tg3 0000:02:00.0 eth0: attached PHY is 57765 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[1])
[    3.888833] psmouse serio1: elantech: assuming hardware version 3 (with firmware version 0x450f01)
[   15.761359] wmi: Mapper loaded
[   15.767489] acer_wmi: Acer Laptop ACPI-WMI Extras
[   15.767502] acer_wmi: Function bitmap for Communication Button: 0x1
[   15.767506] acer_wmi: Brightness must be controlled by generic video driver
[   15.767657] acer_wmi: Disabling ACPI video driver
[   16.182526] bcma: bus0: Found chip with id 0xA8DB, rev 0x00 and package 0x08
[   16.182563] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x25, class 0x0)
[   16.182591] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x1E, class 0x0)
[   16.182651] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x12, class 0x0)
[   16.182678] bcma: bus0: Core 3 found: SDIO Device (manuf 0x4BF, id 0x829, rev 0x07, class 0x0)
[   16.212315] bcma: bus0: Bus registered
[   24.875845] Bluetooth: BNEP (Ethernet Emulation) ver 1.3

    ======== Done ========


```

I attached the output to this post.
Cheers

---

### Post by varunendra on 2014-09-23
You don't seem to have the proprietary driver installed as you mentioned in the first post. While being connected to internet via Ethernet cable, please try that again -
```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
```
Closely watch the outputs in the terminal, and report back if you see any errors. If everything completes without errors, your wifi should start working. Reboot if necessary.

The only other option seems to install kernel 3.17 or later, which is supposed to support this card natively (with firmware installed manually). But let's try what can be done with the default kernel first.

---

### Post by Ben1649 on 2014-09-23
That might be. I'm not sure. It was just the "software center" saying it. Sorry!

So when I enter the commands the following is shown:

```
benedikt@PC-Benedikt:~$ sudo apt-get update
[sudo] password for benedikt: 
sudo: unable to open /var/lib/sudo/benedikt/0: No such file or directory
Ign http://extras.ubuntu.com trusty InRelease
Ign http://de.archive.ubuntu.com trusty InRelease                              
Ign http://extras.ubuntu.com trusty Release.gpg                                
Ign http://de.archive.ubuntu.com trusty-updates InRelease            
Ign http://archive.ubuntu.com trusty InRelease                                 
Hit http://extras.ubuntu.com trusty Release                                    
W: Not using locking for read only lock file /var/lib/apt/lists/lock 
E: Couldn't create temporary file to work with /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_trusty_Release - mkstemp (30: Read-only file system)
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```

and


```

benedikt@PC-Benedikt:~$ sudo apt-get install bcmwl-kernel-source
[sudo] password for benedikt: 
sudo: unable to open /var/lib/sudo/benedikt/0: No such file or directory
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```


and when I try to do what is suggested:

```
benedikt@PC-Benedikt:~$ sudo dpkg --configure -a
[sudo] password for benedikt: 
sudo: unable to open /var/lib/sudo/benedikt/0: No such file or directory
dpkg: error: unable to access dpkg status area: Read-only file system
```

---

### Post by varunendra on 2014-09-23
You seem to have bigger problems than the wifi. Is the filesystem mounted as Read-Only? Check the output of -
```
mount
```

If you have a Live CD/USB handy, boot into a live session with it, then run 'fsck' on the root partition of your current installation. For example, if this partition appears as '/dev/sda1' in the Live session, then to run fsck on it -
```
sudo fsck /dev/sda1
```

Once the errors are fixed, you should be able to boot normally with read-write access, after which, try the previously suggested command(s) again and report back.

---

### Post by Ben1649 on 2014-09-23
So I run mount and got the following

```

benedikt@PC-Benedikt:~$ mount
/dev/mapper/ubuntu--vg-root on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
/dev/sda1 on /boot type ext2 (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=benedikt)

mount: warning: /etc/mtab is not writable (e.g. read-only filesystem).
       It's possible that information reported by mount(8) is not
       up to date. For actual information about system mount points
       check the /proc/mounts file.


```

I will try to organize a live CD/USB and try what you suggested.

edit: May it help to reinstall the system? Or will it just cause the same error?

---

### Post by varunendra on 2014-09-23
I hate to refer a "reinstall" as a solution to everything, makes me feel as if I am talking about Windows again.

But yeah, if it is a fresh install and you have nothing important to save (data, settings etc.), then a reinstall is probably the quickest and most promising approach.

Format the partition before installing again, if you go for it.

---

### Post by praseodym on 2014-09-23
Hi, the driver in 14.04 is not very good. Use the one from 14.10 instead. Please download these files and save them in "Downloads":

[http://de.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu1_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu1_amd64.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu1_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu1_amd64.deb)

De-/Re-Installation:
```

sudo apt-get remove --purge bcmwl-kernel-source #if installed
sudo dpkg -i ~/Downloads/*.deb
```

---

### Post by Ben1649 on 2014-09-24
So finally I reinstalled ubuntu and now it works without any problems.
Also the WIFI is working well (I did what was suggested).
Thank you very much for your help!

---

### Post by artem.morikh on 2014-12-22
thank you

---

