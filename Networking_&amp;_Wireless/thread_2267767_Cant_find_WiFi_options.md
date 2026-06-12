---
title: "Cant find WiFi options"
date: 2015-03-03
forum: Networking &amp; Wireless
---

### Post by DrdlokdSp4rtn on 2015-03-03
Ok so I am having some issues finding my Wifi connections. 
I have just installed Ubuntu 14.10 on my Asus TP500L Transformer and am absolutely loving the OS! except I noticed it hasn't auto searched for Wifi connections. Strange I thought, So I went looking for the Wifi settings "System settings>Networks" Nothing? the only options I have here are Proxy Networks, and Wired Connections (Which is what I am using ATM). After a short cruse through the forums I noticed that some people had suggested putting a command in "Startup Applecations" not being able to find that (and not really sure if I want to be plugging random commands in random terminals). I though I'd just ask :)

So Why isn't Ubuntu auto searching for Wifi connections, and how do I force it to?
I assume its not recognizing my Wifi adaptor? I have tried to update drivers but "no drivers need updating" 

I also noticed that a lot of people asked for this print out in related threads so

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo lshw -C network[/FONT][/COLOR]
```
Prints out:
  ```
*-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.1
       bus info: pci@0000:02:00.1
       logical name: eth0
       version: 12
       serial: 38:2c:4a:53:c9:a2
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8411-2_0.0.1 07/08/13 ip=192.168.2.10 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:63 ioport:e000(size=256) memory:f7914000-f7914fff memory:f7910000-f7913fff
  *-network UNCLAIMED
       description: Network controller
       product: MT7630e 802.11bgn Wireless Network Adapter
       vendor: MEDIATEK Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f7800000-f78fffff
```

Looking forward to fixing this problem and hearing from anyone :)

---

### Post by houstonbofh on 2015-03-04
You do not have the drivers for your WiFi nic installed.  Go to System Settings and select Additional Drivers to see if it can find them for you.

---

### Post by Bucky Ball on 2015-03-04
> **houstonbofh said:**
> You do not have the drivers for your WiFi nic installed.  Go to System Settings and select Additional Drivers to see if it can find them for you.

... but you'll need to be online with a cable, if that's possible.

* Update: on second thoughts ... [this]("http://community.linuxmint.com/tutorial/view/1796") looks like it will work on 14.04, but down below says it doesn't on 14.10. Mediatek haven't made a driver for it. The other one is available for 14.04 [here]("http://www.mediatek.com/en/downloads/mt7630-pcie/"). Only supports kernels 3.13 and 3.14. You might like to try it out anyway and see what happens.

---

### Post by DrdlokdSp4rtn on 2015-03-05
I forgot to mention that the "additional drivers" option tells me I need no more drivers, I will try that link and get back to you Bucky..Thanx :)

---

### Post by DrdlokdSp4rtn on 2015-03-11
Ok I down loaded the "Zip File" and extracted it to the Downloads folder as instructed in the how to then tried to run this:

```
cd ~/Downlaods/MT7630E-master
```
[B]
[/B]in the Terminal and I get File "Path not found"..
I even tried to change the name of the file to what it read in the Downlaods folder thinking that maybe the instructions were out of date, still "File path not found" "Bash...."

Any other suggestions?

So the problem is that the Wifi adapter I have dose not have a Ubuntu 14.10 compatible driver?
So would I be better off just reinstalling Ubuntu 14.04?

I had the same problem with my last laptop and its integrated graphics card with 14.04 :(

---

### Post by DrdlokdSp4rtn on 2015-03-17
So I reinstalled 14.04 and followed the instructions again this time it seemed like it was working untill the end of the script:

```
pDrvPciUnMapSingle&#8217;:/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/mt_linux.c:957:1: warning: control reaches end of non-void function [-Wreturn-type]
 
 ^
  CC [M]  /home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2x00crypto.o
  CC [M]  /home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2x00firmware.o
  CC [M]  /home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2x00leds.o
  LD [M]  /home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2x00lib.o
  CC [M]  /home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2x00mmio.o
  CC [M]  /home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2x00pci.o
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2x00pci.c: In function &#8216;rt2x00pci_probe&#8217;:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2x00pci.c:158:7: warning: unused variable &#8216;tmp&#8217; [-Wunused-variable]
   u32 tmp=0;
       ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2x00pci.c:157:7: warning: unused variable &#8216;MacValue&#8217; [-Wunused-variable]
   u32 MacValue;
       ^
  CC [M]  /home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2x00usb.o
  CC [M]  /home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.o
