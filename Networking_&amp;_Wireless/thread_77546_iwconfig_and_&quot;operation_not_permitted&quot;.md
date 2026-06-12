---
title: "iwconfig and &quot;operation not permitted&quot;"
date: 2005-10-17
forum: Networking &amp; Wireless
---

### Post by jadepenguin on 2005-10-17
I am new to Linux and knew it would be a challenge to get my wireless card working, but I was determined to do so. I used the forums here which were great, then proceeded to manually plug in the cable and download ndiswrapper from Synaptic Package Manager and the graphical frontend utility from it. I then downloaded the drivers for my card (Linksys WPC54G). I installed the ".inf" file using the graphical frontend (Windows Wireless Drivers), and it detected the hardware and wlan0 appeared! To my dismay, I still couldn't connect to my wireless network.

I went into the terminal and typed in "iwconfig" and saw wlan0. I then tried to type "iwconfig wlan0 essid my_network_name" and I get an error:

"Error for wireless request "Set ESSID" (8B1A) :
     SET failed on device wlan0 ; Operation not permitted."

I'm not sure if this has to do with my security level (I was logged in as the user you make during install). I tried to login as root (I changed the password via the users menu), but from the default login screen I can't login as root for some reason.

If anyone could help me some directions on how to login as root, or what else to do to change my essid, or maybe something else, it would be very much appreciated.

Thanks a bunch!

---

### Post by Swab on 2005-10-17
see below :)

---

### Post by Manny C on 2005-10-17
Issue same command as superuser:
```
 sudo iwconfig wlan0 essid FOO 
```
where FOO is the name of ur network.

---

### Post by Swab on 2005-10-17
Login as normal user.... then try "sudo iwconfig wlan0 essid my_network_name" it will ask for your user password.

---

### Post by jadepenguin on 2005-10-17
Thanks for the speedy reply. I typed in:

sudo iwconfig wlan0 essid network_name

It prompted me for a password, I typed it in, but when I went to iwconfig it didn't show the ESSID as being set/saved. Instead it still says ESSID: off/any. Is there something I have to do to apply the changes? Sorry for being a bother, but I'm really new to this and don't get why it's not saving the commands I put in.

---

### Post by cbudden on 2005-10-17
Why not use the graphical interface ( system-> admin -> networking) ?

---

### Post by knappen on 2005-10-17
I had to manually add my wep and essid to the interfaces file. The graphical way did not work at all. Everything was lost when rebooted.

---

### Post by Quirky on 2005-10-17
For example in /etc/network/interfaces:

```

auto ra0
# this works for WEP.
iface ra0 inet dhcp
        wireless-essid XXXXX
        wireless-key restricted 3648ebfc2c4524eb6950b6408fa9

```

I haven't tried muliple keys, but in theory adding wireless-key2 should also work. For WPA it *should* be something like this:

```

auto ra0
iface ra0 inet dhcp
        wireless-essid XXXXX
        wireless-mode managed
        wireless-encryption on
        pre-up iwpriv ra0 set AuthMode=WPAPSK
        pre-up iwpriv ra0 set EncrypType=TKIP
        pre-up iwpriv ra0 set WPAPSK="MyPass"

```

But that doesn't seem to work for me here.

---

