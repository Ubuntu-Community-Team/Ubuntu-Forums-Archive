---
title: "WiFi Problems with Intel 5100 AGN - AP disappear until reboot"
date: 2015-06-02
forum: Networking &amp; Wireless
---

### Post by alberto666 on 2015-06-02
I am having a problem with the WiFi connection in Ubuntu 15.04.

Usually it starts and connects fine, but after a while, it disconnect. Usually when I use it a bit more heavily (e.g. aMule use).
Weirdly, it does not reconnect. And not only that, I can see other APs but not the one I was connected to until I reboot. Every other device at home can. And router is quite close, so that cannot be the problem.
The only solution is to reboot.

In Windows 8.1 it works perfectly.

My computer is a VAIO VGN-SR49XN laptop with 4 GB of RAM, Core 2 Duo processor.

_**What have I already done to try to fix it?**_
[LIST]
[*] Disable ipv6 globally.
[*] Change /etc/default/crda to set a different country code (REGDOMAIN).
[*] Tried changing options (like disabling 11n) in "***/etc/modprobe.d/iwlwifi.conf***": ***options iwlwifi 11n_disable=1 bt_coex_active=0 power_save=0 auto_agg=0 swcrypto=1***. And just in case, this as well: ***options iwlagn 11n_disable=1 11n_disable50=1***
[*] Download and use the new iwlwifi-5000-1.ucode version from intellinuxwireless.org (iwlwifi-5000-ucode-8.83.5.1-1).
[/LIST]

Here I attach some information about my configuration a:


```
#### /etc/lsb-release ####
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=15.04
DISTRIB_CODENAME=vivid
DISTRIB_DESCRIPTION="Ubuntu 15.04"


#### lspci ####
04:00.0 Network controller: Intel Corporation WiFi Link 5100

#### lsusb ####
Bus 002 Device 002: ID 13fd:0840 Initio Corporation INIC-1618L SATA
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 044e:3017 Alps Electric Co., Ltd BCM2046 Bluetooth Device
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05ca:183e Ricoh Co., Ltd Visual Communication Camera VGP-VCC9 [R5U870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 147e:1000 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info #####
####rfkill list ####
0: sony-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: sony-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


####some lsmod info ####
btusb                  32768  0 
bluetooth             491520  22 bnep,btusb,rfcomm
iwldvm                237568  0 
ip6table_filter        16384  1 
ip6_tables             28672  1 ip6table_filter
ath                    32768  3 ath9k_common,ath9k_htc,ath9k_hw
mac80211              720896  2 iwldvm,ath9k_htc
x_tables               36864  13 ip6table_filter,xt_hl,ip_tables,xt_tcpudp,xt_limit,xt_conntrack,xt_LOG,iptable_filter,ip6t_rt,ipt_REJECT,ip6_tables,xt_addrtype,ip6t_REJECT


####iwconfig ####

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"XXXXXXXXXXXX"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: XXXXXXXXXXXXXXXX
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:393  Invalid misc:9251   Missed beacon:0

lo        no wireless extensions.


####iwlist channel####
eth0      no frequency information.

wlan0     18 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:2.457 GHz (Channel 10)

lo        no frequency information.


#### Some information from syslog when connecting (***cat /var/log/syslog | grep -e etwork -e iwl | less***)
Jun  2 16:11:26 null kernel: [    6.977696] iwlwifi: unknown parameter '11n_disable50' ignored
Jun  2 16:11:26 null kernel: [    6.977702] iwlwifi: unknown parameter 'auto_agg' ignored
Jun  2 16:11:26 null kernel: [    6.977706] iwlwifi: unknown parameter '11n_disable50' ignored
Jun  2 16:11:26 null kernel: [    6.977708] iwlwifi: unknown parameter 'auto_agg' ignored
Jun  2 16:11:26 null kernel: [    6.978032] iwlwifi 0000:04:00.0: can't disable ASPM; OS doesn't have ASPM control
Jun  2 16:11:26 null kernel: [    6.999556] iwlwifi 0000:04:00.0: loaded firmware version 8.83.5.1 build 33692 op_mode iwldvm
Jun  2 16:11:26 null kernel: [    7.030186] iwlwifi 0000:04:00.0: CONFIG_IWLWIFI_DEBUG disabled
Jun  2 16:11:26 null kernel: [    7.030189] iwlwifi 0000:04:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
Jun  2 16:11:26 null kernel: [    7.030192] iwlwifi 0000:04:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
Jun  2 16:11:26 null kernel: [    7.030194] iwlwifi 0000:04:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
Jun  2 16:11:26 null kernel: [    7.032087] iwlwifi 0000:04:00.0: L1 Enabled - LTR Disabled
Jun  2 16:11:26 null kernel: [    7.086768] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'


and the only error I find: 
Jun  2 16:11:30 null NetworkManager[1877]: <error> [1433254290.464083] [dns-manager/nm-dns-dnsmasq.c:398] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name

#### dmesg information ####
dmesg | grep -e etwork -e iwl 
[    6.977696] iwlwifi: unknown parameter '11n_disable50' ignored
[    6.977702] iwlwifi: unknown parameter 'auto_agg' ignored
[    6.978032] iwlwifi 0000:04:00.0: can't disable ASPM; OS doesn't have ASPM control
[    6.999556] iwlwifi 0000:04:00.0: loaded firmware version 8.83.5.1 build 33692 op_mode iwldvm
[    7.030186] iwlwifi 0000:04:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    7.030189] iwlwifi 0000:04:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    7.030192] iwlwifi 0000:04:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    7.030194] iwlwifi 0000:04:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[    7.032087] iwlwifi 0000:04:00.0: L1 Enabled - LTR Disabled
[    7.086768] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    9.771972] audit: type=1400 audit(1433254286.600:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1719 comm="apparmor_parser"
[    9.771979] audit: type=1400 audit(1433254286.600:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=1719 comm="apparmor_parser"
[   12.049333] iwlwifi 0000:04:00.0: L1 Enabled - LTR Disabled
[   12.053292] iwlwifi 0000:04:00.0: Radio type=0x1-0x2-0x0
[   12.151264] iwlwifi 0000:04:00.0: L1 Enabled - LTR Disabled
[   12.154213] iwlwifi 0000:04:00.0: Radio type=0x1-0x2-0x0


```

