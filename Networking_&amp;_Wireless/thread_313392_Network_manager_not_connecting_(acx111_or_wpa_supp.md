---
title: "Network manager not connecting (acx111 or wpa_supplicant bug?)"
date: 2006-12-05
forum: Networking &amp; Wireless
---

### Post by zanglang on 2006-12-05
Hi,

i've been trying to use NetworkManager for a while now, but it never seems to connect, and generates 3000+ lines of messages in /var/log/syslog... :-k

P.S: [Connection manager]("http://ubuntuforums.org/showthread.php?t=299462&highlight=connection+manager") and manually using iwconfig and dhclient works fine.

Example output:
> Dec  6 14:08:32 aesir NetworkManager: <information>^Iwpa_supplicant(13732): WEXT: Operstate: linkmode=-1, operstate=5 
Dec  6 14:08:32 aesir NetworkManager: <information>^Iwpa_supplicant(13732): EAPOL: External notification - portEnabled=0 
Dec  6 14:08:32 aesir NetworkManager: <information>^Iwpa_supplicant(13732): EAPOL: External notification - portValid=0 
Dec  6 14:08:32 aesir NetworkManager: <information>^Iwpa_supplicant(13732): CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys 
Dec  6 14:08:32 aesir NetworkManager: <information>^Iwpa_supplicant(13732): CTRL_IFACE monitor send - hexdump(len=41): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 31 33 31 33 37 2d 33 00 
Dec  6 14:08:32 aesir NetworkManager: <information>^Iwpa_supplicant(13732): wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0 
Dec  6 14:08:32 aesir NetworkManager: <information>^Iwpa_supplicant(13732): SIWENCODE 
Dec  6 14:08:32 aesir NetworkManager: <information>^Iwpa_supplicant(13732): wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0 
Dec  6 14:08:32 aesir NetworkManager: <information>^Iwpa_supplicant(13732): Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE 
Dec  6 14:08:32 aesir NetworkManager: <information>^Iwpa_supplicant(13732): wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0 
Dec  6 14:08:32 aesir NetworkManager: <information>^Iwpa_supplicant(13732): Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE 
Dec  6 14:08:32 aesir NetworkManager: <information>^Iwpa_supplicant(13732): wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0 
Dec  6 14:08:32 aesir NetworkManager: <information>^Iwpa_supplicant(13732): Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE 
Dec  6 14:08:32 aesir NetworkManager: <information>^Iwpa_supplicant(13732): wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0 
Dec  6 14:08:32 aesir NetworkManager: <information>^Iwpa_supplicant(13732): Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE 
Dec  6 14:08:32 aesir NetworkManager: <information>^Iwpa_supplicant(13732): Wireless event: cmd=0x8b2a len=8 
Dec  6 14:08:32 aesir NetworkManager: <information>^Iwpa_supplicant(13732): Wireless event: cmd=0x8b15 len=20 
Dec  6 14:08:32 aesir NetworkManager: <information>^Iwpa_supplicant(13732): Wireless event: new AP: 00:00:00:00:00:00 
Dec  6 14:08:32 aesir NetworkManager: <information>^Iwpa_supplicant(13732): BSSID 00:00:00:00:00:00 blacklist count incremented to 4 
Dec  6 14:08:32 aesir NetworkManager: <information>^Iwpa_supplicant(13732): State: DISCONNECTED -> DISCONNECTED
This goes on for a few hundred times before it gives up.

In my case, I am connecting to an unsecured public access point, no password. I've read that older versions of network-manager don't work with public AP's, but wasn't this fixed in Edgy? Previously on Dapper the acx111 wireless driver for my D-Link DWL-G650+ wireless card has been giving me problems, so I'm not sure whether this is a driver problem either.

I'd really like to use a centralised connection management tool for my laptop... Suggestions on fixing this anyone?

---

### Post by jackobean on 2006-12-13
i second that!

Hi I also have a DWL-G650+ and running edgy(kde), and connecting to an unsecured ap. Its been giving me so much pain. most of the time slow, sometimes realy fast, and often drops out for a couple of minutes.

the network manager has crashed a few times also.

i would prefer not to use ndiswrapper.

any suggestions?

---

### Post by zanglang on 2006-12-13
[http://acx100.sourceforge.net/wiki/WPA](http://acx100.sourceforge.net/wiki/WPA)
[https://bugs.launchpad.net/distros/ubuntu/+source/network-manager/+bug/38586](https://bugs.launchpad.net/distros/ubuntu/+source/network-manager/+bug/38586)

Looks like there's no WPA support, and hence no working-out-of-the-box NM for the acx driver in the near future. :( Has anyone else tried out any alternatives on the ACX100 sourceforge page?

On the other hand, I've just tried installing ndiswrapper, and network-manager does work beautifully though. (Networking doesn't appear to be as smooth though... or it could be just me.)

---

