---
title: "no network [FIXED]"
date: 2023-02-17
forum: Networking &amp; Wireless
---

### Post by ziscoplankton on 2023-02-17
Hello world ):P ,


Fixed issue, I connected my phone to the laptop as a hotspot. The laptop detected a connection. I then install the drivers for the interface and the pc is back running... good learnings...I could not delete the post this is why it is now fixed...



I turned on my laptop [ **Macbook **pro 2013 - **dual boot **_*Ubuntu 22.04 - macOS*_ ] yesterday and since then my wifi has disappeared. I tried many things but no success...:icon_frown:


INFO & OUTPUTS:

**ifconfig** outputs only the loopback
```

lo: flags=73<UP, LOOPBACK, RUNNING> mtu 65536
inet 127.0.0.1 netmask 255.0.0.0
[...]

```


Along this step, I still tried to ping my loopback even though it is the loopback lol. It worked...


**/etc/network/interfaces** outputs an empty file [and I tried different inputs but no success]


**lspci** 
```

[...]
03:00.0 Network Controller: Broadcom Inc. and subsidiaries BCM4360 802.11ac Wireless Network Adapter (rev03)
[...]

```





**lsusb**:
```

[...]
Bus 001 Device 002 ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
[...]

```


**lshw -C network**
```

WARNING [...]
*-network
  description: Network Controller
  product: BCM4360 802.11ac Wireless Network Adapter
  [...]
  capabilities: bus_master cap_list
  configuration: driver=bcma-pci-bridge latency=0
  resources: irq:18 memory:b0600000-b0607fff memory: b0400000-b05fffff
WARNING [...]

```



**nmcli device show **-> _*only loopback*_
```

GENERAL.DEVICE:    lo
GENERAL.TYPE:    loopback
[...]

```



**ip link show **->  *loopback only*


**01-network-manager-all.yaml :**
```
  
  network:
    version: 2
    renderer: NetworkManager

```

**lspci -nnk | grep 0280 -A3**
```

03:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM4360 802.11ac Wireless Network Adapter [14e4:43a0] (rev 03)
Subsystem: Apple Inc. [...]
Kernel driver in use: bcma-pci-bridge
Kernel modules: bcma

```
[/CODE]

Since the output of nmcli should have my nic, is the issue coming from network-manager? I tried to download the pkg and bring it to the actual laptop to install but so far no success.


- When I reboot in a different kernel chosen from the GRUB, the issue persist


- When I reboot in a recovery mode kernel and get the *system summary*, 
[FONT=lucida console][SIZE=3]*Network connectivity status none*[/SIZE][/FONT]

and am unable to check for broken packages, etc into this menu. 


- When I am inside the **'Softwares & Updates'** within my desktop applications, in the Additional Drivers tab, it shows my network adapter and says 
[SIZE=3]*[FONT=system]Device is not working[/FONT]*[/SIZE]
[I was trying to re install drivers from ubuntu mounted iso but this did not work either]


- When I reboot unto macOS, my network connectivity works fine but rebooting to macOS and then come back to Ubuntu did not resolve this issue.


- Also tried a **dconf reset /f **but no success


Anyone has an idea or a direction to follow to resolve this issue please?




Thanks heaps O:)

---

### Post by Scottie303 on 2023-02-17
I also have a Broadcom adapter. Yesterday after the update my wifi also disappeared. It took me a few hours to recover it after trying to roll back the updates. But some of the packaged couldn't be found. So I could not roll back. I then almost reinstalled Ubuntu, but the installation failed from an SD card for some reason. 

So, what worked for me was to choose 'do not use the device' in additional drivers. REBOOT. Then choose to once again use the Broadcom driver. REBOOT. After that, my WIFI re-appeared and it's working fine now.
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291807&stc=1[/IMG]

---

### Post by jeremy31 on 2023-02-17
If you are using 22.04 and got a kernel update to 5.19, the loss of wifi was likely due to a gcc version conflict and that issue was recently fixed

---

### Post by Scottie303 on 2023-02-17
:~$ sudo hostnamectl
Operating System: Ubuntu 22.04.1 LTS              
          Kernel: Linux 5.19.0-32-generic
[h=1][IMG]https://em-content.zobj.net/thumbs/120/google/350/thumbs-up_1f44d.png[/IMG][/h]

---

