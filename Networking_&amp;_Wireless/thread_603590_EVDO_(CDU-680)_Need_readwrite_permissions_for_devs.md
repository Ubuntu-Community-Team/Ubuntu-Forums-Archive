---
title: "EVDO (CDU-680) Need read/write permissions for /dev/sd"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by Joaquin Negrete on 2007-11-05
I installed the Franklin EVDO card CDU-680 at my desktop. Using the Linux driver says:


sudo ./connect
680d interface changer-1.0.1
Find CMOTECH CDM680 at scsi 4
Command:: ./itfchg /dev/sdd
Need read/write permissions for /dev/sdd .
Command:: ./itfchg /dev/sde
Need read/write permissions for /dev/sde .

When I use it in my laptop it recognizes it immediately without any read/write permissions. Both computers have the same installation.

I have already modified the mountdevsubfs.sh and blacklist files in order to re enable the /proc/bus/usb/devices.

Please help me with this technical issue.

Thanks!

---

### Post by yellowbread on 2007-11-27
I got the same thing. If I get if figured out, I'll post here.

---

### Post by yellowbread on 2007-11-27
Well, I never did get the connect script that came with the modem to work, but I do have the modem working very nicely. Here's how:

1. I ran wvdialconf with these results:

```

filbert@filbert-desktop:~$ wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- OK
ttyS0<*1>: ATQ0 V1 E1 Z -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyS0<*1>: Modem Identifier: ATI -- 5601
ttyS0<*1>: Speed 4800: AT -- OK
ttyS0<*1>: Speed 9600: AT -- OK
ttyS0<*1>: Speed 19200: AT -- OK
ttyS0<*1>: Speed 38400: AT -- OK
ttyS0<*1>: Speed 57600: AT -- OK
ttyS0<*1>: Speed 115200: AT -- OK
ttyS0<*1>: Max speed is 115200; that should be safe.
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
Modem Port Scan<*1>: S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyACM0<*1>: ATQ0 V1 E1 -- OK
ttyACM0<*1>: ATQ0 V1 E1 Z -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyACM0<*1>: Modem Identifier: ATI -- MANUFACTURER: C-MOTECH Co., Ltd.
ttyACM0<*1>: Speed 4800: AT -- OK
ttyACM0<*1>: Speed 9600: AT -- OK
ttyACM0<*1>: Speed 19200: AT -- OK
ttyACM0<*1>: Speed 38400: AT -- OK
ttyACM0<*1>: Speed 57600: AT -- OK
ttyACM0<*1>: Speed 115200: AT -- OK
ttyACM0<*1>: Speed 230400: AT -- OK
ttyACM0<*1>: Speed 460800: AT -- OK
ttyACM0<*1>: Max speed is 460800; that should be safe.
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found a modem on /dev/ttyS0.
Modem configuration written to /etc/wvdial.conf.
/etc/wvdial.conf<Warn>: Can't write '/etc/wvdial.conf.tmp7182': Permission denied
/etc/wvdial.conf<Warn>: Can't write '/etc/wvdial.conf' ('/etc/wvdial.conf'): Bad file descriptor
ttyS0<Info>: Speed 115200; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
ttyACM0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
```

2. Configured gnome-ppp as follows:

Username: sprintpcs.com
Password: ******* (not needed to connect, but gnome-ppp hangs when I leave this empty)
Phone number: #777

In the setup modem tab:

Device: /dev/ttyACM0
Type: USB Modem
Speed: 921600
Phone Line: Tone

In the setup Networking tab:

IP: Dynamic IP Address
DNS: Automatic DNS

In the options tab:

Only Auto reconnect, Abort connecting if line is busy, and Send custom reply are unchecked.

That's it. It connects very quickly and gives good speeds.

---

### Post by oakie on 2007-12-18
See PS below for a workaround

Has anyone any new thoughts or findings on the program ITFCHG and the CDU 680 in 7.10?

I cannot get ttyACM0 to work since going to 7.10. The suplied  connect program gives a segmentation fault, so I tried to do it all manually similar to yellowbread, but ttyACM0 does not work and does not show up in DMESG when I do everything manually.  

It sems that the functions in ITFCHG are required to make ttyACM0 work on my older machine.  ttyACM0 only shows up the line after ITFCHG diisonnects the device and reconnects it,  doing everything using the supplied programs in DMESG.

I think I can do everything except what is in ITFCHG manually, no problem, but with ITFCHG I get the permission problem - If I could solve that and use ITFCHG or do what it does manually I would be fine.

I tried blacklisting  modules and adding them back in manually too.

Yelowbread, did you have to do anything to make ttyACM0 work?  I have made the node and loaded usbserial and cdc-acm manually, but still no working ttyACM0 per wvdial etc  Joaquin, any luck?

Thanks
Phil/Oakie

PS as a work-around you can boot in an OS that supports the program, EG  run it from connect in 6.1 and then do a  warm reboot with the modem attached.  ITFCHG seems to change the mode of the modem from usb storage only to storage plus modem and changes the ID from 6803 to 6843, hence this trick removes the need to run it in the final OS. A powered hub might help

---

### Post by yellowbread on 2008-01-09
Sorry it took so long to respond. To answer your question, short answer is yes I did. I did not know this at the time though. I must have gotten the connect program to run far enough to switch the mode just before I got it set up the first time. Like you pointed out, a warm reboot preserves the mode, so I did not notice for a while that I needed to set the mode before connecting. 

The itfchg program runs fine on my Gutsy installation, so whenever necessary, I just set the mode there with sudo ./itfchg /dev/sdh (or whatever the device mounts as, sometimes /dev/sdg.)

 I have tried to figure out what itfchg does, without much luck so far. All the loading of drivers and node creation doesn't seem necessary--get the mode changed and everything else is automatic, well, except for configuring a dialer as mentioned above.

---

### Post by yellowbread on 2008-01-17
In case anyone is still interested, I figured out how the itfchg program goes about changing the mode of the cdu680. It opens the device /dev/sd? where the modem is sitting, then changes the mode with a FIBMAP ioctl call with the argument being the address of an structure type variable having 5 integer fields with values

0x00000009
0x00000000
0x454452ff
0x47484356
0x00000031

From the ff down in characters this reads "RDEVCHG1".

I've written a short c program that does this and have successfully changed the mode to "modem mode" using the program.

---

