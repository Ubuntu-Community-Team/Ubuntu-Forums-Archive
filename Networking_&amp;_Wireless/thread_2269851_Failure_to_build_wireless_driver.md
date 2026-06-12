---
title: "Failure to build wireless driver"
date: 2015-03-18
forum: Networking &amp; Wireless
---

### Post by Justin_Kropczynski on 2015-03-18
I am new to Ubuntu and returning to Linux after a few years. I have an ASUS Laptop with a MT7630 wireless device that I cannot seem to get drivers to build and install. I followed the directions from this bug report [HTML]https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1220146/comments/125[/HTML] 
When I get to the step to build I get this result:
 ```
Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=3.16.0-31-generic -C /lib/modules/3.16.0-31-generic/build M=/var/lib/dkms/rt2x00/3.16/build........(bad exit status: 2)
ERROR (dkms apport): binary package for rt2x00: 3.16 not found
Error! Bad return status for module build on kernel: 3.16.0-31-generic (x86_64)
Consult /var/lib/dkms/rt2x00/3.16/build/make.log for more information.


```

The make.log is as follows:

```

DKMS make.log for rt2x00-3.16 for kernel 3.16.0-31-generic (x86_64)
Wed Mar 18 12:54:33 EDT 2015
make: Entering directory `/usr/src/linux-headers-3.16.0-31-generic'
  LD      /var/lib/dkms/rt2x00/3.16/build/built-in.o
  CC [M]  /var/lib/dkms/rt2x00/3.16/build/rt2x00dev.o
  CC [M]  /var/lib/dkms/rt2x00/3.16/build/rt2x00mac.o
  CC [M]  /var/lib/dkms/rt2x00/3.16/build/rt2x00config.o
  CC [M]  /var/lib/dkms/rt2x00/3.16/build/rt2x00queue.o
  CC [M]  /var/lib/dkms/rt2x00/3.16/build/rt2x00link.o
  CC [M]  /var/lib/dkms/rt2x00/3.16/build/mt_linux.o
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c: In function ‘PCIKickOutCmd’:
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:169:10: warning: unused variable ‘bIntContext’ [-Wunused-variable]
  BOOLEAN bIntContext = FALSE; 
          ^
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c: In function ‘RTMPAllocTxRxRingMemory’:
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:376:8: warning: unused variable ‘ErrorValue’ [-Wunused-variable]
  ULONG ErrorValue = 0; 
        ^
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:375:6: warning: unused variable ‘num’ [-Wunused-variable]
  INT num; 
      ^
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c: In function ‘RTMPInitTxRxRingMemory’:
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:406:8: warning: unused variable ‘ErrorValue’ [-Wunused-variable]
  ULONG ErrorValue = 0; 
        ^
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:404:15: warning: unused variable ‘pPacket’ [-Wunused-variable]
  PNDIS_PACKET pPacket; 
               ^
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:403:15: warning: unused variable ‘pDmaBuf’ [-Wunused-variable]
  RTMP_DMABUF *pDmaBuf, *pDescRing; 
               ^
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:400:6: warning: unused variable ‘num’ [-Wunused-variable]
  INT num, index; 
      ^
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c: In function ‘AsicInitTxRxRing’:
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:454:9: warning: unused variable ‘offset’ [-Wunused-variable]
  INT i, offset; 
         ^
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:454:6: warning: unused variable ‘i’ [-Wunused-variable]
  INT i, offset; 
      ^
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c: In function ‘RTMPHandleTxRing8DmaDoneInterrupt’:
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:511:8: warning: unused variable ‘TXWISize’ [-Wunused-variable]
  UINT8 TXWISize = rt2x00dev->TXWISize; 
        ^
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:509:6: warning: unused variable ‘ret’ [-Wunused-variable]
  int ret = 0; 
      ^
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c: In function ‘SendAndesTFSWITCH’:
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:592:30: warning: assignment from incompatible pointer type [enabled by default]
   CmdUnit.u.ANDES.CmdPayload = &coexTF; 
                              ^
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c: In function ‘PrepareProtectionFrame’:
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:680:8: warning: missing braces around initializer [-Wmissing-braces]
        HEADER_802_11     ProtectionFrame ={0}; 
        ^
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:680:8: warning: (near initialization for ‘ProtectionFrame.FC’) [-Wmissing-braces]
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:787:7: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 2 has type ‘ULONG’ [-Wformat=]
  // 
       ^
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:690:16: warning: unused variable ‘pTxInfo’ [-Wunused-variable]
  TXINFO_STRUC *pTxInfo; 
                ^
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c: In function ‘CheckAvailableNullFrameSpace’:
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:813:9: warning: array subscript has type ‘char’ [-Wchar-subscripts]
         { 
         ^
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c: In function ‘RtmpDrvPciUnMapSingle’:
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:956:6: warning: passing argument 2 of ‘linux_pci_unmap_single’ makes integer from pointer without a cast [enabled by default]
 } 
      ^
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:919:6: note: expected ‘dma_addr_t’ but argument is of type ‘VOID *’
 { 
      ^
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c: In function ‘BtAFHCtl’:
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:992:2: warning: missing braces around initializer [-Wmissing-braces]
   
  ^
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:992:2: warning: (near initialization for ‘btFunInfo.field’) [-Wmissing-braces]
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c: In function ‘SendAndesCoexFrameInfo’:
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:1090:15: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘ULONG’ [-Wformat=]
  
               ^
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:1090:15: warning: format ‘%d’ expects argument of type ‘int’, but argument 4 has type ‘ULONG’ [-Wformat=]
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:1090:15: warning: format ‘%d’ expects argument of type ‘int’, but argument 5 has type ‘ULONG’ [-Wformat=]
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:1090:15: warning: format ‘%d’ expects argument of type ‘int’, but argument 6 has type ‘ULONG’ [-Wformat=]
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:1090:15: warning: format ‘%d’ expects argument of type ‘int’, but argument 7 has type ‘ULONG’ [-Wformat=]
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:1099:30: warning: assignment from incompatible pointer type [enabled by default]
  
                              ^
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c: In function ‘UpdateAndesNullFrameSpace’:
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:1118:9: warning: array subscript has type ‘char’ [-Wchar-subscripts]
         { 
         ^
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c: In function ‘MT76x0_Calibration’:
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:1231:9: warning: unused variable ‘RFValue’ [-Wunused-variable]
    
         ^
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:1220:9: warning: unused variable ‘Value’ [-Wunused-variable]
   
         ^
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c: In function ‘MT7630_rfcsr_read’:
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:1566:2: warning: ‘return’ with a value, in function returning void [enabled by default]
 } 
  ^
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c: In function ‘MT7630_rfcsr_write’:
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:1608:2: warning: ‘return’ with a value, in function returning void [enabled by default]
 } 
  ^
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c: In function ‘SendLEDCmd’:
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:1842:3: warning: ‘return’ with a value, in function returning void [enabled by default]
  } 
   ^
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:1847:2: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘ULONG’ [-Wformat=]
  
  ^
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:1847:2: warning: format ‘%d’ expects argument of type ‘int’, but argument 4 has type ‘ULONG’ [-Wformat=]
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:1857:29: warning: assignment from incompatible pointer type [enabled by default]
   
                             ^
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:1866:2: warning: ‘return’ with a value, in function returning void [enabled by default]
  
  ^
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:1827:8: warning: unused variable ‘Pos’ [-Wunused-variable]
  ULONG LEDParameter[2] = {0}; 
        ^
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c: In function ‘SendAndesWLANStatus’:
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:1977:29: warning: assignment from incompatible pointer type [enabled by default]
   
                             ^
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:1986:2: warning: ‘return’ with a value, in function returning void [enabled by default]
   
  ^
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c: In function ‘SendAndesCCUForceMode’:
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:2016:29: warning: assignment from incompatible pointer type [enabled by default]
   
                             ^
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c: In function ‘SendAndesAFH’:
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:2100:29: warning: assignment from incompatible pointer type [enabled by default]
   
                             ^
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c: In function ‘Set_BtDump_Proc’:
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:2146:9: warning: ‘return’ with a value, in function returning void [enabled by default]
     }  
         ^
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:2156:3: warning: passing argument 2 of ‘file->f_op->write’ from incompatible pointer type [enabled by default]
  } 
   ^
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:2156:3: note: expected ‘const char *’ but argument is of type ‘UINT32 *’
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:2166:3: warning: passing argument 2 of ‘file->f_op->write’ from incompatible pointer type [enabled by default]
  } 
   ^
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:2166:3: note: expected ‘const char *’ but argument is of type ‘UINT32 *’
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:2176:3: warning: passing argument 2 of ‘file->f_op->write’ from incompatible pointer type [enabled by default]
  } 
   ^
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:2176:3: note: expected ‘const char *’ but argument is of type ‘UINT32 *’
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:2130:12: warning: unused variable ‘ReadOffset’ [-Wunused-variable]
     UINT32 offset,buf; 
            ^
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:2129:12: warning: unused variable ‘BaseOffset’ [-Wunused-variable]
     UINT16 ReadOffset; 
            ^
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c: In function ‘RTMPHandleTxRing8DmaDoneInterrupt’:
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:553:1: warning: control reaches end of non-void function [-Wreturn-type]
 } 
 ^
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c: In function ‘RtmpDrvPciUnMapSingle’:
/var/lib/dkms/rt2x00/3.16/build/mt_linux.c:957:1: warning: control reaches end of non-void function [-Wreturn-type]
  
 ^
  CC [M]  /var/lib/dkms/rt2x00/3.16/build/rt2x00crypto.o
  CC [M]  /var/lib/dkms/rt2x00/3.16/build/rt2x00firmware.o
  CC [M]  /var/lib/dkms/rt2x00/3.16/build/rt2x00leds.o
  LD [M]  /var/lib/dkms/rt2x00/3.16/build/rt2x00lib.o
  CC [M]  /var/lib/dkms/rt2x00/3.16/build/rt2x00mmio.o
  CC [M]  /var/lib/dkms/rt2x00/3.16/build/rt2x00pci.o
