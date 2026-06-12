---
title: "Perfect wireless, no trouble - until Reboot !"
date: 2008-03-31
forum: Networking &amp; Wireless
---

### Post by PaulHeywood on 2008-03-31
Hi there,

Using Network Settings (on xubuntu 7.10) I can easily configure up my ssid etc. and after it has reported "Changing interface settings" my wireless works well.  I can also save these settings to a particular location - "home" for example.

All is well until I restart - Network Settings have been defaulted back - my "Home" location is still avaliable and if I select this location and click the green tick (apply this location's settings) button then everything is well again... until restart.

I've had a good old search both on here and other forums - and they're is some talk about a bug in Network Settings, but all the posts are rather old,

Anyone have any suggestions ?  I have tried nm-applet and even wcid but none seem as good as the 'working' network manager settings,

Cheers,

Paul.

---

### Post by dmizer on 2008-03-31
sometimes nm-applet and other wireless config settings supersede the network configuration provided by default.  if you still have wcid installed, i suggest removing it.

also follow the steps here (under "Disabling NetworkManager") for disabling nm-applet:
[https://help.ubuntu.com/community/WifiDocs/NetworkManager?#head-1de145d05f957ff659f5fdb58974ec3e5864def5](https://help.ubuntu.com/community/WifiDocs/NetworkManager?#head-1de145d05f957ff659f5fdb58974ec3e5864def5)

reboot and see if that fixes you.

---

### Post by PaulHeywood on 2008-03-31
Thanks dmizer - I'll try that - nm-applet is still installed and comes up on boot, I'll get rid of it and see if wicd is still about.

---

### Post by PaulHeywood on 2008-03-31
Uninstalled nm-applet - but I've had another look at the Network Settings again - the only item it's losing is the password - the ESSID, Configuration etc. is all the same... What has changed is the Network Password, which seems to have far too many chars for my password.

Any ideas  ?

---

### Post by dmizer on 2008-03-31
that is by design, so someone looking over your shoulder cannot tell how many characters are in your password.

please post the contents of (you may want to edit out your password from this file before you post it):
```
/etc/network/interfaces
```

---

### Post by PaulHeywood on 2008-04-01
Thanks again Dmizer - I've learnt a little more, it's not that the config is changing, it's almost as if the Network is not being brought up.  The only thing I have to do post-restart to bring it up is restart networking with  sudo /etc/init.d/networking restart.

Here's the interfaces file -

```
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth1

iface eth1 inet dhcp
wpa-psk xxxxx
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid SKYXXXX

auto eth0
```

I've saved the interfaces file and then diffed it following restart and it is unchanged.

---

### Post by dmizer on 2008-04-01
did you disable NetworkManager according to the link i posted earlier in my first reply?  if not, do so.

if you have followed those directions and are still having problems, your situation is extremely unusual.  are you sure you have not installed any other network managment software?

---

### Post by PaulHeywood on 2008-04-01
Yep - that's disabled, there's a clue (maybe) in /var/log/messages -

At boot -

Apr  1 09:07:55 paul-laptop kernel: [   28.612000] ADDRCONF(NETDEV_UP): eth1: link is not ready

At when I restart networking -

Apr  1 09:09:10 paul-laptop kernel: [  103.240000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr  1 09:09:10 paul-laptop kernel: [  103.488000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready

Does this help ?

---

### Post by dmizer on 2008-04-01
yup.

just add:
```
/etc/init.d/networking restart
```

in front of "exit 0", in the file /etc/rc.local like so (you'll have to edit as sudo):
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

/etc/init.d/networking restart
exit 0
```

---

### Post by PaulHeywood on 2008-04-01
Already tried that !  Though I didn't take a look at the messages log after I tried it.

Just tried it again with a sleep 20 above it - and it's done the trick, I'll whittle down the time... not sure if I've changed anything else since I last tried it - maybe I won't need the sleep.

Thanks for your help dmizer

---

### Post by dmizer on 2008-04-01
is this a usb adapter?  strange that you have to put so much time before the device can activate.

if you bypass the gdm login (ctrl + alt + f2), is the device active then?  check ifconfig, and ping google.com

---

### Post by PaulHeywood on 2008-04-01
Nope, integrated wireless -  it's a HP Pavillion dv1000 laptop.

But I've removed the delay now and all is well.

Thanks for your help.

Paul.

---

