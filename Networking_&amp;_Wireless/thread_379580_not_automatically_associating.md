---
title: "not automatically associating"
date: 2007-03-08
forum: Networking &amp; Wireless
---

### Post by &amp;)ky#)^ on 2007-03-08
I have a problem that should be simple to solve.  I just don't know how to fix it.  :) 

It seems like it started out of nowhere a few weeks ago.  My wireless connection wouldn't be active on boot.  I just discovered why... sort of.  A quick check of iwconfig ath0 shows that the essid field is correct, but the card hasn't associated with my WAP.  What gives?  Why doesn't it automatically associate on boot?

Here's a copy of my interfaces file if it helps.

```
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.5.110
netmask 255.255.255.0

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp


iface ath0 inet dhcp
wireless-essid MN-500

auto wlan0
iface wlan0 inet dhcp






auto ath0

auto eth0
```

---

### Post by chili555 on 2007-03-08
I would try two things; first, because I'm a bit of a neat freak, I'd sudo gedit /etc/network/interfaces and move auto ath0 up above the other ath0 stuff like this: ```
auto ath0
iface ath0 inet dhcp
wireless-essid MN-500
```

Next, I suggest sudo iwlist ath0 scan and see if the ESSID is correct in every respect. Mn-500 will not connect to MN-500. Amend interfaces as necessary and restart networking sudo /etc/init.d/networking restart

Let us know.

---

### Post by Floppyjoe on 2007-03-08
If you don't use Network-Manager then you might benefit from the addition of a few lines to ath0 in your /etc/networking/interfaces file like the following:
```
wireless-channel 7
wireless-mode managed
```
where you use the channel of your router instead of the one listed.

---

### Post by &amp;)ky#)^ on 2007-03-08
I cleaned up the file and tried your suggestions, but it's still the same.
```

auto lo
iface lo inet loopback

auto ath0
iface ath0 inet dhcp
wireless-essid MN-500
wireless-channel 9
wireless-mode managed

```

---

### Post by Floppyjoe on 2007-03-08
Do you use encryption on your wifi? If yes you will need to enter the key in the /etc/network/interfaces file or through the netwoking gui in System/Administration/Networking.

---

### Post by &amp;)ky#)^ on 2007-03-09
No, I don't use encryption.

---

### Post by matthewartz on 2007-03-09
Don't know what your card is, but I had the same problem with a Broadcom 4318.  Final resolution turned out be adding "noapic" to the boot record and rebooting - suddenly it'll associate.

Check out [post 12]("http://www.ubuntuforums.org/showpost.php?p=2271667&postcount=12") for instructions on trying it once (via boot manager) and permanently by editing menu.lst.

---

