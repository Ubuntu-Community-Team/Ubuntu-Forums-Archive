---
title: "Netgear WNDA 3100 wireless adapter issues"
date: 2015-12-22
forum: Networking &amp; Wireless
---

### Post by Thetorq on 2015-12-22
Hey Everyone,

I have a WNDA 3100 Wireless adapter, and it isn't cooperating with my system. I followed this thread
[http://ubuntuforums.org/showthread.php?t=1964173](http://ubuntuforums.org/showthread.php?t=1964173)

And was able to make some progress, but to no avail.

When I put 
> ndiswrapper -l

into the terminal I get 
> 
bcmn43xx32 : driver installed
    device (0846:9011) present
bcmn43xx64 : driver installed

which implies that the software is installed and *should work* but when I type in 

> dmesg | grep ndis
I get 
> [   13.966466] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[   13.967316] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   14.836812] ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[   14.836816] ndiswrapper (load_sys_files:200): couldn't prepare driver 'bcmn43xx32'
[   14.837063] ndiswrapper (load_wrap_driver:103): couldn't load driver bcmn43xx32; check system log for messages from 'loadndisdriver'
[   14.837098] usbcore: registered new interface driver ndiswrapper
[  930.507208] rndis_host 2-1.3:1.0 usb0: register 'rndis_host' at usb-0000:00:1d.0-1.3, RNDIS device, 52:8a:d2:72:5d:eb
[  930.507256] usbcore: registered new interface driver rndis_host


I am 99% sure I installed the 64 bit version, but this is telling me I installed the 32 bit.

I'm on Ubuntu 14.xx and my Windows partition died last night, so I need to get this working.

Thanks.

---

### Post by chili555 on 2015-12-22
It appears that you installed both. Please remove the incorrect version:```
sudo ndiswrapper -e bcmn43xx32
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
```Any improvement? It may take a reboot.

---

### Post by Thetorq on 2015-12-22
Hey, thanks for the fast reply!

I retyped in 

> dmesg | grep ndis

and got

> [   13.390348] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[   13.391177] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   13.461960] usbcore: registered new interface driver ndiswrapper
[   14.857862] rndis_host 2-1.3:1.0 usb0: register 'rndis_host' at usb-0000:00:1d.0-1.3, RNDIS device, 52:8a:d2:72:5d:eb
[   14.857885] usbcore: registered new interface driver rndis_host
[   32.570545] rndis_host 2-1.3:1.0 usb0: unregister 'rndis_host' usb-0000:00:1d.0-1.3, RNDIS device
[   65.626232] rndis_host 2-1.3:1.0 usb0: register 'rndis_host' at usb-0000:00:1d.0-1.3, RNDIS device, 52:8a:d2:72:5d:eb


** Quick Edit**

> ndiswrapper -l

Says that the driver is not connected
All I get is
> ben@Fenrir:~$ ndiswrapper -l 
bcmn43xx64 : driver installed


---

### Post by chili555 on 2015-12-22
That suggests that you have the incorrect bcmn43xx64.inf for your:> device (0846:9011) presentWhere did you get the files? 

There are at least three versions of the WDNA3100 series; not all drivers are correct for all versions.

---

### Post by Thetorq on 2015-12-22
I got these files from this thread
[http://ubuntuforums.org/showthread.php?t=1964173](http://ubuntuforums.org/showthread.php?t=1964173)
Reply #6.


I ran lsusb to try to figure out what my exact device was and it said
> Bus 002 Device 005: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]

So I googled the broadcom device and couldn't find any driver that wasn't an .exe file.

---

### Post by chili555 on 2015-12-22
> So I googled the broadcom device and couldn't find any driver that wasn't an .exe file.Because there aren't any. The clunky and twitchy ndiswrapper is the only choice.

That is, theoretically, correct for your device:> ; inf-File for Broadcom bcm43xx based WLAN Devices
; 64bit

[version]
        Signature       = "$CHICAGO$"
        Class           = Net
        ClassGUID       = {4d36e972-e325-11ce-bfc1-08002be10318}
        Provider        = %Broadcom%
        Compatible      = 1
        DriverVer=08/26/2009, 5.10.79.30

[Manufacturer]
%Broadcom% = Broadcom

