---
title: "Cant install r8168 drivers"
date: 2014-05-28
forum: Networking &amp; Wireless
---

### Post by sheez on 2014-05-28
Yes, I too have the pain in the ass r8168 chipset. I get so much errors when trying to manually install the drivers:

Does anyone have a solution, or is it better to buy a new NIC? (altough there are good solutions to get this chipset to work)

```
root@johan-desktop:~/Desktop/sticky/r8168-8.035.00# ./autorun.sh
 
Check old driver and unload it.
Build the module and install
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c: In function ‘rtl8168_rx_vlan_skb’:
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:2077:3: error: too few arguments to function ‘__vlan_hwaccel_put_tag’
   __vlan_hwaccel_put_tag(skb, swab16(opts2 & 0xffff));
   ^
In file included from /home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:47:0:
include/linux/if_vlan.h:337:31: note: declared here
 static inline struct sk_buff *__vlan_hwaccel_put_tag(struct sk_buff *skb,
                               ^
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c: In function ‘rtl8168_set_features’:
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:2136:22: error: ‘NETIF_F_HW_VLAN_RX’ undeclared (first use in this function)
  if (dev->features & NETIF_F_HW_VLAN_RX)
                      ^
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:2136:22: note: each undeclared identifier is reported only once for each function it appears in
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c: At top level:
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:14545:1: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rtl8168_init_board’
 rtl8168_init_board(struct pci_dev *pdev,
 ^
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:14715:1: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rtl8168_init_sequence’
 rtl8168_init_sequence(struct rtl8168_private *tp)
 ^
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:14968:1: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rtl8168_init_one’
 rtl8168_init_one(struct pci_dev *pdev,
 ^
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:15132:1: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rtl8168_remove_one’
 rtl8168_remove_one(struct pci_dev *pdev)
 ^
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:17651:12: error: ‘rtl8168_init_one’ undeclared here (not in a function)
  .probe  = rtl8168_init_one,
            ^
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:17652:2: error: implicit declaration of function ‘__devexit_p’ [-Werror=implicit-function-declaration]
  .remove  = __devexit_p(rtl8168_remove_one),
  ^
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:17652:25: error: ‘rtl8168_remove_one’ undeclared here (not in a function)
  .remove  = __devexit_p(rtl8168_remove_one),
                         ^
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:17301:12: warning: ‘rtl8168_poll’ defined but not used [-Wunused-function]
 static int rtl8168_poll(napi_ptr napi, napi_budget budget)
            ^
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:1368:1: warning: ‘rtl8168_xmii_reset_pending’ defined but not used [-Wunused-function]
 rtl8168_xmii_reset_pending(struct net_device *dev)
 ^
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:1383:1: warning: ‘rtl8168_xmii_link_ok’ defined but not used [-Wunused-function]
 rtl8168_xmii_link_ok(struct net_device *dev)
 ^
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:1395:1: warning: ‘rtl8168_xmii_reset_enable’ defined but not used [-Wunused-function]
 rtl8168_xmii_reset_enable(struct net_device *dev)
 ^
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:1544:1: warning: ‘rtl8168_link_option’ defined but not used [-Wunused-function]
 rtl8168_link_option(int idx,
 ^
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:1823:1: warning: ‘rtl8168_set_speed_xmii’ defined but not used [-Wunused-function]
 rtl8168_set_speed_xmii(struct net_device *dev,
 ^
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:2151:13: warning: ‘rtl8168_gset_xmii’ defined but not used [-Wunused-function]
 static void rtl8168_gset_xmii(struct net_device *dev,
             ^
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:2886:13: warning: ‘rtl8168_get_mac_version’ defined but not used [-Wunused-function]
 static void rtl8168_get_mac_version(struct rtl8168_private *tp, void __iomem *ioaddr)
             ^
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:3002:1: warning: ‘rtl8168_print_mac_version’ defined but not used [-Wunused-function]
 rtl8168_print_mac_version(struct rtl8168_private *tp)
 ^
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:3044:1: warning: ‘rtl8168_hw_phy_config’ defined but not used [-Wunused-function]
 rtl8168_hw_phy_config(struct net_device *dev)
 ^
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:13681:1: warning: ‘rtl8168_release_board’ defined but not used [-Wunused-function]
 rtl8168_release_board(struct pci_dev *pdev,
 ^
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:14914:17: warning: ‘rtl8168_try_msi’ defined but not used [-Wunused-function]
 static unsigned rtl8168_try_msi(struct pci_dev *pdev, void __iomem *ioaddr)
                 ^
cc1: some warnings being treated as errors
make[3]: *** [/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.o] Error 1
make[2]: *** [_module_/home/johan/Desktop/sticky/r8168-8.035.00/src] Error 2
make[1]: *** [modules] Error 2
make: *** [modules] Error 2
```

