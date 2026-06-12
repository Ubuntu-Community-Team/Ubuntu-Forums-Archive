---
title: "Intel Wireless-AC not working after kernel upgrade"
date: 2020-10-21
forum: Networking &amp; Wireless
---

### Post by daithi_dearg on 2020-10-21
Hello,

The wireless card is no longer working since I upgraded to kernel 5.4.0-51.

I am on Ubuntu version 20.04.01.

I have tried reinstalling the linux-firmware but it makes no difference.

If I run sudo lshw -C network it comes up as unclaimed.

Should this be using the iwlwifi driver?

I can try installing the drivers from the Intel site if required.

Also have gone into the grub menu to go into previous kernels but same issue there.

---

### Post by chili555 on 2020-10-21
```
I can try installing the drivers from the Intel site if required.
```Those are firmware files, not drivers.

Please run and post:

```
sudo modprobe iwlwifi
dmesg | grep iwl
```

Is this a dual-boot with Windows? Does it work in Windows?

---

### Post by daithi_dearg on 2020-10-21
sudo modprobe iwlwifi gives following:
modprobe: ERROR ../libkmod/libkmod-module.c:838 kmod_module_insert_module() could not find module by name='iwlwifi'
 modprobe: ERROR  could not insert 'iwlwifi': Unknown symbol in module, or unknown parameter (see dmesg)

dmesg returns nothing with the grep

---

### Post by chili555 on 2020-10-21
> could not find module by name='iwlwifi'Wow! Let's look for it.

```
sudo updatedb
locate iwlwifi.ko
ls /etc/modprobe.d

```
If you have a file iwlwifi.conf, then let's see what it says:

```
cat /etc/modprobe.d/iwlwifi.conf
```

Is there anything interesting here?

```
grep iwl /var/log/syslog
grep iwl /var/log/syslog.1

```

---

### Post by daithi_dearg on 2020-10-22
I had to go back to an old kernel 5.4.0-42 which had the iwlwifi drivers:

```
   
david@david-N7x0WU:~$ ls /lib/modules/5.4.0-42-generic/kernel/drivers/net/wireless/intel/i
ipw2x00/  iwlegacy/ iwlwifi/  

david@david-N7x0WU:~$ ls /lib/modules/5.4.0-51-generic/kernel/drivers/net/
bonding  dummy.ko  ethernet  geneve.ko  ifb.ko  macvlan.ko  mdio.ko  netconsole.ko    ppp   tap.ko   virtio_net.ko  vxlan.ko
caif     eql.ko    fddi      hyperv     ipvlan  macvtap.ko  mii.ko   net_failover.ko  slip  veth.ko  vmxnet3        xen-netback
```

Suspect there may have been an issue with that newer kernel. Is there a way to navigate down the tree in the kernel and see what is included?

Perhaps on ubuntu.pkgs.org or something similar.

Maybe I just have to copy across files.

If still required here are the outputs of the command:
```
david@david-N7x0WU:~$ cat /etc/modprobe.d/iwlwifi.conf
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

david@david-N7x0WU:~$ grep iwl /var/log/syslog
Oct 22 16:53:38 david-N7x0WU kernel: [   11.823372] iwlwifi 0000:02:00.0: enabling device (0000 -> 0002)
Oct 22 16:53:38 david-N7x0WU kernel: [   12.052166] iwlwifi 0000:02:00.0: Found debug destination: EXTERNAL_DRAM
Oct 22 16:53:38 david-N7x0WU kernel: [   12.052168] iwlwifi 0000:02:00.0: Found debug configuration: 0
Oct 22 16:53:38 david-N7x0WU kernel: [   12.052564] iwlwifi 0000:02:00.0: loaded firmware version 46.6bf1df06.0 op_mode iwlmvm
Oct 22 16:53:38 david-N7x0WU kernel: [   12.677142] iwlwifi 0000:02:00.0: Detected Intel(R) Wireless-AC 9260 160MHz, REV=0x324
Oct 22 16:53:38 david-N7x0WU kernel: [   12.683939] iwlwifi 0000:02:00.0: Applying debug destination EXTERNAL_DRAM
Oct 22 16:53:38 david-N7x0WU kernel: [   12.684467] iwlwifi 0000:02:00.0: Allocated 0x00400000 bytes for firmware monitor.
Oct 22 16:53:38 david-N7x0WU kernel: [   12.728929] iwlwifi 0000:02:00.0: base HW address: 64:5d:86:dd:51:b7
Oct 22 16:53:38 david-N7x0WU kernel: [   12.795338] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
Oct 22 16:53:38 david-N7x0WU kernel: [   12.875931] iwlwifi 0000:02:00.0 wlp2s0: renamed from wlan0
Oct 22 16:53:40 david-N7x0WU kernel: [   16.042161] iwlwifi 0000:02:00.0: Applying debug destination EXTERNAL_DRAM
Oct 22 16:53:41 david-N7x0WU kernel: [   16.154137] iwlwifi 0000:02:00.0: Applying debug destination EXTERNAL_DRAM
Oct 22 16:53:41 david-N7x0WU kernel: [   16.218042] iwlwifi 0000:02:00.0: FW already configured (0) - re-configuring
Oct 22 16:53:41 david-N7x0WU NetworkManager[1283]: <info>  [1603382020.3883] rfkill1: found Wi-Fi radio killswitch (at /sys/devices/pci0000:00/0000:00:1c.3/0000:02:00.0/ieee80211/phy0/rfkill1) (driver iwlwifi)
```

---

