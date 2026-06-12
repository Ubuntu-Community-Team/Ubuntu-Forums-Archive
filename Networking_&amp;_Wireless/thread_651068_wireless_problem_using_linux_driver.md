---
title: "wireless problem using linux driver"
date: 2007-12-27
forum: Networking &amp; Wireless
---

### Post by go_beep_yourself on 2007-12-27
I tried using Vista x86 and x64 drivers with ndiswrapper. Neither
appeared to work.I thought I had to use ndiswrapper, but as I was
browsing around the web to find the windows driver, I found a linux
driver, so I began to follow the directions, but got stuck while
running a command didn't work. I have no experience with wireless in
Linux.

```
chris@ubuntu:~/Desktop/rtl8185_linux_26.1027.0823.2007$ ls
ifcfg-wlan0  release_note    wlan0dhcp  wpa_supplicant-0.4.9.tar.gz
makedrv      rtl8185.tar.gz  wlan0down
readme       stack.tar.gz    wlan0up
chris@ubuntu:~/Desktop/rtl8185_linux_26.1027.0823.2007$ cat readme
RTL8185 Linux Driver v1027.0823.2007 for linux kernel 2.6

  - Support Client mode for either infrastructure or adhoc mode
  - Support WEP and WPAPSK/WPA2PSK connection

===============================================================================================
< Component >
The driver is composed of several parts:
    (1)source code
        rtl8185.tar.gz
        stack.tar.gz

    (2)Script ot build the modules
        makedrv

    (3)Script to load/unload modules
        wlan0up
        wlan0down

    (4)Script and configuration for DHCP
        wlan0dhcp
        ifcfg-wlan0

    (5)Supplicant source code
        wpa_supplicant-0.4.9.tar.gz

    (6)Example of supplicant configuration file
        wpa1.conf




< Installation >
Running the scripts can finish all operations of building up modules
from source code and start the nic:

        (1)Build up the driver from the source code
                ./makedrv

        (2)Load the driver module to kernel and start up nic
                ./wlan0up
           (if "insmod: error inserting 'r8180.ko': -File exists." met,
                ./wlan0rmv
                ./wlan0down
                ./wlan0up
            should be OK.
           )
        (3)Refer to < Set wireless lan MIBs > to set Wireless LAN
specific parameters.





< Set wireless lan MIBs >
This driver uses Wireless Extension as an interface allowing you to set
Wireless LAN specific parameters.

Current driver supports "iwlist" to show the device status of nic

        iwlist wlan0 [parameters]
where

        parameter explaination          [parameters]
        -----------------------         -------------
        Show available chan and freq    freq / channel
        Show and Scan BSS and IBSS      scan[ning]
        Show supported bit-rate         rate / bit[rate]
        Show Power Management mode      power

For example:

        iwlist wlan0 channel
        iwlist wlan0 scan
        iwlist wlan0 rate
        iwlist wlan0 power


Driver also supports "iwconfig", manipulate driver private ioctls, to set MIBs.

        iwconfig wlan0 [parameters] [val]
where

        parameter explaination      [parameters]                [val]
constraints
        -----------------------     -------------
------------------
        Connect to AP by address    ap                          [essid]
        Set the essid, join (I)BSS  essid                       [mac_addr]
        Set operation mode          mode                        {Managed|Ad-hoc}
        Set keys and security mode  key / enc[ryption]
{N|open|restricted|off}


For example:

        iwconfig wlan0 ap XX:XX:XX:XX:XX:XX
        iwconfig wlan0 essid "ap_name"
        iwconfig wlan0 mode Ad-hoc
        iwconfig wlan0 mode essid "name" mode Ad-hoc
        iwconfig wlan0 key 0123456789 [2] open
        iwconfig wlan0 key off
        iwconfig wlan0 key restricted [3] 0123456789

< Getting IP address >
After start up the nic, the network needs to obtain an IP address
before transmit/receive data.
This can be done by setting the static IP via "ifconfig wlan0
IP_ADDRESS" command, or using DHCP.

If using DHCP, setting steps is as below:

        (1)connect to an AP via "iwconfig" settings
                iwconfig wlan0 essid [name]     or
                iwconfig wlan0 ap XX:XX:XX:XX:XX:XX

        (2)run the script which run the dhclient
                ./wlan0dhcp
           or
                dhcpcd wlan0
                (Some network admins require that you use the
                hostname and domainname provided by the DHCP server.
                In that case, use
                dhcpcd -HD wlan0)



< WPAPSK >
WPA_SUPPLICANT help the network to communicate under the protection of
WPAPSK mechanism

        (1)Unpack source code of WPA supplicant:
                tar -zxvf wpa_supplicant-0.4.9.tar.gz
                cd wpa_supplicant-0.4.9

        (2)Create .config file:
                cp defconfig .config

        (3)Edit .config file, uncomment the following line:
                #CONFIG_DRIVER_IPW=y.

        (4)Build WPA supplicant:
                make

        If make error for lack of <include/md5.h>, install the openssl lib:
         1. Install the openssl lib from corresponding installation disc:
            Fedora Core 2/3/4/5/6/7(openssl-0.9.71x-xx),
            Mandrake10.2/Mandriva10.2(openssl-0.9.7x-xmdk),
            Debian 3.1(libssl-dev), Suse 9.3/10.0/10.1(openssl_devl),
            Gentoo(dev-libs/openssl), etc.
         2. Download the openssl open source package from
www.openssl.org, build and install it.

        (5)Edit wpa_supplicant.conf to set up SSID and its passphrase.
        For example, the following setting in "wpa1.conf" means SSID
to join is "BufAG54_Ch6"
        and its passphrase is "87654321".

                network={
                        ssid="BufAG54_Ch6"
                        proto=WPA
                        key_mgmt=WPA-PSK
                        pairwise=CCMP TKIP
                        group=CCMP TKIP WEP104 WEP40
                        psk="87654321"
                        priority=2
                }
        Note: 1. proto=WPA for WPA, proto=RSN for WPA2.
              2. If you want to connect an AP which works under WPA2
mixed mode, you'd better
                 use Realtek customed wpa_supplicant package.


        (6)Execute WPA supplicant (Assume 8185 and related modules had
been loaded):
                ./wpa_supplicant -D ipw -c wpa1.conf -i wlan0 &
chris@ubuntu:~/Desktop/rtl8185_linux_26.1027.0823.2007$   ./makedrv
./ieee80211/
./ieee80211/ieee80211_module.c
./ieee80211/ieee80211_rx.c
./ieee80211/tags
./ieee80211/Makefile
./ieee80211/ieee80211_crypt_tkip.c
./ieee80211/ieee80211_softmac.c
./ieee80211/readme
./ieee80211/ieee80211_crypt_ccmp.c
./ieee80211/ieee80211.h
./ieee80211/ieee80211_tx.c
./ieee80211/ieee80211_softmac_wx.c
./ieee80211/ieee80211_crypt.h
./ieee80211/ieee80211_wx.c
./ieee80211/license
./ieee80211/ieee80211_crypt_wep.c
./ieee80211/ieee80211_crypt.c
rtl8185/
rtl8185/README.adhoc
rtl8185/r8180_sa2400.h
rtl8185/Makefile
rtl8185/copying
rtl8185/README.master
rtl8185/r8180.h
rtl8185/install
rtl8185/r8180_max2820.h
rtl8185/r8180_max2820.c
rtl8185/r8180_rtl8225.h
rtl8185/r8180_wx.h
rtl8185/authors
rtl8185/tags
rtl8185/r8180_pm.c
rtl8185/r8180_hw.h
rtl8185/r8180_gct.c
rtl8185/r8180_gct.h
rtl8185/r8180_rtl8225.c
rtl8185/readme
rtl8185/r8180_93cx6.h
rtl8185/ieee80211.h
rtl8185/license
rtl8185/r8180_pm.h
rtl8185/changes
rtl8185/r8180_rtl8225z2.c
rtl8185/r8180_wx.c
rtl8185/r8180_rtl8255.c
rtl8185/r8180_93cx6.c
rtl8185/r8180_sa2400.c
rtl8185/r8180_core.c
rtl8185/r8180_rtl8255.h
rtl8185/ieee80211_crypt.h
rm -f *.mod.c *.mod *.o .*.cmd *.ko
rm -rf /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/tmp
make -C /lib/modules/2.6.22.9chris1/build
M=/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211 CC=gcc
modules
make[1]: Entering directory `/usr/src/linux-source-2.6.22'
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.o
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:
In function 'ieee80211_softmac_init':
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2236:
warning: assignment from incompatible pointer type
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2237:
warning: assignment from incompatible pointer type
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2238:
warning: assignment from incompatible pointer type
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2239:
warning: assignment from incompatible pointer type
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2240:
warning: assignment from incompatible pointer type
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2241:
warning: assignment from incompatible pointer type
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_rx.o
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_tx.o
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_wx.o
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_module.o
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac_wx.o
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt.o
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.o
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:
In function 'ieee80211_ccmp_aes_encrypt':
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:88:
warning: passing argument 1 of 'crypto_cipher_encrypt_one' from
incompatible pointer type
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:
In function 'ieee80211_ccmp_init':
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:110:
warning: assignment from incompatible pointer type
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:127:
warning: passing argument 1 of 'crypto_free_cipher' from incompatible
pointer type
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:
In function 'ieee80211_ccmp_deinit':
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:144:
warning: passing argument 1 of 'crypto_free_cipher' from incompatible
pointer type
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:
In function 'ieee80211_ccmp_set_key':
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:422:
warning: passing argument 1 of 'crypto_cipher_setkey' from
incompatible pointer type
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip.o
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_wep.o
  LD [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211-rtl.o
  LD [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt-rtl.o
  LD [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_wep-rtl.o
  LD [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip-rtl.o
  LD [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp-rtl.o
  Building modules, stage 2.
  MODPOST 5 modules
  CC      /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211-rtl.mod.o
  LD [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211-rtl.ko
  CC      /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt-rtl.mod.o
  LD [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt-rtl.ko
  CC      /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp-rtl.mod.o
  LD [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp-rtl.ko
  CC      /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip-rtl.mod.o
  LD [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip-rtl.ko
  CC      /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_wep-rtl.mod.o
  LD [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_wep-rtl.ko
make[1]: Leaving directory `/usr/src/linux-source-2.6.22'
rm -f *.mod.c *.mod *.o .*.cmd *.ko *~
rm -rf /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/tmp
make -C /lib/modules/2.6.22.9chris1/build
M=/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185 CC=gcc
modules
make[1]: Entering directory `/usr/src/linux-source-2.6.22'
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.o
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:
In function 'proc_get_stats_hw':
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:375:
warning: cast from pointer to integer of different size
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:376:
warning: cast from pointer to integer of different size
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:379:
warning: cast from pointer to integer of different size
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:380:
warning: cast from pointer to integer of different size
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:383:
warning: cast from pointer to integer of different size
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:384:
warning: cast from pointer to integer of different size
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:
In function 'check_tx_ring':
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:909:
warning: cast from pointer to integer of different size
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:909:
warning: cast from pointer to integer of different size
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:910:
warning: cast from pointer to integer of different size
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:910:
warning: cast from pointer to integer of different size
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:
In function 'alloc_tx_desc_ring':
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:1592:
warning: cast from pointer to integer of different size
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:1592:
warning: cast to pointer from integer of different size
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:
In function 'alloc_rx_desc_ring':
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:1770:
warning: cast from pointer to integer of different size
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:1770:
warning: cast to pointer from integer of different size
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:
In function 'rtl8180_init':
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:3159:
warning: assignment from incompatible pointer type
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:3522:
warning: 'deprecated_irq_flag' is deprecated (declared at
include/linux/interrupt.h:66)
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:3522:
warning: passing argument 2 of 'request_irq' from incompatible pointer
type
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:
At top level:
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:579:
warning: 'r8180_get_wireless_stats' defined but not used
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_sa2400.o
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_93cx6.o
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_wx.o
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_max2820.o
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_gct.o
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_rtl8225.o
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_rtl8225z2.o
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_rtl8255.o
  LD [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "ieee80211_softmac_stop_protocol_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "free_ieee80211_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_get_wap_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wake_queue_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_rx_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_get_mode_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_is_shortslot"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_set_freq_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_get_name_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_get_rate_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_set_rate_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_ps_tx_ack"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_get_freq_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_is_54g"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_stop_queue_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_set_scan_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_get_essid_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_get_scan_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wpa_supplicant_ioctl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_set_mode_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_get_beacon"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_set_rawtx_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_set_encode_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_stop_protocol_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_set_wap_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_get_power_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_get_encode_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_softmac_start_protocol_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wlan_frequencies_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_set_power_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "alloc_ieee80211_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_reset_queue"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_set_essid_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_start_protocol_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
  CC      /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.mod.o
  LD [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko
make[1]: Leaving directory `/usr/src/linux-source-2.6.22'
chris@ubuntu:~/Desktop/rtl8185_linux_26.1027.0823.2007$ ./wlan0up
insmod: error inserting 'ieee80211_crypt-rtl.ko': -1 Operation not permitted
insmod: error inserting 'ieee80211_crypt_wep-rtl.ko': -1 Operation not permitted
insmod: error inserting 'ieee80211_crypt_tkip-rtl.ko': -1 Operation
not permitted
insmod: error inserting 'ieee80211_crypt_ccmp-rtl.ko': -1 Operation
not permitted
insmod: error inserting 'ieee80211-rtl.ko': -1 Operation not permitted
insmod: error inserting 'r8180.ko': -1 Operation not permitted
wlan0: ERROR while getting interface flags: No such device
chris@ubuntu:~/Desktop/rtl8185_linux_26.1027.0823.2007$ sudo ./wlan0up
[sudo] password for chris:
wlan0: ERROR while getting interface flags: No such device
chris@ubuntu:~/Desktop/rtl8185_linux_26.1027.0823.2007$
```

Why does it say wlan0, no such device? I appended this to my
/etc/network/interfaces

```
iface wlan0 inet dhcp

auto wlan0


```
and I restarted the networking service.

---

