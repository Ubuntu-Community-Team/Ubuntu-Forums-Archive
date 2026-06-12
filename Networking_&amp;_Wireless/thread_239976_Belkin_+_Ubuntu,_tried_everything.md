---
title: "Belkin + Ubuntu, tried everything"
date: 2006-08-20
forum: Networking &amp; Wireless
---

### Post by excite on 2006-08-20
Hi there,

I already know it has been posted a lot, but I still cannot find answer. I am completly n00b in linux yet ;) 

So,I am using Ubuntu 6.06 LTS 64-bit and I have Belkin F5D7001uk (catalog.belkin.com/IWCatProductPage.process?Product_Id=18432) i found that it works with ndiswrapper, so I installed it, no problems at all. But when i want to configure it.. i just can't! heeh.. i tried everything what i thought of. Here are LOGs from terminal:

```
My Comp:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present, hardware present
My Comp:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:95 errors:0 dropped:0 overruns:0 frame:0
          TX packets:95 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6444 (6.2 KiB)  TX bytes:6444 (6.2 KiB)

My Comp:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

eth2      IEEE 802.11b/g  ESSID:"linksys"  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```


In **Networking** I can configure my static IP, and all that stuff, but i cannot activate my wireless card :/
And my question is.. how to make it working?! :P I used Win XP before and i was using static ip, not DHCP in my network.

//   EDIT:

the LED's on WiFi card does not shine (light) as they did on windows.

---

### Post by spd106 on 2006-08-20
Try changing the name of the wifi interface in /etc/iftab and /etc/network/interfaces to wlan0 instead of eth2.
```
gksudo gedit /etc/iftab
gksudo gedit /etc/network/interfaces
```
Then restart networking
```
sudo /etc/init.d/networking restart
```

What does this show ```
sudo ifup wlan0
```
You may also need to blacklist bcm43xx, if you haven't already. Back on Ubuntu 5.04 it was sometimes necessary to change the radiostate value to 0 in the driver configuration file. Somewhere like /etc/ndiswrapper/<driver name>/1440:1234:5678.conf or similar.

---

### Post by excite on 2006-08-20
Ok, I did what you said, and here is the log:

```

My Comp:~$ gksudo gedit /etc/network/interfaces
(gedit:5769): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
excite@dawid:~$ gksudo gedit /etc/iftab

(gedit:5795): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
My Comp:~$ sudo /etc/init.d/
sudo: /etc/init.d/: command not found
My Comp:~$ /etc/init.d/networking restart
 * Reconfiguring network interfaces... ifdown: failed to open statefile /var/run/network/ifstate: Permission denied
ifup: failed to open statefile /var/run/network/ifstate: Permission denied
                                                                         [fail]
My Comp:~$ sudo ifup wlan0
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
wlan0: ERROR while getting interface flags: No such device
Failed to bring up wlan0.
My Comp:~$ /etc/ndiswrapper/bcmwl5a/14E4:4320.5.conf
bash: /etc/ndiswrapper/bcmwl5a/14E4:4320.5.conf: Permission denied
My Comp:~$

```

I'm a n00b :/

---

### Post by spd106 on 2006-08-21
Sorry, I forgot that you also needed to change the interface name in the /etc/modprobe.d/ndiswrapper file.
```
gksudo gedit /etc/modprobe.d/ndiswrapper
```
Check out this thread [http://www.ubuntuforums.org/showthread.php?t=201902](http://www.ubuntuforums.org/showthread.php?t=201902) 

I also gave you the wrong command. You needed to restart the interface rather than just the network protocol stack. Instead of /etc/init.d/networking restart. Do ```
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
```This will unload the ndiswrapper kernel module then reload it, causeing the interface to be reset. Alternativly restarting the machine will achieve the same effect.

The config file needs to be opened in a text editor. I should have been a bit more discriptive. ```
gksudo gedit /etc/ndiswrapper/<the rest...>
``` Open the file then look down the list for the radiostate. This needs to be changed to a 0. Then save and close the file and try ```
sudo ifup wlan0
```

You may find that this won't work anyway since you need a 64 bit driver. Have a look at this thread here [http://www.ubuntuforums.org/showthread.php?t=228092](http://www.ubuntuforums.org/showthread.php?t=228092).

For future reference "permission denied" occurs when you try to run a command that needs root privileges. That's why we use sudo for the terminal and gksudo for gui apps.

---