In file included from /home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c:44:0:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800.h:1787:0: warning: "TX_STA_CNT0" redefined [enabled by default]
 #define TX_STA_CNT0   0x170c
 ^
In file included from /home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c:42:0:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2x00.h:703:0: note: this is the location of the previous definition
 #define TX_STA_CNT0  0x170C
 ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c: In function &#8216;rt2800_MT7630_rfcsr_write&#8217;:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c:1315:2: warning: &#8216;return&#8217; with a value, in function returning void [enabled by default]
  return ret;
  ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c: In function &#8216;rt2800_MT7630_rfcsr_read&#8217;:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c:1370:2: warning: &#8216;return&#8217; with a value, in function returning void [enabled by default]
  return ret;
  ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c: In function &#8216;rt2800_write_tx_data&#8217;:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c:1806:9: warning: assignment from incompatible pointer type [enabled by default]
   pTxWI = txwi;
         ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c: In function &#8216;rt2800_process_rxwi&#8217;:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c:1944:8: warning: assignment from incompatible pointer type [enabled by default]
  pRxWI =entry->skb->data;
        ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c: In function &#8216;rt2800_txdone_entry&#8217;:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c:2085:9: warning: assignment from incompatible pointer type [enabled by default]
   pTxWI = txwi;
         ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c: In function &#8216;rt2800_config_channel_rf7630&#8217;:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c:4163:22: warning: assignment discards &#8216;const&#8217; qualifier from pointer target type [enabled by default]
    pMT76x0_freq_item = &MT76x0_Frequency_Plan[i];
                      ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c:4107:6: warning: unused variable &#8216;eeprom&#8217; [-Wunused-variable]
  u16 eeprom;
      ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c:4104:16: warning: unused variable &#8216;bbp_ch_idx&#8217; [-Wunused-variable]
  unsigned char bbp_ch_idx;
                ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c: In function &#8216;rt2800_vco_calibration&#8217;:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c:5090:3: warning: ISO C90 forbids mixed declarations and code [-Wdeclaration-after-statement]
   u32 reg;
   ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c: In function &#8216;rt2800_link_tuner&#8217;:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c:5311:15: warning: unused variable &#8216;i&#8217; [-Wunused-variable]
  unsigned int i;
               ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c: In function &#8216;rt2800_init_rfcsr&#8217;:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c:7381:3: warning: ISO C90 forbids mixed declarations and code [-Wdeclaration-after-statement]
   unsigned char BBPCurrentBW = BW_20;
   ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c:7432:3: warning: &#8216;return&#8217; with a value, in function returning void [enabled by default]
   return 0;
   ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c: In function &#8216;rt2800lib_init_queues&#8217;:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c:7487:4: warning: format &#8216;%x&#8217; expects argument of type &#8216;unsigned int&#8217;, but argument 2 has type &#8216;dma_addr_t&#8217; [-Wformat=]
    printk("-->TX_RING: Base=0x%x, Cnt=%d\n", entry_priv->desc_dma,rt2x00dev->tx[i].limit);
    ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c:7506:3: warning: format &#8216;%x&#8217; expects argument of type &#8216;unsigned int&#8217;, but argument 2 has type &#8216;dma_addr_t&#8217; [-Wformat=]
   printk("-->RX_RING: Base=0x%x, Cnt=%d\n", entry_priv->desc_dma,rt2x00dev->rx[0].limit);
   ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c: In function &#8216;rt2800_enable_radio&#8217;:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c:7743:16: warning: unused variable &#8216;csr3&#8217; [-Wunused-variable]
  MAC_DW1_STRUC csr3;
                ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c:7742:16: warning: unused variable &#8216;csr2&#8217; [-Wunused-variable]
  MAC_DW0_STRUC csr2;
                ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c: In function &#8216;mt7630_show_rf&#8217;:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c:9121:28: warning: unused variable &#8216;rf_bank&#8217; [-Wunused-variable]
   unsigned char regRF = 0, rf_bank = 0;
                            ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c: At top level:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c:1373:12: warning: &#8216;rt2800_enable_wlan_mt7630&#8217; defined but not used [-Wunused-function]
 static int rt2800_enable_wlan_mt7630(struct rt2x00_dev *rt2x00dev)
            ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c:5954:12: warning: &#8216;rt2800_wait_bbp_rf_MT7630_ready&#8217; defined but not used [-Wunused-function]
 static int rt2800_wait_bbp_rf_MT7630_ready(struct rt2x00_dev *rt2x00dev)
            ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c:7547:13: warning: &#8216;MT76x0_CalculateTxpower&#8217; defined but not used [-Wunused-function]
 static void MT76x0_CalculateTxpower(
             ^
In file included from /home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2x00.h:48:0,
                 from /home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c:42:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c: In function &#8216;rt2800_rf_init_calibration&#8217;:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2x00reg.h:251:11: warning: &#8216;rfcsr&#8217; may be used uninitialized in this function [-Wmaybe-uninitialized]
  *(__reg) &= ~((__field).bit_mask); \
           ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c:6622:5: note: &#8216;rfcsr&#8217; was declared here
  u8 rfcsr;
     ^
In file included from /home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2x00.h:48:0,
                 from /home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c:42:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c: In function &#8216;rt2800_normal_mode_setup_3xxx&#8217;:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2x00reg.h:251:11: warning: &#8216;rfcsr&#8217; may be used uninitialized in this function [-Wmaybe-uninitialized]
  *(__reg) &= ~((__field).bit_mask); \
           ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c:6681:15: note: &#8216;rfcsr&#8217; was declared here
  u8 min_gain, rfcsr, bbp;
               ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c: In function &#8216;rt2800_config&#8217;:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c:4290:30: warning: array subscript is above array bounds [-Warray-bounds]
    if (MT76x0_RF_INT_PA_RegTb[i].BwBand & RfBand)
                              ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c:4295:30: warning: array subscript is above array bounds [-Warray-bounds]
        MT76x0_RF_INT_PA_RegTb[i].Bank);
                              ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c:4294:30: warning: array subscript is above array bounds [-Warray-bounds]
        MT76x0_RF_INT_PA_RegTb[i].Value,
                              ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c:4293:30: warning: array subscript is above array bounds [-Warray-bounds]
        MT76x0_RF_INT_PA_RegTb[i].Register,
                              ^