/var/lib/dkms/rt2x00/3.16/build/rt2x00pci.c: In function ‘rt2x00pci_probe’:
/var/lib/dkms/rt2x00/3.16/build/rt2x00pci.c:158:7: warning: unused variable ‘tmp’ [-Wunused-variable]
   u32 tmp=0;
       ^
/var/lib/dkms/rt2x00/3.16/build/rt2x00pci.c:157:7: warning: unused variable ‘MacValue’ [-Wunused-variable]
   u32 MacValue;
       ^
  CC [M]  /var/lib/dkms/rt2x00/3.16/build/rt2x00usb.o
  CC [M]  /var/lib/dkms/rt2x00/3.16/build/rt2800lib.o
In file included from /var/lib/dkms/rt2x00/3.16/build/rt2800lib.c:44:0:
/var/lib/dkms/rt2x00/3.16/build/rt2800.h:1787:0: warning: "TX_STA_CNT0" redefined [enabled by default]
 #define TX_STA_CNT0   0x170c
 ^
In file included from /var/lib/dkms/rt2x00/3.16/build/rt2800lib.c:42:0:
/var/lib/dkms/rt2x00/3.16/build/rt2x00.h:703:0: note: this is the location of the previous definition
 #define TX_STA_CNT0  0x170C
 ^
