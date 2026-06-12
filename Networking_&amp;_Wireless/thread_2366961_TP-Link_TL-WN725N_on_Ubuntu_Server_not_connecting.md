---
title: "TP-Link TL-WN725N on Ubuntu Server not connecting"
date: 2017-07-24
forum: Networking &amp; Wireless
---

### Post by kose-onur on 2017-07-24
I was trying to install original TP-Link driver but it's failed during compiling. So I've found this thread and installed 8188eu. But it's still not activating the wlan0.

Here is my wirless-script results:

[http://paste.ubuntu.com/25161491/](http://paste.ubuntu.com/25161491/)

Any advice welcomed. Thanks.

---

### Post by praseodym on 2017-07-24
Hi,

it loads some Broadcom drivers, too. Blacklist them:
```

echo -e "blacklist bcma\nblacklist b43" | sudo tee /etc/modprobe.d/blacklist-broadcom.conf
```
Reboot.

Does it have a BIOS or UEFI? If UEFI then deactivate Secure Boot

---

### Post by kose-onur on 2017-07-24
Yes I did deactivation and blacklisting. Nothing changed.

When I run ```
ifconfig wlan0 up
``` I got this error:
>  SIOCSIFFLAGS: operation not permitted 

Then I hit ```
systemctl status networking.service
``` and received:
> Job for networking.service failed because the control process exited with error code. See "systemctl status networking.service" and "journalctl -xe" for details.

After ```
systemctl status networking.service
```:
> 
 networking.service - Raise network interfaces
   Loaded: loaded (/lib/systemd/system/networking.service; enabled; vendor preset: enabled)
  Drop-In: /run/systemd/generator/networking.service.d
           &#9492;&#9472;50-insserv.conf-$network.conf
   Active: failed (Result: exit-code) since Mon 2017-07-24 16:48:19 +03; 7s ago
     Docs: man:interfaces(5)
  Process: 1431 ExecStart=/sbin/ifup -a --read-environment (code=exited, status=1/FAILURE)
  Process: 1425 ExecStartPre=/bin/sh -c [ "$CONFIGURE_INTERFACES" != "no" ] && [ -n "$(ifquery --read-environment --list --exclude=lo)" ] && udevadm settle (code=exited, status=0/SUCCESS)
 Main PID: 1431 (code=exited, status=1/FAILURE)

Jul 24 16:48:19 balin wpa_supplicant[1452]: Successfully initialized wpa_supplicant
Jul 24 16:48:19 balin wpa_supplicant[1452]: nl80211: Driver does not support authentication/association or connect commands
Jul 24 16:48:19 balin wpa_supplicant[1452]: nl80211: deinit ifname=wlan0 disabled_11b_rates=0
Jul 24 16:48:19 balin ifup[1431]: /etc/network/if-pre-up.d/wpasupplicant: 120: /etc/network/if-pre-up.d/wpasupplicant: cannot create /dev/stderr: No such device or address
Jul 24 16:48:19 balin ifup[1431]: run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1
Jul 24 16:48:19 balin ifup[1431]: Failed to bring up wlan0.
Jul 24 16:48:19 balin systemd[1]: networking.service: Main process exited, code=exited, status=1/FAILURE
Jul 24 16:48:19 balin systemd[1]: Failed to start Raise network interfaces.
Jul 24 16:48:19 balin systemd[1]: networking.service: Unit entered failed state.
Jul 24 16:48:19 balin systemd[1]: networking.service: Failed with result 'exit-code'.


---

### Post by praseodym on 2017-07-24
You are running the server without GUI? If yes, have a look here:

[https://w1.fi/wpa_supplicant/](https://w1.fi/wpa_supplicant/)

how to configure wpa_supplicant

---