[Broadcom]
%BCM4xx01_DeviceDesc% = BCM43XXN64, USB\VID_050D&PID_825C
%BCM4xx02_DeviceDesc% = BCM43XXN64, USB\VID_050D&PID_6050
%BCM4xx04_DeviceDesc% = BCM43XXN64, USB\VID_050D&PID_615A
%BCM4xx03_DeviceDesc% = BCM43XXN64, USB\VID_[COLOR="#FF0000"]0846[/COLOR]&PID_[COLOR="#FF0000"]9011[/COLOR]
%BCM4xx03_DeviceDesc% = BCM43XXN64, USB\VID_0846&PID_9020

<snip>Please reboot with the USB wireless (tethered??) detached and the Netgear inserted. Is there any change in:```
ndiswrapper -l
dmesg | grep ndis
```

---

### Post by Thetorq on 2015-12-22
okay, before restarting I get

> ben@Fenrir:~$ ndiswrapper -l
bcmn43xx64 : driver installed
ben@Fenrir:~$ dmesg | grep ndis
[   13.338548] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[   13.339199] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   13.419671] usbcore: registered new interface driver ndiswrapper
[   68.949843] rndis_host 2-1.5.1:1.0 usb0: register 'rndis_host' at usb-0000:00:1d.0-1.5.1, RNDIS device, 52:8a:d2:72:5d:eb
[   68.949868] usbcore: registered new interface driver rndis_host
[  528.071542] rndis_host 2-1.5.1:1.0 usb0: unregister 'rndis_host' usb-0000:00:1d.0-1.5.1, RNDIS device
[ 3676.705336] rndis_host 2-1.5.1:1.0 usb0: register 'rndis_host' at usb-0000:00:1d.0-1.5.1, RNDIS device, 52:8a:d2:72:5d:eb
[ 3677.179919] rndis_host 2-1.5.1:1.0 usb0: unregister 'rndis_host' usb-0000:00:1d.0-1.5.1, RNDIS device
[ 3683.871993] rndis_host 2-1.5.1:1.0 usb0: register 'rndis_host' at usb-0000:00:1d.0-1.5.1, RNDIS device, 52:8a:d2:72:5d:eb
[ 3783.651807] rndis_host 2-1.5.1:1.0 usb0: unregister 'rndis_host' usb-0000:00:1d.0-1.5.1, RNDIS device
[ 9046.846764] rndis_host 2-1.5.1:1.0 usb0: register 'rndis_host' at usb-0000:00:1d.0-1.5.1, RNDIS device, 52:8a:d2:72:5d:eb
[ 9612.982229] rndis_host 2-1.5.1:1.0 usb0: unregister 'rndis_host' usb-0000:00:1d.0-1.5.1, RNDIS device
[ 9651.900618] rndis_host 2-1.5.1:1.0 usb0: register 'rndis_host' at usb-0000:00:1d.0-1.5.1, RNDIS device, 52:8a:d2:72:5d:eb
[ 9664.426572] rndis_host 2-1.5.1:1.0 usb0: unregister 'rndis_host' usb-0000:00:1d.0-1.5.1, RNDIS device
[10054.777751] rndis_host 2-1.5.1:1.0 usb0: register 'rndis_host' at usb-0000:00:1d.0-1.5.1, RNDIS device, 52:8a:d2:72:5d:eb
[10055.249659] rndis_host 2-1.5.1:1.0 usb0: unregister 'rndis_host' usb-0000:00:1d.0-1.5.1, RNDIS device
[10061.943580] rndis_host 2-1.5.1:1.0 usb0: register 'rndis_host' at usb-0000:00:1d.0-1.5.1, RNDIS device, 52:8a:d2:72:5d:eb


Will restart and reply any changes

**After restarting**

> ben@Fenrir:~$ ndiswrapper -l
bcmn43xx64 : driver installed
ben@Fenrir:~$ dmesg | grep ndis
[   13.398596] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[   13.399265] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   13.499232] usbcore: registered new interface driver ndiswrapper
[   14.728869] rndis_host 2-1.5.1:1.0 usb0: register 'rndis_host' at usb-0000:00:1d.0-1.5.1, RNDIS device, 52:8a:d2:72:5d:eb
[   14.728886] usbcore: registered new interface driver rndis_host
[  100.393039] rndis_host 2-1.5.1:1.0 usb0: unregister 'rndis_host' usb-0000:00:1d.0-1.5.1, RNDIS device


