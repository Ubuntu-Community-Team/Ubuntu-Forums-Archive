---
title: "Feisty,wpa_supplicant, Asus Z92"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by JC Denton on 2007-04-24
Ok, I'm having some troubles getting my Ubuntu laptop on the wireless network available to me.

I have installed wireless drivers but they don't seem to be necessary. After installation whenever ndisgtk is run it crashes with the output:
 'NoneType' object has no attribute 'group'

I have installed various inf files found on the cd, also two hidden in 2 cab files. 

ndiswrapper -l
net5211 : driver installed
wl-103 : invalid driver!


iwconfig produces:

```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

This would lead me to believe it detects it fine. 

to get on the network I need wpa_supplicant. my configuration file looks like this:

/etc/wpa_supplicant/<network>.conf

```

ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
        ssid="<network name>"
        scan_ssid=1
        proto=WPA RSN
        key_mgmt=IEEE8021X
        eap=TTLS
        identity="<mylogingname>"
        password="<pw>"
        phase2="auth=PAP"
}

```

So to get on the network I run:
sudo  wpa_supplicant -ieth1 -c/etc/wpa_supplicant/<networkname>.conf
The output is:

```

SIOCSIFFLAGS: No such file or directory
Could not set interface 'eth1' UP
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: Invalid argument
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: Invalid argument
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: Invalid argument
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: Invalid argument
l2_packet_receive - recvfrom: Network is down
ioctl[SIOCSIWSCAN]: No such device
Failed to initiate AP scan.
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to initiate AP scan.

```

Thank you for your help.

---

### Post by bruno.vitorino on 2007-04-28
Hi, i have the same problem to, on an Asus A6VA.

---

### Post by JC Denton on 2007-05-07
The assistance offered in this thread solved my problem:
[http://ubuntuforums.org/showthread.php?p=2541805&posted=1#post2541805](http://ubuntuforums.org/showthread.php?p=2541805&posted=1#post2541805)

Best of luck

---