/var/lib/dkms/rt2x00/3.16/build/rt2800lib.c: In function ‘rt2800_MT7630_rfcsr_write’:
/var/lib/dkms/rt2x00/3.16/build/rt2800lib.c:1315:2: warning: ‘return’ with a value, in function returning void [enabled by default]
  return ret;
  ^
/var/lib/dkms/rt2x00/3.16/build/rt2800lib.c: In function ‘rt2800_MT7630_rfcsr_read’:
/var/lib/dkms/rt2x00/3.16/build/rt2800lib.c:1370:2: warning: ‘return’ with a value, in function returning void [enabled by default]
  return ret;
  ^
/var/lib/dkms/rt2x00/3.16/build/rt2800lib.c: In function ‘rt2800_write_tx_data’:
/var/lib/dkms/rt2x00/3.16/build/rt2800lib.c:1806:9: warning: assignment from incompatible pointer type [enabled by default]
   pTxWI = txwi;
         ^
/var/lib/dkms/rt2x00/3.16/build/rt2800lib.c: In function ‘rt2800_process_rxwi’:
/var/lib/dkms/rt2x00/3.16/build/rt2800lib.c:1944:8: warning: assignment from incompatible pointer type [enabled by default]
  pRxWI =entry->skb->data;
        ^
/var/lib/dkms/rt2x00/3.16/build/rt2800lib.c: In function ‘rt2800_txdone_entry’:
/var/lib/dkms/rt2x00/3.16/build/rt2800lib.c:2085:9: warning: assignment from incompatible pointer type [enabled by default]
   pTxWI = txwi;
         ^
/var/lib/dkms/rt2x00/3.16/build/rt2800lib.c: In function ‘rt2800_config_channel_rf7630’:
/var/lib/dkms/rt2x00/3.16/build/rt2800lib.c:4163:22: warning: assignment discards ‘const’ qualifier from pointer target type [enabled by default]
    pMT76x0_freq_item = &MT76x0_Frequency_Plan[i];
                      ^
/var/lib/dkms/rt2x00/3.16/build/rt2800lib.c:4107:6: warning: unused variable ‘eeprom’ [-Wunused-variable]
  u16 eeprom;
      ^
/var/lib/dkms/rt2x00/3.16/build/rt2800lib.c:4104:16: warning: unused variable ‘bbp_ch_idx’ [-Wunused-variable]
  unsigned char bbp_ch_idx;
                ^
