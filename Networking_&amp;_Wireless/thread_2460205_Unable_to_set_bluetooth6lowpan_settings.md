---
title: "Unable to set bluetooth/6lowpan settings"
date: 2021-04-05
forum: Networking &amp; Wireless
---

### Post by nagesh6 on 2021-04-05
My Ubuntu details:
"
# cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=20.04
DISTRIB_CODENAME=focal
DISTRIB_DESCRIPTION="Ubuntu 20.04.2 LTS"
"

when i try lsmod | grep 6lowpan, i can see that the kernel module is avaiable.
"
# lsmod | grep 6low
bluetooth_6lowpan      28672  0
6lowpan                40960  8 nhc_fragment,nhc_dest,nhc_ipv6,bluetooth_6lowpan,nhc_hop,nhc_udp,nhc_mobility,nhc_routing
bluetooth             581632  32 btrtl,bluetooth_6lowpan,btintel,btbcm,bnep,btusb,rfcomm
"

but when i try to enable bluetooth 6lowpan module, i get the error "Operation not permitted"
"
# echo "1" > /sys/kernel/debug/bluetooth/6lowpan_enable
bash: /sys/kernel/debug/bluetooth/6lowpan_enable: Operation not permitted
"

using sudo i have got into root permissions as below:
"
# sudo su
# whoami
root
# modprobe bluetooth_6lowpan
# echo 1 > /sys/kernel/debug/bluetooth/6lowpan_enable
bash: /sys/kernel/debug/bluetooth/6lowpan_enable: Operation not permitted
"
I even tried to set using the suggestion given in one of the post([https://ubuntuforums.org/showthread.php?t=2428547](https://ubuntuforums.org/showthread.php?t=2428547)), still no luck:
"
# sudo sh -c "/bin/echo 1 > /sys/kernel/debug/bluetooth/6lowpan_enable"
sh: /sys/kernel/debug/bluetooth/6lowpan_enable: Operation not permitted
"

dmesg recorded the following error:
"201688.308845] audit: type=1400 audit(1617619807.993:78): apparmor="DENIED" operation="open" profile="snap.snap-store.ubuntu-software" name="/var/lib/snapd/hostfs/usr/share/gdm/greeter/applications/gnome-initial-setup.desktop" pid=1983 comm="snap-store" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0 

[201688.329071] audit: type=1400 audit(1617619808.013:79): apparmor="DENIED" operation="open" profile="snap.snap-store.ubuntu-software" name="/var/lib/snapd/hostfs/usr/share/gdm/greeter/applications/gnome-initial-setup.desktop" pid=1983 comm="snap-store" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[201688.709403] audit: type=1326 audit(1617619808.393:80): auid=1000 uid=1000 gid=1000 ses=3 subj=snap.snap-store.ubuntu-software pid=1983 comm="snap-store" exe="/snap/snap-store/518/usr/bin/snap-store" sig=0 arch=c000003e syscall=93 compat=0 ip=0x7fefe9a1c4e7 code=0x50000
[201744.641113] Lockdown: bash: debugfs access is restricted; see man kernel_lockdown.7
"
i have exhausted the google search, but couldn't find any suggestions that would solve my problem. Kindly help.

---

