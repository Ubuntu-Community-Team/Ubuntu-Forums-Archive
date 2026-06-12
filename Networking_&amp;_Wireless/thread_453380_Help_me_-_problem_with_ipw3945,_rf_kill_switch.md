---
title: "Help me - problem with ipw3945, rf_kill switch"
date: 2007-05-24
forum: Networking &amp; Wireless
---

### Post by cdiem on 2007-05-24
EDIT - solved - look at the end of this thread.

=========================================================

I have an Fujitsu Siemens Amilo pro v3505 with an Intel card 3945abg. The problem is, it lists no device in the network manager. After running some strange commands, it gave me output, saying, that my Radio Frequency Kill Switch is On, and it should be turned off, for to make the networking work:

cdiem@cdiemst:~$ dmesg | grep -C 2 ipw
[   24.416000] ipw3945: Radio Frequency Kill Switch is On:
[   24.416000] Kill switch must be turned off for wireless networking to work.

Now, after searching the net, here's an excerpt from the specification of the driver:
===============================================================================
For the device level files, look in
	
	/sys/bus/pci/drivers/ipw3945/{PCI-ID}/

For example:
	/sys/bus/pci/drivers/ipw3945/0000:02:01.0

For the device level files, see /sys/bus/pci/drivers/ipw3945:

  rf_kill
	read - 
	0 = RF kill not enabled (radio on)
	1 = SW based RF kill active (radio off)
	2 = HW based RF kill active (radio off)
	3 = Both HW and SW RF kill active (radio off)

	write -
	0 = If SW based RF kill active, turn the radio back on
	1 = If radio is on, activate SW based RF kill

	NOTE: If you enable the SW based RF kill and then toggle the HW
  	based RF kill from ON -> OFF -> ON, the radio will NOT come back on
