---
title: "Kill Switch issue (?) with Intel 4965AGN"
date: 2008-08-02
forum: Networking &amp; Wireless
---

### Post by Creap on 2008-08-02
Hi.

I just bought a new [Titan A15]("http://www.zepto.com/Shop/Notebook.aspx?notebookid=990") laptop from Zepto Computers and I'm having some problems. I chose Intel 4965 AG/N, a wireless NIC that I thought would be well supported "out of the box" (see [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel)), but I can't seem to enable it. I cannot find any networks, knowing that my router works great with other computers and that there are several other networks in my vicinity. 

Here's some info:
> $ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11a  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


> $ lspci -v
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
	Subsystem: Intel Corporation Unknown device 1101
	Flags: fast devsel, IRQ 16
	Memory at d4100000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>


> $ sudo lshw -C network
---
  *-network               
       description: Ethernet interface
       product: 191 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 02
       serial: 00:1b:38:e2:b6:ed
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.2 duplex=full ip=192.168.1.100 latency=0 link=yes module=sis190 multicast=yes port=MII speed=100MB/s
  *-network **DISABLED**
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1d:e0:7b:56:79
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11a
Note that this says wmaster0, but iwconfig says that it's wlan0 that's used, right..?

Well, what I personally suspect is the problem is that I have a hardware switch on my laptop for WLAN, and a led to indicate when WLAN or Bluetooth is activated. I have never seen that led alight. When "turning" the switch the first time after a reboot, I get this in dmesg:
> [   96.353679] iwl4965: Radio disabled by HW RF Kill switch
[   96.353733] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[   96.367329] eth0: PHY reset until link up.

Switching it again back and forth, I only get > 
[   98.452569] atkbd.c: Unknown key pressed (translated set 2, code 0xf1 on isa0060/serio0).
[   98.452574] atkbd.c: Use 'setkeycodes e071 <keycode>' to make it known.
[   98.453086] atkbd.c: Unknown key released (translated set 2, code 0xf1 on isa0060/serio0).
[   98.453089] atkbd.c: Use 'setkeycodes e071 <keycode>' to make it known.
[   99.441153] eth0: PHY reset until link up.
[  101.312324] atkbd.c: Unknown key pressed (translated set 2, code 0xf1 on isa0060/serio0).
[  101.312330] atkbd.c: Use 'setkeycodes e071 <keycode>' to make it known.
[  101.314116] atkbd.c: Unknown key released (translated set 2, code 0xf1 on isa0060/serio0).

etc, etc.

Could I do some keymapping, or simply disable the switch all together, keeping the wireless on at all times?

Previously, I had problems getting it to show up anywhere at all, but installing linux-backports-modules-hardy solved that. Then, the network card didn't show up as DISABLED as it does now.

I'd be very, very grateful for any kind of help or hints, anything to get me started to do more research myself. Thanks.

---

### Post by Creap on 2008-08-02
Also; 
> $ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Network is down

$ sudo iwlist wmaster0 scan
wmaster0  Interface doesn't support scanning.

Wether my kill switch is on or off, and cat 5 connected or not.

&

> $ uname -a
Linux munin 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux


---

### Post by ajgreeny on 2008-08-02
This may not have anything to do with your problem but where did your kernel come from and what is the **munin** kernel?  Have you used something different to the usual ubuntu kernel, which is what I see from the **uname -a** command?

---

### Post by Creap on 2008-08-02
> **ajgreeny said:**
> This may not have anything to do with your problem but where did your kernel come from and what is the **munin** kernel?  Have you used something different to the usual ubuntu kernel, which is what I see from the **uname -a** command?
Munin is just the name of my computer... My kernel is from the upgrade manager.

---

### Post by ajgreeny on 2008-08-02
OK, thanks.  My computer is named ubuntu804, so I didn't realise the output would contain that in the line from **uname -a**.

---