May you need some other information to help me?

---

### Post by alberto666 on 2015-06-02
Here I attach information of "/var/log/syslog" error when WiFi disconnect:

```
Jun  2 21:30:16 null NetworkManager[1877]: <warn> Connection disconnected (reason 7)
Jun  2 21:30:16 null NetworkManager[1877]: <info> (wlan0): supplicant interface state: completed -> disconnected
Jun  2 21:30:16 null NetworkManager[1877]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jun  2 21:30:31 null NetworkManager[1877]: <warn> (wlan0): link timed out.
Jun  2 21:30:31 null NetworkManager[1877]: <info> (wlan0): device state change: activated -> failed (reason 'ssid-not-found') [100 120 53]
Jun  2 21:30:31 null NetworkManager[1877]: <info> NetworkManager state is now CONNECTED_LOCAL
Jun  2 21:30:31 null NetworkManager[1877]: <info> NetworkManager state is now DISCONNECTED
Jun  2 21:30:31 null NetworkManager[1877]: <warn> Activation (wlan0) failed for connection 'XXXMYWIFISSIDXXX'
Jun  2 21:30:31 null NetworkManager[1877]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jun  2 21:30:31 null NetworkManager[1877]: <info> (wlan0): deactivating device (reason 'none') [0]
Jun  2 21:30:31 null systemd[1]: Starting Network Manager Script Dispatcher Service...
Jun  2 21:30:31 null systemd[1]: Started Network Manager Script Dispatcher Service.
Jun  2 21:30:31 null NetworkManager[1877]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 2179
Jun  2 21:30:31 null NetworkManager[1877]: _nl_get_vtable: assertion 'vtable.handle' failed
Jun  2 21:30:31 null NetworkManager[1877]: <info> Writing DNS information to /sbin/resolvconf
Jun  2 21:30:31 null NetworkManager[1877]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.



```

---

### Post by alberto666 on 2015-06-05
Nobody can help me with this issue?

---

