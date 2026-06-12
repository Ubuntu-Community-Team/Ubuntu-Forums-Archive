---
title: "HP Pavilion 17  WiFi adapter Realtek RT3290 does not work"
date: 2017-02-24
forum: Networking &amp; Wireless
---

### Post by grigorius0sol on 2017-02-24
For some reason info from wifi_info script became more then 19kb so attaching the tar.gz. Please help me in solving this problem.

**lspci -nnk | grep -iA2 net; rfkill list all:**
```


07:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
    DeviceName: Ralink WLAN Ralink RT3290LE Roma 802.11bgn 1x1 Wi-Fi + BT4.0 co
    Subsystem: Hewlett-Packard Company Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter [103c:18ec]
--
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    DeviceName: Realtek PCIe FE Family Controller
    Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:1972]
    Kernel driver in use: r8169
    Kernel modules: r8169
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes



```

**modinfo iwlwifi | grep 1010:**
```

alias:          pci:v00008086d000024F3sv*sd00001010bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00001010bc*sc*i*

```


[B]uname -r:
[/B]```

4.4.0-64-generic

```

---

### Post by chili555 on 2017-02-25
> 0: phy0: Wireless LAN
	Soft blocked: no
	[COLOR="#FF0000"]Hard blocked: yes[/COLOR]
This implies that the hardware switch is set to disable wireless. Can you please find it and switch it?

This is interesting, too:> rt3290sta            1155072  0
rt2800pci              16384  0
rt2800mmio             20480  1 rt2800pci
rt2800lib              94208  2 rt2800pci,rt2800mmioYou have both the native driver rt2800pci and a compiled driver rt3290sta loaded. You need one or the other, not both.

I suspect that you compiled a different driver because your wireless doesn't work. Of course, no driver can reach out and switch the wireless switch for you.

What is the exact model of your HP?

---

### Post by grigorius0sol on 2017-02-25
The exact model is HP Pavilion 17 e-073sr.

I've tried to switch WiFi to on mode but the button does not work.

As for two drivers I made some tries to enable wifi maybe I've made something wrong.

---

### Post by chili555 on 2017-02-25
Let's try an experiment. Please open a terminal and do:```
sudo modprobe -r rt3290sta
```Now does the wireless button work?```
rfkill list all
```Next, try:```
sudo modprobe -r hp-wmi
```Now does the wireless button work?```
rfkill list all
```Next, try:```
sudo modprobe hp-wireless
```Now does the wireless button work?```
rfkill list all
```We hope that some combination of these commands will enable the switch and allow the wireless to connect. When we find it, we'll write a couple of lines to the system to make it permanent.

---

### Post by grigorius0sol on 2017-02-25
Output:
```

rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

```



next,
```

sudo modprobe -r hp-wmi
 rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

```


and the next one,

```

sudo modprobe hp-wireless
rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes



```


No luck, button still does not work :(

---

### Post by chili555 on 2017-02-25
We are studying this now. It may take a while. Please give us some time.

---

### Post by jeremy31 on 2017-02-25
I would do ```
sudo apt-get update && sudo apt-get install linux-generic-hwe-16.04
```
Reboot and see if some fixes for hp-wmi work on your computer as there was a bug that kept the hardware switch from working

---

### Post by grigorius0sol on 2017-02-25
Hello,

install failes with error:
```

Setting up linux-image-extra-4.8.0-39-generic (4.8.0-39.42~16.04.1) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.8.0-39-generic /boot/vmlinuz-4.8.0-39-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.8.0-39-generic /boot/vmlinuz-4.8.0-39-generic
modprobe: FATAL: Module rt2x00pci is in use.
Error! pre_install failed, aborting install.
You may override by specifying --force.
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/rtlwifi-new-dkms.0.crash'
Error! Bad return status for module build on kernel: 4.8.0-39-generic (x86_64)
Consult /var/lib/dkms/rtlwifi-new/0.10/build/make.log for more information.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.8.0-39-generic /boot/vmlinuz-4.8.0-39-generic
update-initramfs: Generating /boot/initrd.img-4.8.0-39-generic

```

After reboot situation did not change.

---

### Post by jeremy31 on 2017-02-25
What does ```
uname -a
``` show about the kernel version

---

### Post by grigorius0sol on 2017-02-25
> **jeremy31 said:**
> What does ```
uname -a
``` show about the kernel version

4.8.0-39-generic

---

### Post by jeremy31 on 2017-02-25
So the wireless switch has no affect on results in ```
rfkill list
```

---

### Post by grigorius0sol on 2017-02-26
Same thing 
```

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

```

---

### Post by jeremy31 on 2017-02-26
Go into BIOS and reset to defaults and see if that clears the block

---

### Post by grigorius0sol on 2017-02-27
Resetting BIOS to default did no effect except after reset my hard drive was not recognized as boot device so I switched boot method to legacy.

---

### Post by grigorius0sol on 2017-02-28
> **chili555 said:**
> We are studying this now. It may take a while. Please give us some time.

Hello,

I'm asking just for interest is there any progress?

---

### Post by chili555 on 2017-02-28
> **grigorius0sol said:**
> Hello,

I'm asking just for interest is there any progress?Unfortunately, no. I asked Jeremy to step in because he did some work on *hp-wmi *that apparently won't work on your 4.8.0-xx kernel. Unless Jeremy has another thought, then I regret that I haven't any further suggestions.

---

### Post by grigorius0sol on 2017-02-28
I have an old HP notebook it does not work at all but has almost the same wifi  adapter. So I decided to replace WIFI adapter in HP pavilion with WIFI adapter from old notebook and WIFI is working now. [COLOR=#000000]Unfortunately wifi button still does not work :)

[/COLOR]By the way is there any possibility to configure my network adapters to be like eth0 for ethernet adapter and something like that for WIFI because now they are listed like this:
```

eno1      Link encap:Ethernet  HWaddr a0:d3:c1:63:3a:b7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:155145 errors:0 dropped:0 overruns:0 frame:0
          TX packets:155145 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:157984999 (157.9 MB)  TX bytes:157984999 (157.9 MB)


wlp7s0    Link encap:Ethernet  HWaddr e0:2a:82:52:10:46                                  <----------** this is WIFI**
          inet addr:192.168.1.114  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::3291:ec9a:6ba6:2292/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:88649 errors:0 dropped:0 overruns:0 frame:0
          TX packets:99875 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:77880563 (77.8 MB)  TX bytes:99504179 (99.5 MB)



```

This is a little bit annoying me.

---

### Post by jeremy31 on 2017-02-28
I think we can fix the names for you
```
sudo -H gedit /etc/default/grub
```
Scroll to the line that might read
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
Change this to 
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash net.ifnames=0"
```
Save, exit gedit, then
```
sudo update-grub
```

And then
```
sudo ln -s /dev/null /etc/systemd/network/99-default.link
```

Reboot and the ethernet should be eth0 and wifi should be wlan0

Your solution was a bit strange as I would have expected the replacement wifi card to be blocked.

---

### Post by grigorius0sol on 2017-03-01
Thanks a lot for your help. I was surprised about adapter replacement  by myself but it works :).

---