### Post by Creap on 2008-08-14
I still have the same problem. I've also tried a solution for iwl3945 suggested in [another thread]("http://ubuntuforums.org/showthread.php?t=808516"): ```
sudo su
echo -e 'alias wlan0 iwl3945 \noptions iwl3945 disable_hw_scan=1' > /etc/modprobe.d/iwl3945
reboot
``` replacing iwl3945 with iwl4965 of course. That didn't help, so I removed /etc/modprobe.d/iwl4965 again. 

Now my dmesg says "iwl4965: Wait for START_ALIVE timeout after 2000ms." over and over again... All other commands used in the original post give the same results.

Plz help!#@

---

### Post by chili555 on 2008-08-14
Would you please open a terminal and do:```
sudo su
echo "0" > /sys/bus/pci/drivers/iwl4965/*/rf_kill
sudo lshw -C network
```Is you card still DISABLED? If not, can you configure and connect? If so, we can work out how to make this permanent.

---

### Post by Creap on 2008-08-15
> **chili555 said:**
> Would you please open a terminal and do:```
sudo su
echo "0" > /sys/bus/pci/drivers/iwl4965/*/rf_kill
sudo lshw -C network
```Is you card still DISABLED? If not, can you configure and connect? If so, we can work out how to make this permanent.
all commands worked without errors, but I still get the exact same results for lshw -C network as above, still DISABLED :-(

---

### Post by chili555 on 2008-08-15
I am running low on ideas, but here is another thing to try:```
sudo rmmod iwl4965
sudo modprobe iwl4965 disable=0
sudo lshw -C network
```Is your card still disabled?

---

### Post by Creap on 2008-08-18
> **chili555 said:**
> I am running low on ideas, but here is another thing to try:```
sudo rmmod iwl4965
sudo modprobe iwl4965 disable=0
sudo lshw -C network
```Is your card still disabled?
I'm afraid so, yes. :( Still the exact same results for lshw as above.

---

### Post by comradekingu on 2008-08-21
I dont know what did it in the end, but if you got a file called "rf_kill" in the root dir you can gedit from 0 to 1, and it will work.

I have done alot of small configurations, but most notably i installed windows on a partition i made with gparted livecd. (In windows i installed the wireless management program that turned on wireless radio in win.)
That made my ubuntu partition inactive, so i had to install grub with the bootcd. Then i made a windows addition in the grub bootloader menu.lst.

It is really easier to install windows first, and then ubuntu, but...
Its a COMPAL IFL90/91 laptop. The software switch isnt working, and the hardware switch has to be turned on.

---

### Post by Creap on 2008-08-22
> **comradekingu said:**
> I dont know what did it in the end, but if you got a file called "rf_kill" in the root dir you can gedit from 0 to 1, and it will work.
Hm, running *locate rf_kill* I didn't find anything, but in searching for rf_kill in the forums led me to /sys/class/net/wlan0/device where I changed 0 to 1 in the rf_kill file. I also tried *sudo modprobe ath_pci rfkill=0*. Neither of them changed my network from DISABLED.

I think dmesg reacted in some way, but I'm not sure exactly how.
```

[  751.089263] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 16
[  751.089331] PM: Writing back config space on device 0000:02:00.0 at offset 1 (was 180002, writing 100006)
[  753.087692] iwl4965: Wait for START_ALIVE timeout after 2000ms.
[  753.087765] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[  753.695283] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 16
.... etc

```
And then there's this: 
```

[  920.942563] iwl4965: **Error sending REPLY_CARD_STATE_CMD**: time out after 500ms.
[  920.973509] eth0: PHY reset until link up.
...
[  988.804482] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 16
[  988.804550] PM: Writing back config space on device 0000:02:00.0 at offset 1 (was 180002, writing 100006)
[  988.805115] iwl4965: **Radio disabled by SW RF kill (module parameter)**
[  988.805173] ACPI: PCI interrupt for device 0000:02:00.0 disabled

```
This SoftWare Kill (?) must be the change to "1" in rf_kill, right?

Do you think there's any point for me trying ndiswrapper instead?

---

### Post by comradekingu on 2008-08-23
diswrapper is just a bad solution because its a wrapper that uses the windows version of the intel driver on linux. There isnt a problem with the driver as its already in the kernel.

The problem is that FN+F2 doesnt work. In windows there is a program that manages the status, and maps fn+f2 to wireless radio killswitch settings.

Im sorry i cant nail the problem, because i tried lots of such things before getting it to work. Dont know if it was just that final thing that did it or a combination.

I dont have the laptop in my posession anymore, so i cant run checks on it eighter.

---

### Post by DynamicMastermind on 2008-09-26
I am also having this same issue with the killswitch or Fn+F2 not working.  I have a Compal FL92 laptop with the Intel 4965 AGN Wireless card.  Turning the killswitch off does disable the wireless but turning it back on does not reenable it.  I get the following errors in my messages log.

Sep 26 11:54:45 jaysens-laptop kernel: [  198.884501] atkbd.c: Unknown key pressed (translated set 2, code 0xf1 on isa0060/serio0).
Sep 26 11:54:45 jaysens-laptop kernel: [  198.884511] atkbd.c: Use 'setkeycodes e071 <keycode>' to make it known.

---

### Post by jasonkirk2006 on 2008-10-08
If lshw lists the card correctly, and MAC address is displayed alright (I mean not FF:FF:FF:FF:FF:FF) then why not try

```

sudo ifconfig eth1 up

```

I have a similar kill switch problem with my 3945 card. If MAC address is displayed OK, then this way produces positive results. Unfortunately, it does not always displays MAC address correctly.

---

