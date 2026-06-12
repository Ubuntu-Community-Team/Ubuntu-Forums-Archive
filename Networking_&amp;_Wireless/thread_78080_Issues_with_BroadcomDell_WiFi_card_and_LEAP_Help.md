---
title: "Issues with Broadcom/Dell WiFi card and LEAP: Help"
date: 2005-10-17
forum: Networking &amp; Wireless
---

### Post by FocusDriver on 2005-10-17
Apologies for yet another WiFi issues thread, but I couldn't find anything on my problem in repeated searches of the board and Wiki. 

I have 5.10 installed on a Dell Inspiron 5150. According to Dell's online configurator thing, it has a Dell Truemobile 1350 b/g internal wireless card. From previous experience with Fedora, I know this takes the bcmwl5a.inf driver, and have installed that with ndiswrapper. It worked fine on that with a WEP-secured network at home, but now i'd like to get it working under Ubuntu here at school. I think ndiswrapper is working correctly: the card shows up under System > Administration > Networking, and picks up the network that i'm trying to connect to. 

Using the [WPA Howto](https://wiki.ubuntu.com/WPAHowto) in the wiki, I configured wpa_supplicant. There weren't many examples in the wpa_supplicant documentation, the wiki, or the internet at-large about how to make one for LEAP, so i'm not entirely sure if it's right. As of now, it looks like this:
```

# Minimal /etc/wpa_supplicant.conf to associate with open
#  access points. Please see
#  /usr/share/doc/wpasupplicant/wpa_supplicant.conf.gz for more complete
#  configuration parameters.

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=1

### Associate with any open access point
###  Scans/ESSID changes can be done with wpa_cli
network={
        ssid="ssid"
        key_mgmt=IEEE8021X
        eap=LEAP
        identity="username"
        password="password"
        key_mgmt=NONE
}



```
SSID, username, and password are of course switched with actual information. So, question the first: Am I missing something here?

Next: When I attempt to do the "Testing wpa_supplicant" step in the above wiki, using the command sudo wpa_supplicant -i wlan0 -c /etc/wpa_supplicant.conf , I recieve the following error(s):

```

ioctl[SIOCSIWPMKSA]: No such device
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: No such device
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: No such device
ioctl[PRISM2_IOCTL_HOSTAPD]: No such device
Failed to set encryption.
ioctl[PRISM2_IOCTL_HOSTAPD]: No such device
Failed to set encryption.
ioctl[PRISM2_IOCTL_HOSTAPD]: No such device
Failed to set encryption.
ioctl[PRISM2_IOCTL_HOSTAPD]: No such device
Failed to set encryption.
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: No such device
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: No such device

```

If I attempt the same command again, I get this:

```
ioctl[SIOCSIWPMKSA]: No such device
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: No such device
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: No such device
ioctl[PRISM2_IOCTL_HOSTAPD]: No such device
Failed to set encryption.
ioctl[PRISM2_IOCTL_HOSTAPD]: No such device
Failed to set encryption.
ioctl[PRISM2_IOCTL_HOSTAPD]: No such device
Failed to set encryption.
ioctl[PRISM2_IOCTL_HOSTAPD]: No such device
Failed to set encryption.
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: No such device
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: No such device
bind(PF_UNIX): Address already in use
ctrl_iface exists and seems to be in use - cannot override it
Delete '/var/run/wpa_supplicant/wlan0' manually if it is not used anymore
Failed to initialize control interface '/var/run/wpa_supplicant'.
You may have another wpa_supplicant process already running or the file was
left by an unclean termination of wpa_supplicant in which case you will need
to manually remove this file before starting wpa_supplicant again.
ioctl[PRISM2_IOCTL_HOSTAPD]: No such device
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: No such device
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: No such device
Failed to disable WPA in the driver.
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: No such device
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: No such device

```

Note that my command omits the -D ipw command, as my card isn't (to my knowledge) using that driver. If you need to have that, what driver should I reference? What could the error mean?

Finally: An observation. Under Windows, the wireless card requires a software supplicant to work with the LEAP network. The school's documentation is vague and contradictory at points, but from what I can tell, cards that aren't Cisco Aironet 350 or Apple Airport require this software program to successfully connect. The program, Aegis, is only provided for Windows 98/2000/xp, which doesn't help me much. Additionally, the wpa_supplicant site says that support for LEAP is contigent on some special support from the driver. If my card needs this to work under Windows, does it need something similar (but not wpa_supplicant or ndiswrapper) to work under Linux? 

Any ideas? I'm a linux/unix n00b, so if i've left something pertinent out, please let me know. 

Thanks in advance.

---

### Post by armond on 2006-05-05
Hey,
This issue  is also popping up on a dell 8500 with an airlink card.   Ever get anywhere with it?

---

