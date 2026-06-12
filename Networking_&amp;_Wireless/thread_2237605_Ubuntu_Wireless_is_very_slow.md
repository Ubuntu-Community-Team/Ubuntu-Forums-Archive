---
title: "Ubuntu Wireless is very slow"
date: 2014-08-02
forum: Networking &amp; Wireless
---

### Post by l-combs on 2014-08-02
Hello,

I'm running Ubuntu 14.04 LTS on a dell laptop

My wireless is very slow in spells with high ping times.

About my wireless chipset:

```

lucas@lucas-ubuntu:~$ sudo lshw -C network
[sudo] password for lucas: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 05
       serial: 18:03:73:84:c1:53
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:50 ioport:e000(size=256) memory:f1104000-f1104fff memory:f1100000-f1103fff
  *-network
       description: Wireless interface
       product: Centrino Wireless-N 1030 [Rainbow Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: wlan0
       version: 34
       serial: ac:72:89:87:fc:ad
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-32-generic firmware=18.168.6.1 ip=192.168.1.50 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:53 memory:f7e00000-f7e01fff
lucas@lucas-ubuntu:~$ 

```
```

lucas@lucas-ubuntu:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"CCOMBS 2.0"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 04:A1:51:B8:3A:3D   
          Bit Rate=6 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:501   Missed beacon:0



```

---

### Post by chili555 on 2014-08-03
I own and use successfully two Intel wireless devices. I have honed a few techniques in several years and thousands of forum posts.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router.

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

If these changes do not help, please try:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```If it helps, make it permanent:```
sudo -i
echo "options iwlwifi 11n_disable=1"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```It may take a reboot to reconnect.

---

### Post by l-combs on 2014-08-10
I started to run the commands you posted and about 2 or 3 in, I lost connection to WIFI. After I rebooted everything was fine and has been for the most part, but the real test will be over the next couple of weeks

---

### Post by chili555 on 2014-08-10
> **l-combs said:**
> I started to run the commands you posted and about 2 or 3 in, I lost connection to WIFI. After I rebooted everything was fine and has been for the most part, but the real test will be over the next couple of weeksGlad to hear it! I will look forward to your further reports.

---

