---
title: "RTL8188CE Driver Won't Install"
date: 2014-07-05
forum: Networking &amp; Wireless
---

### Post by Tanmay_Narang on 2014-07-05
Hey all, I've tried just about everything, googled it, nothing. I have an HP Pavilion DV6-6C35DX which has a RealTek RTL8188CE chipset for wireless. I'm on Xubuntu 14.04, but I've had this issue on every distro I've ever used (Arch, Ubuntu, Mint, Slackware, etc.).

lspci output:
```

tanmay@lappy:~/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013$ lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek [Radeon HD 6620G]
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series]
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 12h Processor Root Port
00:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 12h Processor Root Port
00:06.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 12h Processor Root Port
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 03)
00:10.1 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 03)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 13)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD] FCH IDE Controller (rev 40)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge (rev 40)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 7
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
03:00.1 SD Host controller: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)

```

Error:
```

tanmay@lappy:~/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013$ make
make -C /lib/modules/3.13.0-24-generic/build M=/home/tanmay/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013 modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
  CC [M]  /home/tanmay/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.o
In file included from /home/tanmay/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c:39:0:
/home/tanmay/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/pci.h:247:15: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rtl_pci_probe&#8217;
 int __devinit rtl_pci_probe(struct pci_dev *pdev,
               ^
/home/tanmay/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c: In function &#8216;rtl_action_proc&#8217;:
/home/tanmay/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c:885:32: error: &#8216;struct ieee80211_conf&#8217; has no member named &#8216;channel&#8217;
       rx_status.freq = hw->conf.channel->center_freq;
                                ^
/home/tanmay/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c:886:32: error: &#8216;struct ieee80211_conf&#8217; has no member named &#8216;channel&#8217;
       rx_status.band = hw->conf.channel->band;
                                ^
/home/tanmay/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c: In function &#8216;rtl_send_smps_action&#8217;:
/home/tanmay/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c:1451:24: error: &#8216;struct ieee80211_conf&#8217; has no member named &#8216;channel&#8217;
   info->band = hw->conf.channel->band;
                        ^
make[2]: *** [/home/tanmay/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.o] Error 1
make[1]: *** [_module_/home/tanmay/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make: *** [all] Error 2
tanmay@lappy:~/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013$ 

```
I also tried this: [https://github.com/FreedomBen/rtl8188ce-linux-driver](https://github.com/FreedomBen/rtl8188ce-linux-driver)
Output:
```

tanmay@lappy:~/Downloads/rtl8188ce-linux-driver-master/rtl8188ce-linux-driver$ ./install.sh 
-e 
[*] So you want to live on the wild side and try a different driver for your RealTek wireless card eh?  Awesome!  I'll help you do it.
-e 
[*] We are going to build and install the driver from source code, compiled specifically for your machine.


-e 
[*] If you want to do the build/install manually, there are instructions in the "README.md" file.
-e 
[*] Please report any bugs/problems at https://github.com/FreedomBen/rtl8188ce-linux-driver


-e 
[*] You will need sudo privileges in order to complete this install.
[*] Press <Enter> when ready to begin, or <Ctrl+C> to quit
-e 
[*] Let's install any dependencies you will need in order to build the driver.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
gcc is already the newest version.
linux-headers-3.13.0-24-generic is already the newest version.
linux-headers-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
git is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
-e 
[*] Now let's compile the driver from source and copy the files to the right directories
if [ -e verify_branch.sh ] ; \
    then \
        ./verify_branch.sh ; \
    fi;
Verifying a sane branch for your kernel version...
Yes
make -C /lib/modules/3.13.0-24-generic/build M=/home/tanmay/Downloads/rtl8188ce-linux-driver-master/rtl8188ce-linux-driver modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make[1]: Entering directory `/home/tanmay/Downloads/rtl8188ce-linux-driver-master/rtl8188ce-linux-driver/rtl8192c'
make -C /lib/modules/3.13.0-24-generic/build M=/home/tanmay/Downloads/rtl8188ce-linux-driver-master/rtl8188ce-linux-driver/rtl8192c modules
make[2]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make[1]: Leaving directory `/home/tanmay/Downloads/rtl8188ce-linux-driver-master/rtl8188ce-linux-driver/rtl8192c'
make[1]: Entering directory `/home/tanmay/Downloads/rtl8188ce-linux-driver-master/rtl8188ce-linux-driver/rtl8192ce'
make -C /lib/modules/3.13.0-24-generic/build M=/home/tanmay/Downloads/rtl8188ce-linux-driver-master/rtl8188ce-linux-driver/rtl8192ce modules
make[2]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
  CC [M]  /home/tanmay/Downloads/rtl8188ce-linux-driver-master/rtl8188ce-linux-driver/rtl8192ce/trx.o
/home/tanmay/Downloads/rtl8188ce-linux-driver-master/rtl8188ce-linux-driver/rtl8192ce/trx.c: In function &#8216;rtl92ce_rx_query_desc&#8217;:
/home/tanmay/Downloads/rtl8188ce-linux-driver-master/rtl8188ce-linux-driver/rtl8192ce/trx.c:396:3: error: implicit declaration of function &#8216;_ieee80211_is_robust_mgmt_frame&#8217; [-Werror=implicit-function-declaration]
   if ( ( _ieee80211_is_robust_mgmt_frame( hdr ) ) &&
   ^
cc1: some warnings being treated as errors
make[3]: *** [/home/tanmay/Downloads/rtl8188ce-linux-driver-master/rtl8188ce-linux-driver/rtl8192ce/trx.o] Error 1
make[2]: *** [_module_/home/tanmay/Downloads/rtl8188ce-linux-driver-master/rtl8188ce-linux-driver/rtl8192ce] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/tanmay/Downloads/rtl8188ce-linux-driver-master/rtl8188ce-linux-driver/rtl8192ce'
make: *** [all] Error 2
-e 
[*] The build has failed! Please make sure you have all dependencies installed and you are building on the correct branch (kernel version, not linux distro version, is most important for the branch)

```


The open source driver works, but it's very slow and there's random packet drops and extra latency. This makes it a real pain to do... pretty much anything.
Any help would be appreciated. Thanks!

---

### Post by varunendra on 2014-07-06
Welcome to the forums Tanmay!

So apparently, the driver code is still not compatible with the current kernel code even though it claims it is compatible. Can we see a diagnostics report to see if a backported driver can do the job or if there is something else we can tweak to make things better? Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

