---
title: "From barebones install getting wireless"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by Julolidine on 2007-04-22
So, I decided fesity gave me a chance to prove to me how much I don't know about linux.  

Anyways, I did a fresh install from the alternative CD, installed the server - then installed enlightenment, gdm, xorg, menu, gnome-core.  

So I pretty much have no applets or anything.  I would like to configure and have my wireless connect automatically if possible.  

I have WPA on the router, and conveniently wpasupplicant is installed.  

Beyond that nm-applet seems to be gone fore feisty.  Is their a replacement?  Or if I can configure it without installing some gui that would be cool too.  

Thanks.....

---

### Post by spd106 on 2007-04-22
You don't need a gui for WPA just use the /etc/network/interfaces file to control wpa_supplicant.

In the interfaces file you need to put the driver and a path to the wpa config file, llike this
```
auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-config /etc/wpa_supplicant/wpa_supplicant.conf

```

Now create wpa_supplicant.conf file using wpa_passphrase. It will look like this
```
~$ cat /etc/wpa_supplicant/wpa_supplicant.conf
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=0
network={
        ssid="your essid"
        scan_ssid=1
        proto=WPA
        key_mgmt=WPA-PSK
        #psk="your passphrase"
        psk=3e24c0cc61ab93e5d0ba23eb2394a2a9b973f7800423296de7138d478eedb7a0
}

```

It should connect automatically on boot. See the wpa link in my sig for more details or check the WPA sticky.

---

### Post by Julolidine on 2007-05-16
After much teeth mashing, I finally got it working correctly.  Surprisingly enough, it was because the last line in the /etc/network/interfaces file 

```
wpa-config /etc/wpa_supplicant/wpa_supplicant.conf
```

if I switched to 


```
wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
```

everything works perfectly.  :confused: 

Furthermore, if I try to invoke wpa_supplicant separately, it complains about my psk, even though it is correct.

---

### Post by spd106 on 2007-05-16
> **Julolidine said:**
> After much teeth mashing, I finally got it working correctly.  Surprisingly enough, it was because the last line in the /etc/network/interfaces file 

```
wpa-config /etc/wpa_supplicant/wpa_supplicant.conf
```

if I switched to 


```
wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
```

everything works perfectly.  :confused: 

Furthermore, if I try to invoke wpa_supplicant separately, it complains about my psk, even though it is correct.

#-o 
I'm so sorry about that, I've no idea where -config came from. I'll try to take more care in future.

I'm not sure about the psk error, I've never seen that before.

---

