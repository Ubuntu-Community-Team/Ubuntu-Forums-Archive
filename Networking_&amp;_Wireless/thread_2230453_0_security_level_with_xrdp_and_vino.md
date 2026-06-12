---
title: "0 security level with xrdp and vino"
date: 2014-06-19
forum: Networking &amp; Wireless
---

### Post by Only1KW on 2014-06-19
I am attempting to connect to my Ubuntu 14.04 installation from Windows using Remote Desktop Connection.  I have installed xrdp and configured vino (Allow other users to control your desktop, not to confirm each access to this machine, and to Require the user to enter this password).  

My xrdp.ini is the following:

```
[globals]
bitmap_cache=yes
bitmap_compression=yes
port=3389
crypt_level=High
channel_code=1
max_bpp=24
#black=000000
#grey=d6d3ce
#dark_grey=808080
#blue=08246b
#dark_blue=08246b
#white=ffffff
#red=ff0000
#green=00ff00
#background=626c72


[xrdp1]
name=Desktop
lib=libvnc.so
username=
password=ask
ip=127.0.0.1
port=5900


```

When I try to connect from Windows using the Desktop option, I get the following output:

```
started connecting
connecting to 127.0.0.1 5900
tcp connected
security level is 0 (1 = none, 2 = standard)
error - problem connecting
```

What is security level 0 and how do I correct it?  Google search finds no helpful pages for this security level.

---

### Post by wrighrc on 2014-07-23
[FONT=Arial][B]You need to run 
gsettings set org.gnome.Vino require-encryption false
and reboot.

[/B][/FONT]

---

