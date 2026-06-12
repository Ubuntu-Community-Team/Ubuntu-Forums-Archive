---
title: "Integrated Wireless on Gateway c-141 XL"
date: 2008-06-14
forum: Networking &amp; Wireless
---

### Post by Mr_Knuckles on 2008-06-14
Need some wireless help. I've searched some other threads, but can't really follow some of the stuff. My hardware is Integrated Intel® 3945 802.11a/b/g wireless networking on a Gateway c-141XL Convertible. The interface doesn't show up in the network manager to configure. 

Here are the outputs you guys need. Thanks for the help. =D

sudo lshw -C network:

  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0


ifconfig -a:

eth0      Link encap:Ethernet  HWaddr 00:e0:b8:d0:50:96  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:b8ff:fed0:5096/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14001 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11070 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:16462996 (15.7 MB)  TX bytes:1634274 (1.5 MB)
          Base address:0x1800 Memory:f8500000-f8520000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:886 errors:0 dropped:0 overruns:0 frame:0
          TX packets:886 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:44300 (43.2 KB)  TX bytes:44300 (43.2 KB)

---

### Post by chili555 on 2008-06-15
First, Network Manager will not activate wireless if you have a working IP address wired, so please detach the wire and reboot. Next, please do:```
sudo modprobe iwl3945
sudo ifconfig wlan0 up
```Does your wireless spring to life? If not, please let us see:```
sudo cat /var/log/messages | grep switch
```Thanks.

---

### Post by Mr_Knuckles on 2008-06-15
> **chili555 said:**
> First, Network Manager will not activate wireless if you have a working IP address wired, so please detach the wire and reboot. Next, please do:```
sudo modprobe iwl3945
sudo ifconfig wlan0 up
```Does your wireless spring to life? If not, please let us see:```
sudo cat /var/log/messages | grep switch
```Thanks.

I was getting an error saying "sudo: unable to resolve hostname linuxbox" but I fixed that by editing the /etc/hosts file. I still get this output.

```

sudo modprobe iw13945
FATAL Module iw13945 not found.

```

```

sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device

```


```

sudo: unable to resolve host linuxbox
Jun 12 18:28:44 steven-laptop kernel: [   22.086006] SMP alternatives: switching to UP code
Jun 12 18:28:44 steven-laptop kernel: [   22.889207] SMP alternatives: switching to SMP code
Jun 12 18:28:44 steven-laptop kernel: [   23.112708] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun 12 20:40:18 steven-laptop kernel: [ 7664.258310] SMP alternatives: switching to UP code
Jun 12 20:40:18 steven-laptop kernel: [   37.723657] SMP alternatives: switching to SMP code
Jun 12 22:30:37 (none) kernel: [   22.187660] SMP alternatives: switching to UP code
Jun 12 22:30:37 (none) kernel: [   22.982286] SMP alternatives: switching to SMP code
Jun 12 22:30:37 (none) kernel: [   23.208503] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun 13 22:14:32 (none) kernel: [   21.473057] SMP alternatives: switching to UP code
Jun 13 22:14:32 (none) kernel: [   22.264976] SMP alternatives: switching to SMP code
Jun 13 22:14:32 (none) kernel: [   22.489772] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun 13 22:39:53 (none) kernel: [   13.568685] SMP alternatives: switching to UP code
Jun 13 22:39:53 (none) kernel: [   13.818199] SMP alternatives: switching to SMP code
Jun 13 22:39:53 (none) kernel: [   14.031022] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun 14 01:02:51 (none) kernel: [   21.505152] SMP alternatives: switching to UP code
Jun 14 01:02:51 (none) kernel: [   22.297121] SMP alternatives: switching to SMP code
Jun 14 01:02:51 (none) kernel: [   22.522370] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun 14 01:02:51 (none) kernel: [   59.933574] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:593: hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x00cf0012
Jun 14 19:22:38 (none) kernel: [   14.209819] SMP alternatives: switching to UP code
Jun 14 19:22:38 (none) kernel: [   15.003653] SMP alternatives: switching to SMP code
Jun 14 19:22:38 (none) kernel: [   15.227560] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun 15 12:32:56 (none) kernel: [   12.435506] SMP alternatives: switching to UP code
Jun 15 12:32:56 (none) kernel: [   13.283424] SMP alternatives: switching to SMP code
Jun 15 12:32:56 (none) kernel: [   13.508249] ACPI: EC: non-query interrupt received, switching to interrupt mode

```


