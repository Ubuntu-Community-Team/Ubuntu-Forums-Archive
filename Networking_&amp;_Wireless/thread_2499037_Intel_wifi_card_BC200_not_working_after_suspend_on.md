---
title: "Intel wifi card BC200 not working after suspend on Ubuntu 24.04"
date: 2024-07-09
forum: Networking &amp; Wireless
---

### Post by danielr0815 on 2024-07-09
After booting Ubuntu 24.04, everything related to the intel BC200 wifi works as expected. 

[https://paste.ubuntu.com/p/TsRP57mnxt/](https://paste.ubuntu.com/p/TsRP57mnxt/)

After a suspend / wakeup the wifi card is still visible in NetworkManager, but no SSID's are shown.

[https://paste.ubuntu.com/p/j3M6GzJWc9/](https://paste.ubuntu.com/p/j3M6GzJWc9/)


The same happens, if after a fresh start with a working wifi I unload + load the iwlwifi module by calling
```

    modprobe -r iwlwifi
    modprobe iwlwifi

```

I tried the following thinks without success to get it running without the need of performing a restart:
[LIST]
[*] downgrade the kernel to v6.5.11 
[*] upgrade the kernel to v6.9.3 
[*] restart of NetworkManager 
[*] switching off / on Wifi 
[*] switching on / off airplane mode 
[*]*rfkill list* shows soft+hard blocked: no 
[/LIST]

It is interesting, that the command `iw dev wlo1 scan` shows the up to date list of SSID's as expected. So it seems, that the network card is working but the network manager is not able to use it... so I don't know if probably some initialization is missed after the reload of iwlwifi.

I'm using a fresh 24.04 Ubuntu installation.


    ```
root@daniel-HP-Spectre:/home/jj# modprobe -r iwlwifi
    root@daniel-HP-Spectre:/home/jj# modprobe iwlwifi
    root@daniel-HP-Spectre:/home/jj# dmesg | grep iwl
    [   17.155169] iwlwifi 0000:01:00.0: enabling device (0000 -> 0002)
    [   17.167490] iwlwifi 0000:01:00.0: Detected crf-id 0x2001910, cnv-id 0x2001910 wfpm id 0x80000000
    [   17.167558] iwlwifi 0000:01:00.0: PCI dev 272b/00f4, rev=0x472, rfid=0x112200
    [   17.172831] iwlwifi 0000:01:00.0: TLV_FW_FSEQ_VERSION: FSEQ Version: 0.0.4.125
    [   17.173106] iwlwifi 0000:01:00.0: loaded firmware version 86.fb5c9aeb.0 gl-c0-fm-c0-86.ucode op_mode iwlmvm
    [   17.492436] iwlwifi 0000:01:00.0: Detected Intel(R) TBD Bz device, REV=0x472
    [   17.523378] iwlwifi 0000:01:00.0: WRT: Invalid buffer destination
    [   17.782569] iwlwifi 0000:01:00.0: loaded PNVM version 8443a58d
    [   17.802464] iwlwifi 0000:01:00.0: Detected RF FM, rfid=0x112200
    [   17.890281] iwlwifi 0000:01:00.0: base HW address: e4:60:17:eb:c5:85
    [   17.955574] iwlwifi 0000:01:00.0 wlo1: renamed from wlan0
    [   19.047005] iwlwifi 0000:01:00.0: WRT: Invalid buffer destination
    [   19.435255] iwlwifi 0000:01:00.0: Registered PHC clock: iwlwifi-PTP, with index: 0
    [  615.498614] iwlwifi 0000:01:00.0: Unregistering PHC clock: iwlwifi-PTP, with index: 0
    [  620.338754] iwlwifi 0000:01:00.0: Detected crf-id 0x2001910, cnv-id 0x2001910 wfpm id 0x80000000
    [  620.338881] iwlwifi 0000:01:00.0: PCI dev 272b/00f4, rev=0x472, rfid=0x112200
    [  620.344160] iwlwifi 0000:01:00.0: TLV_FW_FSEQ_VERSION: FSEQ Version: 0.0.4.125
    [  620.344619] iwlwifi 0000:01:00.0: loaded firmware version 86.fb5c9aeb.0 gl-c0-fm-c0-86.ucode op_mode iwlmvm
    [  620.465017] iwlwifi 0000:01:00.0: Detected Intel(R) TBD Bz device, REV=0x472
    [  620.505885] iwlwifi 0000:01:00.0: WRT: Invalid buffer destination
    [  620.764221] iwlwifi 0000:01:00.0: loaded PNVM version 8443a58d
    [  620.785729] iwlwifi 0000:01:00.0: Detected RF FM, rfid=0x112200
    [  620.874426] iwlwifi 0000:01:00.0: base HW address: e4:60:17:eb:c5:85
    [  620.943665] iwlwifi 0000:01:00.0 wlo1: renamed from wlan0
    [  621.010585] iwlwifi 0000:01:00.0: WRT: Invalid buffer destination
    [  621.397075] iwlwifi 0000:01:00.0: Registered PHC clock: iwlwifi-PTP, with index: 0
    
    root@daniel-HP-Spectre:/home/jj# lspci -nn | grep Network
    01:00.0 Network controller [0280]: Intel Corporation Wi-Fi 7(802.11be) AX1775*/AX1790*/BE20*/BE401/BE1750* 2x2 [8086:272b] (rev 1a)
    
    root@daniel-HP-Spectre:/home/jj# lshw -class network
    *-network                 
       Beschreibung: Ethernet interface
       Produkt: Wi-Fi 7(802.11be) AX1775*/AX1790*/BE20*/BE401/BE1750* 2x2
       Hersteller: Intel Corporation
       Physische ID: 0
       Bus-Informationen: pci@0000:01:00.0
       Logischer Name: wlo1
       Version: 1a
       Seriennummer: e4:60:17:eb:c5:85
       Breite: 64 bits
       Takt: 33MHz
       Fähigkeiten: pm msi pciexpress msix bus_master cap_list ethernet physical
       Konfiguration: broadcast=yes driver=iwlwifi driverversion=6.8.0-36-generic firmware=86.fb5c9aeb.0 gl-c0-fm-c0-86.uc latency=0 link=no multicast=yes
       Ressourcen: irq:16 memory:8c100000-8c103fff
```


Which other thinks can I try to find out the root cause or a workaround of that issue?

---

### Post by currentshaft on 2024-07-09
Is your firmware/EC up to date?

fwupdmgr refresh

---

### Post by danielr0815 on 2024-07-09
It seems to be up to date:

```
jj@daniel-HP-Spectre:~$ sudo fwupdmgr refresh
Metadata is up to date; use --force to refresh again.

```


Output of 
sudo fwupdmgr get-devices
[https://paste.ubuntu.com/p/nK6dNJ3pzG/](https://paste.ubuntu.com/p/nK6dNJ3pzG/)

```

jj@daniel-HP-Spectre:~$ sudo fwupdmgr get-updates
Devices with no available firmware updates: 
 &#8226; SSD 990 PRO 4TB
 &#8226; System Firmware
 &#8226; ELAN07CD:00 04F3:310A
Devices with the latest available firmware version:
 &#8226; UEFI dbx
No updates available

```

---

### Post by currentshaft on 2024-07-09
Possibly related to power saving/regulation? I know there are some kernel parameters which disable those features in cards, but I do not recall them off-hand. May be worthwhile parsing through the entire dmesg and journalctl output after a wake event.

Also may want to try this sleep troubleshooting script [https://github.com/intel/S0ixSelftestTool/blob/main/s0ix-selftest-tool.sh](https://github.com/intel/S0ixSelftestTool/blob/main/s0ix-selftest-tool.sh)

---

### Post by danielr0815 on 2024-07-09
The interesting point is, that I get the same problem with the wifi card, if I unload the module iwlwifi by calling modproble -r iwlwifi followed by loading it again with modprobe iwlwifi. I guess in this situation we have no power saving triggered right?

I'm not sure, which of the existing warnings could be a problem... 

here is the log after unloading and loading iwlwifi:
[https://paste.ubuntu.com/p/CMNyHMQNTs/](https://paste.ubuntu.com/p/CMNyHMQNTs/)

Here is the log after suspend / wakeup:
[https://paste.ubuntu.com/p/4TC3wSdXpn/](https://paste.ubuntu.com/p/4TC3wSdXpn/)

Following the logs from the script:
[https://paste.ubuntu.com/p/nM97WrCR6K/](https://paste.ubuntu.com/p/nM97WrCR6K/)

There are some issues with turbostat, if you think it could help, I will try to fix them.

---

### Post by danielr0815 on 2024-07-11
I found a workaround. After updating the linux kernel from 6.8.0-36 to 6.8.0-38, the wifi is working after the suspend.

I performed the update by command ```
apt install linux-modules-iwlwifi-generic-hwe-24.04
```.. this triggered the update.

But anyway I have a new strange behavior, if I try to unload the module iwlwifi, an error occures:

```
jj@daniel-HP-Spectre:~$ sudo modprobe -vr iwlwifi
remove (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) && /sbin/modprobe -r mac80211
rmmod: ERROR: Module iwlwifi is not currently loaded
modprobe: FATAL: Error running remove command for iwlwifi
jj@daniel-HP-Spectre:~$ sudo modprobe -v iwlwifi
insmod /lib/modules/6.8.0-38-generic/ubuntu/iwlwifi/iwlwifi.ko.zst 
jj@daniel-HP-Spectre:~$ sudo modprobe -vr iwlwifi
remove (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) && /sbin/modprobe -r mac80211
rmmod: ERROR: Module iwlwifi is not currently loaded
modprobe: FATAL: Error running remove command for iwlwifi
jj@daniel-HP-Spectre:~$ sudo modprobe -v iwlwifi
insmod /lib/modules/6.8.0-38-generic/ubuntu/iwlwifi/iwlwifi.ko.zst 
```

But at the end I'm quite happy and everything reated to the wifi connection works as expected now.

---

### Post by danielr0815 on 2024-07-11
I found a workaround. After updating the linux kernel from 6.8.0-36 to 6.8.0-38, the wifi is working after the suspend. But after some time the connection stops. In NetworkManager it looks like still connected, but no packets can be transmitted.

 I performed the update by command ```
apt install linux-modules-iwlwifi-generic-hwe-24.04
```

 Also I have another new strange behavior, if I try to unload the module iwlwifi, an error occures:

 
```
jj@daniel-HP-Spectre:~$ sudo modprobe -vr iwlwifi
remove (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) && /sbin/modprobe -r mac80211
rmmod: ERROR: Module iwlwifi is not currently loaded
modprobe: FATAL: Error running remove command for iwlwifi
jj@daniel-HP-Spectre:~$ sudo modprobe -v iwlwifi
insmod /lib/modules/6.8.0-38-generic/ubuntu/iwlwifi/iwlwifi.ko.zst 
jj@daniel-HP-Spectre:~$ sudo modprobe -vr iwlwifi
remove (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) && /sbin/modprobe -r mac80211
rmmod: ERROR: Module iwlwifi is not currently loaded
modprobe: FATAL: Error running remove command for iwlwifi
jj@daniel-HP-Spectre:~$ sudo modprobe -v iwlwifi
insmod /lib/modules/6.8.0-38-generic/ubuntu/iwlwifi/iwlwifi.ko.zst 

```

---

