---
title: "Cannot Use WPA in feisty"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by alex77 on 2007-04-20
Hi all,

Just installed feisty today, but am having problems connecting to my router.

My wireless adapter is built into my motherboard (Asus P5W DH Deluxe)

The message I get when using the network manager is :

"The requested wireless network requires security capabilities unsupported by your hardware"

I use WPA-PSK to secure the network, and don't want to downgrade it to WEP.

I'm assuming that its just that the driver is a bit dodgy, because everything works fine under windows. Is there a linux driver available? How would I install it? I'm quite new to this linux thing...

Thanks,

Alex

---

### Post by alex77 on 2007-04-21
Shameless bump

---

### Post by alex77 on 2007-04-22
Ok, bit of an update. I have removed the network manager and installed wicd, however, it gets stuck at the obtaining IP phase until it gives up. I can see the network in wicd, and try to connect, but it gets stuck there.

I have also removed rtl8187 from the blacklist.

I have chosen WPA in the advanced settings and also put in the password.

Anyone have any ideas?

---

### Post by grim1234 on 2007-06-30
I have the same problem. Does anyone know how to get this to work?

---

### Post by bollix47 on 2007-06-30
I also have the Asus P5 deluxe wifi and mine is working so I'll list the changes I made to a clean install.

First, ensure the wpasupplicant is installed.  Check in synaptic or in a terminal type:

```
sudo apt-get install wpasupplicant
```

Edit /etc/network/interfaces

```
sudo gedit /etc/network/interfaces
```

Ensure your wlan0 portion looks like:

```
auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-conf /etc/wpa_supplicant.conf

```


Edit /etc/wpa_supplicant.conf

```
sudo gedit /etc/wpa_supplicant.conf
```

Insert the following into the above file:

```
network={
        ssid="YourEssid"
        proto=WPA
        key_mgmt=WPA-PSK
        psk=Your wpa key
}
```

You could try this with or without Network Manager enabled.

System > Preferences > Sessions

Insert or remove checkmark next to Network Manager.

I've never tried wicd.


Hope this helps.

---

### Post by kevdog on 2007-06-30
Hold on

Before tackling WPA encryption, what driver are you trying to use with your card??
You mentioned rt8187 or something like that???

Can you connect to an unencrypted network???

Can you list the following:

lspci
lshw -C network

You might want to check if the native 8187 driver has wpa capabilities.  Im not sure for certain if it does.  Also on most installs do to a bug, you need to add a hack by typing an extra letter to the essid name -- for example if your router name was big, when you entered the ssid, you would have to use bigx <---not use of extra letter.

---

### Post by grim1234 on 2007-07-01
nice post, works well. thanks.


it's the gnome network manager that doesn't support wpa i think, not the driver.

alhough, i don't this works with x64?

---

### Post by bollix47 on 2007-07-01
I'm using it on x64 with Feisty(Xubuntu) and Gutsy(Ubuntu).  Both working well although the Feisty one does drop it's connection occasionally.  On Gutsy 64 the above works very well without dropped connections.

---

### Post by grim1234 on 2007-07-02
ah, so the driver supports wpa okay?

I wonder why it didn't work for me.... I'll just stick with i386 for now I think (time vs result isn't worth a reinstall right now).

---

### Post by MarkRobert on 2007-07-02
Thanks, that helped me on my Dell Inspiron 6400.

---

