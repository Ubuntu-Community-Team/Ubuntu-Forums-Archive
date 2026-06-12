---
title: "Intel Wireless N 7260 on the HP Spectre 13 x2"
date: 2013-11-20
forum: Networking &amp; Wireless
---

### Post by pgratz on 2013-11-20
I was wondering if anyone has had luck with this card.  I've installed Ubuntu 13.10 ([Trials and tribulations here]("http://cesg.tamu.edu/faculty/paul-gratz/personal/linux-on-the-hp-spectre-13-x2/")), and one part I remain stuck on is getting the WIFI working. 
I've tried the backports trick as well as putting the new version of the firmware in /lib/firmware but so far no luck.  Here is what dmesg says:

```
[ 2000.775131] cfg80211: Calling CRDA to update world regulatory domain
[ 2000.780019] Intel(R) Wireless WiFi driver for Linux, in-tree:d
[ 2000.780023] Copyright(c) 2003-2013 Intel Corporation
[ 2000.780147] iwlwifi 0000:07:00.0: can't disable ASPM; OS doesn't have ASPM control
[ 2000.780222] iwlwifi 0000:07:00.0: irq 62 for MSI/MSI-X
[ 2000.782295] cfg80211: World regulatory domain updated:
[ 2000.782299] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2000.782302] cfg80211:   (2402000 KHz - 2472000 KHz @ 40 
[ 2000.782304] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2000.782305] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2000.782307] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2000.782308] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2000.782324] iwlwifi 0000:07:00.0: loaded firmware version 22.0.7.0 op_mode iwlmvm
[ 2000.789097] iwlwifi 0000:07:00.0: Detected Intel(R) Wireless N 7260, REV=0x144
[ 2000.789244] iwlwifi 0000:07:00.0: L1 Disabled; Enabling L0S
[ 2000.789391] iwlwifi 0000:07:00.0: L1 Disabled; Enabling L0S
[ 2000.983776] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[ 2000.996547] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready



```

When I load the driver but I can't seem to get the WIFI to work.  Any help appreciated...
Paul

---

### Post by chili555 on 2013-11-20
Let's see: ```
modinfo iwlwifi | grep -e 7260 -e version
```

---

### Post by pgratz on 2013-12-13
Sorry for the very long turn around, I got tied up with work things. 

In any event, following a few steps I [detail here, I was able to get WIFI sort-of 1/2 working]("http://cesg.tamu.edu/faculty/paul-gratz/personal/linux-on-the-hp-spectre-13-x2/").  As things stand, I can get a somewhat flaky connection working with wpa_supplicant on the command line (though every so often I have to manually reload the iwlwifi modules).  NM does not allow me to "enable wireless" so wifi does not work at all from there.

Here is the answer to your request:

pgratz@pgratz-HP-Spectre-13-x2:~$ modinfo iwlwifi | grep -e 7260 -e version
version:        backported from Linux (v3.11-rc3-0-g5ae90d8) using backports v3.11-rc3-1-0-g4e81a94
version:        in-tree:d
firmware:       iwlwifi-7260-7.ucode
srcversion:     C4366A0CF1E51EBA83BE0A1
vermagic:       3.11.0-14-generic SMP mod_unload modversions

---

### Post by pgratz on 2013-12-13
By the way, I'm not sure if this is related to the WIFI flakiness but I notice these messages in DMESG:
```

[ 2237.121144] iwlwifi 0000:07:00.0: Microcode SW error detected.  Restarting 0x2000000.
[ 2237.121159] iwlwifi 0000:07:00.0: CSR values:
[ 2237.121166] iwlwifi 0000:07:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[ 2237.121176] iwlwifi 0000:07:00.0:        CSR_HW_IF_CONFIG_REG: 0X00489204
[ 2237.121184] iwlwifi 0000:07:00.0:          CSR_INT_COALESCING: 0X0000ff40
[ 2237.121192] iwlwifi 0000:07:00.0:                     CSR_INT: 0X00000000
[ 2237.121200] iwlwifi 0000:07:00.0:                CSR_INT_MASK: 0X00000000
[ 2237.121208] iwlwifi 0000:07:00.0:           CSR_FH_INT_STATUS: 0X00000000
[ 2237.121216] iwlwifi 0000:07:00.0:                 CSR_GPIO_IN: 0X00000000
[ 2237.121224] iwlwifi 0000:07:00.0:                   CSR_RESET: 0X00000000
[ 2237.121232] iwlwifi 0000:07:00.0:                CSR_GP_CNTRL: 0X080403c5
[ 2237.121240] iwlwifi 0000:07:00.0:                  CSR_HW_REV: 0X00000144
[ 2237.121247] iwlwifi 0000:07:00.0:              CSR_EEPROM_REG: 0X00000000
[ 2237.121255] iwlwifi 0000:07:00.0:               CSR_EEPROM_GP: 0X80000000
[ 2237.121263] iwlwifi 0000:07:00.0:              CSR_OTP_GP_REG: 0X803a0000
[ 2237.121271] iwlwifi 0000:07:00.0:                 CSR_GIO_REG: 0X00080044
[ 2237.121279] iwlwifi 0000:07:00.0:            CSR_GP_UCODE_REG: 0X00000000
[ 2237.121286] iwlwifi 0000:07:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[ 2237.121294] iwlwifi 0000:07:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[ 2237.121301] iwlwifi 0000:07:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[ 2237.121309] iwlwifi 0000:07:00.0:                 CSR_LED_REG: 0X00000060
[ 2237.121317] iwlwifi 0000:07:00.0:        CSR_DRAM_INT_TBL_REG: 0X8808b715
[ 2237.121324] iwlwifi 0000:07:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[ 2237.121332] iwlwifi 0000:07:00.0:             CSR_ANA_PLL_CFG: 0Xd55555d5
[ 2237.121340] iwlwifi 0000:07:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[ 2237.121347] iwlwifi 0000:07:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0010
[ 2237.121353] iwlwifi 0000:07:00.0: FH register values:
[ 2237.121370] iwlwifi 0000:07:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X1582d400
[ 2237.121387] iwlwifi 0000:07:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X0156d3c0
[ 2237.121403] iwlwifi 0000:07:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000068
[ 2237.121420] iwlwifi 0000:07:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X00801114
[ 2237.121436] iwlwifi 0000:07:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[ 2237.121453] iwlwifi 0000:07:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X03030000
[ 2237.121470] iwlwifi 0000:07:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[ 2237.121486] iwlwifi 0000:07:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[ 2237.121503] iwlwifi 0000:07:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[ 2237.121619] iwlwifi 0000:07:00.0: Start IWL Error Log Dump:
[ 2237.121625] iwlwifi 0000:07:00.0: Status: 0x00000000, count: 6
[ 2237.121632] iwlwifi 0000:07:00.0: 0x0000003C | NMI_INTERRUPT_DATA_ACTION_PT
[ 2237.121638] iwlwifi 0000:07:00.0: 0x00000230 | uPc
[ 2237.121643] iwlwifi 0000:07:00.0: 0x00000000 | branchlink1
[ 2237.121648] iwlwifi 0000:07:00.0: 0x00000C8A | branchlink2
[ 2237.121653] iwlwifi 0000:07:00.0: 0x00014078 | interruptlink1
[ 2237.121658] iwlwifi 0000:07:00.0: 0x00000676 | interruptlink2
[ 2237.121663] iwlwifi 0000:07:00.0: 0x00000D40 | data1
[ 2237.121668] iwlwifi 0000:07:00.0: 0x00000008 | data2
[ 2237.121673] iwlwifi 0000:07:00.0: 0x03030000 | data3
[ 2237.121678] iwlwifi 0000:07:00.0: 0x11C17BCE | beacon time
[ 2237.121683] iwlwifi 0000:07:00.0: 0xB5CBA42D | tsf low
[ 2237.121688] iwlwifi 0000:07:00.0: 0x000000C0 | tsf hi
[ 2237.121693] iwlwifi 0000:07:00.0: 0x00000000 | time gp1
[ 2237.121698] iwlwifi 0000:07:00.0: 0x006D5C44 | time gp2
[ 2237.121702] iwlwifi 0000:07:00.0: 0x00000000 | time gp3
[ 2237.121707] iwlwifi 0000:07:00.0: 0x00321600 | uCode version
[ 2237.121712] iwlwifi 0000:07:00.0: 0x00000144 | hw version
[ 2237.121717] iwlwifi 0000:07:00.0: 0x00489204 | board version
[ 2237.121722] iwlwifi 0000:07:00.0: 0x02C0001C | hcmd
[ 2237.121727] iwlwifi 0000:07:00.0: 0xA6F62000 | isr0
[ 2237.121731] iwlwifi 0000:07:00.0: 0x01004000 | isr1
[ 2237.121736] iwlwifi 0000:07:00.0: 0x0000000A | isr2
[ 2237.121741] iwlwifi 0000:07:00.0: 0x4041FC85 | isr3
[ 2237.121746] iwlwifi 0000:07:00.0: 0x00000000 | isr4
[ 2237.121751] iwlwifi 0000:07:00.0: 0x10800112 | isr_pref
[ 2237.121755] iwlwifi 0000:07:00.0: 0x00000D40 | wait_event
[ 2237.121760] iwlwifi 0000:07:00.0: 0x000000D0 | l2p_control
[ 2237.121765] iwlwifi 0000:07:00.0: 0x00010030 | l2p_duration
[ 2237.121770] iwlwifi 0000:07:00.0: 0x0000003F | l2p_mhvalid
[ 2237.121775] iwlwifi 0000:07:00.0: 0x000000CE | l2p_addr_match
[ 2237.121780] iwlwifi 0000:07:00.0: 0x00000007 | lmpm_pmg_sel
[ 2237.121785] iwlwifi 0000:07:00.0: 0xE3A4BB1E | timestamp
[ 2237.121790] iwlwifi 0000:07:00.0: 0x00346878 | flow_handler
[ 2237.121798] ieee80211 phy2: Hardware restart was requested
[ 2237.122159] iwlwifi 0000:07:00.0: L1 Disabled; Enabling L0S
[ 2237.122311] iwlwifi 0000:07:00.0: L1 Disabled; Enabling L0S
[ 2237.131967] iwlwifi 0000:07:00.0: Failed to create debugfs directory under netdev:wlan0



