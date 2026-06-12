---
title: "Wifi card not going up after sleep"
date: 2014-08-14
forum: Networking &amp; Wireless
---

### Post by georgesgiralt on 2014-08-14
Hello !
The context : Laptop (Lenovo 3000 N200) with Intel 3945 abg wifi card.
Running Ubuntu LTS 14.04.1 (upgraded from 12.04 LTS).
Interface managed through /etc/network/interfaces (no NetworkManager service but software is installed).
When I activate the laptop from sleep (not hibernate), the Wifi link does not come back. I get this in the logs :
```

When I awake Aug 14 17:48:22 localhost kernel: [  628.885010] video LNXVIDEO:01: Restoring backlight state
Aug 14 17:48:22 localhost bluetoothd[639]: Adapter /org/bluez/639/hci0 has been enabled
Aug 14 17:48:22 localhost bluetoothd[639]: Endpoint registered: sender=:1.50 path=/MediaEndpoint/HFPAG
Aug 14 17:48:22 localhost bluetoothd[639]: Endpoint registered: sender=:1.50 path=/MediaEndpoint/HFPHS
Aug 14 17:48:22 localhost bluetoothd[639]: Endpoint registered: sender=:1.50 path=/MediaEndpoint/A2DPSource
Aug 14 17:48:22 localhost bluetoothd[639]: Endpoint registered: sender=:1.50 path=/MediaEndpoint/A2DPSink
Aug 14 17:48:22 localhost bluetoothd[639]: hci0: Load Long Term Keys (0x0013) failed: Not Supported (0x0c)
Aug 14 17:48:22 localhost anacron[3709]: Anacron 2.3 started on 2014-08-14
Aug 14 17:48:22 localhost anacron[3709]: Normal exit (0 jobs run)
Aug 14 17:48:22 localhost kernel: [  628.991835] cfg80211: Calling CRDA to update world regulatory domain
Aug 14 17:48:22 localhost kernel: [  628.997378] cfg80211: World regulatory domain updated:
Aug 14 17:48:22 localhost kernel: [  628.997383] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Aug 14 17:48:22 localhost kernel: [  628.997385] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 14 17:48:22 localhost kernel: [  628.997387] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 14 17:48:22 localhost kernel: [  628.997389] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug 14 17:48:22 localhost kernel: [  628.997391] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 14 17:48:22 localhost kernel: [  628.997393] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 14 17:48:22 localhost kernel: [  629.011836] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
Aug 14 17:48:22 localhost kernel: [  629.011841] iwl3945: Copyright(c) 2003-2011 Intel Corporation
Aug 14 17:48:22 localhost kernel: [  629.011904] iwl3945 0000:04:00.0: can't disable ASPM; OS doesn't have ASPM control
Aug 14 17:48:22 localhost kernel: [  629.065626] iwl3945 0000:04:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
Aug 14 17:48:22 localhost kernel: [  629.065630] iwl3945 0000:04:00.0: Detected Intel Wireless WiFi Link 3945ABG
Aug 14 17:48:22 localhost kernel: [  629.065699] iwl3945 0000:04:00.0: irq 47 for MSI/MSI-X
Aug 14 17:48:22 localhost kernel: [  629.066104] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
Aug 14 17:48:22 localhost kernel: [  629.067312] iwl3945 0000:04:00.0: loaded firmware version 15.32.2.9
Aug 14 17:48:22 localhost wpa_supplicant[3746]: Successfully initialized wpa_supplicant
Aug 14 17:48:22 localhost kernel: [  629.137803] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 14 17:48:22 localhost wpa_supplicant[3746]: ctrl_iface exists and seems to be in use - cannot override it
Aug 14 17:48:22 localhost wpa_supplicant[3746]: Delete '/var/run/wpa_supplicant/wlan0' manually if it is not used anymore
Aug 14 17:48:22 localhost wpa_supplicant[3746]: Failed to initialize control interface '/var/run/wpa_supplicant'.#012You may have another wpa_supplicant process already running or the file was#012left by an unclean termination of wpa_supplicant in which case you will need#012to manually remove this file before starting wpa_supplicant again.
Aug 14 17:48:22 localhost wpa_supplicant[888]: wlan0: CTRL-EVENT-TERMINATING 
Aug 14 17:48:22 localhost dhclient: Internet Systems Consortium DHCP Client 4.2.4
Aug 14 17:48:22 localhost dhclient: Copyright 2004-2012 Internet Systems Consortium.
Aug 14 17:48:22 localhost dhclient: All rights reserved.
Aug 14 17:48:22 localhost dhclient: For info, please visit https://www.isc.org/software/dhcp/
Aug 14 17:48:22 localhost dhclient: 
Aug 14 17:48:22 localhost kernel: [  629.321190] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 14 17:48:22 localhost dhclient: Listening on LPF/wlan0/00:1b:77:a4:6f:74
Aug 14 17:48:22 localhost dhclient: Sending on   LPF/wlan0/00:1b:77:a4:6f:74
Aug 14 17:48:22 localhost dhclient: Sending on   Socket/fallback
Aug 14 17:48:22 localhost dhclient: DHCPREQUEST of 192.168.0.2 on wlan0 to 255.255.255.255 port 67 (xid=0x8a0e160)
Aug 14 17:48:22 localhost anacron[3873]: Anacron 2.3 started on 2014-08-14
Aug 14 17:48:22 localhost anacron[3873]: Normal exit (0 jobs run)
Aug 14 17:48:29 localhost dhclient: message repeated 2 times: [ DHCPREQUEST of 192.168.0.2 on wlan0 to 255.255.255.255 port 67 (xid=0x8a0e160)]
Aug 14 17:48:39 localhost dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 (xid=0x6bde6af2)
Aug 14 17:48:45 localhost dhclient: message repeated 2 times: [ DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 (xid=0x6bde6af2)]
Aug 14 17:48:48 localhost dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5 (xid=0x6bde6af2)
Aug 14 17:48:53 localhost dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11 (xid=0x6bde6af2)
Aug 14 17:49:04 localhost dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15 (xid=0x6bde6af2)
Aug 14 17:49: 
```
I've no /var/run/wpa_supplicant/wlan0 file nor directory, so I can't remove it !: 
```

root@biniou:/var/log# ll /var/run/wpa_supplicant/
ls: cannot access /var/run/wpa_supplicant/: No such file or directory
root@biniou:/var/log# ll /var/run
lrwxrwxrwx 1 root root 4 août  12 17:51 /var/run -> /run
root@biniou:/var/log# ll /run
total 76
-rw-r--r--  1 root       root          5 août  14 08:04 acpid.pid
srw-rw-rw-  1 root       root          0 août  14 08:04 acpid.socket
drwxr-xr-x  2 root       root         40 août  14 08:04 alsa
-rw-r--r--  1 root       root          5 août  14 08:04 atd.pid
prw-------  1 root       root          0 août  14 08:04 autofs.fifo-menfin
----------  1 root       root          5 août  14 08:04 autofs-running
drwxr-xr-x  2 avahi      avahi        80 août  14 08:04 avahi-daemon
drwxr-xr-x  2 clamav     root         60 août  14 08:04 clamav
drwxr-xr-x  2 root       root         60 août  14 17:49 console
drwxr-xr-x  2 root       root         60 août  14 17:49 ConsoleKit
-rw-r--r--  1 root       root          5 août  14 17:49 console-kit-daemon.pid
-rw-r--r--  1 root       root          5 août  14 08:04 crond.pid
----------  1 root       root          0 août  14 08:04 crond.reboot
drwxr-xr-x  3 root       lp          120 août  14 08:04 cups
drwxr-xr-x  2 messagebus messagebus   80 août  14 08:04 dbus
-rw-r--r--  1 root       root          5 août  14 08:04 dhclient.wlan0.pid
drwxr-xr-x  2 root       root         40 août  14 08:03 initramfs
-rw-r--r--  1 root       root          5 août  14 08:04 kerneloops.pid
drwx--x--x  3 root       root         60 août  14 08:04 lightdm
-rw-r--r--  1 root       root          5 août  14 08:04 lightdm.pid
drwxrwxrwt  2 root       root         40 août  14 08:04 lock
srwxr-xr-x  1 root       root          0 août  14 08:04 mcelog-client
-rw-r--r--  1 root       root          4 août  14 08:04 mcelog.pid
-rw-r--r--  1 root       root        113 août  14 08:04 motd.dynamic
drwxr-xr-x  2 root       root         60 août  14 08:04 mount
drwxr-xr-x  3 root       root        160 août  14 17:48 network
-rw-r--r--  1 root       root          0 août  14 08:04 network-interface-security
-rw-r--r--  1 root       root          5 août  14 08:04 osspd.pid
drwxr-xr-x  2 root       root         40 août  14 08:03 plymouth
drwxr-xr-x  5 root       root        100 août  14 08:14 pm-utils
drwxr-xr-x  2 root       root         40 août  14 08:04 pppconfig
drwxr-xr-x  3 root       root        100 août  14 08:04 resolvconf
drwxr-xr-x  2 root       root         40 août  14 08:04 rpcbind
-r--r--r--  1 root       root          0 août  14 08:04 rpcbind.lock
srw-rw-rw-  1 root       root          0 août  14 08:04 rpcbind.sock
dr-xr-xr-x 10 root       root          0 août  14 08:04 rpc_pipefs
-rw-r--r--  1 statd      nogroup       4 août  14 08:04 rpc.statd.pid
-rw-r--r--  1 root       root          4 août  14 08:04 rsyslogd.pid
srw-rw-rw-  1 root       root          0 août  14 08:04 sdp
drwxr-xr-x  2 root       root         40 août  14 17:48 sendsigs.omit.d
drwxrwxrwt  2 root       root        280 août  14 08:14 shm
-rw-------  1 root       root          4 août  14 08:04 sm-notify.pid
drwxr-xr-x  2 root       root         40 août  14 08:04 sshd
-rw-r--r--  1 root       root          5 août  14 08:04 sshd.pid
drwxr-xr-x  6 root       root        120 août  14 08:04 systemd
drwxr-xr-x  6 root       root        160 août  14 17:48 udev
drwx------  2 root       root         40 août  14 08:05 udisks2
-rw-r--r--  1 root       root          4 août  14 08:04 upstart-file-bridge.pid
-rw-r--r--  1 root       root          4 août  14 08:04 upstart-socket-bridge.pid
-rw-r--r--  1 root       root          4 août  14 08:04 upstart-udev-bridge.pid
drwxr-xr-x  3 root       root         60 août  14 08:05 user
-rw-rw-r--  1 root       utmp       3840 août  14 08:06 utmp

```
If I try to activate the interface, it fails because the kernel *knows* it is already on. So I've to shut it down then up :
```

root@biniou:/var/log# ifup wlan0
ifup: interface wlan0 already configured
root@biniou:/var/log# ifdown wlan0
RTNETLINK answers: No such process
Internet Systems Consortium DHCP Client 4.2.4
Copyright 2004-2012 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/00:1b:77:a4:6f:74
Sending on   LPF/wlan0/00:1b:77:a4:6f:74
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.0.254 port 67 (xid=0x566489b8)
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
dhclient.c:2365: Failed to send 300 byte long packet over fallback interface.
root@biniou:/var/log# ifup wlan0
Internet Systems Consortium DHCP Client 4.2.4
Copyright 2004-2012 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/00:1b:77:a4:6f:74
Sending on   LPF/wlan0/00:1b:77:a4:6f:74
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 (xid=0x12cd092c)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7 (xid=0x12cd092c)
DHCPREQUEST of 192.168.0.2 on wlan0 to 255.255.255.255 port 67 (xid=0x12cd092c)
DHCPOFFER of 192.168.0.2 from 192.168.0.254
DHCPACK of 192.168.0.2 from 192.168.0.254
bound to 192.168.0.2 -- renewal in 18284 seconds.
root@biniou:/var/log#

```
My /etc/network/interfaces file looks like this (edited for obvious reasons...) 
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp

#maison
auto wlan0
iface wlan0 inet dhcp
        wpa-ssid   FreeboxDeGeorges
	wpa-key-mgmt WPA-PSK
        wpa-psk "<my complicated key I've changed a month ago>"

#

```
So nothing fancy.
Questions :
1) what's wrong ? 
2) what should Ido to get the return from sleep running ? 
3) what should I check ? 
Many thanks in advance for your help solving this PITA !

---

### Post by varunendra on 2014-08-15
Does it work if you manually disable the interface (ifdown wlan0) before going to suspend, then manually bringing it up (if required) after resume?

I've absolutely no idea how wpa_supplicant works, but if the above works, you can add the ifdown/up commands to a script in /etc/pm/sleep.d directory to make it work automatically.

---

### Post by georgesgiralt on 2014-08-15
Varun, I'll try this and report back.
Stjohn-michael, "Use hidden network connection this ocks wifi on" I do not understand you. Fool spell checker ? or missing too much chars ? ;-)

---

### Post by varunendra on 2014-08-15
Amazing coincidence that I have to repeat this so many times today, but - 'please make sure to post the update in a new post, else the thread won't get highlighted in my search result and I won't know you have posted an update'. <phew!!>

PS:
Sometimes it makes sense to just ignore things that appear to be nonsense. :)

---

### Post by georgesgiralt on 2014-08-15
Hello !
Something curious : I did the **sudo ifdown wlan0** before going to sleep (well, the PC, not me...) And when I restored the normal state, I was very surprised to get the wifi interface going up instantly. 
So I'm puzzled. 
What do you think ?

---

### Post by varunendra on 2014-08-15
I think the network manager service is having some trouble with suspend/resume cycle in recent versions. It may be the driver that refuses to leave the connection easily while going to suspend mode, thus crashing network-manager service. When you manually force the interface down, the connection is dropped and nm service suspends properly.

But all of this is just a guess based on the behaviour/solution I have seen in some recent threads. So far I have no evidence to corroborate this, or suggest some other issue.

In any case, you may try to add the "ifdown wlan0" command to a script and see if it works normally.

Based on your observation above, let's try only disabling the interface when going to sleep (well, the PC, not you.. ;)) -
```
case "${1}" in
    hibernate|suspend)
        # disable wlan0
        ifdown wlan0
        ;;
