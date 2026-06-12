---
title: "Intel wireless not working after apt update and upgrade"
date: 2021-04-01
forum: Networking &amp; Wireless
---

### Post by 3marproof on 2021-04-01
[COLOR=#242729][FONT=Arial]after i updated, it just disappeared from the network manager UI [/FONT][/COLOR][https://i.stack.imgur.com/JQsDF.png](https://i.stack.imgur.com/JQsDF.png)
```
*-network:0 DISABLED             description: Wireless interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 14.3
       bus info: pci@0000:00:14.3
       logical name: wlo1
       version: 00
       serial: 90:cc:df:40:b5:aa
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.4.0-66-generic firmware=48.13675109.0 latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:ec43c000-ec43ffff
```

---

### Post by mikewhatever on 2021-04-01
Let us see the outputs of:

```

rfkill list all

lsb_release -d

```

---

### Post by 3marproof on 2021-04-01
```
0: phy0: Wireless LAN    Soft blocked: no
    Hard blocked: no
1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no



```

```
Description:    Ubuntu 18.04.5 LTS


```

---

### Post by mikewhatever on 2021-04-01
So, nothing is disabled, and should work.

Let's check if the networking service is disabled, and if you have a custom kernel version:

```

systemctl status networking

uname -rv

```

---

### Post by 3marproof on 2021-04-04
> **mikewhatever said:**
> So, nothing is disabled, and should work.

Let's check if the networking service is disabled, and if you have a custom kernel version:

```

systemctl status networking

uname -rv

```

```
networking.service - Raise network interfaces   Loaded: loaded (/lib/systemd/system/networking.service; enabled; vendor prese
   Active: active (exited) since Sun 2021-04-04 10:57:41 EEST; 6min ago
     Docs: man:interfaces(5)
  Process: 1226 ExecStart=/sbin/ifup -a --read-environment (code=exited, status=
  Process: 1218 ExecStartPre=/bin/sh -c [ "$CONFIGURE_INTERFACES" != "no" ] && [
 Main PID: 1226 (code=exited, status=0/SUCCESS)


Apr 04 10:57:41 oismael-laptop systemd[1]: Starting Raise network interfaces...
Apr 04 10:57:41 oismael-laptop systemd[1]: Started Raise network interfaces.



```


```
5.4.0-70-generic #78~18.04.1-Ubuntu SMP Sat Mar 20 14:10:07 UTC 2021
```

---

### Post by VMC on 2021-04-04
Check output of: ```
sudo dmesg -T |grep wifi
```

---

### Post by 3marproof on 2021-04-04
```
[Sun Apr  4 14:36:46 2021] Loading modules backported from iwlwifi[Sun Apr  4 14:36:46 2021] iwlwifi-stack-public:master:8324:9176b151
[Sun Apr  4 14:36:47 2021] iwlwifi 0000:00:14.3: enabling device (0000 -> 0002)
[Sun Apr  4 14:36:47 2021] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-QuZ-a0-hr-b0-63.ucode failed with error -2
[Sun Apr  4 14:36:47 2021] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-QuZ-a0-hr-b0-62.ucode failed with error -2
[Sun Apr  4 14:36:47 2021] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-QuZ-a0-hr-b0-61.ucode failed with error -2
[Sun Apr  4 14:36:47 2021] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-QuZ-a0-hr-b0-60.ucode failed with error -2
[Sun Apr  4 14:36:47 2021] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-QuZ-a0-hr-b0-59.ucode failed with error -2
[Sun Apr  4 14:36:47 2021] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-QuZ-a0-hr-b0-58.ucode failed with error -2
[Sun Apr  4 14:36:47 2021] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-QuZ-a0-hr-b0-57.ucode failed with error -2
[Sun Apr  4 14:36:47 2021] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-QuZ-a0-hr-b0-56.ucode failed with error -2
[Sun Apr  4 14:36:47 2021] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-QuZ-a0-hr-b0-55.ucode failed with error -2
[Sun Apr  4 14:36:47 2021] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-QuZ-a0-hr-b0-54.ucode failed with error -2
[Sun Apr  4 14:36:47 2021] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-QuZ-a0-hr-b0-53.ucode failed with error -2
[Sun Apr  4 14:36:47 2021] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-QuZ-a0-hr-b0-52.ucode failed with error -2
[Sun Apr  4 14:36:47 2021] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-QuZ-a0-hr-b0-51.ucode failed with error -2
[Sun Apr  4 14:36:47 2021] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-QuZ-a0-hr-b0-50.ucode failed with error -2
[Sun Apr  4 14:36:47 2021] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-QuZ-a0-hr-b0-49.ucode failed with error -2
[Sun Apr  4 14:36:47 2021] iwlwifi 0000:00:14.3: TLV_FW_FSEQ_VERSION: FSEQ Version: 43.2.23.17
[Sun Apr  4 14:36:47 2021] iwlwifi 0000:00:14.3: Found debug destination: EXTERNAL_DRAM
[Sun Apr  4 14:36:47 2021] iwlwifi 0000:00:14.3: Found debug configuration: 0
[Sun Apr  4 14:36:47 2021] iwlwifi 0000:00:14.3: loaded firmware version 48.13675109.0 QuZ-a0-hr-b0-48.ucode op_mode iwlmvm



```

---

### Post by chili555 on 2021-04-04
> networking.service - Raise network interfaces   Loaded: loaded (/lib/systemd/system/networking.service; enabled; vendor prese
   Active: active (exited) since Sun 2021-04-04 10:57:41 EEST; 6min ago
     [COLOR="#FF0000"]Docs: man:interfaces(5)[/COLOR]
  Process: 1226 ExecStart=/sbin/ifup -a --read-environment (code=exited, status=
  Process: 1218 ExecStartPre=/bin/sh -c [ "$CONFIGURE_INTERFACES" != "no" ] && [
 Main PID: 1226 (code=exited, status=0/SUCCESS)Fascinating...

Let's see:

```
cat /etc/network/interfaces
cat /etc/netplan/*.yaml
```

---