```

---

### Post by chili555 on 2013-12-14
> Microcode SW error detected. Let's start there. Let's check a few things first:```
lspci -nn | grep 0280
ls -al /lib/firmware  | grep 7260
cat /etc/network/interfaces
cat /etc/NetworkManager/NetworkManager.conf
```Ideally, we will see:> -rw-r--r--  1 root root  682892 Jul 10 10:59 iwlwifi-7260-7.ucodeThat is, readable by all, owned by root and sized 682892.

We'll try to fix up Network Manager so it takes care of all these details for us.

I'm pretty sure that compiling the driver from backports is unnecessary in Ubuntu 13.10. You are, in effect, backporting the driver from 3.11:> using backports v3.11-rc3-1-0-g4e81a94...to a system running 3.11 already:>  3.11.0-14-genericI actually think your underlying issue is NM or else iwlwifi's notorious difficulty with 802.11N. We shall see!

---

### Post by pgratz on 2013-12-14
Thanks for the quick response, here are the answers to your questions:

```

root@pgratz-HP-Spectre-13-x2:~# lspci -nn | grep 0280
07:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 73)
root@pgratz-HP-Spectre-13-x2:~# ls -al /lib/firmware  | grep 7260
-rw-r--r--  1 root root  682892 Nov 19 00:08 iwlwifi-7260-7.ucode
root@pgratz-HP-Spectre-13-x2:~# cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
root@pgratz-HP-Spectre-13-x2:~# cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false
root@pgratz-HP-Spectre-13-x2:~# 



```

Incidentally, trying more things I've upgraded the kernel to the following:

```

root@pgratz-HP-Spectre-13-x2:~# uname -a
Linux pgratz-HP-Spectre-13-x2 3.12.5-031205-generic #201312120254 SMP Thu Dec 12 07:55:20 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux



```

But still I see the firmware errors and NM won't allow me to enable wireless. 
Paul

---

### Post by pgratz on 2013-12-14
A couple more data points.  When I click on the NM widget in kde (I run kubuntu) and I try to "enable wireless" the check mark will set and then immediately unset. Here are the messages that show up in syslog:

```

Dec 14 14:56:29 pgratz-HP-Spectre-13-x2 NetworkManager[1387]: <info> rfkill6: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1c.3/0000:07:00.0/ieee8
0211/phy1/rfkill6) (driver iwlwifi)
Dec 14 14:56:29 pgratz-HP-Spectre-13-x2 NetworkManager[1387]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:07:00.0/net/wlan0,
 iface: wlan0)
Dec 14 14:56:29 pgratz-HP-Spectre-13-x2 NetworkManager[1387]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:07:00.0/net/wlan0, 
iface: wlan0): no ifupdown configuration found.
Dec 14 14:56:29 pgratz-HP-Spectre-13-x2 kernel: [  911.142999] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec 14 14:56:29 pgratz-HP-Spectre-13-x2 NetworkManager[1387]: <info> (wlan0): using nl80211 for WiFi device control
Dec 14 14:56:29 pgratz-HP-Spectre-13-x2 NetworkManager[1387]: <info> (wlan0): driver supports Access Point (AP) mode
Dec 14 14:56:29 pgratz-HP-Spectre-13-x2 NetworkManager[1387]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlwifi' ifindex: 3)
Dec 14 14:56:29 pgratz-HP-Spectre-13-x2 NetworkManager[1387]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Dec 14 14:56:29 pgratz-HP-Spectre-13-x2 NetworkManager[1387]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 14 14:56:29 pgratz-HP-Spectre-13-x2 NetworkManager[1387]: <info> (wlan0): preparing device.
Dec 14 14:56:29 pgratz-HP-Spectre-13-x2 NetworkManager[1387]: <info> (wlan0): deactivating device (reason 'managed') [2]
Dec 14 14:56:29 pgratz-HP-Spectre-13-x2 whoopsie[1639]: offline
Dec 14 14:56:31 pgratz-HP-Spectre-13-x2 kernel: [  912.975155] wlan0: authenticate with 20:4e:7f:7a:dd:00
Dec 14 14:56:31 pgratz-HP-Spectre-13-x2 kernel: [  912.976536] wlan0: direct probe to 20:4e:7f:7a:dd:00 (try 1/3)
Dec 14 14:56:31 pgratz-HP-Spectre-13-x2 kernel: [  913.180722] wlan0: send auth to 20:4e:7f:7a:dd:00 (try 2/3)
Dec 14 14:56:31 pgratz-HP-Spectre-13-x2 kernel: [  913.182701] wlan0: authenticated
Dec 14 14:56:31 pgratz-HP-Spectre-13-x2 kernel: [  913.183836] wlan0: associate with 20:4e:7f:7a:dd:00 (try 1/3)
Dec 14 14:56:31 pgratz-HP-Spectre-13-x2 kernel: [  913.190047] wlan0: RX AssocResp from 20:4e:7f:7a:dd:00 (capab=0x431 status=0 aid=5)
Dec 14 14:56:31 pgratz-HP-Spectre-13-x2 kernel: [  913.193236] wlan0: associated
Dec 14 14:56:31 pgratz-HP-Spectre-13-x2 kernel: [  913.193321] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Dec 14 14:56:32 pgratz-HP-Spectre-13-x2 kernel: [  914.309198] wlan0: deauthenticating from 20:4e:7f:7a:dd:00 by local choice (reason=3)
Dec 14 14:56:32 pgratz-HP-Spectre-13-x2 NetworkManager[1387]: <info> wpa_supplicant stopped
Dec 14 14:56:32 pgratz-HP-Spectre-13-x2 kernel: [  914.312089] cfg80211: Calling CRDA to update worl

