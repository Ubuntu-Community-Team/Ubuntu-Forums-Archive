---
title: "Ad-Hoc"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by neoviperx on 2008-05-21
I have a Toshiba M700 and I can not get the network manager to create a new wireless network. It tries connecteding to 'null' no matter what ssid I input. I am trying to create a small network between my laptop and my iPhone without having to need a router. I can do it in Vista without any problems. And when I am at my house they connect fine. Any ideas why I can't create a new wireless network from within Ubuntu 8.04?

Thanks

---

### Post by lswb on 2008-05-25
Try this from a terminal. First type iwconfig and look for the interface that says wireless is supported. On my system its eth1, for various other wireless cards I've tried it could be wlan0, ra0, etc. Use whatever is appropriate where I've used eth1 below.

Then,

sudo iwconfig eth1 essid "your-essid" mode "ad-hoc" channel 6

Now type iwconfig eth1 again and see if it reports that it is using these parameters.
If so, you need to get in ip address. With 8.04 avahi is installed by default. If you

sudo dhclient eth1
dhclient will try to get an IP address using dhcp, after it fails, avahi will assign one in the 169.254.xxx.xxx range. Or you could 

sudo avahi-autoipd eth1

to save the time of dhcp timing out.

Now type

ifconfig
or
ip addr 

and see if there is an ip address associated with the wireless address. It should be 169.254.xxx.xxx (the xxx can be any number) If so try to connect from your other computer. 

It took me a while to get this sorted out and I'm going partiall on memory here, so don't be too disappointed it it doesn't work first time. Post your results and let's see what happens.

---

