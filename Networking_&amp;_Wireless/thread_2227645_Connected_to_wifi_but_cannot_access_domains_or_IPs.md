---
title: "Connected to wifi but cannot access domains or IPs outside of network"
date: 2014-06-03
forum: Networking &amp; Wireless
---

### Post by bernard6 on 2014-06-03
I'm running ubuntu saucy 13.10 with NetworkManager using XFCE. 


I can connect to my wifi server just find but cannot seem to get out. I can ping my router and my dns servers. Here is the output from some common commands. Also I empted my /etc/resolv.conf file because it was using my company's dns settings.


```
$ sudo nm-tool


NetworkManager Tool


State: connected (global)


- Device: wlan0 [0AJM7] -------------------------------------------------------
Type: 802.11 WiFi
Driver: iwlwifi
State: connected
Default: yes
HW Address: 3C:A9:F4:56:59:7C


Capabilities:
Speed: 1 Mb/s


Wireless Properties
WEP Encryption: yes
WPA Encryption: yes
WPA2 Encryption: yes


Wireless Access Points (* = current AP)
*0AJM7: Infra, 00:18:01:FE:4A:FE, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WEP
NKMWPA: Infra, 00:0F:61:EF:1F:36, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA2
KVA-Vendor: Infra, 00:0F:61:EF:1F:37, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA2 Enterprise
GMIGuest: Infra, 00:0F:61:EF:1F:32, Freq 2462 MHz, Rate 54 Mb/s, Strength 19
NKMWPA: Infra, 00:0F:61:FF:F9:F6, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA2


IPv4 Settings:
Address: 192.168.1.14
Prefix: 24 (255.255.255.0)
Gateway: 192.168.1.1


DNS: 192.168.1.1
DNS: 71.243.0.12




- Device: eth0 -----------------------------------------------------------------
Type: Wired
Driver: e1000e
State: unavailable
Default: no
HW Address: 3C:97:0E:BA:31:BD


Capabilities:
Carrier Detect: yes


Wired Properties
Carrier: off


$ifconfig
eth0 Link encap:Ethernet HWaddr 3c:97:0e:ba:31:bd 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:20 Memory:f2500000-f2520000 


lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:65536 Metric:1
RX packets:19828 errors:0 dropped:0 overruns:0 frame:0
TX packets:19828 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:1615152 (1.6 MB) TX bytes:1615152 (1.6 MB)


wlan0 Link encap:Ethernet HWaddr 3c:a9:f4:56:59:7c 
inet addr:192.168.1.14 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::3ea9:f4ff:fe56:597c/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:11090 errors:0 dropped:0 overruns:0 frame:0
TX packets:16157 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:1653759 (1.6 MB) TX bytes:1760221 (1.7 MB)


$ grep -i error syslog
Jun 3 06:16:17 user-ws1 kernel: [ 1.048353] tpm_tis 00:09: A TPM error (6) occurred attempting to read a pcr value
Jun 3 06:16:17 user-ws1 kernel: [ 3.103800] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
Jun 3 06:16:17 user-ws1 kernel: [ 3.261134] iwlwifi 0000:03:00.0: Direct firmware load failed with error -2
Jun 3 06:16:17 user-ws1 kernel: [ 3.427961] iwlwifi 0000:03:00.0: Direct firmware load failed with error -2
Jun 3 06:16:28 user-ws1 NetworkManager[1212]: <error> [1401790588.784570] [nm-dns-dnsmasq.c:402] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Jun 3 06:16:29 user-ws1 ntpdate[2116]: Can't find host ntp.ubuntu.com: System error (-11)
Jun 3 06:16:30 user-ws1 ntpdate[2195]: Can't find host ntp.ubuntu.com: System error (-11)

```
I removed dnsmasq from /etc/NetworkManager/NetworkManager.conf and rebooted, it seemed to get rid of those iwlwifi direct firmware load and most dnsmasq errors 


```

Jun 3 07:17:38 user kernel: [ 4.500000] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
Jun 3 07:17:39 user ntpdate[1369]: Can't find host ntp.ubuntu.com: System error (-11)
Jun 3 07:17:47 user NetworkManager[1214]: <error> [1401794267.502070] [nm-dns-dnsmasq.c:402] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Jun 3 07:17:47 user ntpdate[2170]: Can't find host ntp.ubuntu.com: System error (-11)




$ ping google.com
ping: unknown host google.com




$ ping 74.125.237.18 # supposed to be one of google.com's servers
PING 74.125.237.18 (74.125.237.18) 56(84) bytes of data.
^C
--- 74.125.237.18 ping statistics ---
45 packets transmitted, 0 received, 100% packet loss, time 44328ms




$ uname -a
Linux user-ws1 3.8.0-35-generic #50-Ubuntu SMP Tue Dec 3 01:24:59 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux




$ ls -la /boot
total 81616
drwxr-xr-x 3 root root 4096 Jun 3 06:29 ./
drwxr-xr-x 24 root root 4096 Jun 3 06:29 ../
-rw-r--r-- 1 root root 919810 Nov 12 2013 abi-3.8.0-34-generic
-rw-r--r-- 1 root root 919810 Dec 2 20:53 abi-3.8.0-35-generic
-rw-r--r-- 1 root root 154961 Nov 12 2013 config-3.8.0-34-generic
-rw-r--r-- 1 root root 154950 Dec 2 20:53 config-3.8.0-35-generic
drwxr-xr-x 5 root root 4096 Jun 3 06:30 grub/
-rw-r--r-- 1 root root 32036206 Jan 12 11:37 initrd.img-3.8.0-34-generic
-rw-r--r-- 1 root root 32109265 Feb 25 11:20 initrd.img-3.8.0-35-generic
-rw-r--r-- 1 root root 176764 Dec 5 2012 memtest86+.bin
-rw-r--r-- 1 root root 178944 Dec 5 2012 memtest86+_multiboot.bin
-rw------- 1 root root 3062653 Nov 12 2013 System.map-3.8.0-34-generic
-rw------- 1 root root 3068291 Dec 2 20:53 System.map-3.8.0-35-generic
-rw------- 1 root root 5364080 Nov 12 2013 vmlinuz-3.8.0-34-generic
-rw------- 1 root root 5391024 Dec 2 20:53 vmlinuz-3.8.0-35-generic

```




