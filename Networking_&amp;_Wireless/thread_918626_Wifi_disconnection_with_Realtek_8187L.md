---
title: "Wifi disconnection with Realtek 8187L"
date: 2008-09-13
forum: Networking &amp; Wireless
---

### Post by Calimo on 2008-09-13
Hello,

I have an Asus M2N DH motherboard with a Realtek 8187L wifi chipset. It works out-of-the-box in Hardy.
I connect to a DLink G604T router with a dynamic address (DHCP, network name G604T_WIRELESS). The wifi signal is good (usually 50 to 90 %). I'm using the default configuration (NetworkManager and rtl8187 kernel module).

It is working pretty well, except that sometimes I get disconnected. When it happens:[list][*]I cannot even connect the router ([http://192.168.1.1](http://192.168.1.1) in Firefox or any other browser).[*]The NetworkManager applet in the notification area still show a good wifi signal)[/list]Now if I left click on the applet and then on the wifi connecion, I see the throbber with grey dots turning for a while, and then the "no connection" icon displays. I can see the following in my dmesg:```
[ 7293.557756] wlan0: deauthenticate(reason=3)
[ 7317.057836] wlan0: No ProbeResp from current AP 00:0f:3d:97:14:7a - assume out of range
[ 7358.105767] wlan0: Initial auth_alg=0
[ 7358.105775] wlan0: authenticate with AP 00:0f:3d:97:14:7a
[ 7358.303798] wlan0: authenticate with AP 00:0f:3d:97:14:7a
[ 7358.504468] wlan0: authenticate with AP 00:0f:3d:97:14:7a
[ 7358.703157] wlan0: authentication with AP 00:0f:3d:97:14:7a timed out
```


The only way to have the network working again is to change the runlevel with a "sudo telinit 1" and then choose resume (sometimes it is not enough and I need to reboot completely).

I tried to do the following:
```
sudo /etc/init.d/avahi-daemon restart
sudo /etc/init.d/dhcpd restart
sudo /etc/init.d/networking restart
```but this wasn't sufficient.
I also tried with wifi-radar, but it is also unable to connect.

What does the runlevel change, that could allow the network to "restart"? Should I try to do something like reloading the kernel module? If yes, how?

If only I could restart it without stopping all my X apps, I would be very satisfied.
Any hint would be appreciated.

Thanks !
Xavier

---

### Post by Calimo on 2008-09-20
So after much testing it seems that [code]sudo modprobe -r rtl8187
sudo modprobe rtl8187
sudo /etc/init.d/networking restart[/quote]plus waiting a few seconds is sufficient to restart the network.

I could also look at http://rtl-wifi.sourceforge.net/wiki/Main_Page but it seems more complicated (need to reinstall at each kernel update).

---

### Post by Calimo on 2008-09-27
Ok, so for the moment I just created a small restart script :
```
#!/bin/sh

if ! ping -c 1 192.168.1.1 || zenity --question --text="Network already connected and responding\!\nWould you like it to be restarted anyway?" --title='Network connected'
then
	modprobe -r rtl8187
	modprobe rtl8187
	/etc/init.d/networking restart
	zenity --info --text='Network has been restarted.'
	exit 0
else
	zenity --info --text='Nothing has been done.'
	exit 1
fi
```It tries to ping the network. If this fails, the network is restarted with the 3 lines given above.
If the ping succeeds, it ask a confirmation.

Replace 192.168.1.1 with the IP of your router, save it somewhere, for example in ~/bin and create a customized application launcher with the command line "gksudo /path/to/script.sh", and that's it !

Hope it can help someone.

---

### Post by andersja on 2009-06-17
Is this still a problem in Jaunty? If yes, please file a bug with as much information as possible at this address: [https://bugs.launchpad.net/ubuntu/+source/linux]("https://bugs.launchpad.net/ubuntu/+source/linux")

---