---

### Post by sheez on 2014-05-28
Hello,

I installed Ubuntu yesterday, so I am a total noob. I have a r8168 chipset and I need to install the drivers manually. 
So I followed the readme instructions. Im using the terminal and im in the correct folder where the autorun.sh is located for my driver.
When I use 'sudo ./autorun.sh' it says command not found, even when im in root (sudo -s). How do I get this to work?
What am I missing? I cant find any solution on the internet for it.

Thanks,

---

### Post by slickymaster on 2014-05-28
Set the file executable using the chmod command as follows:```
chmod +x [COLOR=#000000]autorun.sh[/COLOR]
```Then you can run your .sh file```
./[COLOR=#000000]autorun.sh[/COLOR]
```

---

### Post by steeldriver on 2014-05-28
You may get that error if the file is present but does not have its executable bit set - if you're really sure that you want to execute the file [DISCLAIMER: I have not checked that it's a recommended way to install drivers for r8168] then try

```

chmod +x autorun.sh
sudo ./autorun.sh

```

Alternatively, if you know what shell language the script is written in you can invoke the appropriate interpreter directly e.g.

```

sudo sh autorun.sh

```
or
```

sudo bash autorun.sh

```

---

### Post by 3rdalbum on 2014-05-28
sudo -s
./autorun.sh

Also, are you sure it is "autorun" and not "autogen"?

---

### Post by sheez on 2014-05-28
what slickymaster said was correct. I can execute it now. However, now a new problem arises:

I get so many errors when executing the autorun. Its a clean install of Ubuntu, so I dont know where all the errors come from.