/var/lib/dkms/rt2x00/3.16/build/rt2800lib.c: In function ‘rt2800_vco_calibration’:
/var/lib/dkms/rt2x00/3.16/build/rt2800lib.c:5090:3: warning: ISO C90 forbids mixed declarations and code [-Wdeclaration-after-statement]
   u32 reg;
   ^
/var/lib/dkms/rt2x00/3.16/build/rt2800lib.c: In function ‘rt2800_link_tuner’:
/var/lib/dkms/rt2x00/3.16/build/rt2800lib.c:5311:15: warning: unused variable ‘i’ [-Wunused-variable]
  unsigned int i;
               ^
/var/lib/dkms/rt2x00/3.16/build/rt2800lib.c: In function ‘rt2800_init_rfcsr’:
/var/lib/dkms/rt2x00/3.16/build/rt2800lib.c:7381:3: warning: ISO C90 forbids mixed declarations and code [-Wdeclaration-after-statement]
   unsigned char BBPCurrentBW = BW_20;
   ^
/var/lib/dkms/rt2x00/3.16/build/rt2800lib.c:7432:3: warning: ‘return’ with a value, in function returning void [enabled by default]
   return 0;
   ^
/var/lib/dkms/rt2x00/3.16/build/rt2800lib.c: In function ‘rt2800lib_init_queues’:
/var/lib/dkms/rt2x00/3.16/build/rt2800lib.c:7487:4: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 2 has type ‘dma_addr_t’ [-Wformat=]
    printk("-->TX_RING: Base=0x%x, Cnt=%d\n", entry_priv->desc_dma,rt2x00dev->tx[i].limit);
    ^
/var/lib/dkms/rt2x00/3.16/build/rt2800lib.c:7506:3: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 2 has type ‘dma_addr_t’ [-Wformat=]
   printk("-->RX_RING: Base=0x%x, Cnt=%d\n", entry_priv->desc_dma,rt2x00dev->rx[0].limit);
   ^
/var/lib/dkms/rt2x00/3.16/build/rt2800lib.c: In function ‘rt2800_enable_radio’:
/var/lib/dkms/rt2x00/3.16/build/rt2800lib.c:7743:16: warning: unused variable ‘csr3’ [-Wunused-variable]
  MAC_DW1_STRUC csr3;
                ^
/var/lib/dkms/rt2x00/3.16/build/rt2800lib.c:7742:16: warning: unused variable ‘csr2’ [-Wunused-variable]
  MAC_DW0_STRUC csr2;
                ^
/var/lib/dkms/rt2x00/3.16/build/rt2800lib.c: In function ‘mt7630_show_rf’:
/var/lib/dkms/rt2x00/3.16/build/rt2800lib.c:9121:28: warning: unused variable ‘rf_bank’ [-Wunused-variable]
   unsigned char regRF = 0, rf_bank = 0;
                            ^
/var/lib/dkms/rt2x00/3.16/build/rt2800lib.c: At top level:
/var/lib/dkms/rt2x00/3.16/build/rt2800lib.c:1373:12: warning: ‘rt2800_enable_wlan_mt7630’ defined but not used [-Wunused-function]
 static int rt2800_enable_wlan_mt7630(struct rt2x00_dev *rt2x00dev)
            ^
/var/lib/dkms/rt2x00/3.16/build/rt2800lib.c:5954:12: warning: ‘rt2800_wait_bbp_rf_MT7630_ready’ defined but not used [-Wunused-function]
 static int rt2800_wait_bbp_rf_MT7630_ready(struct rt2x00_dev *rt2x00dev)
            ^
