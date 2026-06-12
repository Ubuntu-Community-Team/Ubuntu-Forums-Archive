---
title: "Wireless card recognized, network scanned, but no internet"
date: 2006-09-14
forum: Networking &amp; Wireless
---

### Post by jpark514 on 2006-09-14
Hi everyone, 

I bought a Linksys WPC11 network adaptor for my Thinkpad X20 laptop. Its chipset, I believe, is rtl8180, which has been recommended by other people on the forum. I use Xubuntu (Dapper Draker I believe because I downloaded it only a month ago). The network card was recognized by Xubuntu with no problem and the card seemed to scan my school's unsecured network, named "ANY." But I still could not connect to internet. I read posts on the forum and did some diagnostics, but being new to Linux I couldn't figure out what the problem was exactly. 

Here are outputs for:

dmesg | grep rtl8180
> 
[   70.113452] rtl8180: Initializing module
[   70.113463] rtl8180: Wireless extensions version 19
[   70.113475] rtl8180: Initializing proc filesystem
[   70.115204] rtl8180: Configuring chip resources
[   70.115615] rtl8180: Memory mapped space @ 0x22000000
[   70.115706] rtl8180: MAC controller is a RTL8180 (v. F)
[   70.115721] rtl8180: This is a CARDBUS NIC
[   70.115733] rtl8180: Reported EEPROM chip is a 93c56 (2Kbit)
[   70.122434] rtl8180: Card MAC address is 00:0c:41:bb:bb:4c
[   70.131336] rtl8180: EEPROM version 102
[   70.132447] rtl8180: RfParam: 4
[   70.134677] rtl8180: WW:Card reports RF frontend by MAXIM.
[   70.134691] rtl8180: WW:This driver has EXPERIMENTAL support for this chipset.
[   70.134704] rtl8180: WW:use it with care and at your own risk and
[   70.134717] rtl8180: WW:**PLEASE** REPORT SUCCESS/INSUCCESS TO [email]andreamrl@tiscali.it[/email]
[   70.134731] rtl8180: Energy threshold: a
[   70.134743] rtl8180: PAPE from CONFIG2: 2
[   70.134753] rtl8180: Antenna A is default antenna
[   70.134764] rtl8180: Antenna diversity is enabled
[   70.134775] rtl8180: Carrier sense 1
[   70.135764] rtl8180: 40-bit WEP is NOT supported in hardware
[   70.135779] rtl8180: 104-bit WEP is NOT supported in hardware
[   70.135816] rtl8180: IRQ 11
[   70.137006] rtl8180: Driver probe completed
[   71.291847] rtl8180: Bringing up iface
[   71.492800] rtl8180: Card successfully reset
[  159.737632] rtl8180: WW:Phy writing 3 21 failed!