Once I plug my phone back in (Which is giving me temporary Internet access) I get the same return from dmesg |grep ndis

**Second Edit**

I opened the .inf with gedit and it has the same numbers yours does in red.

---

### Post by chili555 on 2015-12-22
And how about:```
ndiswrapper -l
```May I also see:```
cat /etc/modprobe.d/ndiswrapper.conf
```

---

### Post by Thetorq on 2015-12-22
> 
ben@Fenrir:~$ ndiswrapper -l
bcmn43xx64 : driver installed


ben@Fenrir:~$ cat /etc/modprobe.d/ndiswrapper.conf
alias usb:v050Dp6050d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp6050d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp615Ad*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp615Ad*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp825Cd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp825Cd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0846p9011d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0846p9020d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0846p9020d*dc*dsc*dp*ic*isc*ip* ndiswrapper


Not sure what to make of this?

---

### Post by chili555 on 2015-12-22
Looks entirely normal:> alias usb:v[COLOR="#FF0000"]0846[/COLOR]p[COLOR="#FF0000"]9011[/COLOR]d*dc*dsc*dp*ic*isc*ip* ndiswrapperI'm starting to be a bit mystified. Your device should take off like a rocket or, in the alternative, spin off some warnings or error messages. This is my favorite kind of problem. Everything looks perfect except it doesn't work.

