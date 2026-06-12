---
title: "netgear n300 WNA3100 wifi adapter - 'dhclient wlan0' command doesn't works"
date: 2015-02-21
forum: Networking &amp; Wireless
---

### Post by clement6 on 2015-02-21
I have installed all the drivers needed and if i do ```
iwlist wlan0 scan
``` it detects all the wifi near me

This is the output of ifconfig:

```
**eth0      Link encap:Ethernet  HWaddr 00:09:6b:d8:cd:26  **
**          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0**
**          inet6 addr: fe80::209:6bff:fed8:cd26/64 Scope:Link**
**          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1**
**          RX packets:75 errors:0 dropped:0 overruns:0 frame:0**
**          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0**
**          collisions:0 txqueuelen:1000 **
**          RX bytes:10103 (10.1 KB)  TX bytes:8851 (8.8 KB)**


**lo        Link encap:Local Loopback  **
**          inet addr:127.0.0.1  Mask:255.0.0.0**
**          inet6 addr: ::1/128 Scope:Host**
**          UP LOOPBACK RUNNING  MTU:65536  Metric:1**
**          RX packets:32 errors:0 dropped:0 overruns:0 frame:0**
**          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0**
**          collisions:0 txqueuelen:0 **
**          RX bytes:2368 (2.3 KB)  TX bytes:2368 (2.3 KB)**


**wlan0     Link encap:Ethernet  HWaddr 44:94:fc:e8:09:f0  **
**          UP BROADCAST MULTICAST  MTU:1500  Metric:1**
**          RX packets:0 errors:0 dropped:0 overruns:0 frame:0**
**          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0**
**          collisions:0 txqueuelen:1000 **
[B]          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


[/B]

```

iwconfig:

```
**wlan0     IEEE 802.11g  ESSID:off/any  **
**          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   **
**          Bit Rate:300 Mb/s   Tx-Power:32 dBm   **
**          RTS thr:2347 B   Fragment thr:2346 B   **
**          Encryption key:AFB1-2345-67   Security mode:restricted**
**          Power Management:off**
**          Link Quality:0  Signal level:0  Noise level:0**
**          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0**
**          Tx excessive retries:0  Invalid misc:0   Missed beacon:0**


**lo        no wireless extensions.**


**eth0      no wireless extensions.**

```

ndiswrapper -l :

```
**bcmn43xx32 : driver installed**
**        device (0846:9020) present**
**bcmwlhigh5 : driver installed**
**        device (0846:9020) present**

```

dhclient -v wlan0 :

```
**Internet Systems Consortium DHCP Client 4.1-ESV-R4**
**Copyright 2004-2011 Internet Systems Consortium.**
**All rights reserved.**
**For info, please visit https://www.isc.org/software/dhcp/**


**Listening on LPF/wlan0/44:94:fc:e8:09:f0**
**Sending on   LPF/wlan0/44:94:fc:e8:09:f0**
**Sending on   Socket/fallback**
**DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3**
**DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7**
**DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14**

```

And it keeps adding a new DHCPDISCOVER line after a certain amount of time

---

### Post by chili555 on 2015-02-21
Please try:```
sudo ndiswrapper -e bcmwlhigh5
```Detach the ethernet, reboot and let us have your report.

---

### Post by clement6 on 2015-02-21
It still doesn't works

---

### Post by chili555 on 2015-02-21
> **clement6 said:**
> It still doesn't worksThat covers a lot of ground. Do you mean that you do or do not see networks when you click the Network Manager icon? If you see them, what happens when you click on yours and try to connect? Are you challenged for a WPA2 password? When you type it in, does it try to connect and fail or what?? What, exactly, doesn't work.