In file included from /home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c:44:0:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800.h:1787:0: warning: "TX_STA_CNT0" redefined [enabled by default]
 #define TX_STA_CNT0   0x170c
 ^
In file included from /home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800lib.c:42:0:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2x00.h:703:0: note: this is the location of the previous definition
 #define TX_STA_CNT0  0x170C
 ^
  CC [M]  /home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2400pci.o
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2400pci.c:1734:2: warning: initialization from incompatible pointer type [enabled by default]
  .flush   = rt2x00mac_flush,
  ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2400pci.c:1734:2: warning: (near initialization for &#8216;rt2400pci_mac80211_ops.flush&#8217;) [enabled by default]
  CC [M]  /home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2500pci.o
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2500pci.c:2023:2: warning: initialization from incompatible pointer type [enabled by default]
  .flush   = rt2x00mac_flush,
  ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2500pci.c:2023:2: warning: (near initialization for &#8216;rt2500pci_mac80211_ops.flush&#8217;) [enabled by default]
  CC [M]  /home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt61pci.o
In file included from /home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt61pci.c:40:0:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt61pci.h:168:0: warning: "HW_NULL_BASE" redefined [enabled by default]
 #define HW_NULL_BASE   0x2b00
 ^
In file included from /home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt61pci.c:37:0:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2x00.h:380:0: note: this is the location of the previous definition
 #define HW_NULL_BASE            0x7700
 ^
In file included from /home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt61pci.c:40:0:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt61pci.h:1293:0: warning: "TXINFO_SIZE" redefined [enabled by default]
 #define TXINFO_SIZE   ( 6 * sizeof(__le32) )
 ^
In file included from /home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt61pci.c:37:0:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2x00.h:1207:0: note: this is the location of the previous definition
 #define TXINFO_SIZE   4
 ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt61pci.c:2986:2: warning: initialization from incompatible pointer type [enabled by default]
  .flush   = rt2x00mac_flush,
  ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt61pci.c:2986:2: warning: (near initialization for &#8216;rt61pci_mac80211_ops.flush&#8217;) [enabled by default]
  CC [M]  /home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800pci.o
In file included from /home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800pci.c:48:0:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800.h:1787:0: warning: "TX_STA_CNT0" redefined [enabled by default]
 #define TX_STA_CNT0   0x170c
 ^
In file included from /home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800pci.c:43:0:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2x00.h:703:0: note: this is the location of the previous definition
 #define TX_STA_CNT0  0x170C
 ^
In file included from /home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800pci.c:49:0:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800pci.h:55:1: warning: "/*" within comment [-Wcomment]
 /*
 ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800pci.c: In function &#8216;rt2800pci_init_queues&#8217;:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800pci.c:594:4: warning: format &#8216;%x&#8217; expects argument of type &#8216;unsigned int&#8217;, but argument 2 has type &#8216;dma_addr_t&#8217; [-Wformat=]
    printk("-->TX_RING: Base=0x%x, Cnt=%d\n", entry_priv->desc_dma,rt2x00dev->tx[i].limit);
    ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800pci.c:614:3: warning: format &#8216;%x&#8217; expects argument of type &#8216;unsigned int&#8217;, but argument 2 has type &#8216;dma_addr_t&#8217; [-Wformat=]
   printk("-->RX_RING: Base=0x%x, Cnt=%d\n", entry_priv->desc_dma,rt2x00dev->rx[0].limit);
   ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800pci.c: In function &#8216;rt2800pci_write_tx_desc&#8217;:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800pci.c:929:7: warning: assignment from incompatible pointer type [enabled by default]
  pTxD = entry_priv->desc;
       ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800pci.c:953:3: warning: ISO C90 forbids mixed declarations and code [-Wdeclaration-after-statement]
   struct _TXINFO_NMAC_PKT *nmac_info;
   ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800pci.c: In function &#8216;rt2800pci_fill_rxdone&#8217;:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800pci.c:1040:15: warning: assignment from incompatible pointer type [enabled by default]
    pRxFceInfo = &hw_rx_info[12];
               ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800pci.c:1043:12: warning: assignment from incompatible pointer type [enabled by default]
    pRxInfo = entry->skb->data;
            ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800pci.c:1035:12: warning: unused variable &#8216;destrxd&#8217; [-Wunused-variable]
    __le32 *destrxd = NULL;
            ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800pci.c:1034:18: warning: unused variable &#8216;hw_fce&#8217; [-Wunused-variable]
    unsigned char hw_fce[4];
                  ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800pci.c: At top level:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800pci.c:1262:182: warning: backslash and newline separated by space [enabled by default]
                  printk("((typeof(__tmp->type))__kfifo->data)[%d]=0x%x\n",__kfifo->out & __tmp->kfifo.mask, ((typeof(__tmp->type))__kfifo->data)[__kfifo->out & __tmp->kfifo.mask]); \      
 ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800pci.c:1263:35: warning: backslash and newline separated by space [enabled by default]
     *(typeof(__tmp->type))__val = \   
 ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800pci.c:1270:19: warning: backslash and newline separated by space [enabled by default]
                 } \ 
 ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800pci.c:1271:17: warning: backslash and newline separated by space [enabled by default]
               } \    
 ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800pci.c: In function &#8216;rt2800pci_tx8damdone_tasklet&#8217;:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800pci.c:1389:10: warning: unused variable &#8216;bReschedule&#8217; [-Wunused-variable]
  BOOLEAN bReschedule = 0;
          ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800pci.c:1388:23: warning: unused variable &#8216;IntSource&#8217; [-Wunused-variable]
  INT_SOURCE_CSR_STRUC IntSource;
                       ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800pci.c:1387:16: warning: unused variable &#8216;flags&#8217; [-Wunused-variable]
  unsigned long flags;
                ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800pci.c: At top level:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800pci.c:1490:98: warning: backslash and newline separated by space [enabled by default]
    printk("value=0x%x, (typeof(*__tmp->type))__val = 0x%x\n", val, (typeof(*__tmp->type))__val); \    
 ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800pci.c:1498:163: warning: backslash and newline separated by space [enabled by default]
 printk("((typeof(__tmp->type))__kfifo->data)[%d]=0x%x\n",__kfifo->in & __tmp->kfifo.mask, ((typeof(__tmp->type))__kfifo->data)[__kfifo->in & __tmp->kfifo.mask]); \                       
 ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800pci.c:1500:19: warning: backslash and newline separated by space [enabled by default]
                 } \ 
 ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800pci.c:1501:17: warning: backslash and newline separated by space [enabled by default]
               } \    
 ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800pci.c: In function &#8216;rt2800pci_txstatus_interrupt&#8217;:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800pci.c:1529:3: warning: passing argument 3 of &#8216;rt2x00mmio_register_read&#8217; from incompatible pointer type [enabled by default]
   rt2x00mmio_register_read(rt2x00dev, TX_STA_FIFO_EXT, &Fifi_Status_ext.word);
   ^
In file included from /home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800pci.c:44:0:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2x00mmio.h:34:20: note: expected &#8216;u32 *&#8217; but argument is of type &#8216;ULONG *&#8217;
 static inline void rt2x00mmio_register_read(struct rt2x00_dev *rt2x00dev,
                    ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800pci.c: At top level:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800pci.c:1678:2: warning: initialization from incompatible pointer type [enabled by default]
  .flush   = rt2x00mac_flush,
  ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800pci.c:1678:2: warning: (near initialization for &#8216;rt2800pci_mac80211_ops.flush&#8217;) [enabled by default]
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800pci.c:55:13: warning: &#8216;rt2860_int_disable&#8217; defined but not used [-Wunused-function]
 static void rt2860_int_disable(struct rt2x00_dev *rt2x00dev, unsigned int mode)
             ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800pci.c:64:13: warning: &#8216;rt2860_int_enable&#8217; defined but not used [-Wunused-function]
 static void rt2860_int_enable(struct rt2x00_dev *rt2x00dev, unsigned int mode)
             ^
  CC [M]  /home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2500usb.o
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2500usb.c:1836:2: warning: initialization from incompatible pointer type [enabled by default]
  .flush   = rt2x00mac_flush,
  ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2500usb.c:1836:2: warning: (near initialization for &#8216;rt2500usb_mac80211_ops.flush&#8217;) [enabled by default]
  CC [M]  /home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt73usb.o
In file included from /home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt73usb.c:38:0:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt73usb.h:925:0: warning: "TXINFO_SIZE" redefined [enabled by default]
 #define TXINFO_SIZE   ( 6 * sizeof(__le32) )
 ^
In file included from /home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt73usb.c:36:0:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2x00.h:1207:0: note: this is the location of the previous definition
 #define TXINFO_SIZE   4
 ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt73usb.c:2324:2: warning: initialization from incompatible pointer type [enabled by default]
  .flush   = rt2x00mac_flush,
  ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt73usb.c:2324:2: warning: (near initialization for &#8216;rt73usb_mac80211_ops.flush&#8217;) [enabled by default]
  CC [M]  /home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800usb.o
In file included from /home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800usb.c:42:0:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800.h:1787:0: warning: "TX_STA_CNT0" redefined [enabled by default]
 #define TX_STA_CNT0   0x170c
 ^
In file included from /home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800usb.c:39:0:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2x00.h:703:0: note: this is the location of the previous definition
 #define TX_STA_CNT0  0x170C
 ^
In file included from /home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800usb.c:43:0:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800usb.h:44:0: warning: "RXINFO_DESC_SIZE" redefined [enabled by default]
 #define RXINFO_DESC_SIZE  (1 * sizeof(__le32))
 ^
In file included from /home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800usb.c:42:0:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800.h:3151:0: note: this is the location of the previous definition
 #define RXINFO_DESC_SIZE  (4 * sizeof(__le32))
 ^
In file included from /home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2x00.h:40:0,
                 from /home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800usb.c:39:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800usb.c: In function &#8216;rt2800usb_tx_sta_fifo_read_completed&#8217;:
include/linux/kfifo.h:390:37: warning: initialization makes integer from pointer without a cast [enabled by default]
  typeof(*__tmp->const_type) __val = (val); \
                                     ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800usb.c:165:8: note: in expansion of macro &#8216;kfifo_put&#8217;
   if (!kfifo_put(&rt2x00dev->txstatus_fifo, &tx_status))
        ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800usb.c: In function &#8216;rt2800usb_probe_hw&#8217;:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800usb.c:766:2: error: implicit declaration of function &#8216;PREPARE_WORK&#8217; [-Werror=implicit-function-declaration]
  PREPARE_WORK(&rt2x00dev->txdone_work, rt2800usb_work_txdone);
  ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800usb.c: At top level:
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800usb.c:793:2: warning: initialization from incompatible pointer type [enabled by default]
  .flush   = rt2x00mac_flush,
  ^
/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800usb.c:793:2: warning: (near initialization for &#8216;rt2800usb_mac80211_ops.flush&#8217;) [enabled by default]
cc1: some warnings being treated as errors
make[2]: *** [/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00/rt2800usb.o] Error 1
make[1]: *** [_module_/home/drdlokdsp4rtn/Downloads/MT7630E-master/rt2x00] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.16.0-31-generic'
make: *** [all] Error 2
make -C /lib/modules/3.16.0-31-generic/build M=/home/drdlokdsp4rtn/Downloads/MT7630E-master/btloader clean
make[1]: Entering directory `/usr/src/linux-headers-3.16.0-31-generic'
  CLEAN   /home/drdlokdsp4rtn/Downloads/MT7630E-master/btloader/.tmp_versions
  CLEAN   /home/drdlokdsp4rtn/Downloads/MT7630E-master/btloader/Module.symvers
make[1]: Leaving directory `/usr/src/linux-headers-3.16.0-31-generic'
make -C /lib/modules/3.16.0-31-generic/build M=/home/drdlokdsp4rtn/Downloads/MT7630E-master/btloader modules
make[1]: Entering directory `/usr/src/linux-headers-3.16.0-31-generic'
  CC [M]  /home/drdlokdsp4rtn/Downloads/MT7630E-master/btloader/mt76xx.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/drdlokdsp4rtn/Downloads/MT7630E-master/btloader/mt76xx.mod.o
  LD [M]  /home/drdlokdsp4rtn/Downloads/MT7630E-master/btloader/mt76xx.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.16.0-31-generic'
cp: cannot stat &#8216;rt2x00/*.ko&#8217;: No such file or directory
update-rc.d: warning: /etc/init.d/load.sh missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 System start/stop links for /etc/init.d/load.sh already exist.
insmod: ERROR: could not insert module /lib/modules/3.16.0-31-generic/kernel/drivers/misc/eeprom/eeprom.ko: File exists
insmod: ERROR: could not insert module /lib/modules/3.16.0-31-generic/kernel/drivers/misc/eeprom/eeprom_93cx6.ko: File exists
insmod: ERROR: could not insert module /lib/modules/3.16.0-31-generic/kernel/lib/crc-ccitt.ko: File exists
insmod: ERROR: could not insert module /lib/modules/3.16.0-31-generic/kernel/net/wireless/cfg80211.ko: File exists
insmod: ERROR: could not insert module /lib/modules/3.16.0-31-generic/kernel/net/mac80211/mac80211.ko: File exists
insmod: ERROR: could not load module ./rt2x00lib.ko: No such file or directory
insmod: ERROR: could not load module ./rt2x00pci.ko: No such file or directory
insmod: ERROR: could not load module ./rt2x00mmio.ko: No such file or directory
insmod: ERROR: could not load module ./rt2800lib.ko: No such file or directory
insmod: ERROR: could not load module ./rt2800pci.ko: No such file or directory
insmod: ERROR: could not insert module ./mt76xx.ko: File exists
drdlokdsp4rtn@Cortana-14-04:~/Downloads/MT7630E-master$ 
```

What now? ;p

---

