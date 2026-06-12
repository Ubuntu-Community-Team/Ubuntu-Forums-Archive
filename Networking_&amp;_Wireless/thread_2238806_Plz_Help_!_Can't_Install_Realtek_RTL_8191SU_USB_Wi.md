---
title: "Plz Help ! Can't Install Realtek RTL 8191SU USB Wireless Driver"
date: 2014-08-10
forum: Networking &amp; Wireless
---

### Post by a341276 on 2014-08-10
When i try to do "sudo make" command in terminal it shows
```
a341276@trbvm:~/Desktop/rtl$ sudo make
[sudo] password for a341276: 
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.11.0-12-generic/build M=/home/a341276/Desktop/rtl  modules
make[1]: Entering directory `/usr/src/linux-headers-3.11.0-12-generic'
  CC [M]  /home/a341276/Desktop/rtl/cmd/rtl871x_cmd.o
In file included from /home/a341276/Desktop/rtl/cmd/rtl871x_cmd.c:23:0:
/home/a341276/Desktop/rtl/include/osdep_service.h: In function &#8216;_init_timer&#8217;:
/home/a341276/Desktop/rtl/include/osdep_service.h:151:17: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
  ptimer->data = (u32)cntx;
                 ^
In file included from /home/a341276/Desktop/rtl/cmd/rtl871x_cmd.c:23:0:
/home/a341276/Desktop/rtl/include/osdep_service.h: In function &#8216;thread_enter&#8217;:
/home/a341276/Desktop/rtl/include/osdep_service.h:393:2: error: implicit declaration of function &#8216;daemonize&#8217; [-Werror=implicit-function-declaration]
  daemonize("%s", "RTKTHREAD");
  ^
In file included from /home/a341276/Desktop/rtl/include/rtl871x_ht.h:25:0,
                 from /home/a341276/Desktop/rtl/include/drv_types.h:67,
                 from /home/a341276/Desktop/rtl/cmd/rtl871x_cmd.c:24:
/home/a341276/Desktop/rtl/include/wifi.h: In function &#8216;get_da&#8217;:
/home/a341276/Desktop/rtl/include/wifi.h:324:46: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
 #define GetAddr1Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 4))
                                              ^
/home/a341276/Desktop/rtl/include/wifi.h:350:9: note: in expansion of macro &#8216;GetAddr1Ptr&#8217;
    da = GetAddr1Ptr(pframe);
         ^
/home/a341276/Desktop/rtl/include/wifi.h:324:28: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
 #define GetAddr1Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 4))
                            ^
/home/a341276/Desktop/rtl/include/wifi.h:350:9: note: in expansion of macro &#8216;GetAddr1Ptr&#8217;
    da = GetAddr1Ptr(pframe);
         ^
/home/a341276/Desktop/rtl/include/wifi.h:324:46: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
 #define GetAddr1Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 4))
                                              ^
/home/a341276/Desktop/rtl/include/wifi.h:353:9: note: in expansion of macro &#8216;GetAddr1Ptr&#8217;
    da = GetAddr1Ptr(pframe);
         ^
/home/a341276/Desktop/rtl/include/wifi.h:324:28: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
 #define GetAddr1Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 4))
                            ^
/home/a341276/Desktop/rtl/include/wifi.h:353:9: note: in expansion of macro &#8216;GetAddr1Ptr&#8217;
    da = GetAddr1Ptr(pframe);
         ^
/home/a341276/Desktop/rtl/include/wifi.h:328:46: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
 #define GetAddr3Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 16))
                                              ^
/home/a341276/Desktop/rtl/include/wifi.h:356:9: note: in expansion of macro &#8216;GetAddr3Ptr&#8217;
    da = GetAddr3Ptr(pframe);
         ^
/home/a341276/Desktop/rtl/include/wifi.h:328:28: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
 #define GetAddr3Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 16))
                            ^
/home/a341276/Desktop/rtl/include/wifi.h:356:9: note: in expansion of macro &#8216;GetAddr3Ptr&#8217;
    da = GetAddr3Ptr(pframe);
         ^
