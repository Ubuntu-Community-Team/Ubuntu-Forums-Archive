---
title: "Wireless will not auto-activate on boot"
date: 2005-08-17
forum: Networking &amp; Wireless
---

### Post by numberexhaust on 2005-08-17
Hey guys... I finally got wireless by ditching the Proxim and using a netgear WG511T card instead.  I installed it using ndiswrapper and it works fine, except it won't activate itself on boot (I have to go to networking and activate the device manually).  Is there any way to fix this?

Furthermore, the box kinda stalls on "Configuring network devices" when it's not hardwired.  I've disabled ethernet completely, but this doesn't seem to help.  Any way around this as well?

Thanks guys... I owe so much to this community. :)

---

### Post by ssck on 2005-08-17
[QUOTE=numberexhaust]Hey guys... I finally got wireless by ditching the Proxim and using a netgear WG511T card instead.  I installed it using ndiswrapper and it works fine, except it won't activate itself on boot (I have to go to networking and activate the device manually).  Is there any way to fix this?

Furthermore, the box kinda stalls on "Configuring network devices" when it's not hardwired.  I've disabled ethernet completely, but this doesn't seem to help.  Any way around this as well?

Thanks guys... I owe so much to this community. :)[/QUOTE]

Just add a 'auto wlan0' (where wlan0 is your wireless interface name) into your interfaces file

OR 

if you are using gtkwifi, add the following into your panel

refer to screenshot

---

### Post by numberexhaust on 2005-08-17
wierd... I already had that.  I just installed gtkwifi (to check it out) and tried your method... that doesn't make any difference either.  I haven't gotten a chance to play around with that, though.

Any other ideas?

---

### Post by ssck on 2005-08-18
[QUOTE=numberexhaust]wierd... I already had that.  I just installed gtkwifi (to check it out) and tried your method... that doesn't make any difference either.  I haven't gotten a chance to play around with that, though.

Any other ideas?[/QUOTE]

hmm ... i am not sure.if you already have auto in your interfaces file, it should work.could you paste the output of your interfaces file here ?

---

### Post by numberexhaust on 2005-08-18
Sure... here is /etc/network/interfaces

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

iface wlan0 inet dhcp
wireless-essid any



auto wlan0

What happens is that if I insert the card while its booting, it will take a really long time to get past "Configuring network interfaces", and then once it starts I have to do ifdown and ifup to get it to connect.

What I do is just wait until the comp boots and then insert the card and do an ifup.  If you could help me solve this, it would be great.

---

### Post by ssck on 2005-08-18
[QUOTE=numberexhaust]Sure... here is /etc/network/interfaces



What happens is that if I insert the card while its booting, it will take a really long time to get past "Configuring network interfaces", and then once it starts I have to do ifdown and ifup to get it to connect.

What I do is just wait until the comp boots and then insert the card and do an ifup.  If you could help me solve this, it would be great.[/QUOTE]

everything looks normal .... i am afraid i don't know what else i can propose to you.

can anybody help ?

---

### Post by numberexhaust on 2005-08-18
hmm... well any suggestions would be appreciated.  nothing important's on my comp right now so it wouldn't be a big deal if i screwed it up.

---

### Post by ricesteam on 2005-09-23
Boot up is slow for me also if I don't have my laptop wired to my network...

---

### Post by Topper_H on 2006-02-23
I solved this by adding ndiswrapper at the end of my /etc/modules

Hope it helps

---

### Post by lazychris2000 on 2006-04-26
out of curiousity, why are you using ndiswrapper?  my card worked out of the box with breezy and dapper.  
[http://madwifi.org]("http://madwifi.org")

---

