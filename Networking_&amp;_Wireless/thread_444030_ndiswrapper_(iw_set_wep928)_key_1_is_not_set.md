---
title: "ndiswrapper (iw_set_wep:928): key 1 is not set"
date: 2007-05-15
forum: Networking &amp; Wireless
---

### Post by theachillius on 2007-05-15
Hi all,

I am struggling to setup my wireless network interface on Ubuntu 7.04. I have set up Dlink DWL-G122 Rev. D1 using ndiswrapper and installed wifi-radar as my network manager.  My router is set up on WEP/Shared/64 bit /Ascii key.

Below are messages from /var/log/messages

May 14 23:53:25 labster kernel: [ 6007.604111] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May 14 23:53:25 labster kernel: [ 6007.644196] ADDRCONF(NETDEV_UP): eth0: link is not ready
May 14 23:53:25 labster kernel: [ 6007.646677] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
May 14 23:53:26 labster kernel: [ 6008.589467] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
May 14 23:53:40 labster dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
May 14 23:53:40 labster dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
May 14 23:53:40 labster dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
May 14 23:53:51 labster kernel: [ 6033.516160] ndiswrapper (iw_set_wep:928): key 1 is not set

Can you please help me ?

Milind

---

### Post by chili555 on 2007-05-15
I have never seen this message before, so I am making some educated guesses here. Many routers can use up to four unique WEP keys. You can tell your router to use key #3, for example. Linux generally assumes you are using key #1 unless you specify otherwise. I'd guess key #1 is not set to *any* value in your router and, since you have not specified key #3, or whatever is being broadcast, in *iwconfig* or Network Manager, etc. there is no match.

I'd go into the administration page of your router and be sure your key is in postion 1 and key #1 is being broadcast.

---

### Post by theachillius on 2007-05-15
First of all, thanks for your reply !
the router is set Key#1 and thats the one I have configured using wifi-radar. Do you want me to upload any specific config file info or run any tests ?

Milind

---

### Post by theachillius on 2007-05-15
Anyone , any help? Can any one please help me fix this issue?

---

### Post by chili555 on 2007-05-16
May we please see the output of:```
sudo iwlist eth1 key
```Please obscure your key in part. Thanks.

---

### Post by theachillius on 2007-05-16
Hi, Thank you verymuch for your time and help !
I rebooted my laptop and the wifi-radar asked me to chose from 64/128 bit hex/ascii keys  and Open/Shared system and I could precisely enter what I was looking for.
The internet is now working:

geeko@labster:~/downloads$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"dlink"  Nickname:"dlin"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:15:E9:6B:A9:38   
          Bit Rate=1 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:39/100  Signal level:-71 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
-------------------------------------------------------------------------------------------------------------------------
Just incase anyone else would be interested here is how i got it working

1. Install ndiswrapper so we can use the windows driver.

sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9

sudo dpkg -i ndiswrapper-*

2. Make sure your Dlink Adapter is detected. $lsusb Bus 004 Device 002: ID 07d1:3B01 D-Link System

3. Extract the driver from the Driver Installation CD or download it from [ftp://ftp.dlink.com/Wireless/dwlg122_revD/Drivers/DWLG122_revD_drivers_210.zip](ftp://ftp.dlink.com/Wireless/dwlg122_revD/Drivers/DWLG122_revD_drivers_210.zip)

sudo ndiswrapper -i usb55n5x.inf

4. ndiswrapper -l

Installed ndis drivers:

geeko@labster:~$ ndiswrapper -l

usb55n5x :driver installed device (07D1:3B01) present

sudo depmod -a sudo modprobe ndiswrapper

5.Edit /etc/modules file and add ndiswrapper module to be loaded at every system boot.

vi /etc/modules

--Append ndiswrapper to the file

---

