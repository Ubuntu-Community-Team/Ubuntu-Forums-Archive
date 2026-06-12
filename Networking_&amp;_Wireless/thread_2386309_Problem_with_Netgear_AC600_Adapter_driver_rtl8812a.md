---
title: "Problem with Netgear AC600 Adapter driver rtl8812au"
date: 2018-03-03
forum: Networking &amp; Wireless
---

### Post by cryptoshun on 2018-03-03
Hello, I am trying to get my Netgear A6100 AC600 working but am having trouble installing the rtl8812au driver. I have no internet on the computer I want to work the wifi adapter. Here is what lsusb returned 

username@HomeComputer-OptiPlex-760:~$ lsusb
Bus 002 Device 002: ID 0846:9052 NetGear, Inc. A6100 AC600 DB Wireless Adapter [Realtek RTL8811AU]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 0718:0726 Imation Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 005: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Also, I have no other way to connect the internet to the machine I want to run the wifi adapter and have also tried the following:


username@HomeComputer-OptiPlex-760:~/Desktop/rtl8812AU-driver-4.3.14$ make
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/4.4.0-21-generic/build M=/home/username/Desktop/rtl8812AU-driver-4.3.14  modules
make[1]: Entering directory '/usr/src/linux-headers-4.4.0-21-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory '/usr/src/linux-headers-4.4.0-21-generic'
username@HomeComputer-OptiPlex-760:~/Desktop/rtl8812AU-driver-4.3.14$ sudo make install
[sudo] password for username: 
install -p -m 644 8812au.ko  /lib/modules/4.4.0-21-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 4.4.0-21-generic
username@HomeComputer-OptiPlex-760:~/Desktop/rtl8812AU-driver-4.3.14$ sudo modprobe 8812au
username@HomeComputer-OptiPlex-760:~/Desktop/rtl8812AU-driver-4.3.14$ 

Any help would be greatly appreciated. Thanks.

---

### Post by chili555 on 2018-03-03
So far, so good.

What does this tell us?```
modinfo 8812au | grep 9052
```

---