```

BTW, it necessary, I have no problem with just using 802.11a/b/g instead of n. 
Thanks!
Paul

---

### Post by pgratz on 2013-12-14
BTW, before the backports I could not get anything to work at all.  The WIFI indicator light would oscillate between white (working) and orange (killswitch on).  After backports and with the newer kernels, it does not do that (no idea why though...).
Paul

---

### Post by chili555 on 2013-12-14
> [  913.180722] wlan0: send auth to 20:4e:7f:7a:dd:00 (try 2/3)
[  913.182701] wlan0: authenticated
[  913.183836] wlan0: associate with 20:4e:7f:7a:dd:00 (try 1/3)
[  913.190047] wlan0: RX AssocResp from 20:4e:7f:7a:dd:00 (capab=0x431 status=0 aid=5)
[  913.193236] wlan0: associated
[  913.193321] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  914.309198] wlan0: deauthenticating from 20:4e:7f:7a:dd:00 by local choice (reason=3)Well, for approximately 1.1 seconds, you were actually connected. 

Your settings above look just fine; there is nothing I'd change or that looks debilitating. 

Is the ethernet connected as you are doing all this? NM will prefer ethernet and disable wireless. If so, detach the ethernet, wait a few moments and try to enable wireless in NM again. Are you using Wicd, by chance?

---

### Post by pgratz on 2013-12-14
No, actually the laptop doesn't even have a wired ethernet port, though I do have a workable USB-wired ethernet dongle that I use from time to time.  Actually, to get on WIFI with it I have written a small script that manually runs wpa_supplicant with a hand written config file for my WIFI AP, it then runs dhclient to get connected.  If you like I can put that up here. 

When I run that I get the firmware errors you see in my posts above but I can get connected.  I sometimes drops packets though and every so often just stops working and I have to remove the iwlwifi and iwlnvm modules and then reinstall them to get WIFI working again.
Paul

---

### Post by pgratz on 2013-12-14
Incidentally, just to make sure it wasn't my script screwing up NM, I booted clean and tried to enable wireless.  Same behavior, here is what syslog says:

```

Dec 14 20:18:28 pgratz-HP-Spectre-13-x2 NetworkManager[1415]: <info> (wlan0): bringing up device.
Dec 14 20:18:28 pgratz-HP-Spectre-13-x2 kernel: [   37.862510] iwlwifi 0000:07:00.0: L1 Disabled; Enabling L0S
Dec 14 20:18:28 pgratz-HP-Spectre-13-x2 kernel: [   37.862665] iwlwifi 0000:07:00.0: L1 Disabled; Enabling L0S
Dec 14 20:18:28 pgratz-HP-Spectre-13-x2 kernel: [   37.872653] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec 14 20:18:29 pgratz-HP-Spectre-13-x2 NetworkManager[1415]: <info> WiFi hardware radio set enabled
Dec 14 20:18:29 pgratz-HP-Spectre-13-x2 NetworkManager[1415]: <info> WiFi now enabled by radio killswitch
Dec 14 20:18:29 pgratz-HP-Spectre-13-x2 NetworkManager[1415]: <info> (wlan0) supports 5 scan SSIDs
Dec 14 20:18:29 pgratz-HP-Spectre-13-x2 NetworkManager[1415]: <warn> Trying to remove a non-existant call id.
Dec 14 20:18:29 pgratz-HP-Spectre-13-x2 NetworkManager[1415]: <info> (wlan0): supplicant interface state: starting -> ready
Dec 14 20:18:29 pgratz-HP-Spectre-13-x2 NetworkManager[1415]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Dec 14 20:18:29 pgratz-HP-Spectre-13-x2 NetworkManager[1415]: <info> (wlan0): supplicant interface state: ready -> inactive
Dec 14 20:18:29 pgratz-HP-Spectre-13-x2 NetworkManager[1415]: <info> (wlan0) supports 5 scan SSIDs
Dec 14 20:18:29 pgratz-HP-Spectre-13-x2 wpa_supplicant[1479]: rfkill: WLAN soft blocked
Dec 14 20:18:29 pgratz-HP-Spectre-13-x2 NetworkManager[1415]: <info> WiFi now disabled by radio killswitch
Dec 14 20:18:29 pgratz-HP-Spectre-13-x2 NetworkManager[1415]: <info> (wlan0): device state change: disconnected -> unavailable (reason 'none') [30 20 0]
Dec 14 20:18:29 pgratz-HP-Spectre-13-x2 NetworkManager[1415]: <info> (wlan0): deactivating device (reason 'none') [0]
Dec 14 20:18:29 pgratz-HP-Spectre-13-x2 NetworkManager[1415]: <info> (wlan0): taking down device.



```

When I run my wpa_supplicant script this is what is output:

```

Dec 14 20:20:21 pgratz-HP-Spectre-13-x2 NetworkManager[1415]: <info> wpa_supplicant stopped
Dec 14 20:20:21 pgratz-HP-Spectre-13-x2 kernel: [  150.561661] iwlwifi 0000:07:00.0: L1 Disabled; Enabling L0S
Dec 14 20:20:21 pgratz-HP-Spectre-13-x2 kernel: [  150.561799] iwlwifi 0000:07:00.0: L1 Disabled; Enabling L0S
Dec 14 20:20:21 pgratz-HP-Spectre-13-x2 kernel: [  150.571056] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec 14 20:20:22 pgratz-HP-Spectre-13-x2 kernel: [  151.391188] wlan0: authenticate with 20:4e:7f:7a:dd:00
Dec 14 20:20:22 pgratz-HP-Spectre-13-x2 kernel: [  151.392145] wlan0: send auth to 20:4e:7f:7a:dd:00 (try 1/3)
Dec 14 20:20:22 pgratz-HP-Spectre-13-x2 kernel: [  151.393884] wlan0: authenticated
Dec 14 20:20:22 pgratz-HP-Spectre-13-x2 kernel: [  151.396420] wlan0: associate with 20:4e:7f:7a:dd:00 (try 1/3)
Dec 14 20:20:22 pgratz-HP-Spectre-13-x2 kernel: [  151.402727] wlan0: RX AssocResp from 20:4e:7f:7a:dd:00 (capab=0x431 status=0 aid=5)
Dec 14 20:20:22 pgratz-HP-Spectre-13-x2 kernel: [  151.406415] wlan0: associated
Dec 14 20:20:22 pgratz-HP-Spectre-13-x2 kernel: [  151.406502] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Dec 14 20:20:24 pgratz-HP-Spectre-13-x2 avahi-daemon[1281]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::e8b:fdff:fe57:4d83.
Dec 14 20:20:24 pgratz-HP-Spectre-13-x2 avahi-daemon[1281]: New relevant interface wlan0.IPv6 for mDNS.
Dec 14 20:20:24 pgratz-HP-Spectre-13-x2 avahi-daemon[1281]: Registering new address record for fe80::e8b:fdff:fe57:4d83 on wlan0.*.
Dec 14 20:20:26 pgratz-HP-Spectre-13-x2 dhclient: DHCPREQUEST of 192.168.2.3 on wlan0 to 255.255.255.255 port 67 (xid=0x320da2e1)
Dec 14 20:20:28 pgratz-HP-Spectre-13-x2 dhclient: DHCPACK of 192.168.2.3 from 192.168.2.1
Dec 14 20:20:28 pgratz-HP-Spectre-13-x2 avahi-daemon[1281]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.2.3.
Dec 14 20:20:28 pgratz-HP-Spectre-13-x2 avahi-daemon[1281]: New relevant interface wlan0.IPv4 for mDNS.
Dec 14 20:20:28 pgratz-HP-Spectre-13-x2 avahi-daemon[1281]: Registering new address record for 192.168.2.3 on wlan0.IPv4.
Dec 14 20:20:28 pgratz-HP-Spectre-13-x2 dhclient: bound to 192.168.2.3 -- renewal in 34538 seconds.
Dec 14 20:20:31 pgratz-HP-Spectre-13-x2 NetworkManager[1415]: <info> wpa_supplicant die count reset