esac
```
Copy paste the above code in a blank file, and save it as, say, **"wireless_updown"** on your desktop. Then move it to /etc/pm/sleep.d directory and make it executable -
```
sudo mv Desktop/wireless_updown /etc/pm/sleep.d
sudo chmod +x /etc/pm/sleep.d/wireless_updown
```
(of course you can choose any different name instead of "wireless_updown" if you wish, just make sure the name doesn't contain blank spaces or special characters)

If the interface doesn't come up by itself after resume, try adding the "ifup wlan0" as well to the above script -
```
case "${1}" in
    hibernate|suspend)
        # disable wlan0
        ifdown wlan0
        ;;
    resume|thaw)
        # enable wlan0
        ifup wlan0
        ;;
esac
```

Does it work?

---

### Post by georgesgiralt on 2014-08-15
Thank you for your help ! 
It seems to work. I'll put hte code in a script and see tomorrow if it works or not. Then I'll mark the whole thread as "solved". 
By the way, it has nothing to do with NetworkManager as the service is not running at all. I use the automounter to access my home directory. So the network has to be up *before* someone gets logged in ! So my interfaces are managed classically through /etc/network/interfaces file... 
Have a bright day !

---

### Post by varunendra on 2014-08-15
> **georgesgiralt said:**
> By the way, it has nothing to do with NetworkManager as the service is not running at all.
Ugh! Replace the term "network-manager" service with "networking" service then, and maybe the guess will get close :p

> **georgesgiralt said:**
> Have a bright day !
3:26 am here, and still posting. Which means I'll do everything possible to make sure the day remains 'Dark' in my room, so I can snore (do I?) peacefully all day long ;)

---

### Post by georgesgiralt on 2014-08-16
Ah, OK, sleep well, then ;-) 
I've done what you suggested but with a couple of tweaks. Maybe they'll work... 
The script is named as are the other one present and rights adjusted to match the other's scripts. 
```

root@biniou:/etc/pm/sleep.d# ll
total 16
-rwxr-xr-x 1 root root  210 mai   17  2012 10_grub-common
-rwxr-xr-x 1 root root  660 déc.   6  2013 10_unattended-upgrades-hibernate
-rwxr-xr-x 1 root root   99 août  16 09:56 15_wireless-updown
-rwxr-xr-x 1 root root 1260 déc.  25  2011 novatel_3g_suspend
root@biniou:/etc/pm/sleep.d# 

```

I'll tell you how it works. Sleep well and thank you !

---

### Post by georgesgiralt on 2014-08-16
Hello !
So it seems the problem is solved.
IMHO the problem was with wpa_supplicant not stopped before going to sleep and started again after resume (in order to negotiate the keys).
The ifdown before sleeping seems to solve the problem because it stops the wpa_supplicant. 
Thanks to all who responded.

---

