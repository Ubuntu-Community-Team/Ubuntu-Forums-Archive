---
title: "IPW2200 troubles, Ubuntu 5.10, dell 9200"
date: 2005-11-25
forum: Networking &amp; Wireless
---

### Post by eclsnowman on 2005-11-25
Hello,

I have been running my head into a wall for a week now on this and I am on the verge of giving up. As I said in the title I have a dell Inspiron 9200 with an Intel pro 2200 b/g card. All the forums I read say "it works right out of the box"... and I hate all those people. I am on the verge of going back to windows and saying the hell with it if I can't even get a wireless card to work. PLEASE help me regain confidence that Linux is for me. Below is all the information I can think of to help someone understand my configuration:

**iwconfig** yields:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:"snowman"
          Mode:Managed  Channel:0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power=off
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

**sudo iwlist eth1 scan** yields:
eth1      No scan results

**lspci** yields:
0000:00:00.0 Host bridge: Intel Corp. 82855PM Processor to I/O Controller (rev 0 3)
0000:00:01.0 PCI bridge: Intel Corp. 82855PM Processor to AGP Controller (rev 03 )
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) US B UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) US B UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) US B UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 01)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Contro ller (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4 -L/ICH4-M) AC'97 Audio Controller (rev 01)
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem  Controller (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Rad eon 9600 M10]
0000:02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (re v 02)
0000:02:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
0000:02:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev  08)
0000:02:01.2 0805: Ricoh Co Ltd: Unknown device 0822 (rev 17)
0000:02:03.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)

**/var/log/dmesg** contains this:

[4294698.344000] ieee80211_crypt: registered algorithm 'NULL'
[4294698.348000] ieee80211: 802.11 data/management/control stack, 1.0.3
[4294698.348000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[4294698.355000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
[4294698.355000] ipw2200: Copyright(c) 2003-2004 Intel Corporation
[4294698.357000] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
[4294698.358000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[4294698.872000] ipw2200: Radio Frequency Kill Switch is On:
[4294698.872000] Kill switch must be turned off for wireless networking to work.
[4294699.486000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[344fc00005b200e1]
[4294700.293000] Real Time Clock Driver v1.12
[4294700.340000] input: PC Speaker
[4294701.052000] NET: Registered protocol family 17
[4294702.040000] b44: eth0: Link is down.
[4294704.040000] b44: eth0: Link is up at 100 Mbps, full duplex.
[4294704.040000] b44: eth0: Flow control is on for TX and on for RX.
[4294712.851000] ipw2200: failed to send WEP_KEY command
[4294713.246000] NET: Registered protocol family 10
[4294713.246000] Disabled Privacy Extensions on device c02eb280(lo)
[4294713.248000] IPv6 over IPv4 tunneling driver

I think [4294698.872000] is where I have the problem but I cannot figure it out. I have also tried hitting Fn-F2 to turn the wireless card on and off, and played with the bios to make sure it is turning the card on.  PLEASE HELP.

---

### Post by eclsnowman on 2005-11-25
I played around some more and

**/sys/bus/pci/drivers/ipw2200/*/rf_kill** Yields:
0

Which I think is correct

Now **dmesg** reads:
[4294701.072000] ieee80211_crypt: registered algorithm 'NULL'
[4294701.075000] ieee80211: 802.11 data/management/control stack, 1.0.3
[4294701.075000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[4294701.083000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
[4294701.083000] ipw2200: Copyright(c) 2003-2004 Intel Corporation
[4294701.085000] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
[4294701.085000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[4294702.213000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[344fc00005b200e1]
[4294702.913000] Real Time Clock Driver v1.12
[4294702.955000] input: PC Speaker
[4294703.737000] NET: Registered protocol family 17
[4294704.725000] b44: eth0: Link is down.
[4294706.725000] b44: eth0: Link is up at 100 Mbps, full duplex.
[4294706.725000] b44: eth0: Flow control is on for TX and on for RX.
[4294776.221000] NET: Registered protocol family 10
[4294776.221000] Disabled Privacy Extensions on device c02eb280(lo)
[4294776.223000] IPv6 over IPv4 tunneling driver

but I still cannot connect with wep on or off on the router.

---

### Post by Lambert on 2005-11-25
1. After your last change were you able to run the iwlist ... scan command and get output?

The radio off in your first post when you ran iwconfig shows a problem

---

### Post by eclsnowman on 2005-11-26
**sudo iwlist eth1 scan** Yields:

eth1      Scan completed :
          Cell 01 - Address: 00:12:17:1A:FB:31
                    ESSID:"snowman"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rate:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=86/100  Signal level=-44 dBm
                    Extra: Last beacon: 53ms ago
          Cell 02 - Address: 00:0F:3D:43:8E:3C
                    ESSID:"default"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rate:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=35/100  Signal level=-79 dBm
                    Extra: Last beacon: 121ms ago
          Cell 03 - Address: 00:0F:B5:A8:C5:AC
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rate:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 9 11 6 12 18 24 36 48 54
                    Quality=51/100  Signal level=-70 dBm
                    Extra: Last beacon: 6608ms ago

But I still cannot connect. I was also wondering why it shows up as eth1 instead of wlan0? Does that matter?

---

### Post by eclsnowman on 2005-11-26
**sudo iwconfig eth1** Yields:

eth1      unassociated  ESSID:"snowman"
          Mode:Managed  Channel=0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:XXXX-XXXX-XXXX-XXXX-XXXX-XXXX-XX   Security mode:open
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I changed the encription key here for security, thats why it is all X's. Does this tell me anything?

---

### Post by Lambert on 2005-11-26
Let's try this

```
sudo iwconfig eth1 freq 2.437G essid snowman ap 00:12:17:1A:FB:31 key <see examples below> commit
``` 
 key 0123-4567-89   
 key [3] 0123-4567-89 (if you can specify a certain key such as key # 3 here)
 key s:password [2] (if using an ascii key use this [2] identifies key #
 key restricted [3] 0123456789 (same as above except it addes restricted setting)

If you can't get this working, turn wep off and just remove the key part of the command and see if you can connect.

One thing I noticed in the last iwconfig was the channel. The device is not set up to a channel/frequency.

the eth1 is just an alias used so when actions are made the os knows what device to apply it to. So it doesn't matter the exact phrase.

---

### Post by eclsnowman on 2005-11-26
So I disabled wep, and now I get this

**sudo iwconfig eth1** Yields:

eth1      IEEE 802.11g  ESSID:"snowman"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:17:1A:FB:31
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:6D84-9399-AAFF-015C-FEBA-D766-63   Security mode:open
          Power Management:off
          Link Quality=85/100  Signal level=-45 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

And I get my network icons to look like the image below. But I still cannot connect to the internet. Is there a better wifi manager for gnome that I should be using? Should I configure my interfaces file differently?

---

### Post by Lambert on 2005-11-26
You can post your /etc/network/interfaces file here and we'll check to see if something there needs to change. You can blank out any personal data. essid and encryption key.

Also run ifconfig to see if the device is being assigned an ip address. Second line on the device should look like this.

inet addr:192.168.8.13  Bcast:192.168.255.255  Mask:255.255.0.0


Are you using dhcp or static ip addressing?

For wep are you using open or shared setting? hexadecimal or ascii key?

---

