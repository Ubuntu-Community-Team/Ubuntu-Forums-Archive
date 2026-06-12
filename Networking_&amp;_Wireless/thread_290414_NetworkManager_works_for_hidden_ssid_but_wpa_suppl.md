---
title: "NetworkManager works for hidden ssid but wpa_supplicant doesn't"
date: 2006-11-01
forum: Networking &amp; Wireless
---

### Post by Jan Hrbacek on 2006-11-01
Yesterday I was complaining here that since I changed from FC5 to Ubuntu Edgy, my wireless Dell 1490 Minicard integrated in my Latitude D820 doesn't work.

Ok, so I replaced HD with my previous with FC5 on it and investigated differences with FC5 and these are the remarks:

In FC5, the wifi connects to hidden ssid WPA1 through NetworkManager without any problem. If I turn off NetworkManager by killall NetworkManager and then start only wpa_supplicant,

wpa_supplicant -i wlan0 -c /etc/wpa_supplicant.conf -D ndiswrapper -d

I am not able to connet to hidden ssid anymore. It scans only other access points that are not hidden, but I do not see the hidden one.

I find this strange, because to my knowledge, NetworkManager uses wpa_supplicant to connect to wpa ap. As NetworkManager is able to connect to hidden ssid and wpa_supplicant by itself isn't, I believe wpa_supplicant in principle works on my machine, however, I do not have it configured properly and when it gets parameters from NetworkManager, everything is fine.

Could you help? How to find out what parameters gives NetworkManager to wpa_supplicant? Does NetworkManager has its own config file for wpa_supplicant or does it use its own wpa_supplicant.conf?

Thank you.

/etc/wpa_supplicant.conf:

network={
               ssid="Carlo"
               scan_ssid=1
               key_mgmt=WPA-EAP WPA-PSK IEEE8021X NONE
               pairwise=CCMP TKIP
               group=CCMP TKIP WEP104 WEP40
               psk=*******
               eap=TTLS PEAP TLS
          }

---

### Post by Jan Hrbacek on 2006-11-01
[root@electron jan]# /usr/sbin/wpa_supplicant -v
wpa_supplicant v0.4.8
Copyright (c) 2003-2006, Jouni Malinen <jkmaline@cc.hut.fi> and contributors

[root@electron jan]# /usr/sbin/wpa_supplicant -i wlan0 -c /etc/wpa_supplicant.conf -D ndiswrapper -d
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'ndiswrapper' ctrl_interface 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Priority group 0
   id=0 ssid='Carlo'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=20 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
Own MAC address: 00:16:cf:12:78:27
Driver does not support WPA.
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
Setting scan request: 0 sec 100000 usec
Added interface wlan0
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=5):
     43 61 72 6c 6f                                    Carlo
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 161 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
0: 00:00:c5:d2:1e:a5 ssid='64417141' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
No suitable AP found.
Setting scan request: 5 sec 0 usec
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface wlan0
State: SCANNING -> DISCONNECTED
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Failed to disable WPA in the driver.
No keys have been configured - skip key clearing
Cancelling scan request

---

### Post by Jan Hrbacek on 2006-11-01
I found out NetworkManager doesn't use /etc/wpa_supplicant.conf at all. If I erase it, it still successfuly connects based on information that I provide in its gui.

When I connect through NetworkManager, this is what I get:
```

wlan0     Scan completed :
          Cell 01 - Address: 00:C0:49:F3:C3:02
                    ESSID:"Carlo"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-82 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

wlan0     IEEE 802.11g  ESSID:"Carlo"
          Mode:Managed  Frequency:2.462 GHz  Access Point:00:C0:49:F3:C3:02
          Bit Rate:11 Mb/s   Tx-Power:32 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-81 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan0     Link encap:Ethernet  HWaddr 00:16:CF:12:78:27
          inet addr:192.168.2.153  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::216:cfff:fe12:7827/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2361 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2183 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1826553 (1.7 MiB)  TX bytes:327552 (319.8 KiB)
          Interrupt:177 Memory:dcffc000-dd000000
```

