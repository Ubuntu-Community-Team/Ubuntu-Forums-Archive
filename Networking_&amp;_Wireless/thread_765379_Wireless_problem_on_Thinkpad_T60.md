---
title: "Wireless problem on Thinkpad T60"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by Marreboy on 2008-04-24
I have just installed Ubuntu 8.04 on a Thinkpad T60, it has an Intel Pro/Wireless 3945ABG wireless card built in. And i cant get it to activate the card properly and connect to my router. The card seems to be powered down or not trying to connect. After searching this forum and the Wiki i realise that this card is supposed to be fully supported by Ubuntu. And to prove that is the fact that it was working fine in Ubuntu 7.10.

Here is output from some commands: 
------------------------------
**:~$ sudo lshw -C network**
 
 *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:19:d2:08:92:b9
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

**:~$ cat /etc/network/interfaces**
auto lo
iface lo inet loopback

iface wlan0 inet dhcp
wpa-psk 9f756453ab243a44XXXXXXXXXXXXXX
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid Hurley

auto wlan0

**:~$ ifconfig**
wlan0     Link encap:Ethernet  HWaddr 00:19:d2:08:92:b9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:19:d2:08:92:b9  
          inet addr:169.254.7.187  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-19-D2-08-92-B9-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
-----------------------------------

It seems like the Wireless adapter is called wmaster0 and not wlan0 which is strange. And if i access the network tools i cant see any info on any adapters. They are all visible there but no info. I see wlan0, wlan0:avahi and wmaster0 but none of them seems to exist if i click the configure button. Also what is the wlan0:avahi adapter?? Has anyone seen that before?

I previously tried installing the Windows Wireless driver application which was supposed to help with ndiswrapper config. But that screwed up my whole machine. So i have reinstalled the 8.04 completely since then. Worth noting is that ndiswrapper did not help in this case. The windows driver did not work either. 

Wired connection works. But that limits the use of the laptop so wireless is really a requirement for me.

Can anyone advise me how to proceed? What can i do?

---

### Post by mikawber on 2008-04-24
My Intel PRO/Wireless 3945ABG does not work on my Dell D430 either.

---

### Post by ScottY86 on 2008-04-24
my brand new thinkpad r61 doesn't work either.  I have intel 3945 wireless. 

The outputs of various commands.  I was trying to connect while doing tail of the syslog:

syilek@mooputer:~$ dmesg | grep 3945
[   25.989088] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   25.989096] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   25.989380] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   29.425319] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   29.462582] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
syilek@mooputer:~$ lsmod | grep 3945
iwl3945                89844  0 
iwlwifi_mac80211      219108  1 iwl3945
syilek@mooputer:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Nitro"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

syilek@mooputer:~$ tail /var/log/syslog
Apr 24 16:01:54 mooputer dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Apr 24 16:02:00 mooputer dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Apr 24 16:02:07 mooputer dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Apr 24 16:02:19 mooputer dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
Apr 24 16:02:21 mooputer dhclient: No DHCPOFFERS received.
Apr 24 16:02:21 mooputer dhclient: No working leases in persistent database - sleeping.
Apr 24 16:02:21 mooputer avahi-autoipd(wlan0)[8657]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 112).
Apr 24 16:02:21 mooputer avahi-autoipd(wlan0)[8657]: Successfully called chroot().
Apr 24 16:02:21 mooputer avahi-autoipd(wlan0)[8657]: Successfully dropped root privileges.
Apr 24 16:02:21 mooputer avahi-autoipd(wlan0)[8657]: Starting with address 169.254.8.11
syilek@mooputer:~$ tail /var/log/syslog
Apr 24 16:02:21 mooputer dhclient: No working leases in persistent database - sleeping.
Apr 24 16:02:21 mooputer avahi-autoipd(wlan0)[8657]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 112).
Apr 24 16:02:21 mooputer avahi-autoipd(wlan0)[8657]: Successfully called chroot().
Apr 24 16:02:21 mooputer avahi-autoipd(wlan0)[8657]: Successfully dropped root privileges.
Apr 24 16:02:21 mooputer avahi-autoipd(wlan0)[8657]: Starting with address 169.254.8.11
Apr 24 16:02:25 mooputer avahi-autoipd(wlan0)[8657]: Callout BIND, address 169.254.8.11 on interface wlan0
Apr 24 16:02:25 mooputer avahi-daemon[5071]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.8.11.
Apr 24 16:02:25 mooputer avahi-daemon[5071]: New relevant interface wlan0.IPv4 for mDNS.
Apr 24 16:02:25 mooputer avahi-daemon[5071]: Registering new address record for 169.254.8.11 on wlan0.IPv4.
Apr 24 16:02:29 mooputer avahi-autoipd(wlan0)[8657]: Successfully claimed IP address 169.254.8.11
syilek@mooputer:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:25:7e:65:7e  
          UP BROADCAST MULTICAST  MTU:1492  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Base address:0x1840 Memory:fe000000-fe020000 

eth0:avahi Link encap:Ethernet  HWaddr 00:1c:25:7e:65:7e  
          inet addr:169.254.5.235  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1492  Metric:1
          Base address:0x1840 Memory:fe000000-fe020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1587 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1587 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:79412 (77.5 KB)  TX bytes:79412 (77.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:27:cd:c2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:1f:3c:27:cd:c2  
          inet addr:169.254.8.11  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-27-CD-C2-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by g3brownsc on 2008-04-24
My thinkpad r61 also does not have functioning wireless, same card as yours. 
Intel (R) PRO/Wireless 3945
No led, but it manages to see my wireless network, which is is hidden. I input the SSID and it shows up with an accurate measure of signal strength, but cannot connect. 
This is a big deal, I can't upgrade if wireless won't work.

---

### Post by DO55 on 2008-04-25
i have same problem
[http://ubuntuforums.org/showthread.php?t=765615](http://ubuntuforums.org/showthread.php?t=765615)

---

### Post by wilson79 on 2008-04-25
Hello,
I have experienced the same problem on an Acer7720G laptop with Intel (R) PRO/Wireless 3945 card after having upgraded from 7.10.
I don't know if this could be useful to anyone, but I managed to get the wireless adapter work perfectly by choosing (during boot by using GRUB) the kernel with the last numbers on the right .14 instead of .16.
(Even though by doing that the screen driver screwed up...:()

wilson

---

### Post by amazoohwawa on 2008-04-25
i tried this and i am very pleased to report that it worked,, yeaaaaa..

Hello,
I have experienced the same problem on an Acer7720G laptop with Intel (R) PRO/Wireless 3945 card after having upgraded from 7.10.
I don't know if this could be useful to anyone, but I managed to get the wireless adapter work perfectly by choosing (during boot by using GRUB) the kernel with the last numbers on the right .14 instead of .16.
(Even though by doing that the screen driver screwed up...)

wilson

just make sure you hit escape as soon as the system starts loading, you will then see option and choose .14 as mentioned above. in my case it did not screw anything up so far!! :)

thanks a lot wilson. we need more smart people like u!

---

### Post by ScottY86 on 2008-04-25
My wireless started working now after doing the backports installation.  My green wireless light is even illuminated now.  

To do this I followed the instructions from here: [http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/](http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/)

hope this helps someone.

---

