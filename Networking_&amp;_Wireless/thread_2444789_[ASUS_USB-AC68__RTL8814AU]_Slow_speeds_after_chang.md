---
title: "[ASUS USB-AC68 / RTL8814AU] Slow speeds after changing driver (on Ubuntu 18.04 LTS)"
date: 2020-06-04
forum: Networking &amp; Wireless
---

### Post by scporse on 2020-06-04
**First a bit of context:**

I have been using [an older driver]("https://github.com/zebulon2/rtl8814au") for my "ASUS USB-AC68 / RTL8814AU" usb wireless network adapter until quite recently, when I decided to remove it and instead install the "88XXau" one  from [aircrack-ng git repository]("https://github.com/zebulon2/rtl8814au") (due to a suspicion of the old driver causing a  small delay when booting up).

After this change, however, my wifi speeds are quite bad. When  checking with speedtest.net (using the same server) I get 30-40mbps down  & 40-50 mbps up whereas, before, I was able to max out my internet  connection - which is 200/200 fiber. I am still able to max out my  internet connection when doing a speed test to the same server,  from my Android phone (connected to the same network, and from the same area in my home, as where my desktop computer is placed).

 Since the speed was just fine before changing the driver, I can only  assume that the slowness I see now, is due to some problem with the new  driver I have installed.

**Here is a link to all my wireless-info: [https://pastebin.com/YgZ2mNwN](https://pastebin.com/YgZ2mNwN)**

Things I have tried, this far (without any visible effect on connection speed):


[LIST]
[*]Disabling power saving for the WLAN adapter (currently disabled) 
[*]Changing MTU size for the WLAN interface from 2312 to 1500 
[*]Setting a static channel on my wifi network (instead of dynamic/auto) 
[*]Connecting to 2,4GHz wifi instead of 5GHz 
[*]Deselecting "make available to other users" on the connection in wifi settings
[*]Connecting the WLAN adapter to a different USB port 
[/LIST]

**A bit of extra info that might be of relevance:**

Output from "lshw -c network" (omitting ethernet/LAN adapter):

   *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:11
       logical name: wlan0
       serial: 4c:ed:fb:b6:f4:ff
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl88XXau ip=192.168.1.224 multicast=yes wireless=IEEE 802.11AC


Output from "dmesg" when reconnecting the device:

 [ 2065.077051] usb 1-11: new high-speed USB device number 8 using xhci_hcd
[ 2065.225541] usb 1-11: New USB device found, idVendor=0b05, idProduct=1853
[ 2065.225546] usb 1-11: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 2065.225549] usb 1-11: Product: 802.11ac NIC
[ 2065.225552] usb 1-11: Manufacturer: Realtek
[ 2065.225555] usb 1-11: SerialNumber: 123456
[ 2065.345770] usb 1-11: 88XXau 4c:ed:fb:b6:f4:ff hw_info[d8]
[ 2065.369906] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2065.794769] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2065.794796] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2065.852622] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2069.394466] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


Interface shown with "ip link":

 6: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 2312 qdisc mq state UP mode DORMANT group default qlen 1000     link/ether 4c:ed:fb:b6:f4:ff brd ff:ff:ff:ff:ff:ff 
A bit of upload/download statistics (to/from iperf server on same LAN):


 iPerf send:

 iperf3 -c 192.168.1.223 -p 2222
Connecting to host 192.168.1.223, port 2222
[  4] local 192.168.1.224 port 53388 connected to 192.168.1.223 port 2222
[ ID] Interval           Transfer     Bandwidth       Retr  Cwnd
[  4]   0.00-1.00   sec  8.79 MBytes  73.7 Mbits/sec    0    383 KBytes       
[  4]   1.00-2.00   sec  10.0 MBytes  84.0 Mbits/sec    0    766 KBytes       
[  4]   2.00-3.00   sec  11.2 MBytes  94.3 Mbits/sec    0   1.31 MBytes       
[  4]   3.00-4.00   sec  9.38 MBytes  78.7 Mbits/sec    0   1.77 MBytes       
[  4]   4.00-5.00   sec  9.63 MBytes  80.8 Mbits/sec    0   2.26 MBytes       
[  4]   5.00-6.00   sec  5.57 MBytes  46.7 Mbits/sec    0   2.54 MBytes       
[  4]   6.00-7.00   sec  10.4 MBytes  87.5 Mbits/sec    0   3.04 MBytes       
[  4]   7.00-8.00   sec  5.71 MBytes  47.9 Mbits/sec    0   3.04 MBytes       
[  4]   8.00-9.00   sec  10.9 MBytes  91.7 Mbits/sec    0   3.04 MBytes       
[  4]   9.00-10.00  sec  8.92 MBytes  74.9 Mbits/sec    0   3.04 MBytes       
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bandwidth       Retr
[  4]   0.00-10.00  sec  90.6 MBytes  76.0 Mbits/sec    0             sender
[  4]   0.00-10.00  sec  89.6 MBytes  75.2 Mbits/sec                  receiver

 iPerf receive:

 iperf3 -c 192.168.1.223 -p 2222 -R