/home/a341276/Desktop/rtl/include/wifi.h:328:46: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
 #define GetAddr3Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 16))
                                              ^
/home/a341276/Desktop/rtl/include/wifi.h:359:9: note: in expansion of macro &#8216;GetAddr3Ptr&#8217;
    da = GetAddr3Ptr(pframe);
         ^
/home/a341276/Desktop/rtl/include/wifi.h:328:28: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
 #define GetAddr3Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 16))
                            ^
/home/a341276/Desktop/rtl/include/wifi.h:359:9: note: in expansion of macro &#8216;GetAddr3Ptr&#8217;
    da = GetAddr3Ptr(pframe);
         ^
/home/a341276/Desktop/rtl/include/wifi.h: In function &#8216;get_sa&#8217;:
/home/a341276/Desktop/rtl/include/wifi.h:326:46: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
 #define GetAddr2Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 10))
                                              ^
/home/a341276/Desktop/rtl/include/wifi.h:374:9: note: in expansion of macro &#8216;GetAddr2Ptr&#8217;
    sa = GetAddr2Ptr(pframe);
         ^
/home/a341276/Desktop/rtl/include/wifi.h:326:28: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
 #define GetAddr2Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 10))
                            ^
/home/a341276/Desktop/rtl/include/wifi.h:374:9: note: in expansion of macro &#8216;GetAddr2Ptr&#8217;
    sa = GetAddr2Ptr(pframe);
         ^
/home/a341276/Desktop/rtl/include/wifi.h:328:46: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
 #define GetAddr3Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 16))
                                              ^
/home/a341276/Desktop/rtl/include/wifi.h:377:9: note: in expansion of macro &#8216;GetAddr3Ptr&#8217;
    sa = GetAddr3Ptr(pframe);
         ^
/home/a341276/Desktop/rtl/include/wifi.h:328:28: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
 #define GetAddr3Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 16))
                            ^
/home/a341276/Desktop/rtl/include/wifi.h:377:9: note: in expansion of macro &#8216;GetAddr3Ptr&#8217;
    sa = GetAddr3Ptr(pframe);
         ^
/home/a341276/Desktop/rtl/include/wifi.h:326:46: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
 #define GetAddr2Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 10))
                                              ^
/home/a341276/Desktop/rtl/include/wifi.h:380:9: note: in expansion of macro &#8216;GetAddr2Ptr&#8217;
    sa = GetAddr2Ptr(pframe);
         ^
/home/a341276/Desktop/rtl/include/wifi.h:326:28: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
 #define GetAddr2Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 10))
                            ^
/home/a341276/Desktop/rtl/include/wifi.h:380:9: note: in expansion of macro &#8216;GetAddr2Ptr&#8217;
    sa = GetAddr2Ptr(pframe);
         ^
/home/a341276/Desktop/rtl/include/wifi.h:330:46: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
 #define GetAddr4Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 24))
                                              ^
/home/a341276/Desktop/rtl/include/wifi.h:383:9: note: in expansion of macro &#8216;GetAddr4Ptr&#8217;
    sa = GetAddr4Ptr(pframe);
         ^
/home/a341276/Desktop/rtl/include/wifi.h:330:28: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
 #define GetAddr4Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 24))
                            ^
/home/a341276/Desktop/rtl/include/wifi.h:383:9: note: in expansion of macro &#8216;GetAddr4Ptr&#8217;
    sa = GetAddr4Ptr(pframe);
         ^
/home/a341276/Desktop/rtl/include/wifi.h: In function &#8216;get_hdr_bssid&#8217;:
/home/a341276/Desktop/rtl/include/wifi.h:328:46: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
 #define GetAddr3Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 16))
                                              ^
/home/a341276/Desktop/rtl/include/wifi.h:397:9: note: in expansion of macro &#8216;GetAddr3Ptr&#8217;
    sa = GetAddr3Ptr(pframe);
         ^
