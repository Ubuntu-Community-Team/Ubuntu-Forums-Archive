---
title: "Wireless 3165 card problem (Ubuntu 16.04.3 LTS)"
date: 2018-01-14
forum: Networking &amp; Wireless
---

### Post by usides on 2018-01-14
Hello ubuntu community,
I would like kindly to ask your help regarding my issue with ubuntu and wifi.

I have a problem with Notebook Jumper EZbook 3 PRO.
On board it has Wireless 3165 card and I can't make it to work.

I found and tried a lot of different solutions but didn't find the answer.

I have a little bit other symptoms (than others with similar issues) and I hope you will help me to figure out how to fix it.

My actions:
1. I have a laptop with Win 10. Wifi works fine. Device manager shows that I have Intel dual-band wireless-ac-3165 card.
2. I decided to install Ubuntu as second system. I booted from usb disk and installed system as usual. From live-usb system wifi works perfectly without any problems.
3. I rebooted and logged to fresh system. Everything works fine.
4. I decided to update the system. apt-get update, apt-get upgrade...
5. reboot...
6. After reeboting I noticed the strange thing. Wifi is not working and if I press on connections in top-right corner I can see that wifi network sign continiously changes the status - device not ready/not managed (each second)..

Firs of all I tried this solution:
[https://askubuntu.com/questions/672700/how-can-i-install-intel-dual-band-wireless-ac-3165-drivers](https://askubuntu.com/questions/672700/how-can-i-install-intel-dual-band-wireless-ac-3165-drivers)

I downloaded drivers, replaced and renamed them. It didn't help.
I booted from live-usb to check the wifi connections and it worked again. So the problem appears only on installed system after update.
I tried to copy firmware from live-usb system and paste it to my /lib/firmware. It didn't help.
I tried to download official drivers from Intel web-site. The problem is still here.

I don't know what should I try else to solve the problem..

Some info from my laptop:

```
usides@usides-EZbook:~$ uname -a
Linux usides-EZbook 4.15.0-041500rc7-generic #201801072330 SMP Sun Jan 7 23:31:29 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

usides@usides-EZbook:~$ lspci
00:00.0 Host bridge: Intel Corporation Device 5af0 (rev 0b)
00:00.1 Signal processing controller: Intel Corporation Device 5a8c (rev 0b)
00:02.0 VGA compatible controller: Intel Corporation Device 5a85 (rev 0b)
00:0e.0 Audio device: Intel Corporation Device 5a98 (rev 0b)
00:0f.0 Communication controller: Intel Corporation Device 5a9a (rev 0b)
00:12.0 SATA controller: Intel Corporation Device 5ae3 (rev 0b)
00:14.0 PCI bridge: Intel Corporation Device 5ad7 (rev fb)
00:15.0 USB controller: Intel Corporation Device 5aa8 (rev 0b)
00:16.0 Signal processing controller: Intel Corporation Device 5aac (rev 0b)
00:16.1 Signal processing controller: Intel Corporation Device 5aae (rev 0b)
00:16.2 Signal processing controller: Intel Corporation Device 5ab0 (rev 0b)
00:16.3 Signal processing controller: Intel Corporation Device 5ab2 (rev 0b)
00:17.0 Signal processing controller: Intel Corporation Device 5ab4 (rev 0b)
00:17.1 Signal processing controller: Intel Corporation Device 5ab6 (rev 0b)
00:17.2 Signal processing controller: Intel Corporation Device 5ab8 (rev 0b)
00:17.3 Signal processing controller: Intel Corporation Device 5aba (rev 0b)
00:18.0 Signal processing controller: Intel Corporation Device 5abc (rev 0b)
00:18.1 Signal processing controller: Intel Corporation Device 5abe (rev 0b)
00:18.2 Signal processing controller: Intel Corporation Device 5ac0 (rev 0b)
00:18.3 Signal processing controller: Intel Corporation Device 5aee (rev 0b)
00:19.0 Signal processing controller: Intel Corporation Device 5ac2 (rev 0b)
00:19.1 Signal processing controller: Intel Corporation Device 5ac4 (rev 0b)
00:19.2 Signal processing controller: Intel Corporation Device 5ac6 (rev 0b)
00:1b.0 SD Host controller: Intel Corporation Device 5aca (rev 0b)
00:1c.0 SD Host controller: Intel Corporation Device 5acc (rev 0b)
00:1e.0 SD Host controller: Intel Corporation Device 5ad0 (rev 0b)
00:1f.0 ISA bridge: Intel Corporation Device 5ae8 (rev 0b)
00:1f.1 SMBus: Intel Corporation Broxton SMBus Controller (rev 0b)
01:00.0 Network controller: Intel Corporation Wireless 3165 (rev 81)

```

When I try command sudo lshw -C network
Each time it gives different output.

```
usides@usides-EZbook:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: Wireless 3165
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 81
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=iwlwifi latency=0
       resources: irq:127 memory:82100000-82101fff
usides@usides-EZbook:~$ sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: Wireless 3165
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlp1s0
       version: 81
       serial: 28:c6:3f:76:38:0b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.15.0-041500rc7-generic firmware=29.610311.0 latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:127 memory:82100000-82101fff

```

I suppose it has a connection with status of network that I mentioned above.


And dmesg | grep iwl

```
usides@usides-EZbook:~$ dmesg | grep iwl
[   83.648919] iwlwifi 0000:01:00.0: Cannot send HCMD of Phy DB non specific channel section
[   83.761767] iwlwifi 0000:01:00.0: loaded firmware version 29.610311.0 op_mode iwlmvm
[   83.761817] iwlwifi 0000:01:00.0: Detected Intel(R) Dual Band Wireless AC 3165, REV=0x210
[   83.782541] iwlwifi 0000:01:00.0: base HW address: 28:c6:3f:76:38:0b
[   83.842988] ieee80211 phy119: Selected rate control algorithm 'iwl-mvm-rs'
[   83.855480] iwlwifi 0000:01:00.0 wlp1s0: renamed from wlan0
[   83.984096] iwlwifi 0000:01:00.0: Microcode SW error detected.  Restarting 0x2000000.
[   83.984211] iwlwifi 0000:01:00.0: Start IWL Error Log Dump:
[   83.984217] iwlwifi 0000:01:00.0: Status: 0x00000100, count: 6
[   83.984222] iwlwifi 0000:01:00.0: Loaded firmware version: 29.610311.0
[   83.984228] iwlwifi 0000:01:00.0: 0x00002B12 | ADVANCED_SYSASSERT          
[   83.984233] iwlwifi 0000:01:00.0: 0x000002F0 | trm_hw_status0
[   83.984238] iwlwifi 0000:01:00.0: 0x00000000 | trm_hw_status1
[   83.984242] iwlwifi 0000:01:00.0: 0x00043D58 | branchlink2
[   83.984247] iwlwifi 0000:01:00.0: 0x0004B016 | interruptlink1
[   83.984251] iwlwifi 0000:01:00.0: 0x00000000 | interruptlink2
[   83.984256] iwlwifi 0000:01:00.0: 0x00000002 | data1
[   83.984261] iwlwifi 0000:01:00.0: 0x10000000 | data2
[   83.984265] iwlwifi 0000:01:00.0: 0xDEADBEEF | data3
[   83.984270] iwlwifi 0000:01:00.0: 0x00000000 | beacon time
[   83.984274] iwlwifi 0000:01:00.0: 0x00000649 | tsf low
[   83.984279] iwlwifi 0000:01:00.0: 0x00000000 | tsf hi
[   83.984284] iwlwifi 0000:01:00.0: 0x00000000 | time gp1
[   83.984288] iwlwifi 0000:01:00.0: 0x00000649 | time gp2
[   83.984293] iwlwifi 0000:01:00.0: 0x00000001 | uCode revision type
[   83.984298] iwlwifi 0000:01:00.0: 0x0000001D | uCode version major
[   83.984302] iwlwifi 0000:01:00.0: 0x00095007 | uCode version minor
[   83.984307] iwlwifi 0000:01:00.0: 0x00000210 | hw version
[   83.984312] iwlwifi 0000:01:00.0: 0x00C89200 | board version
[   83.984316] iwlwifi 0000:01:00.0: 0x0004016C | hcmd
[   83.984321] iwlwifi 0000:01:00.0: 0x00022080 | isr0
[   83.984325] iwlwifi 0000:01:00.0: 0x00000000 | isr1
[   83.984330] iwlwifi 0000:01:00.0: 0x00000002 | isr2
[   83.984334] iwlwifi 0000:01:00.0: 0x004000C0 | isr3
[   83.984339] iwlwifi 0000:01:00.0: 0x00000000 | isr4
[   83.984343] iwlwifi 0000:01:00.0: 0x0003016C | last cmd Id
[   83.984348] iwlwifi 0000:01:00.0: 0x00000000 | wait_event
[   83.984352] iwlwifi 0000:01:00.0: 0x00005A46 | l2p_control
[   83.984357] iwlwifi 0000:01:00.0: 0x00000000 | l2p_duration
[   83.984361] iwlwifi 0000:01:00.0: 0x00000000 | l2p_mhvalid
[   83.984366] iwlwifi 0000:01:00.0: 0x00000000 | l2p_addr_match
[   83.984370] iwlwifi 0000:01:00.0: 0x00000007 | lmpm_pmg_sel
[   83.984375] iwlwifi 0000:01:00.0: 0x29102230 | timestamp
[   83.984380] iwlwifi 0000:01:00.0: 0x00000010 | flow_handler
[   83.984460] iwlwifi 0000:01:00.0: iwlwifi transaction failed, dumping registers
[   83.984473] iwlwifi 0000:01:00.0: iwlwifi device config registers:
[   83.984534] iwlwifi 0000:01:00.0: 00000000: 31658086 00100406 02800081 00000000 82100004 00000000 00000000 00000000
[   83.984541] iwlwifi 0000:01:00.0: 00000020: 00000000 00000000 00000000 80108086 00000000 000000c8 00000000 000001ff
[   83.984546] iwlwifi 0000:01:00.0: iwlwifi device memory mapped registers:
[   83.984587] iwlwifi 0000:01:00.0: 00000000: 00c89200 0000ff40 00000000 ba00008b 00000000 00000000 00000000 00000000
[   83.984594] iwlwifi 0000:01:00.0: 00000020: 00000000 080403cd 00000210 d55555d5 00000000 d55555d5 80008040 00080044
[   83.984603] iwlwifi 0000:01:00.0: iwlwifi device AER capability structure:
[   83.984631] iwlwifi 0000:01:00.0: 00000000: 14010001 00000000 00000000 00462031 00000000 00002000 00000000 00000000
[   83.984636] iwlwifi 0000:01:00.0: 00000020: 00000000 00000000 00000000
[   83.984642] iwlwifi 0000:01:00.0: iwlwifi parent port (0000:00:14.0) config registers:
[   83.984666] iwlwifi 0000:00:14.0: 00000000: 5ad78086 00100407 060400fb 00810000 00000000 00000000 00010100 200000f0
[   83.984672] iwlwifi 0000:00:14.0: 00000020: 82108210 0001fff1 00000000 00000000 00000000 00000040 00000000 001002ff
[   83.984682] iwlwifi 0000:01:00.0: FW error in SYNC CMD PHY_DB_CMD
[   83.984737]  iwl_trans_pcie_send_hcmd+0x4fb/0x540 [iwlwifi]
[   83.984766]  iwl_trans_send_cmd+0x5c/0xc0 [iwlwifi]
[   83.984784]  iwl_send_phy_db_cmd+0xaf/0xe0 [iwlwifi]
[   83.984804]  iwl_send_phy_db_data+0xe2/0x200 [iwlwifi]
[   83.984822]  ? iwl_send_phy_db_data+0xe2/0x200 [iwlwifi]
[   83.984845]  iwl_mvm_up+0x200/0x950 [iwlmvm]
[   83.984922]  __iwl_mvm_mac_start+0x197/0x2d0 [iwlmvm]
[   83.984940]  iwl_mvm_mac_start+0x4a/0x110 [iwlmvm]
[   83.985281] iwlwifi 0000:01:00.0: Cannot send HCMD of Phy DB non specific channel section
[   84.205395] iwlwifi 0000:01:00.0: Microcode SW error detected.  Restarting 0x2000000.
[   84.205504] iwlwifi 0000:01:00.0: Start IWL Error Log Dump:
[   84.205507] iwlwifi 0000:01:00.0: Status: 0x00000110, count: 6
[   84.205510] iwlwifi 0000:01:00.0: Loaded firmware version: 29.610311.0
[   84.205513] iwlwifi 0000:01:00.0: 0x00002B12 | ADVANCED_SYSASSERT          
[   84.205516] iwlwifi 0000:01:00.0: 0x000002F0 | trm_hw_status0
[   84.205518] iwlwifi 0000:01:00.0: 0x00000000 | trm_hw_status1
[   84.205520] iwlwifi 0000:01:00.0: 0x00043D58 | branchlink2
[   84.205523] iwlwifi 0000:01:00.0: 0x0004B016 | interruptlink1
[   84.205525] iwlwifi 0000:01:00.0: 0x00000000 | interruptlink2
[   84.205527] iwlwifi 0000:01:00.0: 0x00000002 | data1
[   84.205529] iwlwifi 0000:01:00.0: 0x10000000 | data2
[   84.205532] iwlwifi 0000:01:00.0: 0xDEADBEEF | data3
[   84.205534] iwlwifi 0000:01:00.0: 0x00000000 | beacon time
[   84.205536] iwlwifi 0000:01:00.0: 0x000006A3 | tsf low
[   84.205538] iwlwifi 0000:01:00.0: 0x00000000 | tsf hi
[   84.205540] iwlwifi 0000:01:00.0: 0x00000000 | time gp1
[   84.205542] iwlwifi 0000:01:00.0: 0x000006A3 | time gp2
[   84.205545] iwlwifi 0000:01:00.0: 0x00000001 | uCode revision type
[   84.205547] iwlwifi 0000:01:00.0: 0x0000001D | uCode version major
[   84.205549] iwlwifi 0000:01:00.0: 0x00095007 | uCode version minor
[   84.205551] iwlwifi 0000:01:00.0: 0x00000210 | hw version
[   84.205553] iwlwifi 0000:01:00.0: 0x00C89200 | board version
[   84.205556] iwlwifi 0000:01:00.0: 0x0003016C | hcmd
[   84.205558] iwlwifi 0000:01:00.0: 0x00022080 | isr0
[   84.205560] iwlwifi 0000:01:00.0: 0x00000000 | isr1
[   84.205562] iwlwifi 0000:01:00.0: 0x00000002 | isr2
[   84.205564] iwlwifi 0000:01:00.0: 0x004000C0 | isr3
[   84.205566] iwlwifi 0000:01:00.0: 0x00000000 | isr4
[   84.205568] iwlwifi 0000:01:00.0: 0x0002016C | last cmd Id
[   84.205571] iwlwifi 0000:01:00.0: 0x00000000 | wait_event
[   84.205573] iwlwifi 0000:01:00.0: 0x00005A46 | l2p_control
[   84.205575] iwlwifi 0000:01:00.0: 0x00000000 | l2p_duration
[   84.205577] iwlwifi 0000:01:00.0: 0x00000000 | l2p_mhvalid
[   84.205579] iwlwifi 0000:01:00.0: 0x00000000 | l2p_addr_match
[   84.205581] iwlwifi 0000:01:00.0: 0x00000007 | lmpm_pmg_sel
[   84.205584] iwlwifi 0000:01:00.0: 0x29102230 | timestamp
[   84.205586] iwlwifi 0000:01:00.0: 0x00000010 | flow_handler
[   84.205590] iwlwifi 0000:01:00.0: Firmware error during reconfiguration - reprobe!
[   84.205645] iwlwifi 0000:01:00.0: FW error in SYNC CMD PHY_DB_CMD
and repeat the same info...
```

When I reboot or power off I see the same errors and laptop freezes, so I have to make the hard reset.

**Could you please tell me what I could try else to fix it?**

Thank you in advance.

---

### Post by chili555 on 2018-01-14
We see:> driverversion=[COLOR="#FF0000"]4.15.0-041500rc7[/COLOR]-generic I'm not sure we know what to suggest as you are running a 4.15-rc7 kernel. By definition, things may or may not work as expected in an rc kernel. Can you boot into a default Ubuntu kernel? Is the symptom the same?

What you have here is a firmware crash:> [   83.984096] iwlwifi 0000:01:00.0: Microcode SW error detected.  Restarting 0x2000000.
[   83.984211] iwlwifi 0000:01:00.0: Start IWL Error Log Dump:
[   83.984217] iwlwifi 0000:01:00.0: Status: 0x00000100, count: 6
[   83.984222] iwlwifi 0000:01:00.0: Loaded firmware version: 29.610311.0Whether it is the fault of the rc7 driver or the firmware you installed is unknown.

---

### Post by usides on 2018-01-15
chili555 big thank you for your help.
I reinstalled ubuntu from scratch and used 4.10.0-28-generic kernel.
I updated the system and with that kernel everything works perfectly.

Thank you!

---

### Post by chili555 on 2018-01-15
> and with that kernel everything works perfectly.As we suspected.

Glad it's working as expected. Have fun!

---

### Post by usides on 2018-01-25
Unfortunatelly the problem is not solved.
Today I noticed that Ubuntu Software had available OS update and I decided to update it.
After reboot my problem returned. The symptoms are the same as in my first post.
iwlwifi errors and other things...


I noticed that after OS update **uname -r** shows me that I have kernel **4.13.0-31-generic** instead **of 4.10.0-28-generic**.
Is it normal that my kernel was updated?

Is it normal that my kernel was updated?
I suppose that wireless-ac-3165 doesn't work with that kernel.


So the questions is:
How to install 4.10.0-28-generic kernel again and prohibit automatic update to new kernel?
GRUB is not working on this laptop so I use refind for dualboot. As I understood refind doesn't have options to boot from other kernels.

What can you advice?
Thank you in advance for help.

---

### Post by chili555 on 2018-01-25
> I suppose that wireless-ac-3165 doesn't work with that kernel.Before we jump to conclusions prematurely, let's see if the logs hold any interesting clues. Please run and post:```
dmesg | grep iwl
sudo dpkg -s linux-firmware
```

---

### Post by usides on 2018-01-26
Hi chili555,
Thank you for respond.
During my expectation of reply I managed to return the old kernel 4.10.0-28-generic.
As we know with that kernel everything works perfect.

A little off-topic for your understanding.
It's not possible to install ubuntu linux from live usb on my Jumper EZbook 3 PRO. 
The problem is GRUB. Internet is filled of info how to workaround it with refind boot manager. Using isorespin.sh from Linuxium ([http://linuxiumcomau.blogspot.com](http://linuxiumcomau.blogspot.com)) I was able to respin original iso and make it bootable on my laptop.

Yesterday I decided to find the way to return the old kernel.
The only way to boot from another kernel that I know is to use GRUB advanced options. I tried to manually instal GRUB and it was successful.

Then I deleted the new kernel with:
sudo apt-get purge linux-image-4.13.0-31-generic
sudo apt-get purge linux-headers-4.13.0-31-generic


After that Ubuntu Software doesn't show any available OS update.

Today I read your message and decided to install the new kernel again (hoping that we will find the way how to make wifi workable on newer kernels)

I tried to find 4.13.0-31-generic on [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
and wasn't able to do it.
The closest one is linux-image-4.13.0-041300-generic but it's not that kernel that got during automaical update.
So it's kind a confusion for me.

Anyway with automatic update I also got kernel 4.13.0-26-generic and used it to run commands that you adviced.

```
usides@usides-EZbook:~$ dmesg | grep iwl
[  276.063215]  __iwl_mvm_mac_start+0x28b/0x2f0 [iwlmvm]
[  276.063230]  ? __iwl_mvm_mac_start+0x28b/0x2f0 [iwlmvm]
[  276.063245]  iwl_mvm_mac_start+0x4a/0x130 [iwlmvm]
[  276.063439] iwlwifi 0000:01:00.0: Cannot send HCMD of Phy DB non specific channel section
[  276.199329] iwlwifi 0000:01:00.0: loaded firmware version 29.610311.0 op_mode iwlmvm
[  276.199405] iwlwifi 0000:01:00.0: Detected Intel(R) Dual Band Wireless AC 3165, REV=0x210
[  276.219752] iwlwifi 0000:01:00.0: base HW address: 28:c6:3f:76:38:0b
[  276.282026] ieee80211 phy392: Selected rate control algorithm 'iwl-mvm-rs'
[  276.295911] iwlwifi 0000:01:00.0 wlp1s0: renamed from wlan0
[  276.422717] iwlwifi 0000:01:00.0: Microcode SW error detected.  Restarting 0x2000000.
[  276.422838] iwlwifi 0000:01:00.0: Start IWL Error Log Dump:
[  276.422846] iwlwifi 0000:01:00.0: Status: 0x00000200, count: 6
[  276.422852] iwlwifi 0000:01:00.0: Loaded firmware version: 29.610311.0
[  276.422860] iwlwifi 0000:01:00.0: 0x00002B12 | ADVANCED_SYSASSERT          
[  276.422866] iwlwifi 0000:01:00.0: 0x000002F0 | trm_hw_status0
[  276.422872] iwlwifi 0000:01:00.0: 0x00000000 | trm_hw_status1
[  276.422878] iwlwifi 0000:01:00.0: 0x00043D58 | branchlink2
[  276.422884] iwlwifi 0000:01:00.0: 0x0004B016 | interruptlink1
[  276.422889] iwlwifi 0000:01:00.0: 0x00000000 | interruptlink2
[  276.422895] iwlwifi 0000:01:00.0: 0x00000002 | data1
[  276.422901] iwlwifi 0000:01:00.0: 0x10000000 | data2
[  276.422907] iwlwifi 0000:01:00.0: 0xDEADBEEF | data3
[  276.422912] iwlwifi 0000:01:00.0: 0x00000000 | beacon time
[  276.422918] iwlwifi 0000:01:00.0: 0x00000896 | tsf low
[  276.422924] iwlwifi 0000:01:00.0: 0x00000000 | tsf hi
[  276.422930] iwlwifi 0000:01:00.0: 0x00000000 | time gp1
[  276.422935] iwlwifi 0000:01:00.0: 0x00000897 | time gp2
[  276.422941] iwlwifi 0000:01:00.0: 0x00000001 | uCode revision type
[  276.422947] iwlwifi 0000:01:00.0: 0x0000001D | uCode version major
[  276.422953] iwlwifi 0000:01:00.0: 0x00095007 | uCode version minor
[  276.422959] iwlwifi 0000:01:00.0: 0x00000210 | hw version
[  276.422964] iwlwifi 0000:01:00.0: 0x00C89200 | board version
[  276.422970] iwlwifi 0000:01:00.0: 0x0004016C | hcmd
[  276.422976] iwlwifi 0000:01:00.0: 0x00022080 | isr0
[  276.422981] iwlwifi 0000:01:00.0: 0x00000000 | isr1
[  276.422987] iwlwifi 0000:01:00.0: 0x00000002 | isr2
[  276.422992] iwlwifi 0000:01:00.0: 0x004000C0 | isr3
[  276.422998] iwlwifi 0000:01:00.0: 0x00000000 | isr4
[  276.423004] iwlwifi 0000:01:00.0: 0x0003016C | last cmd Id
[  276.423009] iwlwifi 0000:01:00.0: 0x00000000 | wait_event
[  276.423015] iwlwifi 0000:01:00.0: 0x00005A46 | l2p_control
[  276.423021] iwlwifi 0000:01:00.0: 0x00000000 | l2p_duration
[  276.423026] iwlwifi 0000:01:00.0: 0x00000000 | l2p_mhvalid
[  276.423032] iwlwifi 0000:01:00.0: 0x00000000 | l2p_addr_match
[  276.423038] iwlwifi 0000:01:00.0: 0x00000007 | lmpm_pmg_sel
[  276.423044] iwlwifi 0000:01:00.0: 0x29102230 | timestamp
[  276.423049] iwlwifi 0000:01:00.0: 0x00000010 | flow_handler
[  276.423206] iwlwifi 0000:01:00.0: FW error in SYNC CMD PHY_DB_CMD
[  276.423282]  iwl_trans_pcie_send_hcmd+0x435/0x540 [iwlwifi]
[  276.423319]  iwl_trans_send_cmd+0x4e/0xd0 [iwlwifi]
[  276.423342]  iwl_send_phy_db_cmd+0xaf/0xe0 [iwlwifi]
[  276.423366]  iwl_send_phy_db_data+0xdf/0x200 [iwlwifi]
[  276.423388]  ? iwl_send_phy_db_data+0xdf/0x200 [iwlwifi]
[  276.423415]  ? iwl_send_tx_ant_cfg+0x5d/0x80 [iwlmvm]
[  276.423438]  iwl_mvm_up+0x2eb/0xe70 [iwlmvm]
[  276.423478]  __iwl_mvm_mac_start+0x28b/0x2f0 [iwlmvm]
[  276.423507]  ? __iwl_mvm_mac_start+0x28b/0x2f0 [iwlmvm]
[  276.423532]  iwl_mvm_mac_start+0x4a/0x130 [iwlmvm]
...


Package: linux-firmware
Status: install ok installed
Priority: optional
Section: misc
Installed-Size: 207883
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: all
Multi-Arch: foreign
Version: 1.157.15
Replaces: atmel-firmware, linux-firmware-snapdragon (<= 1.2-0ubuntu1), linux-restricted-common
Provides: atmel-firmware
Breaks: linux-firmware-snapdragon (<= 1.2-0ubuntu1)
Conflicts: atmel-firmware
Description: Firmware for Linux kernel drivers
 This package provides firmware used by Linux kernel drivers.

```

---

