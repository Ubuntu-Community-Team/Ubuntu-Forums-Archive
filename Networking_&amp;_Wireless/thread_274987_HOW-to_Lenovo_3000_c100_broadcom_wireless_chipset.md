---
title: "HOW-to Lenovo 3000 c100 broadcom wireless chipset"
date: 2006-10-10
forum: Networking &amp; Wireless
---

### Post by Gargamella on 2006-10-10
i finally set up the wireless broadcom wireless chipset on a lenovo 3000 c100

what i did wrong before it worked was using ndiswrapper and then fwcutter with the wrong windows drivers

so i reccomend people using this laptop not to use ndiswrapper or to put it in the blacklist by doing in a terminal:

sudo gedit /etc/modprobe.d/blacklist

and writing in the last line "blacklist ndiswrapper"

then just download and install bmc43xx-fwcutter with synaptic

then download on the desktop also this firmware "wl_apsta.o" from this link

[http://drinus.net/airport/wl_apsta.o](http://drinus.net/airport/wl_apsta.o)

after that move it to /lib/firmware by writing in terminal

sudo mv /home/YOURNAME/Desktop/wl_apsta.o /lib/firmware/


so now we can set the driver by writing in terminal

sudo bcm43xx-fwcutter -w /lib/firmware/wl_aspta.o

then also

sudo modprobe bcm43xx

now reboot

after this i was able to choose wireless networks and to set connections with pppoeconf

if you have problems due by eth1 instead of wlan0 look this 
[http://ubuntuforums.org/showthread.php?t=259355](http://ubuntuforums.org/showthread.php?t=259355)

bye

---

### Post by itsjustasensation on 2006-12-29
Slight typo in the above post

bmc43xx-fwcutter should read bcm43xx-fwcutter

Which, if u might notice is type correctly the second time in the post. Which I didn't. I call it supermarket-blindness (can see wot ur looking for even tho its right in front of u)


About to try this n see if I can get Wireless to work on my Lenovo 3000 C100



Adam

---

### Post by darrenm on 2007-01-30
Thanks, worked on my new 3000 C100.

Apart from I had to type the fwcutter command differently

```
darrenm@darrenm-laptop:~$ sudo bcm43xx-fwcutter /lib/firmware/wl_apsta.o /lib/firmware/2.6.17-10-generic/
```

Then install NetworkManager

---

