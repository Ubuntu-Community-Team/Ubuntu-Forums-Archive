---
title: "Trouble installing wireless driver?"
date: 2014-01-11
forum: Networking &amp; Wireless
---

### Post by princeofnam on 2014-01-11
I'm trying to install the drivers for Alfa AWUS036NHR.  Is that necessary? Even when I try to do so I get an command not found when I try to sudo /.install.sh

---

### Post by Bucky Ball on 2014-01-11
Could you post the output of this command, please:

```
sudo lshw -C network
```

You need to give more information like what drivers are you trying to install, where did you get them, what instructions were you following and any error messages you are encountering.

---

### Post by praseodym on 2014-01-11
[http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5638107](http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5638107)

Install the respective driver for your ubuntu version (black boxes), and reboot.

---

### Post by princeofnam on 2014-01-17
```
  *-network               
       descripción: Network controller
       producto: BCM4313 802.11bgn Wireless Network Adapter
       fabricante: Broadcom Corporation
       id físico: 0
       información del bus: pci@0000:02:00.0
       versión: 01
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress bus_master cap_list
       configuración: driver=bcma-pci-bridge latency=0
       recursos: irq:16 memoria:b5400000-b5403fff
  *-network
       descripción: Ethernet interface
       producto: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       fabricante: Realtek Semiconductor Co., Ltd.
       id físico: 0
       información del bus: pci@0000:03:00.0
       nombre lógico: eth0
       versión: 05
       serie: 98:4b:e1:c5:bc:6a
       tamaño: 10Mbit/s
       capacidad: 100Mbit/s
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuración: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       recursos: irq:41 ioport:3000(size=256) memoria:b1404000-b1404fff memoria:b1400000-b1403fff
  *-network
       descripción: Interfaz inalámbrica
       id físico: 2
       nombre lógico: wlan0
       serie: cc:52:af:0d:10:d5
       capacidades: ethernet physical wireless
       configuración: broadcast=yes driver=brcmsmac driverversion=3.11.0-15-generic firmware=610.812 ip=129.81.109.129 link=yes multicast=yes wireless=IEEE 802.11bgn


```

I tried installing this driver [http://www.alfa.com.tw/press_c_show.php?sn=5](http://www.alfa.com.tw/press_c_show.php?sn=5) . I got the follwoing order "sudo: ./install.sh: orden no encontrada" which translates to "command not found" 

--

@praiseodym sorry i'm confused about your instructions.  how do i know which realtek driver to install

---

### Post by princeofnam on 2014-01-17
okay well @praiseodym i've followed your instructions. hopefully the device will work better

---

### Post by princeofnam on 2014-01-18
hmm.  internal wireless card seems to work better than the alfa adaptor still strangely.  i'm not sure if it's because i'm not making use of usb 3.0 or if it's still a driver issue.

---

### Post by praseodym on 2014-01-19
Do you use an extension cable for the adapter? Tried to plug it directly? Check

**iwconfig**

---

### Post by princeofnam on 2014-01-19
The last time I tried it I used an extension cable.  Although the problem happened before I used it too.  I'll try it again later to see if it makes a difference.

---

### Post by princeofnam on 2014-01-19
Strange.  I double checked under my wireless driver and it's actually a awus036h.  Would the realtek driver be any different?

---

### Post by chili555 on 2014-01-19
What's wrong with the internal Broadcom aside from possibly missing firmware?

---

### Post by princeofnam on 2014-01-19
aWell I currently depend on a week signal for my internet connection.  My friend lent me his Awus036h which apparently has boosted connectivity.  Unfortunately it isn't working that well even though I've heard the Awus036h should work well with linux (it's advertised as the device of choice for use with backtrack)

---

### Post by princeofnam on 2014-01-19
I tried to follow the instructions here: [http://askubuntu.com/questions/178009/how-do-i-install-drivers-for-the-alfa-awus036h-usb-wireless-adapter](http://askubuntu.com/questions/178009/how-do-i-install-drivers-for-the-alfa-awus036h-usb-wireless-adapter)

I got the following errors unfortunately ```
:~/Downloads/rtl8187L_linux_1041.0209.2012$ make
make[1]: Entering directory `/usr/src/linux-headers-3.11.0-15-generic'
  CC [M]  /home/sushi/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.o
/home/sushi/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:153:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rtl8187_usb_probe’
 static int __devinit rtl8187_usb_probe(struct usb_interface *intf,
                      ^
/home/sushi/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:155:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rtl8187_usb_disconnect’
 static void __devexit rtl8187_usb_disconnect(struct usb_interface *intf);
                       ^
/home/sushi/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:168:12: error: ‘rtl8187_usb_probe’ undeclared here (not in a function)
  .probe  = rtl8187_usb_probe,           
            ^
/home/sushi/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:169:16: error: ‘rtl8187_usb_disconnect’ undeclared here (not in a function)
  .disconnect = rtl8187_usb_disconnect,   
                ^
/home/sushi/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c: In function ‘rtl8180_proc_module_init’:
/home/sushi/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:427:2: error: implicit declaration of function ‘create_proc_entry’ [-Werror=implicit-function-declaration]
  rtl8180_proc=create_proc_entry(RTL8187_MODULE_NAME, S_IFDIR, init_net.proc_net);
  ^
/home/sushi/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:427:14: warning: assignment makes pointer from integer without a cast [enabled by default]
  rtl8180_proc=create_proc_entry(RTL8187_MODULE_NAME, S_IFDIR, init_net.proc_net);
              ^
/home/sushi/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c: In function ‘rtl8180_proc_init_one’:
/home/sushi/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:461:16: warning: assignment makes pointer from integer without a cast [enabled by default]
  priv->dir_dev = create_proc_entry(dev->name, 
                ^
/home/sushi/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:479:2: error: implicit declaration of function ‘create_proc_read_entry’ [-Werror=implicit-function-declaration]
  e = create_proc_read_entry("stats-rx", S_IFREG | S_IRUGO,
  ^
/home/sushi/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:479:4: warning: assignment makes pointer from integer without a cast [enabled by default]
  e = create_proc_read_entry("stats-rx", S_IFREG | S_IRUGO,
    ^
/home/sushi/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:489:4: warning: assignment makes pointer from integer without a cast [enabled by default]
  e = create_proc_read_entry("stats-tx", S_IFREG | S_IRUGO,
    ^
/home/sushi/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:518:4: warning: assignment makes pointer from integer without a cast [enabled by default]
  e = create_proc_read_entry("registers", S_IFREG | S_IRUGO,
    ^
/home/sushi/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c: In function ‘rtl8180_tx’:
/home/sushi/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:1382:12: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
  u8 seg = ((u32)txbuf % 4);
            ^
/home/sushi/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c: In function ‘rtl8187_usb_initendpoints’:
/home/sushi/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:1588:14: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
   seg_size = (u32)ptrcontext->transfer_buffer % 4;
              ^
/home/sushi/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c: At top level:
/home/sushi/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:3762:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rtl8187_usb_probe’
 static int __devinit rtl8187_usb_probe(struct usb_interface *intf,
                      ^
/home/sushi/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:3862:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rtl8187_usb_disconnect’
 static void __devexit rtl8187_usb_disconnect(struct usb_interface *intf)
                       ^
cc1: some warnings being treated as errors
make[2]: *** [/home/sushi/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.o] Error 1
make[1]: *** [_module_/home/sushi/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-15-generic'
make: *** [all] Error 2

```

---