/home/a341276/Desktop/rtl/include/wifi.h:328:28: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
 #define GetAddr3Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 16))
                            ^
/home/a341276/Desktop/rtl/include/wifi.h:397:9: note: in expansion of macro &#8216;GetAddr3Ptr&#8217;
    sa = GetAddr3Ptr(pframe);
         ^
/home/a341276/Desktop/rtl/include/wifi.h:326:46: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
 #define GetAddr2Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 10))
                                              ^
/home/a341276/Desktop/rtl/include/wifi.h:400:9: note: in expansion of macro &#8216;GetAddr2Ptr&#8217;
    sa = GetAddr2Ptr(pframe);
         ^
/home/a341276/Desktop/rtl/include/wifi.h:326:28: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
 #define GetAddr2Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 10))
                            ^
/home/a341276/Desktop/rtl/include/wifi.h:400:9: note: in expansion of macro &#8216;GetAddr2Ptr&#8217;
    sa = GetAddr2Ptr(pframe);
         ^
/home/a341276/Desktop/rtl/include/wifi.h:324:46: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
 #define GetAddr1Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 4))
                                              ^
/home/a341276/Desktop/rtl/include/wifi.h:403:9: note: in expansion of macro &#8216;GetAddr1Ptr&#8217;
    sa = GetAddr1Ptr(pframe);
         ^
/home/a341276/Desktop/rtl/include/wifi.h:324:28: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
 #define GetAddr1Ptr(pbuf) ((unsigned char *)((unsigned int)(pbuf) + 4))
                            ^
/home/a341276/Desktop/rtl/include/wifi.h:403:9: note: in expansion of macro &#8216;GetAddr1Ptr&#8217;
    sa = GetAddr1Ptr(pframe);
         ^
In file included from /home/a341276/Desktop/rtl/include/drv_types.h:70:0,
                 from /home/a341276/Desktop/rtl/cmd/rtl871x_cmd.c:24:
/home/a341276/Desktop/rtl/include/rtl871x_cmd.h: At top level:
/home/a341276/Desktop/rtl/include/rtl871x_cmd.h:107:25: error: field &#8216;event_tasklet&#8217; has incomplete type
   struct tasklet_struct event_tasklet;
                         ^
In file included from /home/a341276/Desktop/rtl/include/drv_types.h:72:0,
                 from /home/a341276/Desktop/rtl/cmd/rtl871x_cmd.c:24:
/home/a341276/Desktop/rtl/include/rtl871x_xmit.h:355:24: error: field &#8216;xmit_tasklet&#8217; has incomplete type
  struct tasklet_struct xmit_tasklet;
                        ^
In file included from /home/a341276/Desktop/rtl/include/drv_types.h:73:0,
                 from /home/a341276/Desktop/rtl/cmd/rtl871x_cmd.c:24:
/home/a341276/Desktop/rtl/include/rtl871x_recv.h:205:24: error: field &#8216;recv_tasklet&#8217; has incomplete type
  struct tasklet_struct recv_tasklet;
                        ^
In file included from /home/a341276/Desktop/rtl/include/drv_types.h:73:0,
                 from /home/a341276/Desktop/rtl/cmd/rtl871x_cmd.c:24:
/home/a341276/Desktop/rtl/include/rtl871x_recv.h: In function &#8216;rxmem_to_recvframe&#8217;:
/home/a341276/Desktop/rtl/include/rtl871x_recv.h:435:30: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
  return (union recv_frame*)(((uint)rxmem>>RXFRAME_ALIGN) <<RXFRAME_ALIGN) ;
                              ^
/home/a341276/Desktop/rtl/include/rtl871x_recv.h:435:9: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
  return (union recv_frame*)(((uint)rxmem>>RXFRAME_ALIGN) <<RXFRAME_ALIGN) ;
         ^