```
root@johan-desktop:~/Desktop/sticky/r8168-8.035.00# ./autorun.sh
 
Check old driver and unload it.
Build the module and install
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c: In function ‘rtl8168_rx_vlan_skb’:
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:2077:3: error: too few arguments to function ‘__vlan_hwaccel_put_tag’
   __vlan_hwaccel_put_tag(skb, swab16(opts2 & 0xffff));
   ^
In file included from /home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:47:0:
include/linux/if_vlan.h:337:31: note: declared here
 static inline struct sk_buff *__vlan_hwaccel_put_tag(struct sk_buff *skb,
                               ^
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c: In function ‘rtl8168_set_features’:
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:2136:22: error: ‘NETIF_F_HW_VLAN_RX’ undeclared (first use in this function)
  if (dev->features & NETIF_F_HW_VLAN_RX)
                      ^
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:2136:22: note: each undeclared identifier is reported only once for each function it appears in
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c: At top level:
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:14545:1: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rtl8168_init_board’
 rtl8168_init_board(struct pci_dev *pdev,
 ^
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:14715:1: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rtl8168_init_sequence’
 rtl8168_init_sequence(struct rtl8168_private *tp)
 ^
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:14968:1: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rtl8168_init_one’
 rtl8168_init_one(struct pci_dev *pdev,
 ^
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:15132:1: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rtl8168_remove_one’
 rtl8168_remove_one(struct pci_dev *pdev)
 ^
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:17651:12: error: ‘rtl8168_init_one’ undeclared here (not in a function)
  .probe  = rtl8168_init_one,
            ^
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:17652:2: error: implicit declaration of function ‘__devexit_p’ [-Werror=implicit-function-declaration]
  .remove  = __devexit_p(rtl8168_remove_one),
  ^
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:17652:25: error: ‘rtl8168_remove_one’ undeclared here (not in a function)
  .remove  = __devexit_p(rtl8168_remove_one),
                         ^
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:17301:12: warning: ‘rtl8168_poll’ defined but not used [-Wunused-function]
 static int rtl8168_poll(napi_ptr napi, napi_budget budget)
            ^
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:1368:1: warning: ‘rtl8168_xmii_reset_pending’ defined but not used [-Wunused-function]
 rtl8168_xmii_reset_pending(struct net_device *dev)
 ^
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:1383:1: warning: ‘rtl8168_xmii_link_ok’ defined but not used [-Wunused-function]
 rtl8168_xmii_link_ok(struct net_device *dev)
 ^
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:1395:1: warning: ‘rtl8168_xmii_reset_enable’ defined but not used [-Wunused-function]
 rtl8168_xmii_reset_enable(struct net_device *dev)
 ^
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:1544:1: warning: ‘rtl8168_link_option’ defined but not used [-Wunused-function]
 rtl8168_link_option(int idx,
 ^
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:1823:1: warning: ‘rtl8168_set_speed_xmii’ defined but not used [-Wunused-function]
 rtl8168_set_speed_xmii(struct net_device *dev,
 ^
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:2151:13: warning: ‘rtl8168_gset_xmii’ defined but not used [-Wunused-function]
 static void rtl8168_gset_xmii(struct net_device *dev,
             ^
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:2886:13: warning: ‘rtl8168_get_mac_version’ defined but not used [-Wunused-function]
 static void rtl8168_get_mac_version(struct rtl8168_private *tp, void __iomem *ioaddr)
             ^
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:3002:1: warning: ‘rtl8168_print_mac_version’ defined but not used [-Wunused-function]
 rtl8168_print_mac_version(struct rtl8168_private *tp)
 ^
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:3044:1: warning: ‘rtl8168_hw_phy_config’ defined but not used [-Wunused-function]
 rtl8168_hw_phy_config(struct net_device *dev)
 ^
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:13681:1: warning: ‘rtl8168_release_board’ defined but not used [-Wunused-function]
 rtl8168_release_board(struct pci_dev *pdev,
 ^
/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.c:14914:17: warning: ‘rtl8168_try_msi’ defined but not used [-Wunused-function]
 static unsigned rtl8168_try_msi(struct pci_dev *pdev, void __iomem *ioaddr)
                 ^
cc1: some warnings being treated as errors
make[3]: *** [/home/johan/Desktop/sticky/r8168-8.035.00/src/r8168_n.o] Error 1
make[2]: *** [_module_/home/johan/Desktop/sticky/r8168-8.035.00/src] Error 2
make[1]: *** [modules] Error 2
make: *** [modules] Error 2
```

---

### Post by slickymaster on 2014-05-28
[COLOR=#000000][FONT=Arial]Threads merged.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Please do not create duplicate threads, it dilutes community effort.

Also, please [use ]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168")[/FONT][/COLOR][COLOR=#000000][FONT=Arial][code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168"). It make the post clean, compact and more appealing, thus getting more attention from readers.[/FONT][/COLOR]

---

### Post by slickymaster on 2014-05-28
Moving the thread from Absolute Beginners to the **Networking & Wireless** sub-forum, which is the proper place for this issue.

---

### Post by sheez on 2014-05-28
somehow I got it to work. I dont know why it suddenly decided to install without errors. This OS does some really random things sometimes.

edit: well, talking about randomness. After playing a game in windows, I booted back to Ubuntu and what do you know... internet didnt work, AGAIN.
I had to reinstall the drivers, AGAIN, and everything was fine. Why do I have to install the drivers again when I reboot? Why cant it just work properly all the time(like in windows)?

---

