---
title: "Re-enabling wireless"
date: 2007-09-20
forum: Networking &amp; Wireless
---

### Post by Sogtulakk on 2007-09-20
Hi,
I've got a problem with my wireless network. Everithing was working fine until I clicked on "Enable Wireless" in the NetworkManager applet, disabling it. The problem is that now there is no way to re-enable it. The "Enable wireless" button is gone and when I reboot, I have to do "modprobe ndiswrapper" in order to get it working again. Is there any way to get things back to normal, that is, not having to do a modprobe every time I start Ubuntu?

Thanks.

---

### Post by bgr on 2007-09-20
It seems that a few of us have had the same problem. I am sure there is a simple solution though it seems nobody with the info is interested enough to let us in on the know.. stuck in noobville.....

---

### Post by hasimir44 on 2007-12-02
OK, someone please post a fix for this.. I disabled my wireless networking at an airport so I could use my laptop on the plane (to follow the regulation of no enabled wifi during a flight) and now I can't re-enable it.  In the meantime, here's how I'm connecting:

First I get a lis tof all available access points (my wireless NIC is eth1):
```
iwlist eth1 scanning
```

I find the essid of an AP that shows:
```
Encryption key:off
```

Example: 
```
arymcdo@labtop:~> iwlist eth1 scanning
eth1      Scan completed :
          Cell 01 - Address: 00:1A:70:F8:D5:27
                    ESSID:"linksys"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=83/100  Signal level=-51 dBm  Noise level=-51 dBm
                    Extra: Last beacon: 76ms ago

```

Then I set the essid for my NIC:

```
 sudo iwconfig eth1 essid "linksys"
```

Then I grab an IP address:

```
sudo dhclient eth1
```

It works, but it was much easier to click a couple of times on the nm-applet.  I don't understand why you'd be able to "disable wireless" so easily and not be able to re-enable it.  I've found nothing in /etc, and no man pages.  The website listed in the about link of NetworkManager is nothing more than an add:   [http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)

I'm sure that there is an easy fix for this, please help!

---

### Post by hasimir44 on 2007-12-03
Has this happened to anyone else?  What's up? how do we re-enable wireless access in NetworkManager?  This seems pretty important.  I've seen talk of "is linux ready for the mainstream?" and all I can say is that I would never expect my parents/grandparents to figure out iwlist/iwconfig because they wanted to use their laptop on a plane. 

Anybody out there?

---

### Post by kevdog on 2007-12-03
Yes

At the terminal type 

echo ndiswrapper | sudo tee -a /etc/modules

This will force the wireless ndiswrapper kernel module to be loaded at boot so you dont have to type modprobe ndiswrapper

---

### Post by hasimir44 on 2007-12-14
thanks kevdog - I was starting to doubt my own existence :)

It didn't exactly work though - there was no problems with the modprobe or adding ndiswrapper to the list of modules to load at boot time, it's just that NetworkManager is still not showing any wireless configurations.. 

I actually got very tired of this problem, so I wrote a little ruby script that compares the quality of all APs in my range with encryption turned off. Then it just requests an IP from the best one. I'll paste it here in case anyone is interested. I use dhcp3-client, so either install that or replace the dhclient line.

```
#!/usr/bin/ruby

nic = "eth1"

aps = Hash.new
essid = nil
`sudo iwlist #{nic} scan`.each do |line|
  if line =~ /ESSID:(.*)/
    essid = $1
  elsif line =~ /Encryption\skey:(.*)/
    encryption = $1
    essid = nil if encryption == 'on'
  elsif line =~ /Quality=(\d+)\/100/
    quality = $1.to_i
    aps[essid] = quality if essid
  end
end

best = ""
last = 0
aps.each_pair do |essid,quality|
  best = essid if quality > last
end

system("sudo iwconfig #{nic} essid #{best}")
system("sudo dhclient #{nic}")

```

---

