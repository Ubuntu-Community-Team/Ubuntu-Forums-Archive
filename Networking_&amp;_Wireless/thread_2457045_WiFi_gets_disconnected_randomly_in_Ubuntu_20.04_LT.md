---
title: "WiFi gets disconnected randomly in Ubuntu 20.04 LTS"
date: 2021-01-24
forum: Networking &amp; Wireless
---

### Post by sureshdesh on 2021-01-24
I am a newbie in Linux. 

I have  a problem - my WiFi Connection gets disconnected randomly and often. Most of the times, it gets reconnected automatically after a few minutes. 

But a few times it does not get reconnected. In that case I have to reboot the Laptop to get reconnected.

I have Dell 14 3000 Core i3 Inspiron 3481 Laptop whcih came preinstalled with Ubuntu 18.04 LTS. 
The system got upgraded to Linux 20.04.1 LTS very recently.
The WiFi Router is Netgear WNR614 N300 Mbps 2.4 Ghz WiFi Router.

The problem existed in the previous version of Ubuntu 18.04 too.

May I request for help to overcome the issue please?

---

### Post by CelticWarrior on 2021-01-25
If the problem preexists the upgrade to 20.04 then it's likely environmental, i.e., router settings and/or relative position/interference related.
Before anything else check the WiFi encryption settings (router). It should be WPA2-AES.

---

### Post by slickymaster on 2021-01-25
*Thread moved to **Networking & Wireless**.*

---

### Post by ActionParsnip on 2021-01-25
What is the output of:
```

sudo lshw -C network; lsb_release -a; uname -a

```
Thanks

---

### Post by sureshdesh on 2021-01-25
@CelticWarrior - thanks for the suggestion, will chek.
@ActionParsnip - Here is the sceenshot showing the Output after the command:

---

### Post by wildmanne39 on 2021-01-25
Hello and welcome to the forum sureshdesh.

Please post the code output on the forum instead of posting images of the code output by using code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Thanks

---

### Post by sureshdesh on 2021-01-26
Thank you for the suggestion. 
The Output of the Command is -

```

[FONT=Arial][COLOR=#069a2e][FONT=sans-serif]suresh@Vasanti-Inspiron-3481[/FONT][/COLOR][COLOR=#000000][FONT=sans-serif]:~$[/FONT][/COLOR][FONT=sans-serif]:[/FONT][COLOR=#355269][FONT=sans-serif]~[/FONT][/COLOR][FONT=sans-serif]$ sudo lshw -C network; lsb_release -a; uname -a[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif][sudo] password for suresh:[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]*-network[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      description: Ethernet interface[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      product: RTL810xE PCI Express Fast Ethernet controller[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      vendor: Realtek Semiconductor Co., Ltd.[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      physical id: 0[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      bus info: pci@0000:01:00.0[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      logical name: enp1s0[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      version: 07[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      serial: d8:d0:90:53:0c:55[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      width: 64 bits[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      clock: 33MHz[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      configuration: broadcast=yes driver=r8169 latency=0 multicast=yes[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      resources: irq:16 ioport:e000(size=256) memory:d1204000-d1204fff memory:d1200000-d1203fff[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]*-network[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      description: Wireless interface[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      product: QCA9377 802.11ac Wireless Network Adapter[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      vendor: Qualcomm Atheros[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      physical id: 0[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      bus info: pci@0000:02:00.0[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      logical name: wlp2s0[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      version: 31[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      serial: b0:68:e6:03:72:83[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      width: 64 bits[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      clock: 33MHz[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      configuration: broadcast=yes driver=ath10k_pci driverversion=5.4.0-64-generic firmware=WLAN.TF.2.1-00021-QCARMSWP-1 ip=192.168.1.6 latency=0 link=yes multicast=yes wireless=IEEE 802.11[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      resources: irq:129 memory:d1000000-d11fffff[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]No LSB modules are available.[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]Distributor ID: Ubuntu[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]Description: Ubuntu 20.04.1 LTS[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]Release: 20.04[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]Codename: focal[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]Linux Vasanti-Inspiron-3481 5.4.0-64-generic #72-Ubuntu SMP Fri Jan 15 10:27:54 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux[/FONT][/FONT]
[FONT=Arial][COLOR=#069a2e][FONT=sans-serif]suresh@Vasanti-Inspiron-3481[/FONT][/COLOR][COLOR=#000000][FONT=sans-serif]:~$[/FONT][/COLOR][FONT=sans-serif]
[/FONT][/FONT]
```

---

### Post by sureshdesh on 2021-01-26
Thank you - Output of the Code in the Text form is as follows:
```

[FONT=Arial][COLOR=#069a2e][FONT=sans-serif]suresh@Vasanti-Inspiron-3481[/FONT][/COLOR][COLOR=#000000][FONT=sans-serif]:~$[/FONT][/COLOR][FONT=sans-serif]:[/FONT][COLOR=#355269][FONT=sans-serif]~[/FONT][/COLOR][FONT=sans-serif]$ sudo lshw -C network; lsb_release -a; uname -a[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif][sudo] password for suresh:[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]*-network[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      description: Ethernet interface[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      product: RTL810xE PCI Express Fast Ethernet controller[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      vendor: Realtek Semiconductor Co., Ltd.[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      physical id: 0[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      bus info: pci@0000:01:00.0[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      logical name: enp1s0[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      version: 07[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      serial: d8:d0:90:53:0c:55[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      width: 64 bits[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      clock: 33MHz[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      configuration: broadcast=yes driver=r8169 latency=0 multicast=yes[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      resources: irq:16 ioport:e000(size=256) memory:d1204000-d1204fff memory:d1200000-d1203fff[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]*-network[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      description: Wireless interface[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      product: QCA9377 802.11ac Wireless Network Adapter[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      vendor: Qualcomm Atheros[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      physical id: 0[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      bus info: pci@0000:02:00.0[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      logical name: wlp2s0[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      version: 31[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      serial: b0:68:e6:03:72:83[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      width: 64 bits[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      clock: 33MHz[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      configuration: broadcast=yes driver=ath10k_pci driverversion=5.4.0-64-generic firmware=WLAN.TF.2.1-00021-QCARMSWP-1 ip=192.168.1.6 latency=0 link=yes multicast=yes wireless=IEEE 802.11[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]      resources: irq:129 memory:d1000000-d11fffff[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]No LSB modules are available.[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]Distributor ID: Ubuntu[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]Description: Ubuntu 20.04.1 LTS[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]Release: 20.04[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]Codename: focal[/FONT][/FONT]
[FONT=Arial][FONT=sans-serif]Linux Vasanti-Inspiron-3481 5.4.0-64-generic #72-Ubuntu SMP Fri Jan 15 10:27:54 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux[/FONT][/FONT]
[FONT=Arial][COLOR=#069a2e][FONT=sans-serif]suresh@Vasanti-Inspiron-3481[/FONT][/COLOR][COLOR=#000000][FONT=sans-serif]:~$
[/FONT][/COLOR][/FONT]
```[FONT=Arial][COLOR=#000000][FONT=sans-serif]


[/FONT][/COLOR][/FONT]

---

### Post by sureshdesh on 2021-01-27
@ActionParsnip Sir - I have posted the output of Code suggested by you - '[COLOR=#000000][FONT=&quot]sudo lshw -C network; lsb_release -a; uname -a'.
I posted the Text File of the Output as well as the screenshot of the Output.
May I get the help Sir?[/FONT][/COLOR]

---