```

Here is my wifi start script:

```

pgratz@pgratz-HP-Spectre-13-x2:~$ cat bin/wifi_start.sh 
#!/bin/bash
killall wpa_supplicant
killall dhclient
rm -rf /var/run/wpa_supplicant
wpa_supplicant -c/etc/wpa_supplicant.conf -iwlan0 -B
sleep 5
dhclient wlan0



```

And here is the wpa_suppliant.conf script I wrote:

```

network={
        ssid="pgnet"
        scan_ssid=1
        key_mgmt=WPA-PSK
        psk="****************"
}



```

If that helps.
Paul

---

### Post by chili555 on 2013-12-14
Is Network Manager stopped reliably stopped or in what way is it restrained from attempting to run networking?

There are a couple of driver parameters that may help here. Temporarily, like this:```
sudo modprobe -r iwldvm  [COLOR="#FF0000"]<--isn't it iwldvm and not iwlnvm?[/COLOR]
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi  11n_disable=1
```If it works, we can write a file to make it persistent. You might also try modprobbing iwlwifi bt_coex_active=N.

I am still stumped as to why NM doesn't operate as expected. Any interesting clues here?```
nm-tool
```> WiFi now disabled by radio killswitchWeird. Before running the script, let's see:```
rfkill list all
```It's almost like NM turns off the switch!!!

---

### Post by pgratz on 2013-12-14
I'm actually doing nothing special to make sure NM doesnt try to take over the interface, it does not seem to do so though, I'm guessing that this is because it views WIFI as "disabled".

Here is the result of running those two commands:
```


pgratz@pgratz-HP-Spectre-13-x2:~/paper_for_review/old$ nm-tool 


NetworkManager Tool


State: disconnected


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             unavailable
  Default:           no
  HW Address:        0C:8B:FD:57:4D:83


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 




pgratz@pgratz-HP-Spectre-13-x2:~/paper_for_review/old$ rfkill list all
0: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
2: acer-wireless: Wireless LAN
        Soft blocked: yes
        Hard blocked: no
3: nfc0: (null)
        Soft blocked: no
        Hard blocked: no
4: hp-wifi: Wireless LAN
        Soft blocked: no
        Hard blocked: no
5: hp-bluetooth: Bluetooth
        Soft blocked: no
        Hard blocked: no


```

Note that I'm doing this after running my script to get WIFI up so I'm not sure if that might mess things up.

I'll report back on running with disabling N later tonight.
Paul

---

### Post by chili555 on 2013-12-14
> 2:[COLOR="#FF0000"] acer-wireless: Wireless LAN
        Soft blocked: yes[/COLOR]
        Hard blocked: no
3: nfc0: (null)
        Soft blocked: no
        Hard blocked: no
4: hp-wifi: Wireless LAN
        Soft blocked: no
        Hard blocked: noWhat?? You don't have an Acer laptop. May we see:```
lsmod
```If the module acer-wmi is loaded, we'll blacklist it and see if we make some headway.

---

### Post by pgratz on 2013-12-15
Interesting.  OK I rmmod'ed acer-wmi and that allowed NM to work!  I actually used NM to attach to my AP and type this.

That said I still have some other issues going on, the microcode SW errors are piling up in dmesg and I'm getting about 20% packet loss when I ping yahoo.com.  Also removing acer-wmi seems to have lost some of my special keyboard keys (volume up/down/mute and related stuff, I can live with out it).

I'll try the disable N option for iwlwifi and see if that helps. 

BTW what is the "right" way to blacklist a module?
Paul

---

### Post by pgratz on 2013-12-15
OK, I blacklisted the acer-wmi module and now NM works correctly on boot.   

I've also placed the following options on iwlwifi:

```

pgratz@pgratz-HP-Spectre-13-x2:~$ cat /etc/modprobe.d/iwlwifi.conf
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options 11n_disable=1 bt_coex_active=N

```

This seems to reduce the count of microcode errors but I'm now seeing some kernel backtraces which seems worse (?).   It seems like my ping packet drop is somewhere in the ~10% range now down from 20%.

Here is a snip from my dmesg right after boot while WIFI is coming up:

```