Thanks for the help. =D

---

### Post by chili555 on 2008-06-15
Please try:```
sudo modprobe ipw3945
```If you get an error, please do:```
sudo updatedb
locate 3945 | grep .ko
```*updatedb* will take a few moments, so be patient.

If you do *not* get an error, please try:```
sudo ifconfig wlan0 up
```Did your wireless come to life?

The switch part was to be sure the kill switch for your wireless card was not thrown. It appears it's not.

---

### Post by Mr_Knuckles on 2008-06-15
```

steven@linuxbox:~$ sudo modprobe ipw3945
FATAL: Module ipw3945 not found.
steven@linuxbox:~$ sudo updatedb
steven@linuxbox:~$ locate 3945 | grep .ko
/lib/modules/2.6.24-16-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko
/lib/modules/2.6.24-16-rt/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko
/lib/modules/2.6.24-18-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko
/lib/modules/2.6.24-18-rt/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko

```

Still does not live. I'm thinking I'm going to have to do some Dr. Frankenstien techniques. You know, connect it to a lighnting rod. =P

I'm guessing the "modprobe" command tests to see if the interface/ device is present/ initiated? Does linux look at hardware as if they are files? I'm kinda interested in how this is working, but you don't have to answer these questions if you don't want. =)

---

### Post by chili555 on 2008-06-16
> I'm guessing the "modprobe" command tests to see if the interface/ device is present/ initiated?Modprobe asks the computer to insert the module and any of its dependencies. In your case, *iwl3945* needs *led-class,iwlwifi_mac80211*. So modprobe says get iwl3945 and all his little henchmen to work driving our wireless card. A card or other device shows in *lshw* as unclaimed when the system can't find a driver for it, either because it isn't anywhere in the system or, as in your case, it is, but the system can't find what's right there before our eyes.

I am quite interested in your installation of the 'rt' kernel image. > /lib/modules/2.6.24-18-rt/ubuntu/Can you please tell me a bit more about this? Which are you running at the moment?```
uname -r
```Does the wireless come to life if you switch to the 'generic' kernel at the GRUB menu? Does the module stick if you give it's absolute path?```
sudo modprobe /lib/modules/`uname -r`/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko
```

---

### Post by Mr_Knuckles on 2008-06-22
> **chili555 said:**
> Modprobe asks the computer to insert the module and any of its dependencies. In your case, *iwl3945* needs *led-class,iwlwifi_mac80211*. So modprobe says get iwl3945 and all his little henchmen to work driving our wireless card. A card or other device shows in *lshw* as unclaimed when the system can't find a driver for it, either because it isn't anywhere in the system or, as in your case, it is, but the system can't find what's right there before our eyes.

I am quite interested in your installation of the 'rt' kernel image. Can you please tell me a bit more about this? Which are you running at the moment?```
uname -r
```Does the wireless come to life if you switch to the 'generic' kernel at the GRUB menu? Does the module stick if you give it's absolute path?```
sudo modprobe /lib/modules/`uname -r`/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko
```


I was running the rt kernel. I switched to the generic, but nothing happened.



uname -r:
```

2.6.24-18-generic

```


sudo modprobe /lib/modules/2.6.24-18-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko:
```

FATAL: Module /lib/modules/2.6.24-18-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko not found. 

```

Still no clue. =/

---