/var/lib/dkms/rt2x00/3.16/build/rt2800lib.c:7547:13: warning: ‘MT76x0_CalculateTxpower’ defined but not used [-Wunused-function]
 static void MT76x0_CalculateTxpower(
             ^
In file included from /var/lib/dkms/rt2x00/3.16/build/rt2x00.h:48:0,
                 from /var/lib/dkms/rt2x00/3.16/build/rt2800lib.c:42:
/var/lib/dkms/rt2x00/3.16/build/rt2800lib.c: In function ‘rt2800_rf_init_calibration’:
/var/lib/dkms/rt2x00/3.16/build/rt2x00reg.h:251:11: warning: ‘rfcsr’ may be used uninitialized in this function [-Wmaybe-uninitialized]
  *(__reg) &= ~((__field).bit_mask); \
           ^
/var/lib/dkms/rt2x00/3.16/build/rt2800lib.c:6622:5: note: ‘rfcsr’ was declared here
  u8 rfcsr;
     ^
In file included from /var/lib/dkms/rt2x00/3.16/build/rt2x00.h:48:0,
                 from /var/lib/dkms/rt2x00/3.16/build/rt2800lib.c:42:
/var/lib/dkms/rt2x00/3.16/build/rt2800lib.c: In function ‘rt2800_normal_mode_setup_3xxx’:
/var/lib/dkms/rt2x00/3.16/build/rt2x00reg.h:251:11: warning: ‘rfcsr’ may be used uninitialized in this function [-Wmaybe-uninitialized]
  *(__reg) &= ~((__field).bit_mask); \
           ^
/var/lib/dkms/rt2x00/3.16/build/rt2800lib.c:6681:15: note: ‘rfcsr’ was declared here
  u8 min_gain, rfcsr, bbp;
               ^
/var/lib/dkms/rt2x00/3.16/build/rt2800lib.c: In function ‘rt2800_config’:
/var/lib/dkms/rt2x00/3.16/build/rt2800lib.c:4290:30: warning: array subscript is above array bounds [-Warray-bounds]
    if (MT76x0_RF_INT_PA_RegTb[i].BwBand & RfBand)
                              ^
/var/lib/dkms/rt2x00/3.16/build/rt2800lib.c:4295:30: warning: array subscript is above array bounds [-Warray-bounds]
        MT76x0_RF_INT_PA_RegTb[i].Bank);
                              ^
/var/lib/dkms/rt2x00/3.16/build/rt2800lib.c:4294:30: warning: array subscript is above array bounds [-Warray-bounds]
        MT76x0_RF_INT_PA_RegTb[i].Value,
                              ^
/var/lib/dkms/rt2x00/3.16/build/rt2800lib.c:4293:30: warning: array subscript is above array bounds [-Warray-bounds]
        MT76x0_RF_INT_PA_RegTb[i].Register,
                              ^
In file included from /var/lib/dkms/rt2x00/3.16/build/rt2800lib.c:44:0:
/var/lib/dkms/rt2x00/3.16/build/rt2800.h:1787:0: warning: "TX_STA_CNT0" redefined [enabled by default]
 #define TX_STA_CNT0   0x170c
 ^
In file included from /var/lib/dkms/rt2x00/3.16/build/rt2800lib.c:42:0:
/var/lib/dkms/rt2x00/3.16/build/rt2x00.h:703:0: note: this is the location of the previous definition
 #define TX_STA_CNT0  0x170C
 ^
  CC [M]  /var/lib/dkms/rt2x00/3.16/build/rt2400pci.o
/var/lib/dkms/rt2x00/3.16/build/rt2400pci.c:1734:2: warning: initialization from incompatible pointer type [enabled by default]
  .flush   = rt2x00mac_flush,
  ^
/var/lib/dkms/rt2x00/3.16/build/rt2400pci.c:1734:2: warning: (near initialization for ‘rt2400pci_mac80211_ops.flush’) [enabled by default]
  CC [M]  /var/lib/dkms/rt2x00/3.16/build/rt2500pci.o
/var/lib/dkms/rt2x00/3.16/build/rt2500pci.c:2023:2: warning: initialization from incompatible pointer type [enabled by default]
  .flush   = rt2x00mac_flush,
  ^
/var/lib/dkms/rt2x00/3.16/build/rt2500pci.c:2023:2: warning: (near initialization for ‘rt2500pci_mac80211_ops.flush’) [enabled by default]
  CC [M]  /var/lib/dkms/rt2x00/3.16/build/rt61pci.o
In file included from /var/lib/dkms/rt2x00/3.16/build/rt61pci.c:40:0:
/var/lib/dkms/rt2x00/3.16/build/rt61pci.h:168:0: warning: "HW_NULL_BASE" redefined [enabled by default]
 #define HW_NULL_BASE   0x2b00
 ^
In file included from /var/lib/dkms/rt2x00/3.16/build/rt61pci.c:37:0:
/var/lib/dkms/rt2x00/3.16/build/rt2x00.h:380:0: note: this is the location of the previous definition
 #define HW_NULL_BASE            0x7700
 ^
In file included from /var/lib/dkms/rt2x00/3.16/build/rt61pci.c:40:0:
/var/lib/dkms/rt2x00/3.16/build/rt61pci.h:1293:0: warning: "TXINFO_SIZE" redefined [enabled by default]
 #define TXINFO_SIZE   ( 6 * sizeof(__le32) )
 ^
In file included from /var/lib/dkms/rt2x00/3.16/build/rt61pci.c:37:0:
/var/lib/dkms/rt2x00/3.16/build/rt2x00.h:1207:0: note: this is the location of the previous definition
 #define TXINFO_SIZE   4
 ^