======================================================================
I tried the following:
sudo cat /sys/bus/pci/drivers/ipw3945/*/rf_kill
which resulted in a "2".
sudo echo 0 > /sys/bus/pci/drivers/ipw3945/*/rf_kill
This command would enable my wireless kill switch, if it would be software disabled (and would end my griefing). But, unlyckily, my rf_kill was enabled by hardware. 
Then, afterwards, when running the command: sudo cat /sys/bus/pci/drivers/ipw3945/*/rf_kill
it gives me a message "service temporarily unavailable". 
Am I doing something wrong?

Pressing a button, which I think is for the wireless, doesn't function, and it does not give me an error message (so that I could assign a value to the button with 'setkeycodes').

I'm out of ideas now; and I'm shouting out for help.

---

### Post by cdiem on 2007-05-24
Ok, I'm getting closer. Making the command:
dmesg | tail -n 10 gives me an error:

[  325.188000] atkbd.c: Unknown key pressed (translated set 2, code 0xd6 on isa0060/serio0).
[  325.188000] atkbd.c: Use 'setkeycodes e056 <keycode>' to make it known.
[  396.952000] ipw3945: Error sending STATISTICS_CMD: time out after 500ms.
[  397.464000] ipw3945: Error sending STATISTICS_CMD: time out after 500ms.
[  397.972000] ipw3945: Error sending STATISTICS_CMD: time out after 500ms.
[  398.472000] ipw3945: Error sending STATISTICS_CMD: time out after 500ms.
[  398.972000] ipw3945: Error sending STATISTICS_CMD: time out after 500ms.
[  399.484000] ipw3945: Error sending STATISTICS_CMD: time out after 500ms.
[  592.720000] atkbd.c: Unknown key released (translated set 2, code 0xe0 on isa0060/serio0).
[  592.720000] atkbd.c: Use 'setkeycodes e060 <keycode>' to make it known.

Now I have to find a way to set a value to this thing. Any ideas will be appreciated though :)

edited: parsing "sudo setkeycodes e060 210" and "sudo setkeycodes e056 211" does not map them! OMG!!!!
When trying afterwards "sudo dumpkeys", the values are still the same!!! Now I feel like I'm never going to make my wireless work.

edited: the right value (from hexadecimal to decimal) to be sent is: sudo setkeycodes e056 214 and sudo setkeycodes e060 224. But still, when afterwards pressing the button, it gives me the following message:
> cdiem@cdiemst:~$ dmesg | grep -C 2 ipw
[   22.524000] ieee80211: 802.11 data/management/control stack, 1.2.17
[   22.524000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   22.632000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
[   22.632000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   22.684000] NET: Registered protocol family 10
[   22.684000] lo: Disabled Privacy Extensions
--
[   22.712000] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 17 (level, low) -> IRQ 16
[   22.712000] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   22.716000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   22.832000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x12a0b1, caps: 0xa04713/0x204000
[   22.864000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
--
[   24.068000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[   24.068000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   24.800000] ipw3945: Max thermal spin reached
[   24.800000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[   34.568000] eth0: no IPv6 routers present
[   85.300000] ipw3945: Error sending LEDS_CMD: time out after 500ms.
[   86.060000] ipw3945: Radio Frequency Kill Switch is On:
[   86.060000] Kill switch must be turned off for wireless networking to work.
[  269.240000] EXT3 FS on sda1, internal journal

and also, "sudo dumpkeys" does not show anything special about these values (214 and 224). At least it does not give me an error message, that it cannot recognoze the buttons anymore (hooray!). 
The next step I'm going to try is going to be, trying to put a livecd with Ubuntu Edgy inside, and check if the wireless is being recognized (I could not remember well, but I think it was). If it is, I will try to install an older version of the driver (the one that comes with Edgy, I think, should be older than the one with Feisty) and check out if it works. Still, as I hate repeating myself, if someone knows a way to help me, I would appreciate ANY advice or suggestion here. Thanks in advance.

---

### Post by chili555 on 2007-05-25
Please try this:```
echo 0 | sudo tee /sys/bus/pci/drivers/ipw3945/*/rf_kill
```Let us know if this turns the kill switch off.

---

### Post by cdiem on 2007-05-26
Thank you for your answer, chili555. However, this does not turn the kill switch off:
> root@cdiemst:~# sudo echo 0 | sudo tee /sys/bus/pci/drivers/ipw3945/*/rf_kill
0
root@cdiemst:~# cat /sys/bus/pci/drivers/ipw3945/*/rf_kill
2
root@cdiemst:~# sudo echo 0 | sudo tee /sys/bus/pci/drivers/ipw3945/*/rf_kill
0
root@cdiemst:~# cat /sys/bus/pci/drivers/ipw3945/*/rf_kill
2

and 
> root@cdiemst:~# dmesg | grep -C 2 ipw
[   22.624000] sky2 0000:02:00.0: v1.13 addr 0xd2000000 irq 17 Yukon-EC Ultra (0xb4) rev 2
[   22.624000] sky2 eth0: addr 00:0a:e4:bb:48:f3
[   22.680000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
[   22.680000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   22.680000] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 17 (level, low) -> IRQ 16
[   22.680000] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   22.680000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   22.708000] sky2 eth0: enabling interface
[   22.708000] sky2 eth0: ram buffer 0K
--
[   24.376000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[   24.376000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   24.816000] ipw3945: Radio Frequency Kill Switch is On:
[   24.816000] Kill switch must be turned off for wireless networking to work.
[   26.044000] NET: Registered protocol family 17


When I find the time, I'm going to try 2 things now: 1. Upgrade the BIOS, as I was proposed to do by someone, who had the same laptop (and problem), and then try to fix it through the BIOS. 2. Try to install the previous version of the driver.

Thanks one more time, chili555, for answering to my asking for help.

---

### Post by goranpop on 2007-05-30
Hi,
I had the same problem on Fujitsu Siemens Amilo pro v3505 with an Intel card 3945abg.

Try to load fsam7400 modul:

modprobe fsam7400
echo 1 > /proc/driver/wireless/radio

This is it. Wireless led should turn on.
It also work with acerhk modul.


Let us know if this work for you

---

### Post by cdiem on 2007-05-31
YES! It worked! Thanks so much!
> root@cdiemst:~# dmesg | grep -C 2 ipw
[   24.004000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x12a0b1, caps: 0xa04713/0x204000
[   24.036000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[   24.100000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
[   24.100000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   24.104000] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 17 (level, low) -> IRQ 16
[   24.104000] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   24.104000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   24.148000] hda: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   24.148000] Uniform CD-ROM driver Revision: 3.20
--
[   27.008000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[   27.120000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   27.120000] ipw3945: Radio Frequency Kill Switch is On:
[   27.120000] Kill switch must be turned off for wireless networking to work.
[   28.696000] NET: Registered protocol family 17
--
[  235.804000] fsam7400: SW RF kill switch for Fujitsu Siemens Amilo M 7400, v0.4.0
[  235.804000] fsam7400: Copyright(c) 2004 zwobbl ;)
[  236.144000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[  236.392000] ADDRCONF(NETDEV_UP): eth1: link is not ready

At the very moment I am not in a wireless area, but this turned the kill switch! Thanks so much, goranpop! Really, I have almost given up the idea of having a wireless connection. Thank you!

---

### Post by darwin_te on 2007-07-16
Hi,

For 7.04 using the latest kernel 2.6.22, I found the following script responsible for setting rf_kill to 2 (hardware radio frequecny off):

/etc/init.d/acpi-support which called:
/usr/share/acpi-support/state-funcs

The script state-funcs checked /sys/class/net/$DEVICE/device/power/state, which has different directory structure in latest kernel, and will flag wireless state as disabled if not found, which in turn will set rf_kill to 2.

Just modify the script state-funcs and it will now work.

---

### Post by cdiem on 2007-07-16
Thanks very much, darwin_te; I have already solved this by the 2 lines from goranpop, 2 messages above:

modprobe fsam7400
echo 1 > /proc/driver/wireless/radio

But, it's nice to know there are also some other solutions to this problem. Thanks for the support one more time.

---

### Post by caffeneide on 2007-07-23
Hi, I've exactly the same problem on an Asus proj31 with an Intel PRO/Wireless 3945abg.  
I've tried with modprobe fsam4700, but /proc/driver/wireless/radio doesn't exist on my filesystem :(
Nothing to do with Fn + F2 and acpi deamon.
I'm a newbie...what exactly have I to to modify in /usr/share/acpi-support/state-funcs?
Please, help me.

thanks


-----------------------------
SOLVED

I've solved this problem, simply usign the phisical switch on my laptop (sorry, it's ludicrous)...

---

### Post by dracomordag on 2007-07-27
alright, my laptop has a hardware switch for wireless, and echo 1 > /proc/driver/wireless/radio returns "bash: /proc/driver/wireless/radio: No such file or directory"

what now?

---

