---
title: "Intel 9x6x Wireless Card not working after 24.04.1 upgrade"
date: 2024-09-02
forum: Networking &amp; Wireless
---

### Post by daithi_dearg on 2024-09-02
Hello,

After the upgrade the Wireless Network Card no longer works so I'm using Wired until that can be sorted out.

Details as follows:
```
sudo lshw -class network
  *-network UNCLAIMED
       description: Network controller
       product: Wi-Fi 5(802.11ac) Wireless-AC 9x6x [Thunder Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 29
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
       resources: memory:df000000-df003fff
```

I think this was working after the upgrade but there were issues with some packages and I was requested to run command "sudo apt-get install -f" and this found Obsolete packages. I was requested to run "sudo apt autoremove" and perhaps all my issues stem from this.

I tried reinstalling Intel packages but still no joy.

See errors in
```
grep iwl /var/log/syslog
2024-09-02T13:02:52.018127+01:00 david-N7x0WU kernel: iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-9260-th-b0-jf-b0-30.ucode failed with error -2
2024-09-02T13:02:52.018129+01:00 david-N7x0WU kernel: iwlwifi 0000:02:00.0: no suitable firmware found!
2024-09-02T13:02:52.018131+01:00 david-N7x0WU kernel: iwlwifi 0000:02:00.0: minimum version required: iwlwifi-9260-th-b0-jf-b0-30
2024-09-02T13:02:52.018136+01:00 david-N7x0WU kernel: iwlwifi 0000:02:00.0: maximum version supported: iwlwifi-9260-th-b0-jf-b0-46
2024-09-02T13:02:52.018243+01:00 david-N7x0WU kernel: iwlwifi 0000:02:00.0: check git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git
```

Kernel in use as follows:
```
uname -r
5.13.0-30-generic
ls /lib/modules/5.13.0-30-generic/kernel/drivers/net/wireless/intel/iwlwifi/
dvm  iwlwifi.ko  mvm
```

Had issues similar to this and hope I followed whatever advice was there:
[https://ubuntuforums.org/showthread.php?t=2452403](https://ubuntuforums.org/showthread.php?t=2452403)

Can run additional*commands as required for more information.

---

### Post by jeremy31 on 2024-09-02
Update the system and reboot.  Ubuntu 22.04 should be using the 5.15 kernel at minimum and updating the linux-firmware package might fix the firmware issue

---

### Post by daithi_dearg on 2024-09-02
Looks to me that it's up to date but concerning that it wouldn't update linux-firmware:
```
sudo apt update
Hit:1 http://security.ubuntu.com/ubuntu noble-security InRelease
Hit:2 https://dl.winehq.org/wine-builds/ubuntu jammy InRelease                 
Hit:3 http://ie.archive.ubuntu.com/ubuntu noble InRelease                      
Hit:4 http://ie.archive.ubuntu.com/ubuntu noble-updates InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
All packages are up to date.

sudo apt dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
Get more security updates through Ubuntu Pro with 'esm-apps' enabled:
  python2.7-minimal libpython2.7 python2.7 libpython2.7-minimal
  libpython2.7-stdlib
Learn more about Ubuntu Pro at https://ubuntu.com/pro
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

sudo apt-get install --reinstall linux-firmware
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/480 MB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 171090 files and directories currently installed.)
Preparing to unpack .../linux-firmware_20240318.git3b128b60-0ubuntu2.2_amd64.deb ...
Unpacking linux-firmware (20240318.git3b128b60-0ubuntu2.2) over (20240318.git3b128b60-0ubuntu2.2) ...
dpkg: error processing archive /var/cache/apt/archives/linux-firmware_20240318.git3b128b60-0ubuntu2.2_amd64.deb (--unpack):
 unable to open '/lib/firmware/mrvl/prestera/mvsw_prestera_fw-v2.0.img.zst.dpkg-new': Operation not permitted
Segmentation fault
```

If there's additional commands I need to run let me know. GUI software updates also run and it's up to date.

Can't see that 5.15 version in my list of kernels:
```
ls /lib/modules/
4.15.0-29-generic  4.15.0-38-generic  4.15.0-45-generic       5.13.0-30-generic  5.4.0-29-generic  5.4.0-37-generic  5.4.0-42-generic
4.15.0-34-generic  4.15.0-39-generic  5.10.12-051012-generic  5.4.0-26-generic   5.4.0-31-generic  5.4.0-39-generic  5.4.0-45-generic
4.15.0-36-generic  4.15.0-43-generic  5.11.3-051103-generic   5.4.0-28-generic   5.4.0-33-generic  5.4.0-40-generic  5.4.0-51-generic
```

---

### Post by daithi_dearg on 2024-09-03
Combination of these got me back in. I'm assuming the update of the kernel was required.

sudo apt-get update
sudo apt-get install linux-image-`uname -r`
sudo apt --fix-broken install

Updated kernel:

uname -r
6.8.0-41-generic

cat /etc/os-release 
PRETTY_NAME="Ubuntu 24.04.1 LTS"

---