Based on the information I created this /etc/wpa_supplicant.conf

```

ctrl_interface=/var/run/wpa_supplicant
ap_scan=2

network={
        ssid="Carlo"
        proto=WPA
        key_mgmt=WPA-PSK
        pairwise=TKIP
        group=TKIP
        scan_ssid=1
        #psk="***"
        psk=***
}

```

And when I run wpa_supplicant -i wlan0 -c /etc/wpa_supplicant.conf -D ndiswrapper -d, I get

```

Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'ndiswrapper' ctrl_interface 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ap_scan=2
Priority group 0
   id=0 ssid='Carlo'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=20 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
Own MAC address: 00:16:cf:12:78:27
Driver does not support WPA.
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
Setting scan request: 0 sec 100000 usec
Added interface wlan0
Wireless event: cmd=0x8b06 len=8
State: DISCONNECTED -> SCANNING
Trying to associate with SSID 'Carlo'
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: No WPA/RSN IE available from association info
WPA: Set cipher suites based on configuration
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
State: SCANNING -> ASSOCIATING
Association request to the driver failed
Setting authentication timeout: 15 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
```

I am running out of ideas... :confused: :confused: ](*,) ](*,) :-k :sad:

---

### Post by wieman01 on 2006-11-01
Ok, you can try this thread. Before you do so, please uninstall NetworkManager completely. Also we won't use wpa_suppliant.conf at all but store all information in "/etc/network/interfaces":

[http://www.ubuntuforums.org/showthread.php?t=202834]("http://www.ubuntuforums.org/showthread.php?t=202834")

This thread addresses both WPA1 and WPA2. Hidden ESSID is also mentioned in  there ("wpa-ap-scan 2"). Post your problem there if you need help. Squibt & I can help you for sure. Post #4 is on WPA1 (TKIP).

---

### Post by Jan Hrbacek on 2006-11-01
Thank you for advice. I am going to try it right now. :twisted:

---

### Post by Jan Hrbacek on 2006-11-01
> **wieman01 said:**
> Ok, you can try this thread. Before you do so, please uninstall NetworkManager completely. Also we won't use wpa_suppliant.conf at all but store all information in "/etc/network/interfaces":

[http://www.ubuntuforums.org/showthread.php?t=202834]("http://www.ubuntuforums.org/showthread.php?t=202834")

This thread addresses both WPA1 and WPA2. Hidden ESSID is also mentioned in  there ("wpa-ap-scan 2"). Post your problem there if you need help. Squibt & I can help you for sure. Post #4 is on WPA1 (TKIP).

LET ME DEDUCATE MY FIRST I-MESSAGE EVER FROM MY NEW UBUNTU EDGY TO YOU, WIEMAN! ;) 

You saved a lot of time and effort to me. I am trying to set it up for two days already! I have spent neverending hours editing /etc/wpa_supplicant.conf without any result... This is what I had to do in /etc/network/interfaces and suddenly everything is fine! It's the same parameters I am trying to push into wpa_supplicant.conf for days!!! :evil: 

```

auto eth1
iface eth1 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid Carlo
wpa-ap-scan 2
wpa-proto TKIP
wpa-pairwise TKIP
wpa-key-mgmt WPA-PSK
wpa-psk hex-pass
```

To make information complete, I have wpa_supplicant v0.5.4 (it is included on install CD of Edgy), ndiswrapper-common a -utils 1.18 (also included on the CD), Dell wireless 1490 minicard with bcmwl5 driver (downloaded from Dell www) on Dell Latitude 820.

Also I find your solution much cleaner than using wpa_supplicant.conf.

Once again, thank you very much, man! \\:D/ \\:D/ \\:D/

---

### Post by Jan Hrbacek on 2006-11-01
One more question to this issue:
When I restart computer I have to manually

sudo depmode -a
sudo modprobe ndiswrapper

and then everything is fine.

When I wanted to ensure automatic loading I did (according to one of Ubuntu HOWTOs)

sudo ndiswrapper -m

However, my computer is missing /etc/modules. Neccesary lines for ndiswrapper are obviously inserted somewhere else. Any idea how to solve it?

---

### Post by wieman01 on 2006-11-01
Glad it did the job. We'll update the WPA howto soon as it only covers a fraction of what is possible. Keep an eye on it. :-)

As for the missing "/etc/modules" I am not sure why it is missing. However, please runs this command & restart the computer:
> sudo ndiswrapper -m
If this does not work for you, we'll create a little startup script. No problem.

---

### Post by Jan Hrbacek on 2006-11-02
> **wieman01 said:**
> Glad it did the job. We'll update the WPA howto soon as it only covers a fraction of what is possible. Keep an eye on it. :-)

As for the missing "/etc/modules" I am not sure why it is missing. However, please runs this command & restart the computer:

If this does not work for you, we'll create a little startup script. No problem.

1] Sorry for mistaking you. I have /etc/modules and this is how it looks:

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
sbp2

