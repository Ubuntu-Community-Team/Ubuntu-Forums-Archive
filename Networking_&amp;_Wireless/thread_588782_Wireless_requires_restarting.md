---
title: "Wireless requires restarting"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by McHenry on 2007-10-23
I have a dual boot machine.

Under XP the wirless works well with no dropouts and sits at 90% signal etc.

Under Gutsy I have no wireless until I restart networking and then it works.

I have read that this can be caused by a conflict with Network Manager so I have removed NM to eliminate any possible conflict:

[http://ubuntuforums.org/showthread.php?t=164864](http://ubuntuforums.org/showthread.php?t=164864)
sudo apt-get remove network-manager-gnome network-manager


My interfaces file is as follows:

maint@PC:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
        wireless-mode managed
        wireless-channel 1
        wireless-essid XXXXXX
maint@PC:~$ 

Can someone enlighten me as to how I can have the wireless up at boot without needing a manual restart of networking?

Thanks in advance...

---

