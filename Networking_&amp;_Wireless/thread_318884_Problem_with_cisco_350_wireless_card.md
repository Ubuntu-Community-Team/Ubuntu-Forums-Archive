---
title: "Problem with cisco 350 wireless card"
date: 2006-12-14
forum: Networking &amp; Wireless
---

### Post by gaoty133 on 2006-12-14
I install ubuntu 6.10 on my notebook. The system can identify my cisco 350 wireless card.
In the systme-administration-networking, there are total four interfaces, two for my cisco 350 wireless device (eth1 and wifi0)
but every time when i try to config the DHCP client by using "dhclient eth1", i got the error message "wifi0: unknown hardware address type 801". I tried few different way to config my wireless card, but no succeed at all. 
Can any one tell me how to solve the problem.](*,) 
Thanks]

---

### Post by FrodoB on 2006-12-14
You can safely ignore these messages. The Aironet 350 and 340 work out of the box with Edgy. Wifi0 is an interface for use with tools that deal with raw packets.  

The errors from dhclient are normal and do not affect operation.

Always configure the eth1 interface.

---

### Post by FrodoB on 2006-12-14
If System -> Administration -> Networking is not getting it then do it manually.

Using the Text Editor (gedit) we need to modify the interfaces file to get the device started correctly:

sudo gedit /etc/network/interfaces 

You need to have a record like this:

auto eth1
iface eth1 inet dhcp
wireless-essid MY_ESSID
wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX       # This line for hexidecimal keys
# wireless-key s:XXXXXXXXXXXXX                              # This line for ASCII (string) keys

Make your WEP keys here:

[http://www.andrewscompanies.com/tools/wep.asp](http://www.andrewscompanies.com/tools/wep.asp)

---

### Post by gaoty133 on 2006-12-14
> **FrodoB said:**
> If System -> Administration -> Networking is not getting it then do it manually.

Using the Text Editor (gedit) we need to modify the interfaces file to get the device started correctly:

sudo gedit /etc/network/interfaces 

You need to have a record like this:

auto eth1
iface eth1 inet dhcp
wireless-essid MY_ESSID
wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX       # This line for hexidecimal keys
# wireless-key s:XXXXXXXXXXXXX                              # This line for ASCII (string) keys

Make your WEP keys here:

[http://www.andrewscompanies.com/tools/wep.asp](http://www.andrewscompanies.com/tools/wep.asp)

**My interface file:**
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

**And after i added:**

auto eth1
iface eth1 inet dhcp
wireless-essid vivaldi
wireless-key 1DB957DF29B06EBA46F33D7BE5

it still not working](*,) 

my ifconfig output:
eth1      Link encap:Ethernet  HWaddr 00:07:EB:30:88:FF  
          inet6 addr: fe80::207:ebff:fe30:88ff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:158 dropped:0 overruns:0 frame:158
          TX packets:12 errors:12 dropped:0 overruns:0 carrier:12
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:2376 (2.3 KiB)
          Interrupt:3 Base address:0x4040 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1284 (1.2 KiB)  TX bytes:1284 (1.2 KiB)
do you have any idea?

---

### Post by FrodoB on 2006-12-15
Try no security on the router and comment out the WEP line in interfaces by placing a # character at the beginning of the wireless-key line.

Control the device with:

sudo ifdown eth1

sudo ifup eth1

See available access points with:

iwlist eth1 scanning

---

### Post by gaoty133 on 2006-12-15
> **FrodoB said:**
> Try no security on the router and comment out the WEP line in interfaces by placing a # character at the beginning of the wireless-key line.

Control the device with:

sudo ifdown eth1

sudo ifup eth1

See available access points with:

iwlist eth1 scanning

Thanks for the help.
i can use iwlist find my access points. after set no security on the router and comment out the WEP line, i still can not get connect. ]
**my iwconfig output: **
root@tianyu-laptop:/# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Encryption key:****-****-****-****-****-****-**   Security mode:open
          Power Management:off
          Link Quality=82/100  Signal level=-54 dBm  Noise level=-91 dBm
          Rx invalid nwid:757  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:5647   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Encryption key:****-****-****-****-****-****-**   Security mode:open
          Power Management:off
          Link Quality=82/100  Signal level=-54 dBm  Noise level=-91 dBm
          Rx invalid nwid:757  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:5647   Missed beacon:0

sit0      no wireless extensions.
after i manually config the interface file, in the "eth1" line, there is still no SSID or "security"information.

---

### Post by gaoty133 on 2006-12-15
finally, I connected to the wireless network using my cisco 350 wireless lan caed.:KS  What i am done is to install the network-manager and it's working fine, but i still can not make it work if i manually config "interfaces"file.:mad:

---

### Post by Joachim Ziegler on 2006-12-25
I am experiencing exactly the same problems with my Aironet 350 (which works fine under Windows). I have followed all advices given so far. Now:

> **FrodoB said:**
> 
sudo ifup eth1

See available access points with:

iwlist eth1 scanning

ifup eth1 gives me 

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

But iwlist sees my WLAN (!!!) and strangely enough, my router claims to have assigned an IP to my wireless card.

What can I do?

Greetings,
Joachim

---

### Post by yotam on 2007-01-26
You are not alone - I got similar problem.

---

### Post by eechan on 2007-03-28
keywords: cisco, wep, dhcp

ah love searching the forums for answers.

I just loaded up 6.10 on an old dell laptop with a cisco 340 card from the office.

after scrounging around on the forums for two days I found out why the card was connecting to the access point but not getting any dhcp addresses assigned. 

it seems the default configuration for setting up the wifi card via the Network Settings administration tool inserts the wep key into slot 4 on the cards I was playing with and the AP was set to expect and use keys from slot 1.

you can verify which key index the AP is using if with 

**sudo iwlist eth1 key**            (substitute eth1 with your appropriate interface)

after I re-inserted my wep key into slot 1 with the following command, I was able to get a DHCP address assigned with no problem

**sudo iwconfig eth1 key [1] ***insert your wep key here*

so now my iwlist output looks like this. it works. I'm happy now :lolflag: 

laptop:~$ **sudo iwlist eth1 key**
Password:
eth1      2 key sizes : 40, 104bits
          4 keys available :
                [1]: ****-****-****-****-****-****-** (104 bits)
                [2]: off
                [3]: off
                [4]: ****-****-****-****-****-****-** (104 bits)
          Current Transmit Key: [1]
          Security mode:open

---

### Post by joenix on 2007-03-30
Thanks a lot! This fixed it for me.
After the iwconfig command you specified, I also had to do the following in order to actually activate key 1:
sudo iwconfig eth1 key [1]
If you add the wep-key at the end, the key is set, but not activated, according to the man-page.

---

### Post by yukonho on 2008-04-26
I fixed it this way, which should still work even if the kernel gets updated (I think). Add the following lines to your /etc/modprobe.d/blacklist file:

# these aes modules break the airo driver
blacklist padlock_aes
blacklist geode_aes

This fixed wireless on my Cisco Aironet 350 and eliminated the hang during boot.

---

### Post by joenix on 2008-04-27
Hi yukonho,

I don't think we're talking about the same problem here. The problem with the keys was present befor Hardy and should not be a problem anymore.
See:
[https://bugs.launchpad.net/bugs/44733](https://bugs.launchpad.net/bugs/44733)

The problem with the modules only appeared in Hardy. That one can be fixed with the workaround you describe.
See:
[https://bugs.launchpad.net/bugs/189398](https://bugs.launchpad.net/bugs/189398)

---