/home/a341276/Desktop/rtl/cmd/rtl871x_cmd.c: In function &#8216;_init_cmd_priv&#8217;:
/home/a341276/Desktop/rtl/cmd/rtl871x_cmd.c:93:75: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
  pcmdpriv->cmd_buf = pcmdpriv->cmd_allocated_buf  +  CMDBUFF_ALIGN_SZ - ( (uint)(pcmdpriv->cmd_allocated_buf) & (CMDBUFF_ALIGN_SZ-1));
                                                                           ^
/home/a341276/Desktop/rtl/cmd/rtl871x_cmd.c:101:60: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
  pcmdpriv->rsp_buf = pcmdpriv->rsp_allocated_buf  +  4 - ( (uint)(pcmdpriv->rsp_allocated_buf) & 3);
                                                            ^
/home/a341276/Desktop/rtl/cmd/rtl871x_cmd.c: In function &#8216;_init_evt_priv&#8217;:
/home/a341276/Desktop/rtl/cmd/rtl871x_cmd.c:135:59: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
  pevtpriv->evt_buf = pevtpriv->evt_allocated_buf  +  4 - ((unsigned int)(pevtpriv->evt_allocated_buf) & 3);
                                                           ^
cc1: some warnings being treated as errors
make[2]: *** [/home/a341276/Desktop/rtl/cmd/rtl871x_cmd.o] Error 1
make[1]: *** [_module_/home/a341276/Desktop/rtl] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-12-generic'
make: *** [modules] Error 2


```

What should i do ?

---

### Post by chili555 on 2014-08-11
Frankly, I have never heard of rtl8191su and I wonder if you have the right driver for your device. Please post:```
lspci -nn
lsusb
```Your 'make' errors suggest the package you are trying to compile is too old for your kernel version.

---

### Post by a341276 on 2014-08-12
Thank you so much for replying...

Here is the Result of lspci
```
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 01)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 01)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 08)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
00:07.7 System peripheral: VMware Virtual Machine Communication Interface (rev 10)
00:0f.0 VGA compatible controller: VMware SVGA II Adapter
00:10.0 SCSI storage controller: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI (rev 01)
00:11.0 PCI bridge: VMware PCI bridge (rev 02)
00:15.0 PCI bridge: VMware PCI Express Root Port (rev 01)
00:15.1 PCI bridge: VMware PCI Express Root Port (rev 01)
00:15.2 PCI bridge: VMware PCI Express Root Port (rev 01)
00:15.3 PCI bridge: VMware PCI Express Root Port (rev 01)
00:15.4 PCI bridge: VMware PCI Express Root Port (rev 01)
00:15.5 PCI bridge: VMware PCI Express Root Port (rev 01)
00:15.6 PCI bridge: VMware PCI Express Root Port (rev 01)
00:15.7 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.0 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.1 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.2 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.3 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.4 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.5 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.6 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.7 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.0 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.1 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.2 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.3 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.4 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.5 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.6 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.7 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.0 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.1 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.2 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.3 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.4 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.5 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.6 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.7 PCI bridge: VMware PCI Express Root Port (rev 01)
02:00.0 USB controller: VMware USB1.1 UHCI Controller
02:01.0 Ethernet controller: Intel Corporation 82545EM Gigabit Ethernet Controller (Copper) (rev 01)
02:02.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 02)
02:03.0 USB controller: VMware USB2 EHCI Controller
02:05.0 SATA controller: VMware Device 07e0
```

And the Result of lsusb
```
Bus 001 Device 002: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 002 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by chili555 on 2014-08-12
A virtual machine, you say?? Have you looked at this? [https://www.virtualbox.org/manual/ch06.html](https://www.virtualbox.org/manual/ch06.html)


-----

Note to chili: r8712u

---

### Post by a341276 on 2014-08-12
Sorry...
But at what should i look for ?

---

### Post by chili555 on 2014-08-12
I am not very familiar with virtual machines and even less so with VMWare. I suggest you study and follow this: [https://www.vmware.com/support/ws55/doc/ws_net_configurations_common.html](https://www.vmware.com/support/ws55/doc/ws_net_configurations_common.html)

---

