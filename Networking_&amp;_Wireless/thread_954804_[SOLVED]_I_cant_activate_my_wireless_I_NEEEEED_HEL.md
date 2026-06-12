---
title: "[SOLVED] I cant activate my wireless I NEEEEED HELP"
date: 2008-10-21
forum: Networking &amp; Wireless
---

### Post by beidache on 2008-10-21
Hello, Im new in ubuntu system and I cant connect via wireless, My computer is dell latitude D620 the wireless is activate already receive the wireless signals but I cant connect, Can Someone help me? Thanks in advance

This is what my computer say about my connection:

 lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:227  Noise level:160
          Rx invalid nwid:0  invalid crypt:16  invalid misc:0

---

### Post by beidache on 2008-10-23
I just did this:

You also need to blacklist b43 and ssb:
Code:

echo -e 'blacklist b43\nblacklist ssb' | sudo tee -a /etc/modprobe.d/blacklist

After that, to test your wireless:
Code:

sudo modprobe -r b43 ssb ndiswrapper wl bcm43xx
sudo modprobe ndiswrapper
sudo iwlist scan

Hope that helps.
Ayuthia

---