[    7.279134] iwlwifi 0000:07:00.0: L1 Disabled; Enabling L0S
[    7.279285] iwlwifi 0000:07:00.0: L1 Disabled; Enabling L0S
[    7.288738] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    9.696088] init: anacron main process (1628) killed by TERM signal
[   11.525657] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   12.192909] wlan0: authenticate with 20:4e:7f:7a:dd:00
[   12.193699] wlan0: direct probe to 20:4e:7f:7a:dd:00 (try 1/3)
[   12.396798] wlan0: direct probe to 20:4e:7f:7a:dd:00 (try 2/3)
[   12.601020] wlan0: direct probe to 20:4e:7f:7a:dd:00 (try 3/3)
[   12.804619] wlan0: authentication with 20:4e:7f:7a:dd:00 timed out
[   13.657600] wlan0: authenticate with 20:4e:7f:7a:dd:00
[   13.658294] wlan0: direct probe to 20:4e:7f:7a:dd:00 (try 1/3)
[   13.844847] iwlwifi 0000:07:00.0: Microcode SW error detected.  Restarting 0x2000000.
[   13.844858] iwlwifi 0000:07:00.0: CSR values:
[   13.844863] iwlwifi 0000:07:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[   13.844870] iwlwifi 0000:07:00.0:        CSR_HW_IF_CONFIG_REG: 0X00489204
[   13.844877] iwlwifi 0000:07:00.0:          CSR_INT_COALESCING: 0X0000ff40
[   13.844883] iwlwifi 0000:07:00.0:                     CSR_INT: 0X00000000
[   13.844889] iwlwifi 0000:07:00.0:                CSR_INT_MASK: 0X00000000
[   13.844911] iwlwifi 0000:07:00.0:           CSR_FH_INT_STATUS: 0X00000000
[   13.844917] iwlwifi 0000:07:00.0:                 CSR_GPIO_IN: 0X00000000
[   13.844923] iwlwifi 0000:07:00.0:                   CSR_RESET: 0X00000000
[   13.844930] iwlwifi 0000:07:00.0:                CSR_GP_CNTRL: 0X080403c5
[   13.844936] iwlwifi 0000:07:00.0:                  CSR_HW_REV: 0X00000144
[   13.844942] iwlwifi 0000:07:00.0:              CSR_EEPROM_REG: 0X00000000
[   13.844949] iwlwifi 0000:07:00.0:               CSR_EEPROM_GP: 0X80000000
[   13.844955] iwlwifi 0000:07:00.0:              CSR_OTP_GP_REG: 0X803a0000
[   13.844961] iwlwifi 0000:07:00.0:                 CSR_GIO_REG: 0X00080044
[   13.844967] iwlwifi 0000:07:00.0:            CSR_GP_UCODE_REG: 0X00000000
[   13.844973] iwlwifi 0000:07:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[   13.844979] iwlwifi 0000:07:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[   13.844985] iwlwifi 0000:07:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[   13.844991] iwlwifi 0000:07:00.0:                 CSR_LED_REG: 0X00000060
[   13.844997] iwlwifi 0000:07:00.0:        CSR_DRAM_INT_TBL_REG: 0X88036186
[   13.845003] iwlwifi 0000:07:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[   13.845009] iwlwifi 0000:07:00.0:             CSR_ANA_PLL_CFG: 0Xd55555d5
[   13.845015] iwlwifi 0000:07:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[   13.845021] iwlwifi 0000:07:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0010
[   13.845025] iwlwifi 0000:07:00.0: FH register values:
[   13.845040] iwlwifi 0000:07:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X156cfc00
[   13.845055] iwlwifi 0000:07:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X0155d5a0
[   13.845069] iwlwifi 0000:07:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000058
[   13.845084] iwlwifi 0000:07:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X00801114
[   13.845098] iwlwifi 0000:07:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[   13.845113] iwlwifi 0000:07:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X03030000
[   13.845128] iwlwifi 0000:07:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[   13.845142] iwlwifi 0000:07:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[   13.845156] iwlwifi 0000:07:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[   13.845266] iwlwifi 0000:07:00.0: Start IWL Error Log Dump:
[   13.845271] iwlwifi 0000:07:00.0: Status: 0x00000000, count: 6
[   13.845275] iwlwifi 0000:07:00.0: 0x0000003C | NMI_INTERRUPT_DATA_ACTION_PT
[   13.845279] iwlwifi 0000:07:00.0: 0x00000230 | uPc
[   13.845283] iwlwifi 0000:07:00.0: 0x00000000 | branchlink1
[   13.845286] iwlwifi 0000:07:00.0: 0x00000C8A | branchlink2
[   13.845290] iwlwifi 0000:07:00.0: 0x00014078 | interruptlink1
[   13.845293] iwlwifi 0000:07:00.0: 0x00000676 | interruptlink2
[   13.845297] iwlwifi 0000:07:00.0: 0x00000D40 | data1
[   13.845300] iwlwifi 0000:07:00.0: 0x00000008 | data2
[   13.845304] iwlwifi 0000:07:00.0: 0x03030000 | data3
[   13.845307] iwlwifi 0000:07:00.0: 0x0007347C | beacon time
[   13.845311] iwlwifi 0000:07:00.0: 0x006407EB | tsf low
[   13.845314] iwlwifi 0000:07:00.0: 0x00000000 | tsf hi
[   13.845318] iwlwifi 0000:07:00.0: 0x00000000 | time gp1
[   13.845321] iwlwifi 0000:07:00.0: 0x006407EC | time gp2
[   13.845325] iwlwifi 0000:07:00.0: 0x00000000 | time gp3
[   13.845328] iwlwifi 0000:07:00.0: 0x00321600 | uCode version
[   13.845332] iwlwifi 0000:07:00.0: 0x00000144 | hw version
[   13.845335] iwlwifi 0000:07:00.0: 0x00489204 | board version
[   13.845339] iwlwifi 0000:07:00.0: 0x0003001C | hcmd
[   13.845342] iwlwifi 0000:07:00.0: 0x26F62000 | isr0
[   13.845346] iwlwifi 0000:07:00.0: 0x01004000 | isr1
[   13.845349] iwlwifi 0000:07:00.0: 0x00000002 | isr2
[   13.845352] iwlwifi 0000:07:00.0: 0x00400081 | isr3
[   13.845356] iwlwifi 0000:07:00.0: 0x00000001 | isr4
[   13.845359] iwlwifi 0000:07:00.0: 0x10000112 | isr_pref
[   13.845363] iwlwifi 0000:07:00.0: 0x00000D40 | wait_event
[   13.845366] iwlwifi 0000:07:00.0: 0x000000D0 | l2p_control
[   13.845370] iwlwifi 0000:07:00.0: 0x00010030 | l2p_duration
[   13.845373] iwlwifi 0000:07:00.0: 0x0000003F | l2p_mhvalid
[   13.845377] iwlwifi 0000:07:00.0: 0x000000CE | l2p_addr_match
[   13.845380] iwlwifi 0000:07:00.0: 0x00000007 | lmpm_pmg_sel
[   13.845384] iwlwifi 0000:07:00.0: 0x6985A68B | timestamp
[   13.845388] iwlwifi 0000:07:00.0: 0x00345868 | flow_handler
[   13.845393] ieee80211 phy0: Hardware restart was requested
[   13.845792] iwlwifi 0000:07:00.0: L1 Disabled; Enabling L0S
[   13.845940] iwlwifi 0000:07:00.0: L1 Disabled; Enabling L0S
[   13.862136] wlan0: send auth to 20:4e:7f:7a:dd:00 (try 2/3)
[   14.169253] iwlwifi 0000:07:00.0: No association and the time event is over already...
[   14.169318] wlan0: Connection to AP 20:4e:7f:7a:dd:00 lost
[   14.883050] wlan0: send auth to 20:4e:7f:7a:dd:00 (try 3/3)
[   15.190262] iwlwifi 0000:07:00.0: No association and the time event is over already...
[   15.190327] wlan0: Connection to AP 20:4e:7f:7a:dd:00 lost
[   15.859206] wlan0: authentication with 20:4e:7f:7a:dd:00 timed out
[   15.863774] iwlwifi 0000:07:00.0: Couldn't drain frames for staid 1
[   15.863784] ------------[ cut here ]------------
[   15.863830] WARNING: CPU: 0 PID: 152 at /home/apw/COD/linux/net/mac80211/sta_info.c:839 __sta_info_destroy+0x25b/0x390 [mac80211]()
[   15.863834] Modules linked in: dm_crypt parport_pc ppdev x86_pkg_temp_thermal coretemp kvm_intel pn544_mei kvm mei_phy crct10dif_pclmul crc32_pclmul rfcomm ghash_clmulni_intel aesni_intel pn544 hid_sensor_als bnep hid_sensor_gyro_3d aes_x86_64 hid_sensor_magn_3d hci hid_sensor_accel_3d lrw gf128mul glue_helper hid_sensor_trigger industrialio_triggered_buffer ablk_helper hp_wmi nfc kfifo_buf cryptd industrialio hid_sensor_iio_common joydev sparse_keymap arc4 snd_hda_codec_hdmi nls_iso8859_1 snd_hda_codec_idt uvcvideo videobuf2_vmalloc snd_hda_intel snd_hda_codec hid_multitouch videobuf2_memops hid_sensor_hub snd_hwdep videobuf2_core microcode videodev snd_pcm btusb bluetooth snd_page_alloc rtsx_pci_ms serio_raw snd_seq_midi snd_seq_midi_event iwlmvm memstick lpc_ich mac80211 snd_rawmidi snd_seq snd_seq_device snd_timer iwlwifi snd cfg80211 mei_me mei soundcore intel_smartconnect tpm_tis mac_hid lp parport hid_generic mmc_block usbhid hid rtsx_pci_sdmmc i915 ahci libahci rtsx_pci i2c_algo_bit drm_kms_helper drm video wmi
[   15.863966] CPU: 0 PID: 152 Comm: kworker/u16:3 Not tainted 3.12.5-031205-generic #201312120254
[   15.863971] Hardware name: Hewlett-Packard HP Spectre 13 x2 PC/2152, BIOS F.16 11/02/2013
[   15.863997] Workqueue: phy0 ieee80211_iface_work [mac80211]
[   15.864002]  0000000000000347 ffff880153a89c48 ffffffff817441e2 0000000000000007
[   15.864010]  0000000000000000 ffff880153a89c88 ffffffff8106784c ffff880035919634
[   15.864017]  ffff880035919000 ffff88003557c600 ffff88003557e840 ffff88003557e840
[   15.864025] Call Trace:
[   15.864036]  [<ffffffff817441e2>] dump_stack+0x46/0x58
[   15.864047]  [<ffffffff8106784c>] warn_slowpath_common+0x8c/0xc0
[   15.864055]  [<ffffffff8106789a>] warn_slowpath_null+0x1a/0x20
[   15.864079]  [<ffffffffa02cc31b>] __sta_info_destroy+0x25b/0x390 [mac80211]
[   15.864103]  [<ffffffffa02cc6e1>] sta_info_destroy_addr+0x41/0x70 [mac80211]
[   15.864140]  [<ffffffffa0304d90>] ieee80211_destroy_auth_data+0x30/0xa0 [mac80211]
[   15.864176]  [<ffffffffa030c2b2>] ieee80211_sta_work+0x3e2/0x470 [mac80211]
[   15.864205]  [<ffffffffa02d9248>] ieee80211_iface_work+0x2b8/0x350 [mac80211]
[   15.864212]  [<ffffffff810843cf>] process_one_work+0x17f/0x4d0
[   15.864219]  [<ffffffff8108560b>] worker_thread+0x11b/0x3d0
[   15.864226]  [<ffffffff810854f0>] ? manage_workers.isra.21+0x190/0x190
[   15.864235]  [<ffffffff8108c820>] kthread+0xc0/0xd0
[   15.864243]  [<ffffffff8108c760>] ? flush_kthread_worker+0xb0/0xb0
[   15.864252]  [<ffffffff81759b3c>] ret_from_fork+0x7c/0xb0
[   15.864260]  [<ffffffff8108c760>] ? flush_kthread_worker+0xb0/0xb0
[   15.864265] ---[ end trace 92fd3c6f3a5ea974 ]---
[   16.714363] wlan0: authenticate with 20:4e:7f:7a:dd:00
[   16.715493] wlan0: direct probe to 20:4e:7f:7a:dd:00 (try 1/3)
[   16.715573] iwlwifi 0000:07:00.0: Microcode SW error detected.  Restarting 0x2000000.
[   16.715584] iwlwifi 0000:07:00.0: CSR values:
[   16.715591] iwlwifi 0000:07:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[   16.715602] iwlwifi 0000:07:00.0:        CSR_HW_IF_CONFIG_REG: 0X00489204
[   16.715612] iwlwifi 0000:07:00.0:          CSR_INT_COALESCING: 0X0000ff40
[   16.715622] iwlwifi 0000:07:00.0:                     CSR_INT: 0X00000000
[   16.715632] iwlwifi 0000:07:00.0:                CSR_INT_MASK: 0X00000000
[   16.715641] iwlwifi 0000:07:00.0:           CSR_FH_INT_STATUS: 0X00000000
[   16.715651] iwlwifi 0000:07:00.0:                 CSR_GPIO_IN: 0X00000000
[   16.715661] iwlwifi 0000:07:00.0:                   CSR_RESET: 0X00000000
[   16.715671] iwlwifi 0000:07:00.0:                CSR_GP_CNTRL: 0X080403c5
[   16.715680] iwlwifi 0000:07:00.0:                  CSR_HW_REV: 0X00000144
[   16.715690] iwlwifi 0000:07:00.0:              CSR_EEPROM_REG: 0X00000000
[   16.715698] iwlwifi 0000:07:00.0:               CSR_EEPROM_GP: 0X80000000
[   16.715705] iwlwifi 0000:07:00.0:              CSR_OTP_GP_REG: 0X803a0000
[   16.715712] iwlwifi 0000:07:00.0:                 CSR_GIO_REG: 0X00080044
[   16.715718] iwlwifi 0000:07:00.0:            CSR_GP_UCODE_REG: 0X00000000
[   16.715725] iwlwifi 0000:07:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[   16.715731] iwlwifi 0000:07:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[   16.715737] iwlwifi 0000:07:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[   16.715744] iwlwifi 0000:07:00.0:                 CSR_LED_REG: 0X00000060
[   16.715751] iwlwifi 0000:07:00.0:        CSR_DRAM_INT_TBL_REG: 0X88036186
[   16.715758] iwlwifi 0000:07:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[   16.715809] iwlwifi 0000:07:00.0:             CSR_ANA_PLL_CFG: 0Xd55555d5
[   16.715820] iwlwifi 0000:07:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[   16.715838] iwlwifi 0000:07:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0010
[   16.715851] iwlwifi 0000:07:00.0: FH register values:
[   16.715876] iwlwifi 0000:07:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X156cfc00
[   16.715898] iwlwifi 0000:07:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X0155d5a0
[   16.715915] iwlwifi 0000:07:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000038
[   16.715934] iwlwifi 0000:07:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80801114
[   16.715952] iwlwifi 0000:07:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[   16.715970] iwlwifi 0000:07:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[   16.715988] iwlwifi 0000:07:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[   16.716007] iwlwifi 0000:07:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[   16.716027] iwlwifi 0000:07:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[   16.716158] iwlwifi 0000:07:00.0: Start IWL Error Log Dump:
[   16.716167] iwlwifi 0000:07:00.0: Status: 0x00000000, count: 6
[   16.716175] iwlwifi 0000:07:00.0: 0x00002B00 | ADVANCED_SYSASSERT          
[   16.716183] iwlwifi 0000:07:00.0: 0x000002F0 | uPc
[   16.716190] iwlwifi 0000:07:00.0: 0x00000000 | branchlink1
[   16.716197] iwlwifi 0000:07:00.0: 0x00000C8A | branchlink2
[   16.716204] iwlwifi 0000:07:00.0: 0x00014078 | interruptlink1
[   16.716210] iwlwifi 0000:07:00.0: 0x00000676 | interruptlink2
[   16.716217] iwlwifi 0000:07:00.0: 0x00000001 | data1
[   16.716224] iwlwifi 0000:07:00.0: 0xDEADBEEF | data2
[   16.716230] iwlwifi 0000:07:00.0: 0xDEADBEEF | data3
[   16.716237] iwlwifi 0000:07:00.0: 0x002AEEB1 | beacon time
[   16.716243] iwlwifi 0000:07:00.0: 0x002BB338 | tsf low
[   16.716249] iwlwifi 0000:07:00.0: 0x00000000 | tsf hi
[   16.716255] iwlwifi 0000:07:00.0: 0x00000000 | time gp1
[   16.716261] iwlwifi 0000:07:00.0: 0x002BB338 | time gp2
[   16.716268] iwlwifi 0000:07:00.0: 0x00000000 | time gp3
[   16.716275] iwlwifi 0000:07:00.0: 0x00321600 | uCode version
[   16.716282] iwlwifi 0000:07:00.0: 0x00000144 | hw version
[   16.716289] iwlwifi 0000:07:00.0: 0x00489204 | board version
[   16.716296] iwlwifi 0000:07:00.0: 0x09300019 | hcmd
[   16.716303] iwlwifi 0000:07:00.0: 0x00022081 | isr0
[   16.716310] iwlwifi 0000:07:00.0: 0x00000000 | isr1
[   16.716317] iwlwifi 0000:07:00.0: 0x00000002 | isr2
[   16.716324] iwlwifi 0000:07:00.0: 0x0041DCC0 | isr3
[   16.716331] iwlwifi 0000:07:00.0: 0x00000000 | isr4
[   16.716339] iwlwifi 0000:07:00.0: 0x01002112 | isr_pref
[   16.716346] iwlwifi 0000:07:00.0: 0x000255D8 | wait_event
[   16.716353] iwlwifi 0000:07:00.0: 0x00000000 | l2p_control
[   16.716360] iwlwifi 0000:07:00.0: 0x00000020 | l2p_duration
[   16.716367] iwlwifi 0000:07:00.0: 0x00000000 | l2p_mhvalid
[   16.716374] iwlwifi 0000:07:00.0: 0x00000000 | l2p_addr_match
[   16.716382] iwlwifi 0000:07:00.0: 0x00000005 | lmpm_pmg_sel
[   16.716389] iwlwifi 0000:07:00.0: 0x17061625 | timestamp
[   16.716396] iwlwifi 0000:07:00.0: 0x00003848 | flow_handler
[   16.716406] ieee80211 phy0: Hardware restart was requested
[   16.716429] iwlwifi 0000:07:00.0: FW error in SYNC CMD REMOVE_STA
[   16.716440] CPU: 3 PID: 127 Comm: kworker/3:1 Tainted: G        W    3.12.5-031205-generic #201312120254
[   16.716446] Hardware name: Hewlett-Packard HP Spectre 13 x2 PC/2152, BIOS F.16 11/02/2013
[   16.716486] Workqueue: events iwl_mvm_sta_drained_wk [iwlmvm]
[   16.716494]  ffff8800360c9d20 ffff8800360c9c58 ffffffff817441e2 0000000000000000
[   16.716508]  ffff880035708000 ffff8800360c9cd8 ffffffffa02a3fb9 ffff8800360c9cc8
[   16.716520]  ffff880158d79400 ffff8800360c9ce8 0000000000000000 ffff880153ce0000
[   16.716532] Call Trace:
[   16.716548]  [<ffffffff817441e2>] dump_stack+0x46/0x58
[   16.716580]  [<ffffffffa02a3fb9>] iwl_pcie_send_hcmd_sync+0x4f9/0x510 [iwlwifi]
[   16.716595]  [<ffffffff8108d380>] ? add_wait_queue+0x60/0x60
[   16.716623]  [<ffffffffa02a541a>] iwl_trans_pcie_send_hcmd+0x2a/0x80 [iwlwifi]
[   16.716647]  [<ffffffffa036967e>] iwl_mvm_send_cmd+0x7e/0xa0 [iwlmvm]
[   16.716669]  [<ffffffffa03696dd>] iwl_mvm_send_cmd_pdu+0x3d/0x40 [iwlmvm]
[   16.716692]  [<ffffffffa036d13d>] iwl_mvm_rm_sta_common+0x4d/0xa0 [iwlmvm]
[   16.716715]  [<ffffffffa036dab1>] iwl_mvm_sta_drained_wk+0xb1/0x160 [iwlmvm]
[   16.716726]  [<ffffffff810843cf>] process_one_work+0x17f/0x4d0
[   16.716736]  [<ffffffff8108560b>] worker_thread+0x11b/0x3d0
[   16.716747]  [<ffffffff810854f0>] ? manage_workers.isra.21+0x190/0x190
[   16.716759]  [<ffffffff8108c820>] kthread+0xc0/0xd0
[   16.716771]  [<ffffffff8108c760>] ? flush_kthread_worker+0xb0/0xb0
[   16.716782]  [<ffffffff81759b3c>] ret_from_fork+0x7c/0xb0
[   16.716794]  [<ffffffff8108c760>] ? flush_kthread_worker+0xb0/0xb0
[   16.716805] iwlwifi 0000:07:00.0: Failed to remove station. Id=1
[   16.716812] iwlwifi 0000:07:00.0: Couldn't remove sta 1 after it was drained
[   16.716866] wlan0: direct probe to 20:4e:7f:7a:dd:00 (try 2/3)
[   16.717279] iwlwifi 0000:07:00.0: L1 Disabled; Enabling L0S
[   16.717433] iwlwifi 0000:07:00.0: L1 Disabled; Enabling L0S
[   16.920882] wlan0: direct probe to 20:4e:7f:7a:dd:00 (try 3/3)
[   17.124122] wlan0: authentication with 20:4e:7f:7a:dd:00 timed out
[   17.144173] iwlwifi 0000:07:00.0: Invalid station id
[   29.502046] wlan0: authenticate with 20:4e:7f:7a:dd:00
[   29.504178] wlan0: send auth to 20:4e:7f:7a:dd:00 (try 1/3)
[   29.523601] wlan0: authenticated
[   29.526161] wlan0: associate with 20:4e:7f:7a:dd:00 (try 1/3)
[   29.531012] wlan0: RX AssocResp from 20:4e:7f:7a:dd:00 (capab=0x431 status=0 aid=5)
[   29.532326] wlan0: associated
[   29.532385] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready



```

---

### Post by chili555 on 2013-12-15
I feel like a hungry man at a buffet! Ideally at the Boca Raton Hotel and Club where they seem to have strawberries dipped in chocolate that are nearly the size of golf balls! I am rubbing my hands together wondering which delicacy to pick first!

First, I suggest you try compiling an even newer driver from backports. I'd try 3.12.2-1 here: [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.12.2/](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.12.2/) If you still get microcode (i.e. firmware) errors, I'd wonder if the device were seated properly in the slot and if the antenna wires were connected snugly.

I'd love to find out why acer-wmi is loaded on an HP laptop. I wonder if Acer is the OEM and HP simply supplies the badge. Is hp-wmi loaded now?```
lsmod | grep wmi
```If so, you might experiment with un-blacklisting acer-wmi and blacklisting hp-wmi. 

This is actually a fascinating case. I'm glad you are on the other end of it because you seem very willing to experiment and learn.

---

### Post by pgratz on 2013-12-15
This is one of the things I love about linux, everything is comprehensible and generally fixable (unlike closed source stuff where if it doesn't work you're SOL).

Anyways, I was momentarily excited that I didn't get any backtraces or firmware errors in dmesg after booting just now... then I launched the browser and the firmware errors started showing up...

Anyways, here is the output of lsmod:

```
pgratz@pgratz-HP-Spectre-13-x2:~$ lsmod|grep wmihp_wmi                 18202  0 
sparse_keymap          13890  1 hp_wmi
snd_rawmidi            30465  1 snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd                    73802  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
wmi                    19363  1 hp_wmi