```

I have manually added "ndiswrapper" to it as I believe this is what "ndiswrapper -m" does.

2] I have found in my computer in /etc/modprobe.d/ndiswrapper following

```

options ndiswrapper if_name=eth1
alias wlan0 ndiswrapper
```

Shoudln't this be in /etc/modules?

I also added a script 

```
/etc/init.d/networking restart
```

to /etc/init/d/wireless-network.sh as discribed in the forum you reminded me of and created symbolic link S35wireless-network in the same directory.

3] When I restart computer, now I can see eth1 up with ifconfing and iwconfig, however it is not properly configured. I do "ifdown eth1" and then "ifup eth1" and everything is fine.

...

Obviously script in /etc/modprobe.d/ndiswrapper is not executed during startup (otherwise I would have wlan0 instead of eth1), right?

What is relationship between /etc/modules and files in .etc/modprobe.d/?

Something during bootup brings eth1 up. Is it the line ndiswrapper that I have manually added to /etc/modules? Nevertheless, after being brought up, it is not properly configured. The script in S35wireless-network is perhaps not executed either.

---

### Post by wieman01 on 2006-11-02
Ok, first of all... Have you blacklisted the native Linux driver for your card? It looks as if you have not. That's probably why "eth1" keeps appearing. What's your card's chipset?

"/etc/modules" let's you load additional modules (such as "ndiswrapper"), "/etc/modprobe.d/ndiswrapper" is responsible for the alias (= "wlan0") of your wireless adapter. That's as much as the relationship goes.

"ifdown eth1" & "ifup eth1" should not have any impact on your system. Your wireless interfaces is "wlan0". 

Please edit "/etc/network/interfaces" and ensure that only 3 adapters are mentioned in there:

1. lo (loopback)
2. eth0 (Ethernet)
3. wlan0 (wireless via "ndiswrapper")

Delete all the rest.

As for the problem with the startup script, have you made it executable by type "chmod +x..."?

---

### Post by wieman01 on 2006-11-02
To blacklist the Linux driver (Broadcom) please follow the first three steps of this howto: [http://www.ubuntuforums.org/showthread.php?t=285809&highlight=howto+broadcom]("http://www.ubuntuforums.org/showthread.php?t=285809&highlight=howto+broadcom")

---

### Post by Jan Hrbacek on 2006-11-02
> **wieman01 said:**
> Ok, first of all... Have you blacklisted the native Linux driver for your card? It looks as if you have not. That's probably why "eth1" keeps appearing. What's your card's chipset?

Yes, I have blacklisted the original driver previously. This is not the case.

See log from dmesg:

```
[17179591.568000] ndiswrapper: using irq 177
[17179591.872000] NET: Registered protocol family 17
[17179592.296000] wlan0: vendor: ''
[17179592.296000] wlan0: ethernet device 00:16:cf:12:78:27 using NDIS driver bcmwl5, 14E4:4312.5.conf
[17179592.296000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[17179592.300000] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
```

It is the ndiswrapper itself that changes wlan0 to eth1. Therefore I had to replace all 'wlan0' to 'eth1' in '/etc/network/interfaces' and in '/etc/modprobe.d/ndiswrapper'

If I keep 'wlan0' in these files, I only see 'lo' and 'eth0' after booting the system. If I try to bring 'wlan0' up:


```
jan@electron:~$ sudo ifup wlan0
ioctl[SIOCSIWPMKSA]: No such device
ioctl[SIOCSIWMODE]: No such device
Could not configure driver to use managed mode
ioctl[SIOCGIFFLAGS]: No such device
Could not set interface 'wlan0' UP
ioctl[SIOCGIWRANGE]: No such device
ioctl[SIOCGIFINDEX]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWAUTH]: No such device
WEXT auth param 7 value 0x0 - Failed to disable WPA in the driver.
ioctl[SIOCSIWAUTH]: No such device
WEXT auth param 5 value 0x0 - ioctl[SIOCSIWAUTH]: No such device
WEXT auth param 4 value 0x0 - ioctl[SIOCSIWAP]: No such device
ioctl[SIOCGIFFLAGS]: No such device
wpa_supplicant: ctrl_interface socket not found at /var/run/wpa_supplicant/wlan0...aborting!
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
```

> **wieman01 said:**
> Please edit "/etc/network/interfaces" and ensure that only 3 adapters are mentioned in there:

1. lo (loopback)
2. eth0 (Ethernet)
3. wlan0 (wireless via "ndiswrapper")


Yes, I only have these. (But I had to change to 'eth1' again to make it work.)

> **wieman01 said:**
> 
As for the problem with the startup script, have you made it executable by type "chmod +x..."?

I have done it before.

---

### Post by wieman01 on 2006-11-02
Ok, apparently the "eth1" thing is peculiar to Edgy. The previous versions of Ubuntu were different. 

I also see in the dmesg log that the interfaces changes from "wlan0" to "eth1". So that's fine then.

Do you still have to modprobe after the system has booted? I assume that has been resolved.

The remaining bit is that you cannot successfully restart your network, correct? Could you please post all commands that you have executed? Where have you created the symb-link? That may be the problem... my instructions in the other thread have been unclear. I need to correct them when I get back home.

---

### Post by scoobyNZ on 2006-11-02
Hi Wieman01, I have been trudging through these forums and note that you have been able to assist a few people. My thread is below, would apprecaite some help if possible.

[http://ubuntuforums.org/showthread.php?t=290857](http://ubuntuforums.org/showthread.php?t=290857)

Thanks,
C

---

### Post by wieman01 on 2006-11-02
Jan:

This is the right version...

_Create startup script:_
> cd /etc/init.d/
sudo gedit wireless-network.sh
_Add 1 line & save file:_
> /etc/init.d/networking restart
_Change permission (executable):_
> sudo chmod +x wireless-network.sh
_Create symbolic link:_
> cd /etc/rcS.d/
sudo ln -s /etc/init.d/wireless-network.sh **[COLOR="Red"]S40[/COLOR]**wireless-network
[Note: You may have to choose a boot sequence other than **[COLOR="Red"]S40[/COLOR]**.]

Restart...

---

### Post by Jan Hrbacek on 2006-11-03
Thank you for all your effort **Wieman01**. 

I did everything as you said and here are my observations:

1) Device really needs to be reffered to as 'eth1', not 'wlan0'.

2) I have added the S40wireless-network link to the script exactly as you have described it and rebooted. Booting time has significantly prolonged. Before my linuxbox booted in quite impresive 21 seconds, now it was over a minute. Booting got stuck on the added link. I guess it has something to do with negotiation with dhcp server. However, if I try to restart networking from command line, it is never more than 5 seconds.

3) I have also tried to change the number and instead of S40 I used S99 to make it the last item in the booting sequence. It had no influence on booting behavior.

4) I tried to boot in 10 times. In 5 out of 10 tries, 'eth1' was up and successfuly configured and I could go directly on internet.

5) In the remaining 5 cases, 'eth1' was up, however not configured properly (it had no IP address assigned). I had to do first 

```
sudo ifdown eth1
sudo ifup eth1
```

and everything was fine within 5 seconds. Sometimes I had to reapeat 

```
sudo ifup eth1
```

once or twice.

6) As bringing up of wifi during bootup doesn't work 100% and it prolongs the boot time too much, I have removed it from /etc/rcS.d/

7) Then I tried to boot up linuxbox several times again. It boots again in 21 seconds and sometimes 'eth1' is fully configured after boot, sometimes it is not and I have to repeat the procedure described in step 5)

I am sure, sooner or later some solution will appear. I guess it is about negotiating with dhcp.

Once again, thank you for all your help!

---

### Post by wieman01 on 2006-11-03
Hello Jan, 

This is really odd. You could possibly play around with your router settings (wireless network settings, static IP, etc.). Perhaps the problem hides there.

If the startup script is an issue & your system basically freezes for more than 5 seconds it could mean the following:

1. When Ubuntu boots, it tries to synchronize the system clock with a server on the Internet (forgot the exact name... need to check back home).
2. If the DNS has a problem (or your DNS settings) the name resolution will fail & hence the system simply hangs there until it can resolve the name OR times out.
3. So I reckon that there is an issue with the DNS settings... 

You can check your DNS settings via this file:
> /etc/resolv.conf
This file is dynamically updated upon boot, however, you can configure the DNS manually (simply add your ISP's DNS IP address there & remove the local IP address = your router). That done you need to ensure that the system won't overwrite this file. Simply do this:
> sudo chattr +i /etc/resolv.conf
Could you try that?

---

### Post by Jan Hrbacek on 2006-11-12
Hi wieman01,

I think I managed to solve the issue...

Recently I have found out that my Edgy Eft boots to the runlevel 2. Of course, the procedure woudn't work for me as it was written for runlevel 5. 

I didn't expect this at all.

Up to now I just have run manually a little script to bring down and again up eth1. It seems I will not have to do this annoying procedure anymore.

I also run in another issue. After several hours, connection interrupts and it is not possible to bring it up anymore. IP address is not recieved from DHCP server.

I have looked in dmesg dump and found there must be some hardware conflict. I recieve irq#177 nobody cared... Try to boot with irqpoll option.

I have added irqpoll to grub config file and now I test it if it will appear again. To be honest, I have no clue what irqpoll does...

---

### Post by Jan Hrbacek on 2006-11-13
Yes, unfortunatelly irq#177 nobody cared... appears again... and searching this forum I see I am not the only one...

conflict of nvidia driver and wireless... :-? :-? :-?

---

### Post by wieman01 on 2006-11-13
Yes, meaning that you need to disable the "nvidia" driver as long as there is not patch available. See this thread for more details (post #1 in particular):

[http://www.ubuntuforums.org/showthread.php?t=295787]("http://www.ubuntuforums.org/showthread.php?t=295787")

---

### Post by phelixnyc on 2006-11-13
This may be off the topic and the wrong place to post this question but I cant seem to log on to my router start up page. Iam using a Linksys WRT54G v.5. How do I begin to fix this problem?

---

### Post by Jan Hrbacek on 2006-11-13
> **wieman01 said:**
> Yes, meaning that you need to disable the "nvidia" driver as long as there is not patch available. See this thread for more details (post #1 in particular):

[http://www.ubuntuforums.org/showthread.php?t=295787]("http://www.ubuntuforums.org/showthread.php?t=295787")

Well, I am not really excited about this solution as the performance of the native nv driver really sucks...

I think up to the moment it is solved, I will restart my computer every time it happens. It is usually good for one or two hours. 

It's not simple to be a linux user :-) one problem solved, another appears. But it is fun to solve them, if they have solution on user level...

---

### Post by wieman01 on 2006-11-13
> **Jan Hrbacek said:**
> Well, I am not really excited about this solution as the performance of the native nv driver really sucks...

I think up to the moment it is solved, I will restart my computer every time it happens. It is usually good for one or two hours. 

It's not simple to be a linux user :-) one problem solved, another appears. But it is fun to solve them, if they have solution on user level...
Question: Have you tested it while using "nv" rather than "nvidia"? Asking because I was wondering if that is the cause of your problem or perhaps something else.

So I'd use "nv" & have the computer running for a few hours. If the problem reoccurs, then something else is the culprit.

---

### Post by Jan Hrbacek on 2006-11-14
I have been using nv for about a month and it was just last week I have installed nvidia driver. I didn't have the problem before. Nevertheless, it was not even possible to run screensavers nicely and the graphic performance was soooooo bad...

---

### Post by katsi on 2007-03-05
Hello,


I hope you could help me. I'm having problems setting up my wlan with wpa on kubuntu 6.10.
I tried the following things:

(1) Access to wlan without any encryption, successfull
(2) Installed knetworkmanager, successfull connection to router
(3) uninstalled knetworkmanager and setup /etc/network/interface with the following settings:

iface eth1 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid Katsi
wpa-ap-scan 1
wpa-proto TKIP
wpa-pairwise TKIP
wpa-key-mgmt WPA-PSK
wpa-psk <key>

... I have no luck if I call ifup eth1

(4) Then I tried with wpa_supplicant (with knetworkmanager deinstalled) with the following configuration:

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=1
ap_scan=1

network={
        ssid="Katsi"
        key_mgmt=WPA-PSK
        scan_ssid=1
        pairwise=TKIP
        group=TKIP
        proto=WPA
        psk=<key>
}

... calling wpa_supplicant -D wext -ieth1 -c /etc/wpa_supplicant/home.conf -dd -t -K -w

... but I haven't got any luck either.

In /var/log/messages I can see the error

ADDRCONF(NETDEV_UP): eth1: link is not ready

Very rarely I can see

ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready

... then the connection works. But this happens in 1 out of 10 or more tries.

I'm fighting for more then 2 days now, I don't know what else can I try.

ipw3945 is loaded

Any help would be appreciated.

Thanks a lot in advance

---

### Post by GMU_DodgyHodgy on 2007-03-05
> **wieman01 said:**
> Ok, you can try this thread. Before you do so, please uninstall NetworkManager completely. Also we won't use wpa_suppliant.conf at all but store all information in "/etc/network/interfaces":

[http://www.ubuntuforums.org/showthread.php?t=202834]("http://www.ubuntuforums.org/showthread.php?t=202834")

This thread addresses both WPA1 and WPA2. Hidden ESSID is also mentioned in  there ("wpa-ap-scan 2"). Post your problem there if you need help. Squibt & I can help you for sure. Post #4 is on WPA1 (TKIP).

I am running into a similar situation.  I have a Linksys Ralink RT2500 chipset wireless card and I am trying to connect to a wireless access point (also Linksys).  Since the drivers for this chip are included in Edgy, I can see my card under the ra0 interface.   

My key question is this - How do I Uninstall Network Manager?

Sorry if I am being dumb - but I am a noob to Linux and Ubuntu.

---

### Post by wieman01 on 2007-03-06
> **GMU_DodgyHodgy said:**
> I am running into a similar situation.  I have a Linksys Ralink RT2500 chipset wireless card and I am trying to connect to a wireless access point (also Linksys).  Since the drivers for this chip are included in Edgy, I can see my card under the ra0 interface.   

My key question is this - How do I Uninstall Network Manager?

Sorry if I am being dumb - but I am a noob to Linux and Ubuntu.
This way:
> sudo apt-get remove network-manager network-manager-gnome

---

### Post by katsi on 2007-03-08
Could somebody please help me with my previous post?

I don't want to use knetworkmanager, as I prefer using scripting and controlling what happens.

Thanks in advance,

Silvio

---

### Post by wieman01 on 2007-03-08
> **katsi said:**
> Could somebody please help me with my previous post?

I don't want to use knetworkmanager, as I prefer using scripting and controlling what happens.

Thanks in advance,

Silvio
Then try the HOWTO in my signature... :-) Post there if you need help.

---

