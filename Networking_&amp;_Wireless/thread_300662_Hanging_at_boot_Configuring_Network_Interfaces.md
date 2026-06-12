---
title: "Hanging at boot: Configuring Network Interfaces"
date: 2006-11-16
forum: Networking &amp; Wireless
---

### Post by goanna on 2006-11-16
Can anyone please help me?  I had installed Ubuntu 6.06 LTS on a Celeron desktop with a D-link wireless card and it was working fine. 

I had even rebooted it before and had everything working fine. However, a recent reboot hung at: Configuring Network Interfaces.

I have checked the forums and I have tried the following:

1. changing /etc/dhcp3/dhclient.conf so the timeout is set to 20
2. unlocking /etc/resolv.conf (using chattr -i )
3. commenting out auto eth0 in /etc/network/interfaces (still hangs)
4. Pressing ctrl-c - this skips ahead, but Xwindows hangs after 
  I log in.
5. Commenting out all ethX entries in /etc/network/interfaces
    but again, Xwindows does not work properly.

As things stand, even if I cntl-c, log in, get out of X-windows and type ifconfig - it just hangs.  If I reboot, it hangs on shutdown at "Deconfiguring Network Interfaces". 

The only thing that even remotely worked (at least it let me use Xwindows) was when I had eth0 in the /etc/network/interfaces accidentally twice.  This time "Configuring Network Interfaces" failed on boot, but skipped ahead and I could use X-windows correctly, but I had no networking still.

I am considering trying:
  update-rc.d networking remove
  update-rc.d networking defaults 99
However, I noticed a post from someone else saying that he did that and now DHCP does not work at all.

I could reinstall (not that desirable) but my big concern is that
the problem will just re-occur again later.  

Any help would be appreciated at this point, even if it is just to prevent this problem after reinstalling.

---

### Post by dmizer on 2006-11-16
post the entire contents of your /etc/network/interfaces file.

---

### Post by goanna on 2006-11-16
> **dmizer said:**
> post the entire contents of your /etc/network/interfaces file.


Ok. Thanks for your interest. While there were messages when I plugged in my USB (I am using my dual boot windows to send this) I could not find the normal entries in /mnt for cdrom and removable (or am I mistaken and looking in the wrong place?)

So I will type it in and attempt to avoid errors:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan
iface wlan inet dhcp

iface ra0 inet dhcp
wireless-essid default

auto ra0

```

Thats it.

---

### Post by dmizer on 2006-11-16
i assume you've confirmed that ra0 is your wireless adapter?  if so, make a backup of the file:
```
sudo cp /etc/network/interfaces /etc/network/interfaces_old
```
and delete all entries except for the lo and ra0.  modify ra0 so it looks like this:
```
auto ra0
iface ra0 inet dhcp
        wireless-mode managed
        wireless-essid default
```
and see if it still hangs.

---

### Post by goanna on 2006-11-17
Thank you kind person.  Everything now works perfectly.

---

### Post by dmizer on 2006-11-17
that's fantastic!  glad i could help.

---

### Post by oliwally on 2006-11-22
> **dmizer said:**
> i assume you've confirmed that ra0 is your wireless adapter?  if so, make a backup of the file:
```
sudo cp /etc/network/interfaces /etc/network/interfaces_old
```
and delete all entries except for the lo and ra0.  modify ra0 so it looks like this:
```
auto ra0
iface ra0 inet dhcp
        wireless-mode managed
        wireless-essid default
```
and see if it still hangs.

Thank you so much !!!
After much searching this has worked perfectly on my Dell D820. Booting is now quite fast and everything appears to work.
Only difference was that on the Dell the wireless adapter was wlan0. So my interfaces file now looks like this:

```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
        wireless-mode managed
        wireless-essid default
```

---