```


incidentally, the special keys are working again so I'm guessing that hp_wmi wasn't loading and acer_wmi was instead.  I'll blacklist hp_wmi and let you know what happens in a moment...

---

### Post by pgratz on 2013-12-15
Blacklisting hp_wmi puts me back where I was in terms of getting NM working.  Anecdotally, it seems like the FW errors are worse too but I'm not sure if that is just luck.

BTW, I don't think it is a hardware problem because it works fine from Windows 8.1 (as painful as that is to use).
Paul

---

### Post by chili555 on 2013-12-15
Here is what I suggest now. Please remove both of the xx-wmi blacklists. Now do:```
gksudo gedit /etc/rc.local
```Add a single line above exit 0:```
rfkill unblock all
```Proofread carefully, save and close gedit. Reboot. Now how does everything work?

I saw this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1221202](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1221202)> I received an answer from a developer with an updated firmware to test that fixed the issue. In my understanding, this firmware will be officially released soon.I downloaded the latest from Ubuntu 14.04 and checked it:```
md5sum linux-firmware_1.117_all/lib/firmware/iwlwifi-7260-7.ucode 
d07c309aed97fe4e2c43918aaef5b4d7 
```And also:```
md5sum /lib/firmware/iwlwifi-7260-7.ucode
d07c309aed97fe4e2c43918aaef5b4d7
```In other words, the files are identical. I am working to track down the later firmware.

---

### Post by pgratz on 2013-12-15
Looks like I have the same version of the firmware as you list below, md5sum is the same.

I tried adding the rfkill line to rc.local and removing the blacklisted modules and that seems to put me back where I was WRT NM not working, though I could still use my script to start networking.  

I also tried manually running rfkill unblock all when acer_wmi is loaded. Interestingly, it does not seem to remove the "soft" block on acer_wifi (early on, before posting here, I also played with rfkill and noticed this).  

I've reverted to blacklisting acer_wmi so that I can get NM working for now, though the firmware crashes seem to cause dropped packets every few seconds.

I'm very interested in trying a new FW to see if it will work.  The version I have is also the current one of the wireless.kernel.org site as of a week or so ago (site seems to be down so I can't see if they have updated it recently).

Paul

---

### Post by chili555 on 2013-12-16
> I'm pretty sure that compiling the driver from backports is unnecessary in Ubuntu 13.10. You are, in effect, backporting the driver from 3.11:
[QUOTE]using backports v3.11-rc3-1-0-g4e81a94
...to a system running 3.11 already:
> 3.11.0-14-generic
[/QUOTE]Let's address this while we wait for a hopefully favorable email on the firmware issue. I suggest you download this file to your desktop: [http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.12.2/backports-3.12.2-1.tar.bz2](http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.12.2/backports-3.12.2-1.tar.bz2)  Right-click it and select 'Extract Here.' Now to the terminal:```
cd ~/Desktop/backports-3.12.2-1
make defconfig-iwlwifi
make
sudo make install
```Reboot and tell us if there is any improvement.

I am suggesting this in the hope that it may not just be the firmware, but the interaction between firmware and driver.

---

### Post by pgratz on 2013-12-16
I'm actually currently on 3.12.5.  I upgraded my kernel using the packages found at [http://kernel.ubuntu.com/~kernel-ppa/mainline](http://kernel.ubuntu.com/~kernel-ppa/mainline) (this kernel seems to have other advantages WRT screen brightness).  Would you want me to back this out to get back to 3.11 and try the backports?

---

### Post by pgratz on 2013-12-16
BTW, just a heads up.  There was a new firmware version released for the 7260 on the [http://wireless.kernel.org/en/users/Drivers/iwlwifi](http://wireless.kernel.org/en/users/Drivers/iwlwifi) website (version 22.1.7.0, as opposed to 22.0.7.0 which is what I had before).  I just installed it and I'll post back on my experience with it.
Paul

---

### Post by pgratz on 2013-12-17
Success! Looks like the new firmware (and possibly the new kernel) have gotten rid of the firmware crashes and kernel backtraces, at least so far.  I've had it up for about 10 minutes so take it with a grain of salt, but I had been racking up a crash every few seconds so 10 minutes is definitely a big win.  I've also suspended a couple times and had it come back cleanly with wifi working (which did not happen before :-P).

BTW in a possibly unrelated issue. I see this in dmesg:

```
mce: [Hardware Error]: Machine check events logged


