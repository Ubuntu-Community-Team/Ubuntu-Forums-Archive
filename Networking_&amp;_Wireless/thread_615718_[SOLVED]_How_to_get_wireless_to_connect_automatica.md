---
title: "[SOLVED] How to get wireless to connect automatically on T42 with 2200BG wireless in"
date: 2007-11-17
forum: Networking &amp; Wireless
---

### Post by tedrogers on 2007-11-17
Hi all,

Bit of a strange one this...and I though I had wireless connectivity finally licked with wiemans great tutorial for edgy / feisty etc.

I'm not using bcm43xx anymore, this problem is on an IBM T42 with Intel® PRO/Wireless 2200BG (IPW2200) wireless and in Gutsy.

I can connect fine, but it just won't do it automatically.

Everytime I log in I have to manually connect to my network, input my passkey and also tell it to use WPA2.

For some reason it keeps forgetting about WPA2 and reverting to WPA1?? This is annoying in itself...but I'd really like this to connect automatically and remember my key too.

I've looked at my interfaces file and it looks like this:

```

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp
wpa-psk [my very long 63 character key]
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA2
wpa-ssid [my essid]

```

As far as I know there is nothing wrong with this at all.

I have checked and wpasupplicant is installed...and if it wasn't I presume the network wouldn't work...but when connected its fine - I'm posting from it now.

Anybody out there know the reason?

Could it be due to the nm-applet 0.6.5 and network monitor 2.12.1 both at the top as shown in the picture?

[IMG]http://i77.photobucket.com/albums/j58/fiddybux/nm.jpg[/IMG]

The reason I have both is that the notification area is stupidly attached to the nm-applet, but the nm-applet doesn't show my network activity using wireless or my connection status, i.e. the green bars. Grrrr.

So has anyone got any ideas out there? This would be really great to get solved.

Thanks in advance to everyone.

Keep ubuntuing.

---

### Post by wieman01 on 2007-12-19
Ted, 

Do you still face this issue? If yes, please let me know otherwise we can close this thread.

---

### Post by tedrogers on 2007-12-22
All fixed thanks.

---