Connecting to host 192.168.1.223, port 2222
Reverse mode, remote host 192.168.1.223 is sending
[  4] local 192.168.1.224 port 53404 connected to 192.168.1.223 port 2222
[ ID] Interval           Transfer     Bandwidth
[  4]   0.00-1.00   sec  4.43 MBytes  37.2 Mbits/sec                  
[  4]   1.00-2.00   sec  4.44 MBytes  37.3 Mbits/sec                  
[  4]   2.00-3.00   sec  4.43 MBytes  37.1 Mbits/sec                  
[  4]   3.00-4.00   sec  4.43 MBytes  37.1 Mbits/sec                  
[  4]   4.00-5.00   sec  4.48 MBytes  37.5 Mbits/sec                  
[  4]   5.00-6.00   sec  4.48 MBytes  37.5 Mbits/sec                  
[  4]   6.00-7.00   sec  4.47 MBytes  37.5 Mbits/sec                  
[  4]   7.00-8.00   sec  4.48 MBytes  37.6 Mbits/sec                  
[  4]   8.00-9.00   sec  4.45 MBytes  37.3 Mbits/sec                  
[  4]   9.00-10.00  sec  4.45 MBytes  37.3 Mbits/sec                  
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bandwidth       Retr
[  4]   0.00-10.00  sec  45.6 MBytes  38.3 Mbits/sec    1             sender
[  4]   0.00-10.00  sec  45.6 MBytes  38.3 Mbits/sec                  receiver

[HR][/HR]
Please let me know if more information is required to properly assist me with this issue.

Any input would be much  appreciated, as I really would like to avoid reverting to the old driver :)

---

### Post by chili555 on 2020-06-04
```
wlan0     IEEE 802.11AC  ESSID:"moonraker"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:5.22 GHz  Access Point: <MAC 'moonraker' [AC1]>  
          Bit Rate:400 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
         [COLOR="#FF0000"] Encryption key:****-****-****-****-****-****-****-****   Security mode:open[/COLOR]
          Power Management:off
          Link Quality=66/100  Signal level=48/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```This implies that either you have erroneously set the encryption mode in Network Manager to the ancient, insecure and largely forgotten WEP or else, the router is set to autoselect WEP, WPA or WPA2. I always recommend the very latest and most secure encryption method *only*; in this case, WPA2, as fixed and not autoselect.

What can you tell us about this eye-popping finding?

---

### Post by scporse on 2020-06-04
Hmm.. I see what you mean, but I don't understand why it would show up  with "security mode: open", since the network has in fact been  configured with WPA Personal / WPA2 as seen in [this screendump from my wifi config page]("https://drive.google.com/file/d/1zxGNTZMryTBqrxWuZVoyQwlUyYYPvg6D/view?usp=drivesdk").


This is also confirmed by network-manager:

nmcli device wifi list

IN-USE  SSID       MODE   CHAN  RATE        SIGNAL  BARS  SECURITY 
*       moonraker  Infra  44    270 Mbit/s  66      &#9602;&#9604;&#9606;_  WPA2


EDIT: fixing link for universal access.

---