```

Should I be concerned about this and/or is this related to WIFI or is something else going on?  I found this in the /var/log/mcelog :
```

mcelog: Unsupported new Family 6 Model 45 CPU: only decoding architectural errors
mcelog: failed to prefill DIMM database from DMI data
mcelog: Unsupported new Family 6 Model 45 CPU: only decoding architectural errors
Hardware event. This is not a software error.
MCE 0
CPU 0 BANK 5 
MISC b8a0000086 ADDR fef81c40 
TIME 1387255919 Mon Dec 16 22:51:59 2013
MCG status:
MCi status:
Error overflow
Uncorrected error
MCi_MISC register valid
MCi_ADDR register valid
Processor context corrupt
MCA: corrected filtering (some unreported errors in same region)
Generic CACHE Level-2 Generic Error
STATUS ee0000000040110a MCGSTATUS 0
MCGCAP c07 APICID 0 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 69
mcelog: Unsupported new Family 6 Model 45 CPU: only decoding architectural errors
Hardware event. This is not a software error.
MCE 1
CPU 0 BANK 6 
MISC 1f8a0000086 ADDR fef81d00 
TIME 1387255919 Mon Dec 16 22:51:59 2013
MCG status:
MCi status:
Uncorrected error
MCi_MISC register valid
MCi_ADDR register valid
Processor context corrupt
MCA: corrected filtering (some unreported errors in same region)
Generic CACHE Level-2 Generic Error
STATUS ae0000000040110a MCGSTATUS 0
MCGCAP c07 APICID 0 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 69



```

If you think it is a problem but one that is unrelated to WIFI, I'll post up another thread.
Thanks!
Paul

---

### Post by chili555 on 2013-12-17
> Success! Looks like the new firmware (and possibly the new kernel) have gotten rid of the firmware crashes and kernel backtraces, at least so far.Great news! I shall note and download the firmware file; I am confident we'll need it again. As well, I'm confident you will have helped many searchers.> mce: [Hardware Error]: Machine check events loggedIt is not wifi related; it is, I believe, related to how the operating system recognizes and utilizes your CPU cores. I suggest you Google the error and post a question here: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

[https://www.kernel.org/doc/Documentation/x86/x86_64/machinecheck](https://www.kernel.org/doc/Documentation/x86/x86_64/machinecheck)

---

### Post by pgratz on 2013-12-17
Great, I hope this help others that are trying to get this (or similar) machines working.  Incidentally, I've had it up for about 12 hours with no firmware errors so I think the new firmware definitely did the trick.

If anyone else is looking for notes on running ubuntu on the HP Spectre 13 x2, [I have a written a guide of what I went through to get ubuntu on it that can be found here]("http://cesg.tamu.edu/faculty/paul-gratz/personal/linux-on-the-hp-spectre-13-x2/").

Thanks for all the help!
Paul

---

### Post by chili555 on 2013-12-17
> If anyone else is looking for notes on running ubuntu on the HP Spectre 13 x2, I have a written a guide of what I went through to get ubuntu on it that can be found here.I hope you will add the firmware story to the excellent guide. As well, if you searchers are trying to solve a wireless issue on your Spectre, before you apply the fixes above, be certain you have the same device:> root@pgratz-HP-Spectre-13-x2:~# lspci -nn | grep 0280
07:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [[COLOR="#FF0000"]8086:08b1[/COLOR]] (rev 73)If your Spectre comes with a Broadcom or an Atheros or whatever wireless card, these fixes will be ineffective.

Glad it's mostly working, Mr. Gratz! You might consider registering and posting a bug report against acer-wmi: [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

Also see:```
modinfo acer-wmi
```> parm:           force_series:Force a different laptop series (int)I am not an expert or even a talented amateur in this area; I simply offer a few nuggets to get you started.

---

### Post by pgratz on 2013-12-17
I've updated the guide to discuss the firmware a bit more.   I'll file the bug on acer-wmi tonight...
Thanks!
Paul

---

### Post by pgratz on 2013-12-18
FYI, the WIFI has been rock solid for more than a day's use through several APs using WPA and not.  I think it is safe to say this is solved.  Thanks!
Paul

---