[http://jaap.haitsma.org/wp-content/uploads/2010/08/nm12.png](http://jaap.haitsma.org/wp-content/uploads/2010/08/nm12.png)

---

### Post by clement6 on 2015-02-21
I mean the command 'dhclient wlan0' doesn't works it still do the same thing
And i am on a ubuntu server so there is no network manager icon
My wifi password is of type WEP

I do this before doing the dhclient command:

```
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid [NetworkName]
sudo iwconfig wlan0 key [myKey]
sudo iwconfig wlan0 enc on
```

---

### Post by chili555 on 2015-02-21
The wireless isn't ever going to connect if you don't supply the password and specify which network you want. You can do so at the command line or the more conventional way, in /etc/network/interfaces. I suggest you amend the file to something like:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-ssid <your_network>
wireless-key <your_wep_key>

```Then try:```
sudo ifdown wlan0 && sudo ifup wlan0
```WEP is very insecure; you may as well paint your password on your front door. I highly recommend you change the encryption method to WPA2-AES as soon as possible.

Moreover, if you expect to reach the server by FTP and SSH, you should specify a static IP address. Therefore, I suggest:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.150
netmask 255.255.255.0
gateway 192.168.1.1
wpa-ssid <your_network>
wpa-psk <your_wpa2_key>
```Of course, select an address outside the DHCP pool in the router and substitute your details here.

---

### Post by clement6 on 2015-02-21
After doing: ```
[COLOR=#000000][FONT=Ubuntu Mono]ifdown wlan0 && sudo ifup wlan0[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono] i get:

[/FONT][/COLOR]```
[B]ifdown: interface wlan0 not configured
[/B]**ioctl[SIOCSIWENCODEEXT]: Invalid argument**
**ioctl[SIOCSIWENCODEEXT]: Invalid argument**
**RTNETLINK answers: File exists**

**Failed to bring up wlan0.**
```

[COLOR=#000000][FONT=Ubuntu Mono][SIZE=2]This is my /etc/wpa_supplicant.conf file:

[/SIZE]```
ctrl_interface=/var/run/wpa_supplicant
network={
    ssid="MySSID"
    #psk="MyPassword"
    psk= [String of digits and letter]
}
```



[/FONT][/COLOR]

---

### Post by chili555 on 2015-02-21
In /etc/network/interfaces, is the key [String of digits and letter] or the key in clear text? It should be the latter.> ctrl_interface=/var/run/wpa_supplicant
network={
    ssid="MySSID"
    #psk="MyPassword"
    [COLOR="#FF0000"]psk[/COLOR]= [String of digits and letter]
}This suggests you've changed to WPA2. Is that true?

---

### Post by clement6 on 2015-02-21
It's like: psk=492ac6ca55ab3f2dd3... (without the '...')

Yes i've changed to wpa2

---

### Post by chili555 on 2015-02-21
My question is, is the key in /etc/network/interfaces shown as:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.150
netmask 255.255.255.0
gateway 192.168.1.1
wpa-ssid <your_network>
wpa-psk 492ac6ca55ab3f2dd3..
```Where 492ac6ca55ab3f2dd3.. is your _actual_ WPA2 password, not the disguised version?

---

### Post by clement6 on 2015-02-21
In [COLOR=#000000]/etc/network/interfaces it's the real[/COLOR]

---

### Post by chili555 on 2015-02-21
/etc/network/interfaces requires the password in clear text, not the disguised version.

---

### Post by clement6 on 2015-02-21
I've edited my response in [COLOR=#000000]/etc/network/interfaces it's the real but in [/COLOR][COLOR=#000000][FONT=Ubuntu Mono]/etc/wpa_supplicant.conf it isn't[/FONT][/COLOR]

---

### Post by chili555 on 2015-02-21
Now does it connect with:```
sudo ifdown wlan0 && sudo ifup -v wlan0
```

---

### Post by clement6 on 2015-02-21
No i get:

```
**ifdown: interface wlan0 not configured**
**Configuring interface wlan0=wlan0 (inet)**
**run-parts --verbose /etc/network/if-pre-up.d**
**run-parts: executing /etc/network/if-pre-up.d/ethtool**
**run-parts: executing /etc/network/if-pre-up.d/wireless-tools**
**run-parts: executing /etc/network/if-pre-up.d/wpasupplicant**
**wpa_supplicant: terminating wpa_supplicant daemon via pidfile /var/run/wpa_supplicant.wlan0.pid**
**Stopped /sbin/wpa_supplicant (pid 1521).**
**wpa_supplicant: removing /run/sendsigs.omit.d/wpasupplicant.wpa_supplicant.wlan0.pid**
**wpa_supplicant: wpa-driver nl80211,wext (default)**
**wpa_supplicant: /sbin/wpa_supplicant -s -B -P /var/run/wpa_supplicant.wlan0.pid -i wlan0 -D nl80211,wext -C /var/run/wpa_supplicant**
**Starting /sbin/wpa_supplicant...**
**ioctl[SIOCSIWENCODEEXT]: Invalid argument**
**ioctl[SIOCSIWENCODEEXT]: Invalid argument**
**wpa_supplicant: waiting for "/var/run/wpa_supplicant.wlan0.pid":  0 (max. 5)**
**wpa_supplicant: creating sendsigs omission pidfile: /run/sendsigs.omit.d/wpasupplicant.wpa_supplicant.wlan0.pid**
**wpa_supplicant: ctrl_interface socket located at /var/run/wpa_supplicant/wlan0**
**wpa_supplicant: configuring network block -- 0**
**wpa_supplicant: wpa-ssid "VIDEOTRON1588" -- OK**
**wpa_supplicant: wpa-psk ***** -- OK**
**wpa_supplicant: enabling network block 0 -- OK**
**ip addr add 192.168.0.200/255.255.255.0 broadcast + 	  dev wlan0 label wlan0**
**RTNETLINK answers: File exists**
**Failed to bring up wlan0.**

```

---

### Post by clement6 on 2015-02-21
I've noticed that if i do: ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo ifdown wlan0 && sudo ifup -v wlan0[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono] and then ```
iwconfig
``` while i am connected with my ethernet cable, wlan0 seems connected but if i remove the ethernet cable and redo these 2 command it seems not connected
[SIZE=4]

[SIZE=5]Edit:

[/SIZE][/SIZE]Sometime if i do iwconfig i get:

[/FONT][/COLOR]```
**wlan0     IEEE 802.11g  ESSID:off/any  **[B]          
         Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   [/B]
**          Bit Rate:144 Mb/s   Tx-Power:32 dBm   **
**          RTS thr:2347 B   Fragment thr:2346 B   **
**          Encryption key:off**
**          Power Management:off**
**          Link Quality:60/100  Signal level:-57 dBm  Noise level:-96 dBm**
**          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0**
**          Tx excessive retries:0  Invalid misc:0   Missed beacon:0**


**lo        no wireless extensions.**



**eth0      no wireless extensions.**
```[COLOR=#000000][FONT=Ubuntu Mono]

But sometime i get:

[/FONT][/COLOR]```
[B]wlan0     IEEE 802.11g  ESSID:"VIDEOTRON1588"
[/B]**         Mode:Managed  Frequency:2.437 GHz  Access Point: 84:C9:B2:D1:BC:72   **
**          Bit Rate=144 Mb/s   Tx-Power:32 dBm   **
**          RTS thr:2347 B   Fragment thr:2346 B   **
**          Encryption key:off**
**          Power Management:off**
**          Link Quality:59/100  Signal level:-58 dBm  Noise level:-96 dBm**
**          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0**
**          Tx excessive retries:0  Invalid misc:0   Missed beacon:0**


**lo        no wireless extensions.**



**eth0      no wireless extensions.**
```[COLOR=#000000][FONT=Ubuntu Mono]




[/FONT][/COLOR]

---

### Post by chili555 on 2015-02-21
> I only had to wait now wlan0 seems connected if i do 'iwconfig' but if i ping google.com i get: Netwok is unreachable
Oops! Old Chili is trying to juggle too many threads at once. Please add to /etc/network/interfaces:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.150
netmask 255.255.255.0
gateway 192.168.1.1
wpa-ssid <your_network>
wpa-psk <your_wpa2_key>
[COLOR="#FF0000"]dns-nameservers 8.8.8.8 192.168.1.1[/COLOR]
```Then check:```
sudo ifdown wlan0 && sudo ifup -v wlan0
ping -c3 www.google.com
```

---

### Post by clement6 on 2015-02-21
It says: ping: unknown host

And please check the edit i made on my last reply

---

### Post by chili555 on 2015-02-21
Why does it say encryption key: off? Isn't it on?

I will be away for the evening. See you tomorrow.

---

### Post by clement6 on 2015-02-21
I try to put the encryption key on by doing:

```
iwconfig wlan0 enc on
```

But i get :

```
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0: invalid argument
```

---

### Post by chili555 on 2015-02-22
In that context, iwconfig expects the key itself:```
 key/enc[ryption]
              Used  to  manipulate  encryption or scrambling keys and security
              mode.
              To set the current encryption key, just enter  the  key  in  hex
              digits  as  XXXX-XXXX-XXXX-XXXX or XXXXXXXX.  To set a key other
              than the current key, prepend  or  append  [index]  to  the  key
              itself (this won't change which is the active key). You can also
              enter the key as  an  ASCII  string  by  using  the  s:  prefix.
              **Passphrase is currently not supported**.

```As you can see, setting a WPA2 key is not supported.

Let's see again:```
sudo ifdown wlan0 && sudo ifup -v wlan0
ping -c3 192.168.1.1  <--or whatever your gateway address is.
ping -c3 8.8.8.8
ping -c3 www.google.com
```

---

### Post by clement6 on 2015-02-22
[SIZE=3]Output of [COLOR=#000000][FONT=Ubuntu Mono]**sudo *ifdown wlan0 && sudo ifup -v wlan0***:

[/FONT][/COLOR][/SIZE]```
**ifdown: interface wlan0 not configured****Configuring interface wlan0=wlan0 (inet)**
**run-parts --verbose /etc/network/if-pre-up.d**
**run-parts: executing /etc/network/if-pre-up.d/ethtool**
**run-parts: executing /etc/network/if-pre-up.d/wireless-tools**
**run-parts: executing /etc/network/if-pre-up.d/wpasupplicant**
**wpa_supplicant: terminating wpa_supplicant daemon via pidfile /var/run/wpa_supplicant.wlan0.pid**
**Stopped /sbin/wpa_supplicant (pid 1609).**
**wpa_supplicant: removing /run/sendsigs.omit.d/wpasupplicant.wpa_supplicant.wlan0.pid**
**wpa_supplicant: wpa-driver nl80211,wext (default)**
**wpa_supplicant: /sbin/wpa_supplicant -s -B -P /var/run/wpa_supplicant.wlan0.pid -i wlan0 -D nl80211,wext -C /var/run/wpa_supplicant**
**Starting /sbin/wpa_supplicant...**
**ioctl[SIOCSIWENCODEEXT]: Invalid argument**
**ioctl[SIOCSIWENCODEEXT]: Invalid argument**
**wpa_supplicant: waiting for "/var/run/wpa_supplicant.wlan0.pid":  0 (max. 5)**
**wpa_supplicant: creating sendsigs omission pidfile: /run/sendsigs.omit.d/wpasupplicant.wpa_supplicant.wlan0.pid**
**wpa_supplicant: ctrl_interface socket located at /var/run/wpa_supplicant/wlan0**
**wpa_supplicant: configuring network block -- 0**
**wpa_supplicant: wpa-ssid "VIDEOTRON1588" -- OK**
**wpa_supplicant: wpa-psk ***** -- OK**
**wpa_supplicant: enabling network block 0 -- OK**
**ip addr add 192.168.0.101/255.255.255.0 broadcast +       dev wlan0 label wlan0**
**RTNETLINK answers: File exists**

**Failed to bring up wlan0.**
```[SIZE=3][COLOR=#000000][FONT=Ubuntu Mono]

[SIZE=4]output of [I]**ping -c3 192.168.0.1**:

[/I][/SIZE][/FONT][/COLOR][/SIZE]```
[B]PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.\
[/B]**From 192.168.0.101 icmp_seq=3 Destination Host Unreachable**

**--- 192.168.0.1 ping statistics ---**
**3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2016ms**


```[SIZE=4][COLOR=#000000][FONT=Ubuntu Mono]output of ***ping -c3 8.8.8.8***:

[/FONT][/COLOR][/SIZE]```
connect: Network is unreachable
```[SIZE=3][COLOR=#000000][FONT=Ubuntu Mono][SIZE=4]

output of ***ping -c3 google.com***:

```
ping: unknown host google.com
```


[/SIZE][/FONT][/COLOR][/SIZE]

---

### Post by chili555 on 2015-02-22
> ioctl[SIOCSIWENCODEEXT]: Invalid argument
ioctl[SIOCSIWENCODEEXT]: Invalid argumentThis suggests that the system doesn't like the way you've declared the encryption key. Please check carefully that the key matches what you set in the router. 

Also, WPA2 keys are typically a passphrase of 8 to 63 printable ASCII characters. If you tried to set a key outside these boundaries, it will not work. Finally, make sure the /etc/network/interfaces file is like this:```
wpa-psk 123abc456
```And not:```
wpa-psk123abd456
```Or this:```
wpa-psk '123abc456'
```Unless, of course, the key in the router actually contains ' and '. Very unusual, but possible.

---

### Post by clement6 on 2015-02-22
My /etc/network/interfaces look like this:

```
auto lo
iface lo inet loopback


auto wlan0
iface wlan0 inet static
address 192.168.0.101
netmask 255.255.255.0
gateway 192.168.0.1
wpa-ssid VIDEOTRON1588
wpa-psk 6ai7z3j53h #Not actually my password
dns-nameservers 8.8.8.8 192.168.0.1
```

And my password is 10 character long

---

### Post by clement6 on 2015-02-22
I've changed the address in /etc/network/interface from 192.168.0.101 to 192.168.0.111 and now the command 'sudo ifdown wlan0 && sudo ifup -v wlan0' return something diferent:

```
**Configuring interface wlan0=wlan0 (inet)****run-parts --verbose /etc/network/if-pre-up.d**
**run-parts: executing /etc/network/if-pre-up.d/ethtool**
**run-parts: executing /etc/network/if-pre-up.d/wireless-tools**
**run-parts: executing /etc/network/if-pre-up.d/wpasupplicant**
**wpa_supplicant: wpa-driver nl80211,wext (default)**
**wpa_supplicant: /sbin/wpa_supplicant -s -B -P /var/run/wpa_supplicant.wlan0.pid -i wlan0 -D nl80211,wext -C /var/run/wpa_supplicant**
**Starting /sbin/wpa_supplicant...**
**ioctl[SIOCSIWENCODEEXT]: Invalid argument**
**ioctl[SIOCSIWENCODEEXT]: Invalid argument**
**wpa_supplicant: waiting for "/var/run/wpa_supplicant.wlan0.pid":  0 (max. 5)**
**wpa_supplicant: creating sendsigs omission pidfile: /run/sendsigs.omit.d/wpasupplicant.wpa_supplicant.wlan0.pid**
**wpa_supplicant: ctrl_interface socket located at /var/run/wpa_supplicant/wlan0**
**wpa_supplicant: configuring network block -- 0**
**wpa_supplicant: wpa-ssid "VIDEOTRON1588" -- OK**
**wpa_supplicant: wpa-psk ***** -- OK**
**wpa_supplicant: enabling network block 0 -- OK**
**ip addr add 192.168.0.111/255.255.255.0 broadcast +       dev wlan0 label wlan0**
**ip link set dev wlan0   up**
** ip route add default via 192.168.0.1 metric 100 dev wlan0 **
**run-parts --verbose /etc/network/if-up.d**
**run-parts: executing /etc/network/if-up.d/000resolvconf**
**run-parts: executing /etc/network/if-up.d/ethtool**
**run-parts: executing /etc/network/if-up.d/ntpdate**
**run-parts: executing /etc/network/if-up.d/openssh-server**
**ssh stop/waiting**
**ssh start/running, process 2221**
**run-parts: executing /etc/network/if-up.d/postfix**
**run-parts: executing /etc/network/if-up.d/upstart**
**run-parts: executing /etc/network/if-up.d/wpasupplicant**
```

But i still can't ping or ssh to this server

---

### Post by chili555 on 2015-02-23
I wonder if your old original /etc/wpa_supplicant.conf file is somehow interfering. Let's move it aside temporarily and see if it helps eliminate this:> ioctl[SIOCSIWENCODEEXT]: Invalid argument
ioctl[SIOCSIWENCODEEXT]: Invalid argumentPlease do:```
sudo mv /etc/wpa_supplicant.conf  /etc/wpa_supplicant.bak
```Now try again:```
sudo ifdown wlan0 && sudo ifup -v wlan0
ping -c3 www.google.com
```It may take a reboot.

---

### Post by clement6 on 2015-02-23
when i do 'sudo ifdown wlan0 && sudo ifup -v wlan0' I get the same thing with the > 
[COLOR=#000000]*ioctl[SIOCSIWENCODEEXT]: Invalid argument*[/COLOR]
[COLOR=#000000]*ioctl[SIOCSIWENCODEEXT]: Invalid argument*[/COLOR]

And the ping command still doesn't works

---

### Post by clement6 on 2015-02-25
up

---

### Post by chili555 on 2015-02-25
What version of Ubuntu server are you running?```
lsb_release -d
```What is found here?```
ls /etc/wpa_supplicant
```For comparison, my 14.04 and 14.10 machines have:```
$ ls /etc/wpa_supplicant/
action_wpa.sh  functions.sh  ifupdown.sh

```One of my 14.04 machines is set with a static IP address in /etc/network/interfaces and connects perfectly:> Configuring interface eth0=eth0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/ethtool
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
ip addr add 10.255.16.150/255.255.255.0 broadcast 10.255.16.255       dev eth0 label eth0
ip link set dev eth0   up
 ip route add default via 10.255.16.99  dev eth0
run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/000resolvconf
run-parts: executing /etc/network/if-up.d/avahi-autoipd
run-parts: executing /etc/network/if-up.d/avahi-daemon
run-parts: executing /etc/network/if-up.d/ethtool
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/openssh-server
run-parts: executing /etc/network/if-up.d/upstart
run-parts: executing /etc/network/if-up.d/wpasupplicantThanks.

---

### Post by clement6 on 2015-02-25
[COLOR=#000000]What version of Ubuntu server are you running?: [/COLOR][B]Ubuntu 14.04.2 LTS

[/B][COLOR=#000000]What is found here?: [/COLOR]```
**action_wpa.sh ****functions.sh ****ifupdown.sh****  networks.txt**
```

---

### Post by chili555 on 2015-02-25
Did you add *networks.txt *or what is it? I wonder when and how it is called. Any clues?

---

### Post by clement6 on 2015-02-25
It's just the output of a command that shows the networks near me I don't remember the command name

---

### Post by chili555 on 2015-02-25
I am stumped. I will call in the smart and fast guys to help us.

---

### Post by chili555 on 2015-02-25
May we see:```
route -n
ifconfig
```Thanks.

---

### Post by clement6 on 2015-02-25
route -n:

```
[B]Kernel IP routing table
[/B]**Destination     Gateway         Genmask         Flags Metric Ref    Use Iface**
**0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0**
**192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0**
**192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0**
```

ifconfig:

```
[B]eth0      Link encap:Ethernet  HWaddr 00:09:6b:d8:cd:26
[/B]**         inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0**
**          inet6 addr: fe80::209:6bff:fed8:cd26/64 Scope:Link**
**          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1**
**          RX packets:578 errors:0 dropped:0 overruns:0 frame:0**
**          TX packets:202 errors:0 dropped:0 overruns:0 carrier:0**
**          collisions:0 txqueuelen:1000 **
**          RX bytes:126614 (126.6 KB)  TX bytes:28974 (28.9 KB)**


**lo        Link encap:Local Loopback  **
**          inet addr:127.0.0.1  Mask:255.0.0.0**
**          inet6 addr: ::1/128 Scope:Host**
**          UP LOOPBACK RUNNING  MTU:65536  Metric:1**
**          RX packets:16 errors:0 dropped:0 overruns:0 frame:0**
**          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0**
**          collisions:0 txqueuelen:0 **
**          RX bytes:1184 (1.1 KB)  TX bytes:1184 (1.1 KB)**


**wlan0     Link encap:Ethernet  HWaddr 44:94:fc:e8:09:f0  **
**          inet addr:192.168.0.111  Bcast:192.168.0.255  Mask:255.255.255.0**
**          inet6 addr: fe80::4694:fcff:fee8:9f0/64 Scope:Link**
**          UP BROADCAST MULTICAST  MTU:1500  Metric:1**
**          RX packets:86 errors:0 dropped:0 overruns:0 frame:0**
**          TX packets:94 errors:0 dropped:0 overruns:0 carrier:0**
**          collisions:0 txqueuelen:1000 **
**          RX bytes:9718 (9.7 KB)  TX bytes:12258 (12.2 KB)**
```


I have eth0 up for the moment so i can ssh to this server but  when i do 'sudo ifdown wlan0 && sudo ifup -v wlan0' i put eth0 down

---

### Post by chili555 on 2015-02-25
> eth0      Link encap:Ethernet  HWaddr 00:09:6b:d8:cd:26
         inet addr:192.168.[COLOR="#FF0000"]2[/COLOR].2  Bcast:192.168.2.255  Mask:255.255.255.0> wlan0     Link encap:Ethernet  HWaddr 44:94:fc:e8:09:f0  
          inet addr:192.168.[COLOR="#FF0000"]0[/COLOR].111  Bcast:192.168.0.255  Mask:255.255.255.0These are two different routers or access points? Or what?

---

### Post by clement6 on 2015-02-25
I share my internet from my macbook to my server I think that's why it's 2 instead of 0

---

### Post by chili555 on 2015-02-26
Let's see what the driver is doing all this time:```
dmesg | grep ndis
```Are other devices able to connect wirelessly using the Macbook as an access point? May we rule out a configuration issue in the Macbook?

---

### Post by clement6 on 2015-02-26
I get this when doing the command 'dmesg | grep ndis' :
```
**[   23.050475] ****ndis**[B]wrapper: module verification failed: signature and/or  required key missing - tainting kernel
[/B]**[   23.117888] ****ndis****wrapper version 1.59 loaded (smp=yes, preempt=no)**
**[   23.716413] ****ndis****wrapper: driver bcmn43xx32 (,08/26/2009, 5.10.79.30) loaded**
**[   24.750334] usbcore: registered new interface driver ****ndis****wrapper**
**[   96.277266] ****ndis****wrapper (iw_set_freq:436): setting configuration failed (00010003)**
**[  131.275616] ****ndis****wrapper (iw_set_freq:436): setting configuration failed (00010003)**
**[  233.397726] ****ndis****wrapper (iw_set_freq:436): setting configuration failed (00010003)**
**[  283.397403] ****ndis****wrapper (iw_set_freq:436): setting configuration failed (00010003)**
**[  363.425990] ****ndis****wrapper (iw_set_freq:436): setting configuration failed (00010003)**
**[  443.425563] ****ndis****wrapper (iw_set_freq:436): setting configuration failed (00010003)**
**[  523.426241] ****ndis****wrapper (iw_set_freq:436): setting configuration failed (00010003)**
**[  603.425948] ****ndis****wrapper (iw_set_freq:436): setting configuration failed (00010003)**
**[  683.425437] ****ndis****wrapper (iw_set_freq:436): setting configuration failed (00010003)**
**[  823.486342] ****ndis****wrapper (iw_set_freq:436): setting configuration failed (00010003)**
**[  963.486784] ****ndis****wrapper (iw_set_freq:436): setting configuration failed (00010003)**
**[ 1245.193328] ****ndis****wrapper (iw_set_freq:436): setting configuration failed (00010003)**
**[ 1385.186630] ****ndis****wrapper (iw_set_freq:436): setting configuration failed (00010003)**
```

---

### Post by chili555 on 2015-02-26
> ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)Ah, haaa! I think this means that the driver can't or won't switch frequency as directed by the access point. Normally, when trying to connect, the access point or router advertises what channel it's on and the wireless card/driver combination switches to it. Yours won't.

I notice this:> wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  [COLOR="#FF0000"]Frequency:2.412 GHz[/COLOR]  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:AFB1-2345-67   Security mode:restricted
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
I believe that is channel 1. I suggest you try setting the access point, your Macbook, to use channel 1 only; certainly no auto channel selection, and see if you connect.

---

### Post by clement6 on 2015-02-26
I am trying to connect to the wifi of my router not of my Macbook. I only use my Macbook to share my router wifi to an ethernet cable to my server so i can ssh to it using 192.168.2.2. And what i wan't is to be able to ssh to my server from everywhere in the house and not have to be with my Macbook connected to the server with the ethernet cable

---

### Post by chili555 on 2015-02-26
Would you please try with it switched to use channel 1?

---

### Post by clement6 on 2015-02-26
I've changed the 2.4GHZof my router to channel 1 but i still can't connect

---

### Post by chili555 on 2015-02-27
I have tried everything at my disposal. I haven't any idea how to overcome this:> [  131.275616] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
[  233.397726] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
[  283.397403] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
[  363.425990] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
[  443.425563] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)I regret that I haven't any other suggestions.

---

### Post by clement6 on 2015-02-27
I've solved the problem. The problem was that my router configuration weren't the same as my /etc/wpa_supplicant.conf for example i had:

```

[B]proto=WPA
[/B]**key_mgmt=WPA-PSK**
**pairwise=**[COLOR=#111111][FONT=Consolas]CCMP TKIP[/FONT][/COLOR]
**group=**[COLOR=#111111][FONT=Consolas]CCMP TKIP[/FONT][/COLOR]
```

and my router was set to WPA2 not WPA and the pairwise and group on my router were AES so i changed them to TKIP and i changed my password to use WPA and changed my /etc/wpa_supplicant.conf to:

```
[B]proto=WPA
[/B]**key_mgmt=WPA-PSK**
**pairwise=**[COLOR=#111111][FONT=Consolas]TKIP[/FONT][/COLOR]
**group=**[COLOR=#111111][FONT=Consolas]TKIP[/FONT][/COLOR]
```

---