### Post by cryptoshun on 2018-03-03
username@HomeComputer-OptiPlex-760:~/Desktop/rtl8812AU-driver-4.3.14$ modinfo 8812au | grep 9052
alias:          usb:v0846p[COLOR=#ff0000]&#8203;9052[/COLOR]d*dc*dsc*dp*ic*isc*ip*in*

---

### Post by chili555 on 2018-03-03
It looks like the driver you compiled has claimed your device. Now let's check:```
iwconfig
dmesg | grep -e wl -e 8812
```And because I'm OCD suspicious:```
rfkill list all
```

---

### Post by cryptoshun on 2018-03-03
```
username@HomeComputer-OptiPlex-760:~/Desktop/rtl8812AU-driver-4.3.14$ iwconfig
enp0s25   no wireless extensions.


lo        no wireless extensions.


wlx8c3bad1288ee  unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


username@HomeComputer-OptiPlex-760:~/Desktop/rtl8812AU-driver-4.3.14$ dmesg | grep -e wl -e 8812
[  100.922433] 8812au: module verification failed: signature and/or required key missing - tainting kernel
[  113.790490] RTL871X: rtw_ndev_init(wlan0)
[  114.852322] rtl8821au 1-4:1.0 wlx8c3bad1288ee: renamed from wlan0
[  114.865245] IPv6: ADDRCONF(NETDEV_UP): wlx8c3bad1288ee: link is not ready
[  115.317403] IPv6: ADDRCONF(NETDEV_UP): wlx8c3bad1288ee: link is not ready
[  115.344843] IPv6: ADDRCONF(NETDEV_UP): wlx8c3bad1288ee: link is not ready
[11013.140858] RTL871X: rtw_ndev_uninit(wlx8c3bad1288ee)
[11127.718744] RTL871X: rtw_ndev_init(wlan0)
[11128.756090] rtl8821au 2-4:1.0 wlx8c3bad1288ee: renamed from wlan0
[11128.777276] IPv6: ADDRCONF(NETDEV_UP): wlx8c3bad1288ee: link is not ready
[11129.224552] IPv6: ADDRCONF(NETDEV_UP): wlx8c3bad1288ee: link is not ready
[11129.241939] IPv6: ADDRCONF(NETDEV_UP): wlx8c3bad1288ee: link is not ready

username@HomeComputer-OptiPlex-760:~/Desktop/rtl8812AU-driver-4.3.14$ rfkill list all
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

---

### Post by chili555 on 2018-03-03
Nothing too alarming there. Now the big one!```
sudo iwlist scan
```Just tell us if it sees networks or not and, if not, what the error or warning message was. We needn't see all the scan details.

---

### Post by cryptoshun on 2018-03-03
enp0s25 Interface doesn't support scanning.

lo Interface doesn't support scanning.

wlx8c3bad1288ee No scan results

---

### Post by chili555 on 2018-03-03
Please run:```
sudo iwlist chan
```Is your router on one of the listed channels? Is the SSID hidden? Any clues with:```
dmesg | grep -i rtl
```My favorite kind of problem: everything looks perfect but it just doesn't work.

---

### Post by cryptoshun on 2018-03-03
The SSID was hidden. Look what showed up:

username@HomeComputer-OptiPlex-760:~/Desktop/rtl8812AU-driver-4.3.14$ sudo iwlist scan
enp0s25   Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlx8c3bad1288ee  Scan completed :
          Cell 01 - Address: 8E:F5:A3:05:B8:3A
                    ESSID:"Verizon-SM-G930V-B83A"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=48/100  Signal level=100/100  
                    Extra:fm=0003

---

### Post by chili555 on 2018-03-03
Please click the Network Manager icon and connect.

---

### Post by cryptoshun on 2018-03-03
For some reason I still cannot connect. :confused: Any other thoughts?

---

### Post by chili555 on 2018-03-03
```
dmesg | grep -i -e rtl -e network
```Off for the evening. I'll check in tomorrow.

---

### Post by cryptoshun on 2018-03-03
username@HomeComputer-OptiPlex-760:~$ dmesg | grep -i -e rtl -e network
[    2.991662] e1000e: Intel(R) PRO/1000 Network Driver - 3.2.6-k
[    3.401393] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[   34.778835] RTL871X: module init start
[   34.778837] RTL871X: rtl8821au v4.3.14
[   34.778838] RTL871X: rtl8821au BT-Coex version = BTCOEX20150128-51
[   34.943704] RTL871X: rtw_ndev_init(wlan0)
[   34.944641] usbcore: registered new interface driver rtl8821au
[   34.944643] RTL871X: module init ret=0
[   34.965626] rtl8821au 2-4:1.0 wlx8c3bad1288ee: renamed from wlan0
[   36.504137] audit: type=1400 audit(1520113469.372:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=716 comm="apparmor_parser"
[   36.504141] audit: type=1400 audit(1520113469.372:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=716 comm="apparmor_parser"
[   42.204489] RTL871X: assoc success
[   42.210358] RTL871X: set group key camid:1, addr:00:00:00:00:00:00, kid:1, type:TKIP

[  642.202533] RTL871X: set group key camid:2, addr:00:00:00:00:00:00, kid:2, type:TKIP

---

### Post by chili555 on 2018-03-04
> [ 42.204489] RTL871X: assoc successIt looks like you did connect. We are confused by this:>  42.210358] RTL871X: set group key camid:1, addr:00:00:00:00:00:00, kid:1, type:TKIP

[ 642.202533] RTL871X: set group key camid:2, addr:00:00:00:00:00:00, kid:2, type:TKIPYour driver and old Chili hate TKIP; however, your scan says:```
Cell 01 - Address: 8E:F5:A3:05:B8:3A
ESSID:"Verizon-SM-G930V-B83A"
Protocol:IEEE 802.11bgn
Mode:Master
Frequency:2.437 GHz (Channel 6)
Encryption keyn
Bit Rates:144 Mb/s
Extra:rsn_ie=30140100000fac040100000fac040100000fa c020c00
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher :[COLOR="#FF0000"] CCMP[/COLOR]
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
Quality=48/100 Signal level=100/100 
Extra:fm=0003
```Please clarify. Is your router set to use TKIP or CCMP, also known as AES?

What happens when you try to connect?  Does it try and fail? Or...what?

FYI, my default advice is this.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
sudo nano /etc/default/crda
```Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd disable power saving in Network Manager; from the terminal:```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```Restart NM:```
sudo service network-manager restart
```

---

### Post by cryptoshun on 2018-03-04
I am OK until I try and disable power save in  Network Manager. I get

sed: can't read /etc/NetworkManager/conf.d/*: No such file or directory

---

### Post by jeremy31 on 2018-03-04
Post results for ```
ls /etc/NetworkManager/conf.d/
```

---

### Post by cryptoshun on 2018-03-04
ls: cannot access 'etc/NetworkManager.conf.d/' : No such file or directory

---

### Post by chili555 on 2018-03-04
> **cryptoshun said:**
> ls: cannot access 'etc/NetworkManager.conf.d/' : No such file or directoryIt is:```
ls /etc/NetworkManager[COLOR="#FF0000"]**/**[/COLOR]conf.d/
```Please try again.

---

### Post by cryptoshun on 2018-03-04
I tried it again, corrected, and only get another input line like this:

username@HomeComputer-OptiPlex-760:~$

---

### Post by cryptoshun on 2018-03-06
I followed all the directions given here on another (identical) computer and was able to get the Netgear adapter to work. So this is kinda solved, or in other words, everything in this thread worked, just on another machine.

I think the problem with the machine that refuses to allow me to use the adapter to connect to the internet has problems from when Ubuntu was installed and I was not able to figure out how to turn off pnpbios. For some reason, on this machine I no longer have a Network Manager Icon that allows me to connect. Any more help with getting this adapter to work on this machine would be appreciated, but I did get the adapter to work on my other machine that runs linux. 

Thank you Chili55 and Jeremy31 for all your help!

---

