---
title: "[SIMPLE] How To authenticate 802.1x over a WIRED network [Including install script]"
date: 2008-02-27
forum: Networking &amp; Wireless
---

### Post by banjo man on 2008-02-27
[COLOR="Red"]_EDIT:_8.04 Hardy heron will make this method obsolete.[/COLOR]

There are many methods out there for this, but I think mine is the easiest. (Just my opinion)

open a terminal (Applications > Accessories > Terminal)

type:

```
sudo gedit wired.conf
```

this will open up a text editor, then put this in it

```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=root
ap_scan=0
network={
key_mgmt=IEEE8021X
eap=PEAP
identity="[COLOR="Red"]THIS IS WHERE YOU WILL PUT YOUR USERNAME[/COLOR]"
password="[COLOR="#ff0000"]THIS IS WHERE YOU WILL PUT YOUR PASSWORD[/COLOR]"
phase1="peaplabel=0"
phase2="auth=MSCHAPV2"
}
```

where it says identity and password, that is where you put them...no spaces, and include the ""

then, save it and close...

then, back in the terminal, type:

```
sudo chown root:root wired.conf
```

and

```
sudo chmod 600 wired.conf
```

next, in the terminal, type

```
sudo gedit script1
```

this will again open a blank text editor, in it type

```
wpa_supplicant -Dwired -B -i eth0 -c wired.conf
dhclient eth0 -nw
```

if you have an unusual setup, make sure your ethernet port is indeicated in place of "eth0", otherwise, that should be good

then save it and close...

next, enter this in the terminal:

```
sudo chmod a+x script1
```

now, to initialize, in a terminal type:

```
sudo ./script1
```

and you should be good...

if you want a shortcut, you can place one in the upper panel thinger, or on the desktop...



I have created a script that does this all automatically, I will put it up here if anyone wants it...

---

