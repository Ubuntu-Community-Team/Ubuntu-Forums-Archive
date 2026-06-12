---
title: "Wifi Help Needed pls."
date: 2007-10-16
forum: Networking &amp; Wireless
---

### Post by distortedecho on 2007-10-16
Hi,

I've tried to follow the HowTo: 

[http://ubuntuforums.org/showthread.php?t=26623](http://ubuntuforums.org/showthread.php?t=26623)

But no luck :(

I'm using a Cisco Aironet 350 series wireless card.

I think I'm falling over at this part:

> 6) Add the following lines in the part regarding your wireless card, as in the example below:
```


pre-up wpa_supplicant -Bw -Dwext -ieth0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```

Note: "eth0" is your wireless device and "wext" is the driver; this is a kind of generic driver, so it should work with most wireless cards. If it doesn't, please try another driver, such as hostap, ndiswrapper, etc.
Here is an example:
```


iface eth0 inet static
address 192.168.1.15
netmask 255.255.255.0
wireless-essid my_essid
gateway 192.168.1.1
pre-up wpa_supplicant -Bw -Dwext -ieth0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```

7) Now run wpa_supplicant:
```


sudo wpa_supplicant -Bw -Dwext -i eth0 -c/etc/wpa_supplicant.conf
```

You should be online!

I don't quite see how part 6 ties in with the example. In my "Interfaces", I don't have the IP details. 
Should i?

Please help, I would like to use my laptop on ubuntu wirelessly.

---

### Post by Lambert on 2007-10-17
That section is an example using a static ip address. If you use dhcp to retrieve your ip address and other network information then it should look like this.

iface eth0 inet dhcp
pre-up wpa_supplicant -Bw -Dwext -ieth0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant

---

### Post by distortedecho on 2007-10-18
Yes, 

That's what I had. But I still couldn't get online?

I would have expecting an interface version by now though, considering how popular wireless is?
Surely it's must going forward for Ubuntu?

---

### Post by distortedecho on 2007-10-19
Bumping for help, please!

---

### Post by distortedecho on 2007-10-19
I've tried to follow a tutorial over at Debianadmin, that many people were having success with.

However, I've done a restart,and now the desktop doesn't load. Just Orange and the top left of the screen is grey.

Anyone got a clue?

Linux or Ubuntu will never win the Windows users if they can't provide an easier, graphical way of doing things.

---

### Post by distortedecho on 2007-10-20
Up.

---

