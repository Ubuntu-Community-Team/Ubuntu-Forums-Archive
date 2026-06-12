---
title: "Ubuntu 6.10 &amp; Wireless Intel 3945ABG connection problem"
date: 2006-12-28
forum: Networking &amp; Wireless
---

### Post by Dr0n3 on 2006-12-28
Hello everyone. I'm new to Linux and just installed Ubuntu 6.10 Edgy. The Linux environment is new to me and I'm having some big troubles getting my wireless connection to work properly. In Windows XP the wireless connection is running just fine with WPA2/AES, no broadcast ESSID, and MAC ACL.
 
Now not being a total noob I did do research on the subject at hand. I'll first list some configuration information and the things I've tried.


**Current configuration**

root@Unimatrix0:/home/drone# **uname -r**
2.6.17-10-generic

root@Unimatrix0:/home/drone# **lspci**
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

root@Unimatrix0:/home/drone# **dmesg | grep 3945**
[17179590.356000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.1.0mp
[17179590.356000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[17179590.944000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[17179592.892000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[17182672.440000] ipw3945: Radio Frequency Kill Switch is On:
[17182675.304000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)

root@Unimatrix0:/home/drone# **ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:16:36:AF:AE:AE  
          inet addr:192.168.1.67  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:feaf:aeae/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:37999 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37437 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:7200618 (6.8 MiB)  TX bytes:3104527 (2.9 MiB)
          Base address:0x5000 Memory:da000000-da020000 

eth1      Link encap:Ethernet  HWaddr 00:13:02: DD:B3:13  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3368 errors:0 dropped:528 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:520 (520.0 b)
          Interrupt:169 Base address:0x6000 Memory:d8000000-d8000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 b)  TX bytes:300 (300.0 b)

root@Unimatrix0:/home/drone# **iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"Borg Collective"  
          Mode:Managed  Frequency=2.442 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:0ff   Fragment thr:0ff
          Encryption key:0ff
          Power Management:0ff
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:561   Missed beacon:0

sit0      no wireless extensions.

root@Unimatrix0:/home/drone# **iwlist eth1 scan**
eth1      Scan completed :
          Cell 01 - Address: 00:11:F5:C9:F3:53
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:7
                    Encryption key:0n
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=90/100  Signal level=-41 dBm  Noise level=-41 dBm
                    IE: WPA Version 1
                        Group Cipher : CCMP 
                        Pairwise Ciphers (1) : CCMP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 3744ms ago

I removed the other networks it found and only displayed mine. I only turned encryption off to test if the wireless connection would come up. Since it didn't I turned it back on. I don't like keeping my network unprotected for too long.

root@Unimatrix0:/home/drone# **lsmod | grep ieee80211**
ieee80211_crypt_wep     6528  0 
ieee80211              35272  1 ipw3945
ieee80211_crypt         7552  2 ieee80211_crypt_wep,ieee80211

root@Unimatrix0:/home/drone# **lsmod | grep ipw3945**
ipw3945               124576  1 
ieee80211              35272  1 ipw3945

root@Unimatrix0:/home/drone# **modprobe -l ipw3945**
/lib/modules/2.6.17-10-generic/kernel/drivers/net/wireless/ipw3945/ipw3945.ko

root@Unimatrix0:/home/drone# **modprobe -l ieee80211**
/lib/modules/2.6.17-10-generic/kernel/net/ieee80211/ieee80211.ko


**Things I've tried**

The wireless switch on my laptop is turned on. The wireless connection works just fine in Windows XP. I've installed all updates the Synaptic Package Manager suggested. I turned off encryption in my router and turned ESSID broadcasting on. WPA_supplicant is installed. I checked this in the Synaptic Package Manager. Wired Internet is working just fine as device eth0. My wireless eth1 device is listed in System > Administration > Networking. I enabled the device  there. I can only set an ESSID and an ASCII or HEX key. I have no WPA/WP2 options, which I don't get, since I have WPA_supplicant installed and all the required modules for it.  Even when I only enter an ESSID and no key the connection just isn't coming up.

When I remove the password in Networking it keeps entering a key of al zeros when using iwconfig. Whenever I turn off encryption with ifconfig, it keeps setting the key zero when I iwconfig some time later. I tried manually changing the /etc/network/interfaces with the instructions mentioned in this thread. 
[http://www.ubuntuforums.org/showthread.php?t=318539](http://www.ubuntuforums.org/showthread.php?t=318539)

I tried to install the linux-restricted-modules-generic but it says I already have the latest version.

 How to get ipw3945 and wep/wpa to work

    * Read #General Notes
    * Read #How to add extra repositories
    * Edgy already has all the drivers built in, except for the ipw3945 regulatory daemon. There are two ways to get it:
    * Install it manually from source: 

    See the daemon source and the Intel ipw3945 project page. 

OR

    * Install the daemon using apt (recommended for new users): 

root@Unimatrix0:/home/drone# **apt-get install linux-restricted-modules-generic**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-restricted-modules-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I even tried manually installing the driver following the advice on ipw3945.sourceforge.net. I tried reconfiguring the current kernel withouth ipw3945 support and then manually install the driver. For some reason I can't recompile a new kernel version from the kernel headers of the original Ubuntu release. It says that it works out of the box. I shouldn't be needing to recompile the kernel to get it to work properly. What's going on here? I'm at a loss. I've been at it for two days and can't figure this out. :( 

Why don't I have more options in the network tool besides ASCII and Hexadecimal?
What am I doing terribly wrong?

Help is much appreciated.

---

### Post by c.dric on 2006-12-28
could u put the output of the following command ?

less /etc/network/interfaces

(you can blank the key if you like)

The networking program in System > Administration doesn't support WPA that's why you don't have a WPA option in that program. U can edit your WPA settings manually tho.

---

### Post by Dr0n3 on 2006-12-28
> **c.dric said:**
> could u put the output of the following command ?

less /etc/network/interfaces

(you can blank the key if you like)

The networking program in System > Administration doesn't support WPA that's why you don't have a WPA option in that program. U can edit your WPA settings manually tho.

**drone@Unimatrix0:~$ less /etc/network/interfaces**
auto lo
iface lo inet loopback


iface eth0 inet dhcp


iface eth1 inet dhcp
wpa-driver wext
wpa-conf /etc/wpa_supplicant.conf
wireless-essid Borg Collective
wireless-key
wireless-channel 7
wireless-mode managed


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth1

auto eth0

**drone@Unimatrix0:~$ less /etc/wpa_supplicant.conf**
network={
        ssid="Borg Collective"
        scan_ssid=1 # only needed if your access point uses a hidden ssid
        proto=WPA
        key_mgmt=WPA-PSK
        psk=<output of wpa_passphrase "essid" "password">
  }

I also tested wpa_supplicant with
**root@Unimatrix0:/home/drone# sudo wpa_supplicant -ieth1 -c/etc/wpa_supplicant.conf -Dwext -w**

I get nothing as output. the expected output should be something like this:
**Trying to associate with 00:ff:00:1e:a7:7d (SSID='NetworkEssid' freq=0 MHz)**

I get absolutely nothing. I have to ctrl-c to get back to the prompt with the event:
**CTRL-EVENT-TERMINATING - signal 2 received**

I can recall I saw a screenshot of the program with all the options available. Was that another program? Is there a GUI tool for Ubuntu which does show all the options for encryption?

Thanks for your help.

---

### Post by sulli219 on 2006-12-28
I had the same wireless problem with the same card.  I commented out all references to eth1 in /etc/network/interfaces and then restarted.  That worked for me.  Prior to that I had installed gnome-network-manager

---

### Post by louistan3 on 2006-12-28
like the previous poster said.. install gnome-network-manager and take eth1 out of ur interfaces file and reboot.. that worked for me too.. im not sure about WPA2 stuff.. but hidden essid's work with network manager.. hope u figure it out... il try to think of sumthn to help u out more.. :D goodluck..

---

### Post by c.dric on 2006-12-28
i would suggest that you follow this how-to : 
[http://www.ubuntuforums.org/showthread.php?t=202834](http://www.ubuntuforums.org/showthread.php?t=202834)

i'm going to copy/paste the part that are relevant to your case, you should check the original and the replies if you have more problem.

it looks like you already have wpa_supplicant installed so i'm skipping to step 2/ 
Editing /etc/network/interfaces

sudo gedit /etc/network/interfaces

auto eth1
iface eth1 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid <your_essid>
wpa-ap-scan 2
wpa-proto WPA RSN
wpa-pairwise TKIP CCMP
wpa-group TKIP CCMP
wpa-key-mgmt WPA-PSK
wpa-psk <output of wpa_passphrase "essid" "password">

save and restart the network with the following command : 

sudo /etc/init.d/networking restart

your connection should work now.
if your connection doesn't work at reboot, follow the steps in the second post of the how-to mentioned above.

---

### Post by Dr0n3 on 2006-12-28
> **c.dric said:**
> i would suggest that you follow this how-to : 
[http://www.ubuntuforums.org/showthread.php?t=202834](http://www.ubuntuforums.org/showthread.php?t=202834)

i'm going to copy/paste the part that are relevant to your case, you should check the original and the replies if you have more problem.

it looks like you already have wpa_supplicant installed so i'm skipping to step 2/ 
Editing /etc/network/interfaces

sudo gedit /etc/network/interfaces

auto eth1
iface eth1 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid <your_essid>
wpa-ap-scan 2
wpa-proto WPA RSN
wpa-pairwise TKIP CCMP
wpa-group TKIP CCMP
wpa-key-mgmt WPA-PSK
wpa-psk <output of wpa_passphrase "essid" "password">

save and restart the network with the following command : 

sudo /etc/init.d/networking restart

your connection should work now.
if your connection doesn't work at reboot, follow the steps in the second post of the how-to mentioned above.

Thanks for bringing this up. I did come accross this post and did try what was mentioned. It didn't work then. There must've been some other factors why this didn't work at first.

I first followed the advice of commenting out the eth1 in /etc/networking/interfaces. I thought why not delete the interfaces file and let Linux make a new one. I was thinking of Windows, because it often recreates config files too when deleted. Well, lol my Linux froze after logging in. It seems the interfaces file can't be deleted and that Linux requires one. It'll probably sound very noobish to you all, but I'm not used to working with Linux. :D

After a complete reinstall of Ubuntu, installing updates, I thought why not try the advice you gave me again. And yes it works! Amazing! It took me over 2 days and this didn't work at first. I'm pretty happy now. I'm gonna install Gnome Network Manager now and see if the network also comes up after rebooting. If not I'll follow the advice in the 2nd post.

Thank you all for the quick assistence, much appreciated! \\:D/

---

### Post by Dr0n3 on 2006-12-28
I got my wireless connection working now and it's starting automatically at every boot. I noticed that the symbolic link S40networking points to the script /etc/init.d/networking. However that scripts needs an argument in order to work. It should run as /etc/init.d/networking start. Is  that the bug maybe?

There's still a little problem though. I've installed Gnome Network Manager and its dependencies. The standard networking tools of Ubuntu in System > Administration show the eth1 wireless adapter even though I've disabled all adapters in System > Administration > networking. The wireless connection is working just fine. The Gnome Network Manager doesn't show any connections. It says that no networking devices are found even though my wireless connection eth1 is up and running. ](*,) 

I'm afraid to turn on the wireless connection in System > Administration > Networking since it'll mess with the interfaces file settings regarding SSID and WEP password. The first time it didn't work with the wireless interface enabled in System > Administration > Networking. I'd really like to be able to have a GUI in order to change network settings. Now the Gnome Network Manager doesn't show anything.

Does anyone know why this is the case? I'm puzzled by this. :-k

---

### Post by c.dric on 2006-12-28
i'm glad u got it working. 

(i have never used any of those graphical interfaces so i can't help you with those.)

---

### Post by nicknn on 2006-12-30
check out [http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)
Used it to get wireless going on Intel 3945ABG on dell inspiron 6400 running 6.10

---

### Post by nicknn on 2006-12-30
> **Dr0n3 said:**
> **drone@Unimatrix0:~$ less /etc/network/interfaces**
auto lo
iface lo inet loopback


iface eth0 inet dhcp


iface eth1 inet dhcp
wpa-driver wext
wpa-conf /etc/wpa_supplicant.conf
wireless-essid Borg Collective
wireless-key
wireless-channel 7
wireless-mode managed


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth1

auto eth0

**drone@Unimatrix0:~$ less /etc/wpa_supplicant.conf**
network={
        ssid="Borg Collective"
        scan_ssid=1 # only needed if your access point uses a hidden ssid
        proto=WPA
        key_mgmt=WPA-PSK
        psk=<output of wpa_passphrase "essid" "password">
  }

I also tested wpa_supplicant with
**root@Unimatrix0:/home/drone# sudo wpa_supplicant -ieth1 -c/etc/wpa_supplicant.conf -Dwext -w**

I get nothing as output. the expected output should be something like this:
**Trying to associate with 00:ff:00:1e:a7:7d (SSID='NetworkEssid' freq=0 MHz)**

I get absolutely nothing. I have to ctrl-c to get back to the prompt with the event:
**CTRL-EVENT-TERMINATING - signal 2 received**

I can recall I saw a screenshot of the program with all the options available. Was that another program? Is there a GUI tool for Ubuntu which does show all the options for encryption?

Thanks for your help.
try this:
[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

---

