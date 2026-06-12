---
title: "VNC, almost got it!"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by WarholsGhost on 2008-11-04
hey,

so i'v been working on getting VNC working all morning and i finally got to the point where i could log in, but the screen that pops up is just a bash screen. 

How do i make it so i can control the desktop on my server?

---

### Post by nixscripter on 2008-11-04
For reasons I can't explain without more information, you probably have a virtual console.

Just try Try starting an X windows session from it with: ```
startx
``` If it does run but doesn't do anything useful, you can get out of it with Cntl-Alt-Backspace

---

### Post by WarholsGhost on 2008-11-04
i did startx and i wasn't authorized

i did sudo start x and it gave me:
```
Fatal server Error:
Server is already active for display 0
if this server is no longer running, remove /tmp/.X0-lock
and start again
```

---

### Post by nixscripter on 2008-11-04
Okay, so much for the obvious.

Which VNC server are you using, and how is it configured?

---

### Post by WarholsGhost on 2008-11-04
i'm using vnc4server for the server and xvnc4viewer for the viewer. 

i just installed the programs, i didn't do much set up, i couldn't find good documentation..

---

### Post by nixscripter on 2008-11-05
How did you set it up? Did you do something like this?

[http://ubuntuforums.org/showthread.php?t=197964](http://ubuntuforums.org/showthread.php?t=197964)

---

### Post by WarholsGhost on 2008-11-05
i set it up using that tutorial and now i get an error of

read:connection reset by peer (104)

---

### Post by nixscripter on 2008-11-06
If you got the error remotely, what happens when you try to check locally as in step 7? ```
vncviewer localhost:1
``` If it doesn't work either, it might be a problem with xinetd.

---

### Post by WarholsGhost on 2008-11-07
yea i get the same error when connected locally too

---

### Post by nixscripter on 2008-11-07
Make sure you re-initialized the connection after you changed the xinetd conf file:

```

sudo /etc/init.d/xinetd stop
sudo killall Xvnc
sudo /etc/init.d/xinetd start

```

Also, try telling it to connect on port 5901 (the default is 5900):

```

vncviewer ip.address.of.server:5901

```

---

### Post by WarholsGhost on 2008-11-08
tried both still getting the same error

rest by peer error (104)

---

### Post by nixscripter on 2008-11-09
Please post your xinetd.conf file, just to make sure you did it right. I'm still convinced that's where the problem is.

---

### Post by WarholsGhost on 2008-11-09
where is the .conf file?

---

### Post by nixscripter on 2008-11-10
It's **/etc/xinetd.conf**.

Also, please post **/etc/xinetd.d/Xvnc**, which is the file you just created.

---

### Post by WarholsGhost on 2008-11-10
/etc/xinetd.conf

```

# Simple configuration file for xinetd
#
# Some defaults, and include /etc/xinetd.d/

defaults
{

# Please note that you need a log_type line to be able to use log_on_success
# and log_on_failure. The default is the following :
# log_type = SYSLOG daemon info

}

includedir /etc/xinetd.d

```

/etc/xinetd.d/Xvnc

```

service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd
        port = 5901
}

```

---

### Post by nixscripter on 2008-11-11
Try changing the Xvnc file under service from

```

server = /usr/bin/Xvnc
server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd

```

to

```

server = /usr/sbin/tcpd
server_args = /usr/bin/Xvnc -inetd -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd :1

```

Then we can look at syslog to get a better idea of what's going on, i.e. who is doing the dropping.

---

### Post by WarholsGhost on 2008-11-12
ok, now it says it's connected but nothing pops up and no screen is there.

---

### Post by nixscripter on 2008-11-14
That's what I expected.

Now check the file **/var/log/daemon.log** and see if there are any errors in it.

---

### Post by WarholsGhost on 2008-11-14
```

Nov 13 08:18:25 endgame NetworkManager: <debug> [1226593105.023631] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E'). 
Nov 13 08:18:25 endgame NetworkManager: <debug> [1226593105.208468] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E_if0'). 
Nov 13 08:18:30 endgame NetworkManager: <debug> [1226593110.140826] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E_if0_scsi_host'). 
Nov 13 08:18:30 endgame NetworkManager: <debug> [1226593110.151993] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E_if0_scsi_host_scsi_device_lun0'). 
Nov 13 08:18:30 endgame NetworkManager: <debug> [1226593110.748656] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov 13 08:18:31 endgame NetworkManager: <debug> [1226593111.443187] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial__USB_DISK_2_0_07000774113B016E_0_0'). 
Nov 13 08:18:31 endgame NetworkManager: <debug> [1226593111.718563] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48B4_6306'). 
Nov 13 08:18:32 endgame hald: mounted /dev/sdf1 on behalf of uid 1000
Nov 13 08:32:58 endgame hald: unmounted /dev/sdf1 from '/media/disk' on behalf of uid 1000
Nov 13 08:33:00 endgame NetworkManager: <debug> [1226593980.075718] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48B4_6306'). 
Nov 13 08:33:04 endgame NetworkManager: <debug> [1226593984.156317] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov 13 08:33:04 endgame NetworkManager: <debug> [1226593984.169022] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial__USB_DISK_2_0_07000774113B016E_0_0'). 
Nov 13 08:33:04 endgame NetworkManager: <debug> [1226593984.174867] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E_if0_scsi_host_scsi_device_lun0'). 
Nov 13 08:33:04 endgame NetworkManager: <debug> [1226593984.178321] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E_if0_scsi_host'). 
Nov 13 08:33:04 endgame NetworkManager: <debug> [1226593984.185238] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E_if0'). 
Nov 13 08:33:04 endgame NetworkManager: <debug> [1226593984.193288] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E'). 
Nov 13 08:37:07 endgame NetworkManager: <debug> [1226594227.055657] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E'). 
Nov 13 08:37:07 endgame NetworkManager: <debug> [1226594227.258993] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E_if0'). 
Nov 13 08:37:12 endgame NetworkManager: <debug> [1226594232.233442] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E_if0_scsi_host'). 
Nov 13 08:37:12 endgame NetworkManager: <debug> [1226594232.244450] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E_if0_scsi_host_scsi_device_lun0'). 
Nov 13 08:37:12 endgame NetworkManager: <debug> [1226594232.633740] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov 13 08:37:13 endgame NetworkManager: <debug> [1226594233.300251] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial__USB_DISK_2_0_07000774113B016E_0_0'). 
Nov 13 08:37:13 endgame NetworkManager: <debug> [1226594233.571016] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48B4_6306'). 
Nov 13 08:37:14 endgame hald: mounted /dev/sdf1 on behalf of uid 1000
Nov 13 09:03:55 endgame hald: unmounted /dev/sdf1 from '/media/disk' on behalf of uid 1000
Nov 13 09:03:56 endgame NetworkManager: <debug> [1226595836.070601] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48B4_6306'). 
Nov 13 09:03:58 endgame NetworkManager: <debug> [1226595838.205720] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov 13 09:03:58 endgame NetworkManager: <debug> [1226595838.220325] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial__USB_DISK_2_0_07000774113B016E_0_0'). 
Nov 13 09:03:58 endgame NetworkManager: <debug> [1226595838.226553] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E_if0_scsi_host_scsi_device_lun0'). 
Nov 13 09:03:58 endgame NetworkManager: <debug> [1226595838.231087] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E_if0_scsi_host'). 
Nov 13 09:03:58 endgame NetworkManager: <debug> [1226595838.239368] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E_if0'). 
Nov 13 09:03:58 endgame NetworkManager: <debug> [1226595838.249355] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E'). 
Nov 13 09:04:41 endgame NetworkManager: <debug> [1226595881.171196] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E'). 
Nov 13 09:04:41 endgame NetworkManager: <debug> [1226595881.392622] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E_if0'). 
Nov 13 09:04:46 endgame NetworkManager: <debug> [1226595886.341145] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E_if0_scsi_host'). 
Nov 13 09:04:46 endgame NetworkManager: <debug> [1226595886.352242] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E_if0_scsi_host_scsi_device_lun0'). 
Nov 13 09:04:46 endgame NetworkManager: <debug> [1226595886.756823] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov 13 09:04:47 endgame NetworkManager: <debug> [1226595887.436319] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial__USB_DISK_2_0_07000774113B016E_0_0'). 
Nov 13 09:04:47 endgame NetworkManager: <debug> [1226595887.719825] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48B4_6306'). 
Nov 13 09:04:48 endgame hald: mounted /dev/sdg1 on behalf of uid 1000
Nov 13 09:11:20 endgame hald: unmounted /dev/sdg1 from '/media/disk' on behalf of uid 1000
Nov 13 09:13:02 endgame NetworkManager: <debug> [1226596382.812267] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov 13 09:13:02 endgame NetworkManager: <debug> [1226596382.825760] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48B4_6306'). 
Nov 13 09:13:02 endgame NetworkManager: <debug> [1226596382.834791] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial__USB_DISK_2_0_07000774113B016E_0_0'). 
Nov 13 09:13:02 endgame NetworkManager: <debug> [1226596382.840434] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E_if0_scsi_host_scsi_device_lun0'). 
Nov 13 09:13:02 endgame NetworkManager: <debug> [1226596382.843964] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E_if0_scsi_host'). 
Nov 13 09:13:02 endgame NetworkManager: <debug> [1226596382.851071] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E_if0'). 
Nov 13 09:13:02 endgame NetworkManager: <debug> [1226596382.858951] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E'). 
Nov 13 09:13:06 endgame NetworkManager: <debug> [1226596386.203446] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E'). 
Nov 13 09:13:06 endgame NetworkManager: <debug> [1226596386.412029] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E_if0'). 
Nov 13 09:13:11 endgame NetworkManager: <debug> [1226596391.364771] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E_if0_scsi_host'). 
Nov 13 09:13:11 endgame NetworkManager: <debug> [1226596391.373674] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E_if0_scsi_host_scsi_device_lun0'). 
Nov 13 09:13:12 endgame NetworkManager: <debug> [1226596392.496304] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov 13 09:13:13 endgame NetworkManager: <debug> [1226596393.168334] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial__USB_DISK_2_0_07000774113B016E_0_0'). 
Nov 13 09:13:13 endgame NetworkManager: <debug> [1226596393.440793] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48B4_6306'). 
Nov 13 09:13:14 endgame hald: mounted /dev/sdf1 on behalf of uid 1000
Nov 13 09:13:44 endgame hald: unmounted /dev/sdf1 from '/media/disk' on behalf of uid 1000
Nov 13 09:13:45 endgame NetworkManager: <debug> [1226596425.064562] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48B4_6306'). 
Nov 13 09:13:51 endgame NetworkManager: <debug> [1226596431.667998] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov 13 09:13:51 endgame NetworkManager: <debug> [1226596431.680309] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial__USB_DISK_2_0_07000774113B016E_0_0'). 
Nov 13 09:13:51 endgame NetworkManager: <debug> [1226596431.686026] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E_if0_scsi_host_scsi_device_lun0'). 
Nov 13 09:13:51 endgame NetworkManager: <debug> [1226596431.689566] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E_if0_scsi_host'). 
Nov 13 09:13:51 endgame NetworkManager: <debug> [1226596431.696444] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E_if0'). 
Nov 13 09:13:51 endgame NetworkManager: <debug> [1226596431.704335] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E'). 
Nov 13 09:16:27 endgame NetworkManager: <debug> [1226596587.315238] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E'). 
Nov 13 09:16:27 endgame NetworkManager: <debug> [1226596587.518527] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E_if0'). 
Nov 13 09:16:32 endgame NetworkManager: <debug> [1226596592.468888] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E_if0_scsi_host'). 
Nov 13 09:16:32 endgame NetworkManager: <debug> [1226596592.478883] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E_if0_scsi_host_scsi_device_lun0'). 
Nov 13 09:16:32 endgame NetworkManager: <debug> [1226596592.881330] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov 13 09:16:33 endgame NetworkManager: <debug> [1226596593.548435] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial__USB_DISK_2_0_07000774113B016E_0_0'). 
Nov 13 09:16:33 endgame NetworkManager: <debug> [1226596593.823673] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48B4_6306'). 
Nov 13 09:16:34 endgame hald: mounted /dev/sdf1 on behalf of uid 1000
Nov 13 09:22:18 endgame hald: unmounted /dev/sdf1 from '/media/disk' on behalf of uid 1000
Nov 13 09:22:20 endgame NetworkManager: <debug> [1226596940.072129] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov 13 09:22:20 endgame NetworkManager: <debug> [1226596940.084595] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48B4_6306'). 
Nov 13 09:22:20 endgame NetworkManager: <debug> [1226596940.094530] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial__USB_DISK_2_0_07000774113B016E_0_0'). 
Nov 13 09:22:20 endgame NetworkManager: <debug> [1226596940.101155] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E_if0_scsi_host_scsi_device_lun0'). 
Nov 13 09:22:20 endgame NetworkManager: <debug> [1226596940.104476] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E_if0_scsi_host'). 
Nov 13 09:22:20 endgame NetworkManager: <debug> [1226596940.111822] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E_if0'). 
Nov 13 09:22:20 endgame NetworkManager: <debug> [1226596940.119933] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1c00_07000774113B016E'). 
Nov 13 11:43:06 endgame init: tty4 main process (4962) killed by TERM signal
Nov 13 11:43:06 endgame init: tty5 main process (4963) killed by TERM signal
Nov 13 11:43:06 endgame init: tty2 main process (4967) killed by TERM signal
Nov 13 11:43:06 endgame init: tty3 main process (4968) killed by TERM signal
Nov 13 11:43:06 endgame init: tty6 main process (4970) killed by TERM signal
Nov 13 11:43:06 endgame init: tty1 main process (6410) killed by TERM signal
Nov 13 11:43:07 endgame avahi-daemon[5426]: Got SIGTERM, quitting.
Nov 13 11:43:07 endgame avahi-daemon[5426]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.66.
Nov 13 11:43:08 endgame xinetd[5703]: Exiting...
Nov 13 11:43:11 endgame mt-daapd[5933]: Got shutdown signal. 
Nov 13 11:43:11 endgame mt-daapd[5933]: Stopping gracefully 
Nov 13 11:43:11 endgame mt-daapd[5933]: Stopping rendezvous daemon 
Nov 13 11:43:11 endgame mt-daapd[5933]: Closing database 
Nov 13 11:43:11 endgame mt-daapd[5933]: Done! 
Nov 13 11:44:53 endgame NetworkManager: <info>  starting... 
Nov 13 11:44:53 endgame avahi-daemon[5423]: Found user 'avahi' (UID 108) and group 'avahi' (GID 117).
Nov 13 11:44:53 endgame avahi-daemon[5423]: Successfully dropped root privileges.
Nov 13 11:44:53 endgame avahi-daemon[5423]: avahi-daemon 0.6.22 starting up.
Nov 13 11:44:53 endgame avahi-daemon[5423]: Successfully called chroot().
Nov 13 11:44:53 endgame avahi-daemon[5423]: Successfully dropped remaining capabilities.
Nov 13 11:44:53 endgame avahi-daemon[5423]: No service file found in /etc/avahi/services.
Nov 13 11:44:53 endgame avahi-daemon[5423]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.66.
Nov 13 11:44:53 endgame avahi-daemon[5423]: New relevant interface eth0.IPv4 for mDNS.
Nov 13 11:44:53 endgame avahi-daemon[5423]: Network interface enumeration completed.
Nov 13 11:44:53 endgame avahi-daemon[5423]: Registering new address record for fe80::219:21ff:fee4:ae40 on eth0.*.
Nov 13 11:44:53 endgame avahi-daemon[5423]: Registering new address record for 192.168.1.66 on eth0.IPv4.
Nov 13 11:44:53 endgame avahi-daemon[5423]: Registering HINFO record with values 'I686'/'LINUX'.
Nov 13 11:44:54 endgame avahi-daemon[5423]: Server startup complete. Host name is endgame.local. Local service cookie is 991555504.
Nov 13 11:45:00 endgame xinetd[5728]: Reading included configuration file: /etc/xinetd.d/Xvnc [file=/etc/xinetd.conf] [line=14]
Nov 13 11:45:00 endgame xinetd[5728]: Reading included configuration file: /etc/xinetd.d/chargen [file=/etc/xinetd.d/chargen] [line=12]
Nov 13 11:45:00 endgame xinetd[5728]: Reading included configuration file: /etc/xinetd.d/daytime [file=/etc/xinetd.d/daytime] [line=28]
Nov 13 11:45:00 endgame xinetd[5728]: Reading included configuration file: /etc/xinetd.d/discard [file=/etc/xinetd.d/discard] [line=26]
Nov 13 11:45:00 endgame xinetd[5728]: Reading included configuration file: /etc/xinetd.d/echo [file=/etc/xinetd.d/echo] [line=25]
Nov 13 11:45:00 endgame xinetd[5728]: Reading included configuration file: /etc/xinetd.d/time [file=/etc/xinetd.d/time] [line=26]
Nov 13 11:45:00 endgame xinetd[5728]: removing chargen
Nov 13 11:45:00 endgame xinetd[5728]: removing chargen
Nov 13 11:45:00 endgame xinetd[5728]: removing daytime
Nov 13 11:45:00 endgame xinetd[5728]: removing daytime
Nov 13 11:45:00 endgame xinetd[5728]: removing discard
Nov 13 11:45:00 endgame xinetd[5728]: removing discard
Nov 13 11:45:00 endgame xinetd[5728]: removing echo
Nov 13 11:45:00 endgame xinetd[5728]: removing echo
Nov 13 11:45:00 endgame xinetd[5728]: removing time
Nov 13 11:45:00 endgame xinetd[5728]: removing time
Nov 13 11:45:00 endgame xinetd[5728]: xinetd Version 2.3.14 started with libwrap loadavg options compiled in.
Nov 13 11:45:00 endgame xinetd[5728]: Started working: 1 available service
Nov 13 11:45:01 endgame hcid[5899]: Bluetooth HCI daemon
Nov 13 11:45:01 endgame hcid[5899]: Starting SDP server
Nov 13 11:45:01 endgame hcid[5899]: Created local server at unix:abstract=/var/run/dbus-CtMjHOXj2O,guid=16aa23c7ff4b9948ba981622491c83bd
Nov 13 11:45:01 endgame audio[5916]: Bluetooth Audio daemon
Nov 13 11:45:01 endgame audio[5916]: Unix socket created: 5
Nov 13 11:45:01 endgame audio[5916]: audio.conf: Key file does not have key 'Enable'
Nov 13 11:45:01 endgame audio[5916]: audio.conf: Key file does not have key 'Disable'
Nov 13 11:45:01 endgame NetworkManager: <debug> [1226605501.981060] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Nov 13 11:45:02 endgame audio[5916]: add_service_record: got record id 0x10000
Nov 13 11:45:02 endgame audio[5916]: audio.conf: Key file does not have key 'Disable'
Nov 13 11:45:02 endgame audio[5916]: audio.conf: Key file does not have group 'A2DP'
Nov 13 11:45:02 endgame last message repeated 3 times
Nov 13 11:45:02 endgame audio[5916]: SEP 0x806d218 registered: type:0 codec:0 seid:1
Nov 13 11:45:02 endgame audio[5916]: add_service_record: got record id 0x10001
Nov 13 11:45:02 endgame audio[5916]: add_service_record: got record id 0x10002
Nov 13 11:45:02 endgame input[5921]: Bluetooth Input daemon
Nov 13 11:45:02 endgame input[5921]: Registered input manager path:/org/bluez/input
Nov 13 11:45:02 endgame audio[5916]: add_service_record: got record id 0x10003
Nov 13 11:45:02 endgame audio[5916]: Registered manager path:/org/bluez/audio
Nov 13 11:45:02 endgame mt-daapd[5929]: Firefly Version svn-1696: Starting with debuglevel 2 
Nov 13 11:45:02 endgame mt-daapd[5929]: Error loading plugin /usr/lib/mt-daapd/plugins/ssc-script.so: plugin declined to load 
Nov 13 11:45:02 endgame mt-daapd[5929]: Plugin loaded: ssc-ffmpeg/svn-1696 
Nov 13 11:45:02 endgame mt-daapd[5929]: Plugin loaded: daap/svn-1696 
Nov 13 11:45:02 endgame mt-daapd[5929]: Plugin loaded: rsp/svn-1696 
Nov 13 11:45:02 endgame mt-daapd[5929]: Starting rendezvous daemon 
Nov 13 11:45:02 endgame mt-daapd[5929]: Starting signal handler 
Nov 13 11:45:02 endgame mt-daapd[5933]: Initializing database 
Nov 13 11:45:03 endgame hal_lpadmin: add
Nov 13 11:45:03 endgame mt-daapd[5933]: Starting web server from /usr/share/mt-daapd/admin-root on port 3689 
Nov 13 11:45:03 endgame mt-daapd[5933]: Registering rendezvous names 
Nov 13 11:45:04 endgame mt-daapd[5933]: Serving 6578 songs.  Startup complete in 2 seconds 
Nov 13 11:45:04 endgame hal_lpadmin: URIs: ['hp:/usb/PSC_2350_series?serial=MY55IF53N8KJ', 'usb://HP/PSC%202350%20series?serial=MY55IF53N8KJ', 'hal:///org/freedesktop/Hal/devices/usb_device_3f0_4911_MY55IF53N8KJ_if1_printer_MY55IF53N8KJ']
Nov 13 11:45:04 endgame hal_lpadmin: HPLIP Fax URIs: None
Nov 13 11:45:04 endgame hal_lpadmin: Not adding printer: PSC_2350_series already exists
Nov 13 11:45:05 endgame NetworkManager: <debug> [1226605505.046079] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_4911_MY55IF53N8KJ_if1_printer_MY55IF53N8KJ'). 
Nov 13 11:45:19 endgame proftpd[6188]: endgame.sonic.net - ProFTPD 1.3.1 (stable) (built Wed Jun 18 06:16:21 UTC 2008) standalone mode STARTUP 
Nov 13 11:46:56 endgame NetworkManager: <info>  Updating allowed wireless network lists. 
Nov 13 11:46:56 endgame NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Nov 13 14:54:29 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 14:58:36 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 14:59:40 endgame last message repeated 13 times
Nov 13 15:03:23 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 15:07:53 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 15:09:27 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 15:13:49 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 15:14:34 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 15:16:12 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 15:16:44 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 15:17:31 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 15:20:37 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 15:35:02 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 15:35:13 endgame last message repeated 4 times
Nov 13 15:38:46 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 15:43:04 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 15:43:11 endgame proftpd[6188]: endgame.sonic.net - ProFTPD killed (signal 15) 
Nov 13 15:43:11 endgame proftpd[6188]: endgame.sonic.net - ProFTPD 1.3.1 standalone mode SHUTDOWN 
Nov 13 15:43:21 endgame proftpd[7150]: endgame.sonic.net - ProFTPD 1.3.1 (stable) (built Wed Jun 18 06:16:21 UTC 2008) standalone mode STARTUP 
Nov 13 15:46:22 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 15:47:09 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 15:52:43 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 15:53:18 endgame last message repeated 10 times
Nov 13 15:54:27 endgame last message repeated 16 times
Nov 13 15:54:31 endgame mt-daapd[5933]: Error writing to client socket: Connection reset by peer 
Nov 13 15:54:31 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 15:54:43 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 15:54:43 endgame mt-daapd[5933]: Error writing to client socket: Connection reset by peer 
Nov 13 15:54:48 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 15:54:48 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 15:58:47 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 15:58:55 endgame last message repeated 2 times
Nov 13 16:02:28 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 16:03:03 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 16:08:00 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 16:12:32 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 16:15:39 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 16:16:27 endgame last message repeated 8 times
Nov 13 16:20:16 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 16:23:47 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 16:25:50 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 16:30:40 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 16:34:10 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 16:35:16 endgame last message repeated 14 times
Nov 13 16:35:16 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 16:39:50 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 16:43:41 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 16:48:00 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 16:48:58 endgame last message repeated 5 times
Nov 13 16:49:24 endgame last message repeated 2 times
Nov 13 16:51:14 endgame last message repeated 22 times
Nov 13 16:51:35 endgame last message repeated 4 times
Nov 13 16:56:56 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 17:03:28 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 17:04:47 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 17:13:28 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 17:19:30 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 17:24:46 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 17:28:07 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 17:28:51 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 17:33:00 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 17:34:04 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 17:39:13 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 18:15:03 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 18:15:14 endgame last message repeated 2 times
Nov 13 18:20:46 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 18:23:36 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 18:31:20 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 18:33:02 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 18:40:33 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 19:15:35 endgame mt-daapd[5933]: Write error: Connection reset by peer 
Nov 13 19:15:42 endgame last message repeated 2 times
Nov 13 22:36:23 endgame init: tty4 main process (4959) killed by TERM signal
Nov 13 22:36:23 endgame init: tty5 main process (4960) killed by TERM signal
Nov 13 22:36:23 endgame init: tty2 main process (4964) killed by TERM signal
Nov 13 22:36:23 endgame init: tty3 main process (4965) killed by TERM signal
Nov 13 22:36:23 endgame init: tty6 main process (4967) killed by TERM signal
Nov 13 22:36:23 endgame init: tty1 main process (6264) killed by TERM signal
Nov 13 22:36:24 endgame avahi-daemon[5423]: Got SIGTERM, quitting.
Nov 13 22:36:24 endgame avahi-daemon[5423]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.66.
Nov 13 22:36:25 endgame xinetd[5728]: Exiting...
Nov 13 22:36:26 endgame mt-daapd[5933]: Got shutdown signal. 
Nov 13 22:36:26 endgame mt-daapd[5933]: Stopping gracefully 
Nov 13 22:36:26 endgame mt-daapd[5933]: Stopping rendezvous daemon 
Nov 13 22:36:26 endgame mt-daapd[5933]: Closing database 
Nov 13 22:36:26 endgame mt-daapd[5933]: Done! 
Nov 14 08:40:47 endgame NetworkManager: <info>  starting... 
Nov 14 08:40:47 endgame avahi-daemon[5422]: Found user 'avahi' (UID 108) and group 'avahi' (GID 117).
Nov 14 08:40:47 endgame avahi-daemon[5422]: Successfully dropped root privileges.
Nov 14 08:40:47 endgame avahi-daemon[5422]: avahi-daemon 0.6.22 starting up.
Nov 14 08:40:47 endgame avahi-daemon[5422]: Successfully called chroot().
Nov 14 08:40:47 endgame avahi-daemon[5422]: Successfully dropped remaining capabilities.
Nov 14 08:40:48 endgame avahi-daemon[5422]: No service file found in /etc/avahi/services.
Nov 14 08:40:48 endgame avahi-daemon[5422]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.66.
Nov 14 08:40:48 endgame avahi-daemon[5422]: New relevant interface eth0.IPv4 for mDNS.
Nov 14 08:40:48 endgame avahi-daemon[5422]: Network interface enumeration completed.
Nov 14 08:40:48 endgame avahi-daemon[5422]: Registering new address record for fe80::219:21ff:fee4:ae40 on eth0.*.
Nov 14 08:40:48 endgame avahi-daemon[5422]: Registering new address record for 192.168.1.66 on eth0.IPv4.
Nov 14 08:40:48 endgame avahi-daemon[5422]: Registering HINFO record with values 'I686'/'LINUX'.
Nov 14 08:40:48 endgame avahi-daemon[5422]: Server startup complete. Host name is endgame.local. Local service cookie is 1874591342.
Nov 14 08:40:54 endgame xinetd[5702]: Reading included configuration file: /etc/xinetd.d/Xvnc [file=/etc/xinetd.conf] [line=14]
Nov 14 08:40:54 endgame xinetd[5702]: Reading included configuration file: /etc/xinetd.d/chargen [file=/etc/xinetd.d/chargen] [line=12]
Nov 14 08:40:54 endgame xinetd[5702]: Reading included configuration file: /etc/xinetd.d/daytime [file=/etc/xinetd.d/daytime] [line=28]
Nov 14 08:40:54 endgame xinetd[5702]: Reading included configuration file: /etc/xinetd.d/discard [file=/etc/xinetd.d/discard] [line=26]
Nov 14 08:40:54 endgame xinetd[5702]: Reading included configuration file: /etc/xinetd.d/echo [file=/etc/xinetd.d/echo] [line=25]
Nov 14 08:40:54 endgame xinetd[5702]: Reading included configuration file: /etc/xinetd.d/time [file=/etc/xinetd.d/time] [line=26]
Nov 14 08:40:54 endgame xinetd[5702]: removing chargen
Nov 14 08:40:54 endgame xinetd[5702]: removing chargen
Nov 14 08:40:54 endgame xinetd[5702]: removing daytime
Nov 14 08:40:54 endgame xinetd[5702]: removing daytime
Nov 14 08:40:54 endgame xinetd[5702]: removing discard
Nov 14 08:40:54 endgame xinetd[5702]: removing discard
Nov 14 08:40:54 endgame xinetd[5702]: removing echo
Nov 14 08:40:54 endgame xinetd[5702]: removing echo
Nov 14 08:40:54 endgame xinetd[5702]: removing time
Nov 14 08:40:54 endgame xinetd[5702]: removing time
Nov 14 08:40:54 endgame xinetd[5702]: xinetd Version 2.3.14 started with libwrap loadavg options compiled in.
Nov 14 08:40:54 endgame xinetd[5702]: Started working: 1 available service
Nov 14 08:40:56 endgame hcid[5898]: Bluetooth HCI daemon
Nov 14 08:40:56 endgame hcid[5898]: Starting SDP server
Nov 14 08:40:56 endgame hcid[5898]: Created local server at unix:abstract=/var/run/dbus-eaYZEqf9GB,guid=ca9a5786813d9a30f4175d9c491daa18
Nov 14 08:40:56 endgame NetworkManager: <debug> [1226680856.301335] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Nov 14 08:40:56 endgame audio[5915]: Bluetooth Audio daemon
Nov 14 08:40:56 endgame audio[5915]: Unix socket created: 5
Nov 14 08:40:56 endgame audio[5915]: audio.conf: Key file does not have key 'Enable'
Nov 14 08:40:56 endgame audio[5915]: audio.conf: Key file does not have key 'Disable'
Nov 14 08:40:56 endgame audio[5915]: add_service_record: got record id 0x10000
Nov 14 08:40:56 endgame audio[5915]: audio.conf: Key file does not have key 'Disable'
Nov 14 08:40:56 endgame audio[5915]: audio.conf: Key file does not have group 'A2DP'
Nov 14 08:40:56 endgame last message repeated 3 times
Nov 14 08:40:56 endgame audio[5915]: SEP 0x806d218 registered: type:0 codec:0 seid:1
Nov 14 08:40:56 endgame audio[5915]: add_service_record: got record id 0x10001
Nov 14 08:40:56 endgame audio[5915]: add_service_record: got record id 0x10002
Nov 14 08:40:56 endgame audio[5915]: add_service_record: got record id 0x10003
Nov 14 08:40:56 endgame audio[5915]: Registered manager path:/org/bluez/audio
Nov 14 08:40:56 endgame input[5920]: Bluetooth Input daemon
Nov 14 08:40:56 endgame input[5920]: Registered input manager path:/org/bluez/input
Nov 14 08:40:56 endgame mt-daapd[5928]: Firefly Version svn-1696: Starting with debuglevel 2 
Nov 14 08:40:56 endgame mt-daapd[5928]: Error loading plugin /usr/lib/mt-daapd/plugins/ssc-script.so: plugin declined to load 
Nov 14 08:40:56 endgame mt-daapd[5928]: Plugin loaded: ssc-ffmpeg/svn-1696 
Nov 14 08:40:56 endgame mt-daapd[5928]: Plugin loaded: daap/svn-1696 
Nov 14 08:40:56 endgame mt-daapd[5928]: Plugin loaded: rsp/svn-1696 
Nov 14 08:40:56 endgame mt-daapd[5928]: Starting rendezvous daemon 
Nov 14 08:40:56 endgame mt-daapd[5928]: Starting signal handler 
Nov 14 08:40:56 endgame mt-daapd[5931]: Initializing database 
Nov 14 08:40:57 endgame hal_lpadmin: add
Nov 14 08:40:58 endgame mt-daapd[5931]: Starting web server from /usr/share/mt-daapd/admin-root on port 3689 
Nov 14 08:40:58 endgame mt-daapd[5931]: Registering rendezvous names 
Nov 14 08:40:58 endgame mt-daapd[5931]: Serving 6578 songs.  Startup complete in 2 seconds 
Nov 14 08:40:58 endgame hal_lpadmin: URIs: ['hp:/usb/PSC_2350_series?serial=MY55IF53N8KJ', 'usb://HP/PSC%202350%20series?serial=MY55IF53N8KJ', 'hal:///org/freedesktop/Hal/devices/usb_device_3f0_4911_MY55IF53N8KJ_if1_printer_MY55IF53N8KJ']
Nov 14 08:40:59 endgame hal_lpadmin: HPLIP Fax URIs: None
Nov 14 08:40:59 endgame hal_lpadmin: Not adding printer: PSC_2350_series already exists
Nov 14 08:40:59 endgame NetworkManager: <debug> [1226680859.503920] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_4911_MY55IF53N8KJ_if1_printer_MY55IF53N8KJ'). 
Nov 14 08:41:12 endgame proftpd[6190]: endgame.sonic.net - ProFTPD 1.3.1 (stable) (built Wed Jun 18 06:16:21 UTC 2008) standalone mode STARTUP 
Nov 14 08:41:37 endgame NetworkManager: <info>  Updating allowed wireless network lists. 
Nov 14 08:41:37 endgame NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 


```

thanks for the help

---

### Post by nixscripter on 2008-11-18
Hmm, I couldn't tell if it worked or not. I don't see what I'm looking for.

But I did want to ask: it looks like daapd (music sharing, if I recall correctly) is getting a lot of dropped connections too. Have you noticed any problems with it? I want to rule out the firewall/network interface.

---

### Post by Cool Javelin on 2008-12-15
WarholsGhost:

See a reply I posted earlier about x11vnc here

[http://ubuntuforums.org/showthread.php?t=1002240&highlight=path](http://ubuntuforums.org/showthread.php?t=1002240&highlight=path)

Good luck.

Mark.

---

### Post by cirobr on 2008-12-18
Try this.

[http://ubuntuforums.org/showthread.php?t=1013499](http://ubuntuforums.org/showthread.php?t=1013499)

---

