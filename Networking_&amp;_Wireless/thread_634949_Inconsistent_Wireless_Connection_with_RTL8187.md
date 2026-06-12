---
title: "Inconsistent Wireless Connection with RTL8187"
date: 2007-12-08
forum: Networking &amp; Wireless
---

### Post by nortino on 2007-12-08
Recently installed Ubuntu 7.10 on a laptop which has a Realtek RTL8187 WLAN card. The good news is that it often connects. The bad news is that if it doesn't connect initially (i.e. when I first switch the laptop on), it absolutely refuses to connect from then on. The only way I can get it working again when this happens is to change the SSID of the router and then in the nm-applet click on the new ID, enter the WPA password and then it often reconnects, and from then on will be fine, until the next day when I switch it on when it will either connect, or not in which case it again simply will not connect from that point on no matter what I do.
This is obviously quite annoying; I've already wasted a lot of time on this and I don't want to be changing the SSID every time I want to connect.

So, I'm using the RTL8187 driver that comes bundled with Ubuntu (not ndiswrapper). The wireless router is a Belkin 54g. I don't think the problem is the router; my Nintendo Wii can connect to it just fine while Linux is refusing to do so, and once I'm connected it's fine.
ESSID broadcast is ON.
Security settings are WPA / PSK.

In Ubuntu I set up the connection by clicking on the nm-applet, and clicking on my SSID in the list. This opens up a dialog saying that the network requires a password. I set the security type to WPA Personal, enter the password, and most of the time it connects.

When it doesn't connect, I can still see my router when I do "iwlist wlan0 scan", but it just won't connect to it, even though the WPA settings / password haven't changed and it connected on those settings previously.

So basically it seems to me that when it doesn't connect right off the bat, either the driver or something else gets its knickers in a knot and just decides that it's never going to connect to that router again for as long as it lives, which is why I can only get it to connect again by changing the SSID, and therefore giving Linux a 'clean slate' by making it think that it's a brand-new network.

Also, note that it won't reconnect even after I reboot Linux (and restarting the router doesn't make any difference). So is there some config file that gets 'bad' values in it after the first failure to connect? Is there some way of making it have a genuine fresh attempt to connect after the first failure? I tried doing things like "iwconfig wlan0 up" "iwconfig wlan0 down" "/etc/init.d/network restart" and it doesn't help.

Thanks in advance for any help.

---

### Post by nortino on 2007-12-10
Thanks for all the suggestions. I've got a work-around now for this, which is to use Kubuntu instead of Ubuntu. This means that I'm using KNetworkManager by default now, which seems to work a lot better than the frankly horrible nm-applet in Gnome. It helpfully drops the connection exactly once every time I boot the laptop, which is nice, but after that it will reconnect fine and from then on is stable, and I don't have to rename my SSID every time I want to reconnect. Of course, Compiz doesn't work properly now that I'm using KDE, so I've had to uninstall that, but you can't have everything I guess, at least not when you're using Linux.

---

