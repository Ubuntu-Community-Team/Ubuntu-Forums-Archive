---
title: "Netgear WG111 and ndiswrapper"
date: 2007-02-03
forum: Networking &amp; Wireless
---

### Post by boudders on 2007-02-03
I am having trouble getting my Netgear WG111 working on Ubuntu 6.10.
I got the windows driver loaded in ndiswrapper, and it detects the hardware. But the light still doesnt turn on. And when I type in:

sudo ndiswrapper -m 

I am greeted with this:
modprobe config already contains alias directive

any ideas?


I have followed this guide to no avail.
[http://ubuntuforums.org/showthread.php?t=51993](http://ubuntuforums.org/showthread.php?t=51993)

---

### Post by boudders on 2007-02-03
So, it works now...I powered down for awhile turned it back on and noticed wifi0 in my network config. Then I just...connected...any explantions?

---

### Post by jml on 2007-02-03
Gremlins.  Seriously, wireless networking is a black art.  I also have found my system magically works after I shut it down and restart.  I don't have an explanation, but if it work.....

Joe

---

### Post by boudders on 2007-02-04
So yippie kiyay was workin. Then I shut down and Ubuntu would freeze during start-up unless I remove the wireless adapter. Then I can put it back in once Ubuntu has launched but then the wireless doesn't work anymore...

I can scan using iwlist wlan0 scan and I can see my access point but I cant connect through Network Manager. No option available even thought I have wireless connection.

I also get this when I type in:
ndiswrapper -m

module configuration contains directive install pci:v000014E4d00004301sv00001737sd00004301bc*sc*i* /sbin/modprobe ndiswrapper
;you should delete thatmodule configuration contains directive install pci:v000014E4d00004301sv*sd*bc*sc*i* /sbin/modprobe ndiswrapper
;you should delete thatmodule configuration contains directive install pci:v000014E4d00004320sv000014E4sd00000417bc*sc*i* /sbin/modprobe ndiswrapper
;you should delete thatmodule configuration contains directive install pci:v000014E4d00004320sv00001737sd00004320bc*sc*i* /sbin/modprobe ndiswrapper
;you should delete thatmodule configuration contains directive install pci:v000014E4d00004320sv*sd*bc*sc*i* /sbin/modprobe ndiswrapper
;you should delete thatmodule configuration contains directive install usb:v0846p4220d*dc*dsc*dp*ic*isc*ip* /sbin/modprobe ndiswrapper
;you should delete thatmodule configuration contains directive install usb:v0846p4240d*dc*dsc*dp*ic*isc*ip* /sbin/modprobe ndiswrapper
;you should delete thatmodprobe config already contains alias directive

---

### Post by willz06jw on 2007-03-04
I found if you remove all of the information in the Network control in administration (remove Network Name, password, etc) that NetworkManager then tries to manage it for you.  I don't know if this helped ya especially since you wrote this 3 weeks ago.

---