/var/lib/dkms/rt2x00/3.16/build/rt61pci.c:2986:2: warning: initialization from incompatible pointer type [enabled by default]
  .flush   = rt2x00mac_flush,
  ^
/var/lib/dkms/rt2x00/3.16/build/rt61pci.c:2986:2: warning: (near initialization for ‘rt61pci_mac80211_ops.flush’) [enabled by default]
  CC [M]  /var/lib/dkms/rt2x00/3.16/build/rt2800pci.o
In file included from /var/lib/dkms/rt2x00/3.16/build/rt2800pci.c:48:0:
/var/lib/dkms/rt2x00/3.16/build/rt2800.h:1787:0: warning: "TX_STA_CNT0" redefined [enabled by default]
 #define TX_STA_CNT0   0x170c
 ^
In file included from /var/lib/dkms/rt2x00/3.16/build/rt2800pci.c:43:0:
/var/lib/dkms/rt2x00/3.16/build/rt2x00.h:703:0: note: this is the location of the previous definition
 #define TX_STA_CNT0  0x170C
 ^
In file included from /var/lib/dkms/rt2x00/3.16/build/rt2800pci.c:49:0:
/var/lib/dkms/rt2x00/3.16/build/rt2800pci.h:55:1: warning: "/*" within comment [-Wcomment]
 /*
 ^
/var/lib/dkms/rt2x00/3.16/build/rt2800pci.c: In function ‘rt2800pci_init_queues’:
/var/lib/dkms/rt2x00/3.16/build/rt2800pci.c:594:4: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 2 has type ‘dma_addr_t’ [-Wformat=]
    printk("-->TX_RING: Base=0x%x, Cnt=%d\n", entry_priv->desc_dma,rt2x00dev->tx[i].limit);
    ^
/var/lib/dkms/rt2x00/3.16/build/rt2800pci.c:614:3: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 2 has type ‘dma_addr_t’ [-Wformat=]
   printk("-->RX_RING: Base=0x%x, Cnt=%d\n", entry_priv->desc_dma,rt2x00dev->rx[0].limit);
   ^
/var/lib/dkms/rt2x00/3.16/build/rt2800pci.c: In function ‘rt2800pci_write_tx_desc’:
/var/lib/dkms/rt2x00/3.16/build/rt2800pci.c:929:7: warning: assignment from incompatible pointer type [enabled by default]
  pTxD = entry_priv->desc;
       ^
/var/lib/dkms/rt2x00/3.16/build/rt2800pci.c:953:3: warning: ISO C90 forbids mixed declarations and code [-Wdeclaration-after-statement]
   struct _TXINFO_NMAC_PKT *nmac_info;
   ^
/var/lib/dkms/rt2x00/3.16/build/rt2800pci.c: In function ‘rt2800pci_fill_rxdone’:
/var/lib/dkms/rt2x00/3.16/build/rt2800pci.c:1040:15: warning: assignment from incompatible pointer type [enabled by default]
    pRxFceInfo = &hw_rx_info[12];
               ^
/var/lib/dkms/rt2x00/3.16/build/rt2800pci.c:1043:12: warning: assignment from incompatible pointer type [enabled by default]
    pRxInfo = entry->skb->data;
            ^
/var/lib/dkms/rt2x00/3.16/build/rt2800pci.c:1035:12: warning: unused variable ‘destrxd’ [-Wunused-variable]
    __le32 *destrxd = NULL;
            ^
/var/lib/dkms/rt2x00/3.16/build/rt2800pci.c:1034:18: warning: unused variable ‘hw_fce’ [-Wunused-variable]
    unsigned char hw_fce[4];
                  ^
/var/lib/dkms/rt2x00/3.16/build/rt2800pci.c: At top level:
/var/lib/dkms/rt2x00/3.16/build/rt2800pci.c:1262:182: warning: backslash and newline separated by space [enabled by default]
                  printk("((typeof(__tmp->type))__kfifo->data)[%d]=0x%x\n",__kfifo->out & __tmp->kfifo.mask, ((typeof(__tmp->type))__kfifo->data)[__kfifo->out & __tmp->kfifo.mask]); \      
 ^
/var/lib/dkms/rt2x00/3.16/build/rt2800pci.c:1263:35: warning: backslash and newline separated by space [enabled by default]
     *(typeof(__tmp->type))__val = \   
 ^
/var/lib/dkms/rt2x00/3.16/build/rt2800pci.c:1270:19: warning: backslash and newline separated by space [enabled by default]
                 } \ 
 ^
/var/lib/dkms/rt2x00/3.16/build/rt2800pci.c:1271:17: warning: backslash and newline separated by space [enabled by default]
               } \    
 ^
/var/lib/dkms/rt2x00/3.16/build/rt2800pci.c: In function ‘rt2800pci_tx8damdone_tasklet’:
/var/lib/dkms/rt2x00/3.16/build/rt2800pci.c:1389:10: warning: unused variable ‘bReschedule’ [-Wunused-variable]
  BOOLEAN bReschedule = 0;
          ^
/var/lib/dkms/rt2x00/3.16/build/rt2800pci.c:1388:23: warning: unused variable ‘IntSource’ [-Wunused-variable]
  INT_SOURCE_CSR_STRUC IntSource;
                       ^
/var/lib/dkms/rt2x00/3.16/build/rt2800pci.c:1387:16: warning: unused variable ‘flags’ [-Wunused-variable]
  unsigned long flags;
                ^
/var/lib/dkms/rt2x00/3.16/build/rt2800pci.c: At top level:
/var/lib/dkms/rt2x00/3.16/build/rt2800pci.c:1490:98: warning: backslash and newline separated by space [enabled by default]
    printk("value=0x%x, (typeof(*__tmp->type))__val = 0x%x\n", val, (typeof(*__tmp->type))__val); \    
 ^
/var/lib/dkms/rt2x00/3.16/build/rt2800pci.c:1498:163: warning: backslash and newline separated by space [enabled by default]
 printk("((typeof(__tmp->type))__kfifo->data)[%d]=0x%x\n",__kfifo->in & __tmp->kfifo.mask, ((typeof(__tmp->type))__kfifo->data)[__kfifo->in & __tmp->kfifo.mask]); \                       
 ^
/var/lib/dkms/rt2x00/3.16/build/rt2800pci.c:1500:19: warning: backslash and newline separated by space [enabled by default]
                 } \ 
 ^
/var/lib/dkms/rt2x00/3.16/build/rt2800pci.c:1501:17: warning: backslash and newline separated by space [enabled by default]
               } \    
 ^
/var/lib/dkms/rt2x00/3.16/build/rt2800pci.c: In function ‘rt2800pci_txstatus_interrupt’:
/var/lib/dkms/rt2x00/3.16/build/rt2800pci.c:1529:3: warning: passing argument 3 of ‘rt2x00mmio_register_read’ from incompatible pointer type [enabled by default]
   rt2x00mmio_register_read(rt2x00dev, TX_STA_FIFO_EXT, &Fifi_Status_ext.word);
   ^
In file included from /var/lib/dkms/rt2x00/3.16/build/rt2800pci.c:44:0:
/var/lib/dkms/rt2x00/3.16/build/rt2x00mmio.h:34:20: note: expected ‘u32 *’ but argument is of type ‘ULONG *’
 static inline void rt2x00mmio_register_read(struct rt2x00_dev *rt2x00dev,
                    ^
/var/lib/dkms/rt2x00/3.16/build/rt2800pci.c: At top level:
/var/lib/dkms/rt2x00/3.16/build/rt2800pci.c:1678:2: warning: initialization from incompatible pointer type [enabled by default]
  .flush   = rt2x00mac_flush,
  ^
/var/lib/dkms/rt2x00/3.16/build/rt2800pci.c:1678:2: warning: (near initialization for ‘rt2800pci_mac80211_ops.flush’) [enabled by default]
/var/lib/dkms/rt2x00/3.16/build/rt2800pci.c:55:13: warning: ‘rt2860_int_disable’ defined but not used [-Wunused-function]
 static void rt2860_int_disable(struct rt2x00_dev *rt2x00dev, unsigned int mode)
             ^
/var/lib/dkms/rt2x00/3.16/build/rt2800pci.c:64:13: warning: ‘rt2860_int_enable’ defined but not used [-Wunused-function]
 static void rt2860_int_enable(struct rt2x00_dev *rt2x00dev, unsigned int mode)
             ^
  CC [M]  /var/lib/dkms/rt2x00/3.16/build/rt2500usb.o
/var/lib/dkms/rt2x00/3.16/build/rt2500usb.c:1836:2: warning: initialization from incompatible pointer type [enabled by default]
  .flush   = rt2x00mac_flush,
  ^
/var/lib/dkms/rt2x00/3.16/build/rt2500usb.c:1836:2: warning: (near initialization for ‘rt2500usb_mac80211_ops.flush’) [enabled by default]
  CC [M]  /var/lib/dkms/rt2x00/3.16/build/rt73usb.o
In file included from /var/lib/dkms/rt2x00/3.16/build/rt73usb.c:38:0:
/var/lib/dkms/rt2x00/3.16/build/rt73usb.h:925:0: warning: "TXINFO_SIZE" redefined [enabled by default]
 #define TXINFO_SIZE   ( 6 * sizeof(__le32) )
 ^
In file included from /var/lib/dkms/rt2x00/3.16/build/rt73usb.c:36:0:
/var/lib/dkms/rt2x00/3.16/build/rt2x00.h:1207:0: note: this is the location of the previous definition
 #define TXINFO_SIZE   4
 ^
/var/lib/dkms/rt2x00/3.16/build/rt73usb.c:2324:2: warning: initialization from incompatible pointer type [enabled by default]
  .flush   = rt2x00mac_flush,
  ^
/var/lib/dkms/rt2x00/3.16/build/rt73usb.c:2324:2: warning: (near initialization for ‘rt73usb_mac80211_ops.flush’) [enabled by default]
  CC [M]  /var/lib/dkms/rt2x00/3.16/build/rt2800usb.o
In file included from /var/lib/dkms/rt2x00/3.16/build/rt2800usb.c:42:0:
/var/lib/dkms/rt2x00/3.16/build/rt2800.h:1787:0: warning: "TX_STA_CNT0" redefined [enabled by default]
 #define TX_STA_CNT0   0x170c
 ^
In file included from /var/lib/dkms/rt2x00/3.16/build/rt2800usb.c:39:0:
/var/lib/dkms/rt2x00/3.16/build/rt2x00.h:703:0: note: this is the location of the previous definition
 #define TX_STA_CNT0  0x170C
 ^
In file included from /var/lib/dkms/rt2x00/3.16/build/rt2800usb.c:43:0:
/var/lib/dkms/rt2x00/3.16/build/rt2800usb.h:44:0: warning: "RXINFO_DESC_SIZE" redefined [enabled by default]
 #define RXINFO_DESC_SIZE  (1 * sizeof(__le32))
 ^
In file included from /var/lib/dkms/rt2x00/3.16/build/rt2800usb.c:42:0:
/var/lib/dkms/rt2x00/3.16/build/rt2800.h:3151:0: note: this is the location of the previous definition
 #define RXINFO_DESC_SIZE  (4 * sizeof(__le32))
 ^
In file included from /var/lib/dkms/rt2x00/3.16/build/rt2x00.h:40:0,
                 from /var/lib/dkms/rt2x00/3.16/build/rt2800usb.c:39:
/var/lib/dkms/rt2x00/3.16/build/rt2800usb.c: In function ‘rt2800usb_tx_sta_fifo_read_completed’:
include/linux/kfifo.h:390:37: warning: initialization makes integer from pointer without a cast [enabled by default]
  typeof(*__tmp->const_type) __val = (val); \
                                     ^
/var/lib/dkms/rt2x00/3.16/build/rt2800usb.c:165:8: note: in expansion of macro ‘kfifo_put’
   if (!kfifo_put(&rt2x00dev->txstatus_fifo, &tx_status))
        ^
/var/lib/dkms/rt2x00/3.16/build/rt2800usb.c: In function ‘rt2800usb_probe_hw’:
/var/lib/dkms/rt2x00/3.16/build/rt2800usb.c:766:2: error: implicit declaration of function ‘PREPARE_WORK’ [-Werror=implicit-function-declaration]
  PREPARE_WORK(&rt2x00dev->txdone_work, rt2800usb_work_txdone);
  ^
/var/lib/dkms/rt2x00/3.16/build/rt2800usb.c: At top level:
/var/lib/dkms/rt2x00/3.16/build/rt2800usb.c:793:2: warning: initialization from incompatible pointer type [enabled by default]
  .flush   = rt2x00mac_flush,
  ^
/var/lib/dkms/rt2x00/3.16/build/rt2800usb.c:793:2: warning: (near initialization for ‘rt2800usb_mac80211_ops.flush’) [enabled by default]
cc1: some warnings being treated as errors
make[1]: *** [/var/lib/dkms/rt2x00/3.16/build/rt2800usb.o] Error 1
make: *** [_module_/var/lib/dkms/rt2x00/3.16/build] Error 2
make: Leaving directory `/usr/src/linux-headers-3.16.0-31-generic'

```

For reference I am running Ubuntu 14.04 LTS. If anyone has any ideas, they would be greatly appreciated.

---

### Post by praseodym on 2015-03-18
Is it MT7630e?

[https://github.com/tobiasBora/MT7630E_3.16](https://github.com/tobiasBora/MT7630E_3.16)

---

### Post by Justin_Kropczynski on 2015-03-18
Thanks! It worked great.

---

