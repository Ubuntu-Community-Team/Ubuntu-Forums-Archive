---
title: "Update to 4.4.0-71 failed no wifi at all"
date: 2017-04-03
forum: Networking &amp; Wireless
---

### Post by mick-au on 2017-04-03
Hi gurus,
I let automatic upgrade run overnight - very slow speed and all through firewall as I'm in China. At end of process all of my wifi failed. There is absolutely no wifi available. I using an ASUS UX305F notebook.
Some tests are
```
mick@wildone:~$ cat /etc/modprobe.d/iwlwifi.conf
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
```

```
mick@wildone:~$ ls /etc/modprobe.d/
alsa-base.conf              blacklist-oss.conf
asus.conf                   blacklist-rare-network.conf
asus_nb_wmi.conf            blacklist-watchdog.conf
blacklist-ath_pci.conf      dkms.conf
blacklist-bcm43.conf        fbdev-blacklist.conf
blacklist.conf              intel-microcode-blacklist.conf
blacklist-firewire.conf     iwlwifi.conf
blacklist-framebuffer.conf  mlx4.conf
blacklist-modem.conf        vmwgfx-fbdev.conf
```

```
dmesg | grep iwl 
> empty
```

Please note that communications here are difficult :(
Mick

---

### Post by mick-au on 2017-04-04
When I booted tonight I had wi-fi so I assume the problem is hardware possibly loose in socket.
I'll get that checked next week.

---

### Post by ubfan1 on 2017-04-04
Good to hear.  You can mark the thread as "Solved" from the "thread tools" button near the top.

---

### Post by slickymaster on 2017-04-04
*Thread moved to **Networking & Wireless**.*

---