It seems this problem happened after upgrading to the new kernel image 3.14. While the kernel image was running (probably a bad idea), I removed the 3.14 kernel image and updated grub. I then went back to the 3.8.0-35 and tried -34 kernel images but the same issue exists. 


```

Also checked apt log file and these were the last installations and removals from when it used to work:
$ cat /var/log/apt/history.log
Start-Date: 2014-05-29 10:57:04
Commandline: apt-get remove virtualbox
Remove: virtualbox:amd64 (4.2.10-dfsg-0ubuntu2.1), virtualbox-dkms:amd64 (4.2.10-dfsg-0ubuntu2.1), virtualbox-qt:amd64 (4.2.10-dfsg-0ubuntu2.1)
End-Date: 2014-05-29 10:57:18




Start-Date: 2014-05-29 11:44:01
Commandline: apt-get remove dkms
Remove: dkms:amd64 (2.2.0.3-1.1ubuntu2), virtualbox-guest-dkms:amd64 (4.2.10-dfsg-0ubuntu2.1)
End-Date: 2014-05-29 11:44:15




Start-Date: 2014-05-29 12:54:42
Commandline: apt-get install virtualbox
Install: virtualbox:amd64 (4.2.10-dfsg-0ubuntu2.1), virtualbox-dkms:amd64 (4.2.10-dfsg-0ubuntu2.1, automatic), dkms:amd64 (2.2.0.3-1.1ubuntu2, automatic), virtualbox-qt:amd64 (4.2.10-dfsg-0ubuntu2.1, automatic)
End-Date: 2014-05-29 12:55:40




Start-Date: 2014-05-30 09:23:10
Commandline: apt-get remove virtualbox
Remove: virtualbox:amd64 (4.2.10-dfsg-0ubuntu2.1), virtualbox-dkms:amd64 (4.2.10-dfsg-0ubuntu2.1), virtualbox-qt:amd64 (4.2.10-dfsg-0ubuntu2.1)
End-Date: 2014-05-30 09:23:19




Start-Date: 2014-06-03 06:29:47
Commandline: apt-get purge linux-image-3.14.4-031404-generic linux-headers-3.14.4-031404*
Purge: linux-headers-3.14.4-031404-generic:amd64 (3.14.4-031404.201405130853), linux-headers-3.14.4-031404:amd64 (3.14.4-031404.201405130853), linux-image-3.14.4-031404-generic:amd64 (3.14.4-031404.201405130853)
End-Date: 2014-06-03 06:29:56

```
Could you recommend me a way to remedy this issue?


Thanks,

---

### Post by TheFu on 2014-06-03
Lets be a little systematic to determine exactly where the issue lies.
From [here]("http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking"), is says:
# Ping the router by IP
# ping a commonly known internet IP - 8.8.8.8 is an example
# see if DNS is working - try a few different, well-known, sites by name

Please do that and post the results back here (please use "code" tags too).

---

### Post by bernard6 on 2014-06-03
Hi TheFu, 

Thanks for commenting. The first post was edited to use code tags instead of quote tags for readability. 

I can ping my router and my router's DNS servers
I cannot ping google.com or yahoo.com
I cannot ping google's IP address e.g. 74.125.226.9 or 8.8.8.8

I've been working on this issue all day and still no luck. I'm looking at the following options...

(1) Best case scenario, this issue is solved without a reinstall
(2) if not, is it possible I can use a recovery CD / DVD
(3) or would it be better to backup my home directory, backup history of apt-get install commands, and reinstall?

Thanks,

---

### Post by TheFu on 2014-06-04
So 
* local networking works.
* WAN networking is broken.

Please post the output from the "route" command.
What are your router's DNS servers?  Are they at the ISP or somewhere else?  That could be the differentiator .... WAN broken, but to the ISP network is working?

Deleting the resolv.conf means DNS won't work - at least that's how it works on my systems.
I don't think anything as drastic as a reinstall is needed.  Perhaps reinstalling network-manager would reset the default configs? I dunno.

Do you have any other computer that is working to get everywhere?  Basically, to get a set of network settings that we can copy?

---

