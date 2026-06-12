---
title: "Please help me get networking to autostart"
date: 2007-03-18
forum: Networking &amp; Wireless
---

### Post by toddhd on 2007-03-18
After much trial and trepidation, I finally got my wireless network running using WPA-PSK under Ubuntu 6.10. All is well and good except for one thing - the network does not start itself when Ubuntu starts. Instead, I have to open a terminal and start it by hand:

```
sudo /etc/init.d/networking restart
```

Can anyone assist me in getting the network to autostart on boot?

---

### Post by chili555 on 2007-03-18
Please see post #2 here: [http://www.ubuntuforums.org/showthread.php?t=387421](http://www.ubuntuforums.org/showthread.php?t=387421)

Substitute your wireless interface, eth1, wlan0, ra0, etc. as needed.

---

### Post by toddhd on 2007-03-18
Thanks Chili. I do have my interfaces file setup as described, but that doesn't seem to make a difference. Here is my entire interfaces file:

```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid SeaburyDesign
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk <hidden>
```

---

### Post by toddhd on 2007-03-21
I'm just *bump*ing this because I'm still unable to get it working right. I had the bright idea of trying to add the restart command to my gnome-sessions, but that doesn't seem to be working correctly for reason. 

Someone else reccomended I try Wicd. Just like network-manager and Wifi-radar, Wicd goes through the whole process of trying to connect, and never does. The only thing that seems to work consistently is running the restart command from the terminal. 

There MUST be a way to automate this during startup! I'm so confused... please help!
:confused: :confused: :confused:

---

### Post by eSinner on 2007-03-23
I am having the same issue.

Wont load at startup, but will at the command line with restart.

Has anyone got a fix for this?

What's most annoying is that you would assume that at boot the init sequence is using the "start" function (as the interface is coming up for the first time), and therefore I'd expect the same "start" function to fail once the service is "stopped". But no. I can restart, then stop, then start, and every subsequent try works, just not at boot.

Any help would be appreciated :)

---

### Post by eSinner on 2007-03-24
KNetworkManager to the rescue!

Damn thing wouldn't work while I was trying to use wpa_supplicant and config through /etc/network/interfaces

Instead I had to go into /etc/network/interfaces and comment out all network interfaces other than "lo" (the loopback device). After doing this I ran a...

"sudo apt-get install network-manager-kde" and fired it up. At this stage it still didn't work...however this was because I hadn't rebooted yet

After leaving Knetworkmanager running on logout KDE saves it in your configuration to automatically restart for future logins, so after I rebooted, with /etc/network/interfaces now **not** trying to bring the interface up, it freed the device for Knetwork manager to connect without issue.

I can't see a reason why anyone using a GUI would use anything other that NetworkManager (in either gnome or kde) to setup their WPA wireless. It's simple!

---

### Post by eSinner on 2007-04-03
Being the perfectionist that I am, and seeing as though knetworkmanager didn't always autoconnect due to it sometimes not starting with KDE, I went back to figure out how to get wpa_supplicant & /etc/init.d/networking to autostart.

In the end the issue came down to IPv6. See here for how to disable:

[https://help.ubuntu.com/community/We...ngSlowIPv6IPv4]("https://help.ubuntu.com/community/We...ngSlowIPv6IPv4")

After that my interfaces and wpa_supplicant.conf settings worked no worries. No delays at boot, IP assigned by DHCP, bingo, we're up and running! :)

---

