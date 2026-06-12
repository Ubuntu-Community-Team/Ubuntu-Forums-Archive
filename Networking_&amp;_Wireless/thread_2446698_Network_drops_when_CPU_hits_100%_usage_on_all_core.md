---
title: "Network drops when CPU hits 100% usage on all cores"
date: 2020-07-04
forum: Networking &amp; Wireless
---

### Post by taubin on 2020-07-04
This has been plaguing me since Ubuntu 18.04. I have a desktop  machine running Ubuntu Server 20.04 that I use it jellyfin and a few other  items. I have a problem in that whenever the CPU hits 100% on all  threads, the network drops completely and does not come back until I perform a reboot. This is a wired only network, using the nic on the motherboard. 


 I've tried googling the issue a few times and haven't come up with  anything to try. I have no idea where to even start with trying to fix  this issue, but it's making me pull my hair out.
 The system is an ASUS Prime PRIME B350-PLUS with an AMD Ryzen 5 1500X and 16 gigs of G.Skill 2400 memory.


 The CPU and memory have both been changed since this issue started  (upgraded from an old computer) and the issue has persisted. Any  suggestions on where I could even start with troubleshooting this would  be greatly appreciated. It's affecting my ability to transcode among  other things.


 This is occurring whenever CPU usage hits 100% no matter what is using the cores.

```


sudo dmidecode -s bios-version
5407
```


```
              total        used        free      shared  buff/cache   available
Mem:           15Gi       4.7Gi       156Mi       6.0Mi        10Gi        10Gi
Swap:         4.0Gi        26Mi       4.0Gi
```

```

sudo lshw -C memory
  *-firmware
       description: BIOS
       vendor: American Megatrends Inc.
       physical id: 0
       version: 5407
       date: 12/31/2019
       size: 64KiB
       capacity: 16MiB
       capabilities: pci apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
  *-memory
       description: System Memory
       physical id: 26
       slot: System board or motherboard
       size: 16GiB
     *-bank:0
          description: [empty]
          product: Unknown
          vendor: Unknown
          physical id: 0
          serial: Unknown
          slot: DIMM_A1
     *-bank:1
          description: DIMM DDR4 Synchronous Unbuffered (Unregistered) 2400 MHz (0.4 ns)
          product: F4-2400C15-8GTZR
          vendor: G-Skill
          physical id: 1
          serial: 00000000
          slot: DIMM_A2
          size: 8GiB
          width: 64 bits
          clock: 2400MHz (0.4ns)
     *-bank:2
          description: [empty]
          product: Unknown
          vendor: Unknown
          physical id: 2
          serial: Unknown
          slot: DIMM_B1
     *-bank:3
          description: DIMM DDR4 Synchronous Unbuffered (Unregistered) 2400 MHz (0.4 ns)
          product: F4-2400C15-8GTZR
          vendor: G-Skill
          physical id: 3
          serial: 00000000
          slot: DIMM_B2
          size: 8GiB
          width: 64 bits
          clock: 2400MHz (0.4ns)
  *-cache:0
       description: L1 cache
       physical id: 28
       slot: L1 - Cache
       size: 384KiB
       capacity: 384KiB
       clock: 1GHz (1.0ns)
       capabilities: pipeline-burst internal write-back unified
       configuration: level=1
  *-cache:1
       description: L2 cache
       physical id: 29
       slot: L2 - Cache
       size: 2MiB
       capacity: 2MiB
       clock: 1GHz (1.0ns)
       capabilities: pipeline-burst internal write-back unified
       configuration: level=2
  *-cache:2
       description: L3 cache
       physical id: 2a
       slot: L3 - Cache
       size: 16MiB
       capacity: 16MiB
       clock: 1GHz (1.0ns)
       capabilities: pipeline-burst internal write-back unified
       configuration: level=3
```

Any help with this would be greatly appreciated.

---

### Post by TheFu on 2020-07-05
Check the system log files for warnings and errors.
```
egrep -i 'warn|erro' /var/log/*g
```
That will get you close - the files, line number and messages.  Check out the files with issues and look a little above where the error or warning is, see what is says leading up to the issue.  Use google to find the non-local parts of the line and solutions.

For example:
```
/var/log/kern.log:Jul  5 07:39:40 hadar kernel: [76227.846661] audit: type=1400 audit(1593949180.210:189): apparmor="DENIED" operation="mount" info="failed flags match" error=-13 profile="lxd-pihole_</var/lib/lxd>" name="/home/" pid=24108 comm="(ionclean)" flags="ro, nosuid, nodev, remount, bind"
```
is a complete line with an error= -13.  -13 is a permission denied error. I know this from decades of knowledge, but let's assume that I didn't.  The parts that aren't local would be 
```
audit: type=1400 audit apparmor="DENIED" operation="mount" info="failed flags match" error=-13 profile name="/home/"flags="ro, nosuid, nodev, remount, bind"
```
The other parts would only happen on my machine, so google with those terms won't help.  The top result from that is this page: [https://askubuntu.com/questions/1107169/lxd-apparmor-denied-operation-mount-info-failed-flags-match](https://askubuntu.com/questions/1107169/lxd-apparmor-denied-operation-mount-info-failed-flags-match) which seems to match.

So, if you do the same, bet lots of possible answers would be returned.

---