ifconfig
> 
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:172 (172.0 b)  TX bytes:172 (172.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:0C:41:BB:BB:4C
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:7213 errors:0 dropped:0 overruns:0 frame:0
          TX packets:450 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:484032 (472.6 KiB)  TX bytes:14400 (14.0 KiB)
          Interrupt:11 Memory:d4a56000-d4a56100


iwconfig:
> 
lo        no wireless extensions.

wlan0     802.11b  Mode:Managed  Frequency:2.432 GHz
          Access Point: Not-Associated   Bit Rate=11 Mb/s
          Retry:on   Fragment thr:off
          Power Management:off
          Link Quality=15/100  Signal level=-53 dBm  Noise level=-171 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


ifup:
> 
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/wlan0/00:0c:41:bb:bb:4c
Sending on   LPF/wlan0/00:0c:41:bb:bb:4c
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


And my /etc/network/interfaces looks llike:
> 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid ANY


I tried tiding up the interfaces file by removing every entry except ones related to l0, eth0, and wlan0 but it did not help. 

My suspicion is the problem has something to do with 
> [  159.737632] rtl8180: WW:Phy writing 3 21 failed!
in my dmesg output. I searched for the error messege but couldn't find anything. 

Any help and clue into what the problem is would be greatly appreciated. Thank you!

---

### Post by trubblemaker on 2006-09-14
ok so lets try some more commands lets try

```
 iwlist scan 
``` 

if you get your school network listed then do this

```
 iwconfig wlan0 essid <school network> 
sudo dhclient wlan0
```
if that gets you an IP then we can change your /etc/interfaces/network file. Sub in the <school network> for the 'any' but lets not get ahead of ourselves.

---

### Post by jpark514 on 2006-09-14
Thanks for the reply. 

iwlist scan:
> 
lo      Interface doesn't support scanning
wlan0   Scan completed:
        Cell 01 - Address: 00:E0:63:50:67:1B
                  ESSID: "ANY"
                  Protocol:IEEE 802.11b
                  Mode:Master
                  Channel:6
                  Encryption Key:off
                  Bit Rates: 11 Mb/s
                  Extra: Rates (Mb/s): 1 2 5 5.5 11
                  Quality:225  Signal level:0  Noise level:97
                  Extra: Last beacon: 28ms ago

sit0    Interface doesn't support scanning


Sometimes it just shows 
> 
wlan0   No scan results


After the network was scanned I did "sudo iwconfig wlan0 essid ANY" (without sudo it would say permission denied); it didn't give me any feedback. 

With "sudo dhclient wlan0" it essentially gave me the same result as when I did "ifup."

>  
Listening on LPF/wlan0/00:0c:41:bb:bb:4c
Sendig on    LPF/wlan0/00:0c:41:bb:bb:4c
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working lease in persistent database - sleeping.


This is what my school website says about wireless networking:

[http://citwiki.oberlin.edu/index.php/Network_Configuration](http://citwiki.oberlin.edu/index.php/Network_Configuration)
> 
If you connect via Wireless (also known as WiFi, or 802.11b), you will configure your computer's wireless networking to use DHCP, then choose the "ANY" wireless network. Oberlin has a wireless network infrastructure that will allow computers to connect to the network at  several locations around campus.


So it seems there's no special setting required. Right?

---

### Post by trubblemaker on 2006-09-14
> **jpark514 said:**
> Thanks for the reply. 

iwlist scan:


Sometimes it just shows 


After the network was scanned I did "sudo iwconfig wlan0 essid ANY" (without sudo it would say permission denied); 

my bad yes sudo is needed
> **jpark514 said:**
> 
it didn't give me any feedback. 

yup, no news, is good news.
> **jpark514 said:**
> 
With "sudo dhclient wlan0" it essentially gave me the same result as when I did "ifup."

yeah, sortof 'ifup' reads your /etc/network/interfaces file and then tries to get a ip, 'sudo dhclient wlan0' just tries to get you an ip now with current settings, it's subtle but worth knowing the difference.

> **jpark514 said:**
> 
This is what my school website says about wireless networking:

[http://citwiki.oberlin.edu/index.php/Network_Configuration](http://citwiki.oberlin.edu/index.php/Network_Configuration)


So it seems there's no special setting required. Right?
right, but the 'any' is a key word that might be giving you an issue. 

ah-hah it is the issue! man page says so you need to do this
```

iwconfig eth0 essid -- "ANY"

```
to connect to a network called 'any'.  Not the network admins best choice for a network name.  Let me know if this helps.  if it does work I can show you how to write a script so it locates it at boot.

---

### Post by jpark514 on 2006-09-14
Thank you very much! It worked!! 

The command ```
iwconfig wlan0 essid -- "ANY"
``` did the trick. So I guess the configuration that loads up at boot is not correct? Anyway, thanks a lot :D

---

### Post by trubblemaker on 2006-09-14
[check out this post]("http://ubuntuforums.org/showpost.php?p=899926&postcount=24") 
the part you need is right at the bottom where it shows a way of adding a script to your interfaces file so that it will automtically select the correct network at boot time

you obvoiusly will need to adjust it a bit (like renaming the interfaces and the special case of your add -- "any") but I'm sure you can make the changes.  if you need help with it post back and I will help you.  I would highly suggest not using variables and using specific commands, also you don't need the last 4 lines as your on ndiswrapper

---

### Post by midtoad on 2006-11-23
trubblemaker, what would you suggest adding to your post on automatic start-up scripts if your wireless network requires a fixed IP address? That's how mine is set up and I'm having getting connected to it even though I've turned off WEP.  I *am* able to connect to another unsecured network that uses DHCP.  

Also, where would you store or set the WEP key if connecting to a secured network?

BTW thanks for [this post]("http://ubuntuforums.org/showpost.php?p=899926&postcount=24") which was quite helpful. 

I'm running Edgy Eft and using a Linksys WPC11 card, which apparently requires and uses the RTL8180 driver. I'm using it to post this message!

---

### Post by midtoad on 2006-11-23
> **midtoad said:**
> Also, where would you store or set the WEP key if connecting to a secured network?

Answering part of my own question, 
[PHP]iwconfig wlan0 mode managed essid network_name key WEP_key
[/PHP]

I'm assuming that if in my router's web configuration page the WEP key is "ABC" (it's actually 26 characters), then I should enter "ABC" in the above.

---

### Post by trubblemaker on 2006-11-23
to tell the truth I wrote that a long time ago and I've made alot of changes to the file since then, I will have to update it one day.  (Not today my girl to the computer with the script on it.)

to set an ip with a specified essid and an address, add this somewhere to the script.

```
#try setting you interface to the essid
sudo iwconfig $interface essid "specific-essid" 

# is it a valid choice of essid? see if it's Not-Associated --> failed to connect to essid
test=`iwconfig $interface | grep Not-Asso | wc -l`  

if [ $test -eq 0 ]; then # 0 means it is associted to an ap
     sudo ifconfig $interface 192.168.1.100 # ip address you want.
     #other commands to connect to the network.
fi

```

I've taken to actually running the this old version of this script on Startup as it slows boot time down in edgy, you can do that by:
going into System->Preferences->Sessions->Startup-Programs and then selecting the script.  If you did do that then you would have to add "sudo dhclient $essid" to the end of the file to actually get the ip.

---

