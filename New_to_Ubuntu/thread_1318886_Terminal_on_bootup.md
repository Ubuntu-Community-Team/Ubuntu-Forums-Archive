---
title: "Terminal on bootup"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by travmanx on 2009-11-08
I have 9.10, but I doubt that matters. Was workin fine till I restarted cpu. Then, Once the glowing ubuntu logo appears, it goes straight to tty terminal. I login and try startx. Then I get a blackish screen but I have a mouse pointer I can move. Nothing else works.

---

### Post by lubberlick on 2009-11-08
what video card are you using? and what drivers for said card?

---

### Post by xehapo on 2009-11-08
Same here
Mobility RADEON 9200

happened on a fresh install, after a few days and restarts.

---

### Post by travmanx on 2009-11-08
GeForce 8600
I did remove bluetooth, printer and other packages that was useless to me. Do you think I removed something important?

---

### Post by Sealbhach on 2009-11-08
> **travmanx said:**
> GeForce 8600
I did remove bluetooth, printer and other packages that was useless to me. Do you think I removed something important?

That's probably what you did. Simplest thing to try is to login when you get to the terminal screen and do 

```

sudo apt-get install ubuntu-desktop
```

then 

```
sudo /etc/init.d/gdm start
```

.

---

### Post by travmanx on 2009-11-08
> **Sealbhach said:**
> That's probably what you did. Simplest thing to try is to login when you get to the terminal screen and do 

```

sudo apt-get install ubuntu-desktop
```

then 

```
sudo /etc/init.d/gdm start
```

.


When I do update I get a whole bunch of 

W: Failed to fetch * Could not resolve '*'.
W: Some index files failed to download, they have been ignored, or old ones used instead.

Thanks for helping tho.

---

### Post by travmanx on 2009-11-08
Got it fixed...

```
sudo aptitude install ubuntu-desktop
```

Thanks to all who helped. Hope this helps the guy who had trouble as well!

---

### Post by xehapo on 2009-11-13
Yes, this helped me a bit too :)

The problem was:

I have an Ubuntu 9.10 Server (same situation was with 9.10 Studio, also). It was installed without LAMP server, so once I decided to install it. Using:

```
tasksel install lamp-server
```

Then I have met another bug, that Firefox was not parsing PHP files.
I tried:

```
tasksel remove lamp-server
```

and by some reason, this command removed my Gnome desktop environment (But I did not realized the connection, because I rebooted much more later and only then I noticed that).

A bit back to LAMP - 
The real problem with PHP parsing, actually, was in symlinks:
```
ln -s /etc/apache2/mods-available/php5.load ./php5.load
ln -s /etc/apache2/mods-available/php5.conf ./php5.conf
```

NOTE: Restart Firefox after linking!!!

So... I rebooted and got the tty terminal welcome screen.

But, one more problem appeared - my network was also broken! :)
So reinstalling a gnome using apt-get failed.

I started to discover, what the problem with the Ubuntu 9.10 network...

```
dhclient -r
ifconfig eth1 down
iwconfig essid "my_wireless_essid" mode Managed
ifconfig eth1 up
dhclient eth1
```

but got

```
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
```
a few times and:
```
No DHCPOFFERS received
```

that was very surprising, because a day before I just installed this Ubuntu 9.10 Server and have had a success with the same sequence! Immediately after install....

Then I found that, the problem is because of IPv6 has been enabled by some reason (so, right after install it wasn't, but after some change, like LAMP, gdm or something else, IPv6 support suddenly enabled).

So the disabling IPv6 resolved the network problem:

```
sudo gedit /etc/default/grub
```

find the line starting with "GRUB_CMDLINE_LINUX"

in my case it was
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

then I added "ipv6.disable=1" to this and got:

```
GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 quiet splash"
```

After reboot I got the network and installed gnome as describe before, using apt-get :)

Hope this helps somebody

---