### Post by scporse on 2020-06-04
It seems there is no problem with security and encryption on my wifi network, as per this thread on Ubiquiti forums, which adresses the security mode "open" that was reported by iwconfig: [https://community.ui.com/questions/Security-mode-open-but-WPA2-configured-3-7-37/8780b708-4b5a-45e8-806e-1a91920f4377#answer/3af0cbf4-8b0b-42db-ba4f-7d9f30083ab7](https://community.ui.com/questions/Security-mode-open-but-WPA2-configured-3-7-37/8780b708-4b5a-45e8-806e-1a91920f4377#answer/3af0cbf4-8b0b-42db-ba4f-7d9f30083ab7)

---

### Post by chili555 on 2020-06-04
It certainly goes further than the word "open." Please notice the encryption key in plain text (It is redacted, as are all sensitive details, in the wireless script). 

Here, for comparison, is my iwconfig:

```
wlp3s0    IEEE 802.11  ESSID:"GBR5"  
          Mode:Managed  Frequency:5.745 GHz  Access Point:xx:xx:xx
          Bit Rate=468 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:111   Missed beacon:0
```No key, no open.

It looks suspicious to me.

---

### Post by scporse on 2020-06-04
I see that, but still I don't think there is a problem since all looks well when checking again with wpa_cli status and iwlist:

sudo wpa_cli status
Selected interface 'wlan0'
bssid=<omitted>
freq=5220
ssid=moonraker
id=0
mode=station
pairwise_cipher=CCMP
group_cipher=CCMP
key_mgmt=WPA2-PSK
wpa_state=COMPLETED
ip_address=192.168.1.224
p2p_device_address=<omitted>
address=<omitted>
uuid=<omitted>

sudo iwlist wlan0 scan

wlan0     Scan completed :
          Cell 01 - Address:  <omitted>
                    ESSID:"moonraker"
                    Protocol:IEEE 802.11AC
                    Mode:Master
                    Frequency:5.22 GHz (Channel 44)
                    Encryption key:on
                    Bit Rates:867 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=68/100  Signal level=45/100  
                    Extra:fm=0003

Cell 03 - Address:  <omitted>
                    ESSID:"moonraker guest"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=100/100  Signal level=52/100  
                    Extra:fm=0003
          Cell 04 - Address: <omitted>
                    ESSID:"moonraker"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=86/100  Signal level=43/100  
                    Extra:fm=0003

---

### Post by scporse on 2020-06-04
I think [this thread on LinuxQuestions]("https://www.linuxquestions.org/questions/slackware-14/wpa2-encryption-key-off-818527/") gives a partial explanation of why the particular command of "sudo iwconfig" would report security mode: open (and why it's not  necessarily any cause for concern).

But anyway, this whole discussion is a little off-topic, since I really don't see how it would have any impact on the network throughput/speed that I'm able to get on the WLAN interface.

---

### Post by scporse on 2020-06-04
Btw, I don't get any "encryption key" or "security mode" output either, when I do just the command iwconfig. 
Only when executing that same command with sudo, I see the aforementioned output. Did you use sudo when running the iwconfig command, or no?

---

### Post by praseodym on 2020-06-04
Lets try deactivating the power management of the network manager

```
sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
sudo systemctl restart network-manager.service
```

---

### Post by scporse on 2020-06-04
> **praseodym said:**
> Lets try deactivating the power management of the network manager

```
sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
sudo systemctl restart network-manager.service
```

Thanks for the suggestion, but I already did this, as noted in my initial post.

Proof:
```

cat /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
[connection]
wifi.powersave = 2
```

---

### Post by chili555 on 2020-06-04
> Did you use sudo when running the iwconfig command, or no?Please see:

```
chili@T440p:~$ sudo iwconfig
[sudo] password for chili: 
wlp3s0    IEEE 802.11  ESSID:"GBR5"  
          Mode:Managed  Frequency:5.745 GHz  Access Point: xx:xx:xx
          Bit Rate=390 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:105   Missed beacon:0

lo        no wireless extensions.

enp0s25   no wireless extensions.

```The issue is only relevant because some Linux wireless drivers struggle with WEP and WPA/WPA2-TKIP. I'm simply trying to rule out this possibility.

---

### Post by scporse on 2020-06-05
> **chili555 said:**
> Please see:

```
chili@T440p:~$ sudo iwconfig
[sudo] password for chili: 
wlp3s0    IEEE 802.11  ESSID:"GBR5"  
          Mode:Managed  Frequency:5.745 GHz  Access Point: xx:xx:xx
          Bit Rate=390 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:105   Missed beacon:0

lo        no wireless extensions.

enp0s25   no wireless extensions.

```The issue is only relevant because some Linux wireless drivers struggle with WEP and WPA/WPA2-TKIP. I'm simply trying to rule out this possibility.


OK, well how would I go about ruling it out completely?

---

