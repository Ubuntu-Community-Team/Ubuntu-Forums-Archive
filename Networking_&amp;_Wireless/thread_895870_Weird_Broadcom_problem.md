---
title: "Weird Broadcom problem"
date: 2008-08-20
forum: Networking &amp; Wireless
---

### Post by jhoe on 2008-08-20
Hey...

I just got finished reinstalling Hardy (hard drive was dying).
Wireless on this machine worked with no problems before, but after the re-installation, I find that the 'Broadcom B43 wireless driver' is green and in use, but I cannot enable it (this is under System>Admin>Hardware Drivers).  I reboot but the driver is still not 'enabled' (no check mark).

I have tried countless forums but haven't found my solution yet.  What should I try?  I am not very good with the linux hardware side yet and have been running around copying and pasting into the terminal hoping something works.

I used Wicd before and I am trying to use it again, but it see no wireless connections.

So far I know:
```

jhoe@jhoe-hp:~$ lspci | grep Broadcom
01:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

```

```

jhoe@jhoe-hp:~$ sudo iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```

jhoe@jhoe-hp:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

```

Would it be easier to somehow just reinstall all associated network items (aka start from scratch)?

---

### Post by Ayuthia on 2008-08-20
> **jhoe said:**
> Hey...

I just got finished reinstalling Hardy (hard drive was dying).
Wireless on this machine worked with no problems before, but after the re-installation, I find that the 'Broadcom B43 wireless driver' is green and in use, but I cannot enable it (this is under System>Admin>Hardware Drivers).  I reboot but the driver is still not 'enabled' (no check mark).

I have tried countless forums but haven't found my solution yet.  What should I try?  I am not very good with the linux hardware side yet and have been running around copying and pasting into the terminal hoping something works.

I used Wicd before and I am trying to use it again, but it see no wireless connections.

So far I know:
```

jhoe@jhoe-hp:~$ lspci | grep Broadcom
01:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

```

```

jhoe@jhoe-hp:~$ sudo iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```

jhoe@jhoe-hp:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

```

Would it be easier to somehow just reinstall all associated network items (aka start from scratch)?

If you have an internet connection, you can try the following:
```
sudo apt-get install b43-fwcutter
```
It should ask you if you want it to find the firmware for you so say yes.  Then you can either reboot or do the following:
```
sudo modprobe -r b43 ssb
sudo modprobe b43
sudo ifconfig wlan0 up
```
This set of commands just removes the wireless module and reloads it then tries to bring it up.

Hope that works.

---

### Post by jhoe on 2008-08-20
> **Ayuthia said:**
> If you have an internet connection, you can try the following:
```
sudo apt-get install b43-fwcutter
```
It should ask you if you want it to find the firmware for you so say yes.  Then you can either reboot or do the following:
```
sudo modprobe -r b43 ssb
sudo modprobe b43
sudo ifconfig wlan0 up
```
This set of commands just removes the wireless module and reloads it then tries to bring it up.

Hope that works.

Thanks for the help.  I already had b43-fwcutter installed so...
```

jhoe@jhoe-hp:~$ sudo apt-get install b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

The rest got me:
```

jhoe@jhoe-hp:~$ sudo modprobe -r b43 ssb
FATAL: Module ssb is in use.
jhoe@jhoe-hp:~$ sudo modprobe b43
jhoe@jhoe-hp:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: No such file or directory

```

---

### Post by J$oney on 2008-08-20
This is a known bug, the support team has many posts about this with no known fix as of yet. You can manually change the SSID in the manager to what you know is the SSID, and it should work. I also have a broadcom iwl3495 module, I boot into a different kernel 22.14 to find them if I don't know what they are. Hope this helps. I know it sucks. SORRY.

---

### Post by jhoe on 2008-08-20
Strange, as I had no problems before.  I guess I will just reinstall Ubuntu as the only hardware that changed was the HDD.  Thanks for the info. on the bug.

---

### Post by jhoe on 2008-08-20
Well it seems "SIOCSIFFLAGS: No such file or directory" means there is no firmware installed.

So I had two options:
1.) Reinstall Ubuntu and click yes when it asked to 'Fetch and install firmware'

or

2.) Install the firmware by clicking 'Fetch and install firmware'

Of course, I didn't find out option two until I had already gone through with option 1 ](*,) but hey there is always next time.

---

### Post by cdtech on 2008-08-20
> I just got finished reinstalling Hardy (hard drive was dying).
Wireless on this machine worked with no problems before, but after the re-installation, I find that the 'Broadcom B43 wireless driver' is green and in use, but I cannot enable it (this is under System>Admin>Hardware Drivers). I reboot but the driver is still not 'enabled' (no check mark).

Be sure the module is not blacklisted in the /etc/modprobe.d/blacklist file.
ie: blacklist b43

---

### Post by Ayuthia on 2008-08-20
> **J$oney said:**
> This is a known bug, the support team has many posts about this with no known fix as of yet. You can manually change the SSID in the manager to what you know is the SSID, and it should work. I also have a broadcom iwl3495 module, I boot into a different kernel 22.14 to find them if I don't know what they are. Hope this helps. I know it sucks. SORRY.

Actually, the iwl3495 module is for the Intel cards and not the Broadcom.  So your solution is a little different.

As for the 4311 rev 01 card, it usually is one of the few that seems to work with most of the drivers.  However, there are now four different driver options available (ndiswrapper, b43, bcm43xx, and wl).  Because of this, it becomes more difficult to configure.

Your scenario appears that either the firmware did not get installed or else there was a conflicting wireless module that was causing it to not start up.

---