Let's see if there are any clues in syslog. Unplug the device, open a terminal and run:```
tail -f /var/log/syslog
```Plug in the device and note all the new activity in the terminal. Post it here.

Get out of 'tail' with Ctrl+c.

---

### Post by Thetorq on 2015-12-22
With the device unplugged:

> ben@Fenrir:~$ tail -f /var/log/syslog
Dec 22 17:51:06 Fenrir avahi-daemon[856]: Registering new address record for 2600:1001:b000:9b04:383b:c887:784d:ba13 on usb0.*.
Dec 22 17:51:07 Fenrir NetworkManager[1044]: <info> Policy set 'Wired connection 1' (usb0) as default for IPv6 routing and DNS.
Dec 22 17:51:07 Fenrir NetworkManager[1044]: <info> Writing DNS information to /sbin/resolvconf
Dec 22 17:51:07 Fenrir dnsmasq[1122]: setting upstream servers from DBus
Dec 22 17:51:07 Fenrir dnsmasq[1122]: using nameserver 192.168.42.129#53
Dec 22 17:51:07 Fenrir dnsmasq[1122]: using nameserver fe80::9442:95ff:fecc:9d9a#53
Dec 22 17:51:07 Fenrir NetworkManager[1044]: <info> Activation (usb0) Stage 5 of 5 (IPv6 Commit) complete.
Dec 22 17:51:10 Fenrir ntpdate[4501]: adjust time server 91.189.94.4 offset 0.015253 sec
Dec 22 17:51:20 Fenrir ntpdate[4527]: adjust time server 91.189.94.4 offset -0.005067 sec
Dec 22 17:52:56 Fenrir kernel: [ 6631.769532] usb 2-1.4: USB disconnect, device number 5
^C


With the device plugged in:
> 
ben@Fenrir:~$ tail -f /var/log/syslog
Dec 22 17:51:20 Fenrir ntpdate[4527]: adjust time server 91.189.94.4 offset -0.005067 sec
Dec 22 17:52:56 Fenrir kernel: [ 6631.769532] usb 2-1.4: USB disconnect, device number 5
Dec 22 17:54:27 Fenrir kernel: [ 6722.315499] usb 2-1.4: new high-speed USB device number 97 using ehci-pci
Dec 22 17:54:27 Fenrir kernel: [ 6722.410963] usb 2-1.4: New USB device found, idVendor=0846, idProduct=9011
Dec 22 17:54:27 Fenrir kernel: [ 6722.410969] usb 2-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Dec 22 17:54:27 Fenrir kernel: [ 6722.410971] usb 2-1.4: Product: Remote Download Wireless Adapter
Dec 22 17:54:27 Fenrir kernel: [ 6722.410974] usb 2-1.4: Manufacturer: Broadcom
Dec 22 17:54:27 Fenrir kernel: [ 6722.410976] usb 2-1.4: SerialNumber: 0
Dec 22 17:54:27 Fenrir mtp-probe: checking bus 2, device 97: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4"
Dec 22 17:54:27 Fenrir mtp-probe: bus: 2, device: 97 was not an MTP device


With the device plugged in, but without my phone providing Tethering wifi:

> 
ben@Fenrir:~$ tail -f /var/log/syslog
Dec 22 17:56:11 Fenrir NetworkManager[1044]: <info> Removing DNS information from /sbin/resolvconf
Dec 22 17:56:11 Fenrir dnsmasq[1122]: setting upstream servers from DBus
Dec 22 17:56:11 Fenrir NetworkManager[1044]: <info> (usb0): cleaning up...
Dec 22 17:56:11 Fenrir NetworkManager[1044]: <warn> (13) failed to find interface name for index
Dec 22 17:56:11 Fenrir NetworkManager[1044]: (nm-system.c:766):nm_system_iface_get_flags: runtime check failed: (iface != NULL)
Dec 22 17:56:11 Fenrir NetworkManager[1044]: <error> [1450824971.803997] [nm-system.c:768] nm_system_iface_get_flags(): (unknown): failed to get interface link object
Dec 22 17:56:11 Fenrir NetworkManager[1044]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Dec 22 17:56:11 Fenrir NetworkManager[1044]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Dec 22 17:56:11 Fenrir NetworkManager[1044]: <info> NetworkManager state is now CONNECTED_GLOBAL
Dec 22 17:56:11 Fenrir NetworkManager[1044]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
^C
ben@Fenrir:~$ 


---

### Post by chili555 on 2015-12-23
> <info> Unmanaged Device found; state CONNECTED forced. This suggests that the device is managed elsewhere. Do you have Wicd installed? Is there an entry aside from the loopback stanza in /etc/network/interfaces?```
cat  /etc/network/interfaces
```Does the interface scan?```
sudo iwlist scan
```Please run this with the tether detached.

---

### Post by Thetorq on 2015-12-24
Last night I tried to reinstall Windows (Since I use it primarily) and ended up deleting my unix partition since the Windows hard drive is shot. I reinstalled everything though.

With the tether detached I get the following responses:

> 
ndiswrapper -l
bcmn43xx64 : driver installed
    device (0846:9011) present


> 
dmesg | grep ndis

[   11.896881] rndis_host 2-1.6:1.0 usb0: register 'rndis_host' at usb-0000:00:1d.0-1.6, RNDIS device, 52:8a:d2:72:5d:eb
[   11.896900] usbcore: registered new interface driver rndis_host
[  393.223106] rndis_host 2-1.6:1.0 usb0: unregister 'rndis_host' usb-0000:00:1d.0-1.6, RNDIS device


> cat  /etc/network/interfaces

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


> 
sudo iwlist scan

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Wicd is not installed.

** Edit**

Installed WICD, and it says no wireless networks found

*Second Edit**

Running
> 
tail -f /var/log/syslog


while untethered gives

> 
Dec 24 16:36:06 Fenrir AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/daa5bb4fe62f43778f63cb294c425344
Dec 24 16:36:11 Fenrir AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/daa5bb4fe62f43778f63cb294c425344
Dec 24 16:36:39 Fenrir AptDaemon: INFO: RemovePackages() was called: 'dbus.Array([dbus.String('unity-webapps-common')], signature=dbus.Signature('s'))'
Dec 24 16:36:39 Fenrir AptDaemon.Trans: INFO: Queuing transaction /org/debian/apt/transaction/0e58739f2fa74c8c8b5e1863675ee262
Dec 24 16:36:39 Fenrir AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/0e58739f2fa74c8c8b5e1863675ee262
Dec 24 16:36:40 Fenrir AptDaemon.Worker: INFO: Committing packages: dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([dbus.String('unity-webapps-common')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
Dec 24 16:36:41 Fenrir AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/0e58739f2fa74c8c8b5e1863675ee262
Dec 24 16:36:43 Fenrir AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/0e58739f2fa74c8c8b5e1863675ee262
Dec 24 16:46:46 Fenrir AptDaemon: INFO: Quitting due to inactivity
Dec 24 16:46:46 Fenrir AptDaemon: INFO: Quitting was requested


**Edit #3**

sudo modprobe ndiswrapper 

yields the error message

modprobe: FATAL: Module ndiswrapper not found.

But doing ndiswrapper -l  works. 

I installed "Windows Wireless Drivers" from the software center, but no luck.

---

