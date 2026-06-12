---
title: "update to 9.04 and got wifi problems"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by spacecase on 2009-05-07
well i upgrade to 9.04 from 8.10 where wifi was working perfectly fine, 
i had an problem where ath5k was loading and not allowing madwifi to work i went to /etc/modprobe.d/madwifi.conf and blacklisted ath5k and un commented all the madwifi stuff and reboot and started working again so i figured that i would need to do that again now but no its all exactly how i left it.  
now with system testing under administrator it tells me that i need to use jockey to pick one driver or the other, cant find jockey anywhere and its all installed under synaptec package manager, i just don't know how to start it.. i don't know how dumb this sound but i sure could use some help here. below is some more info

Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
ubuntu 9.04
linux kernel 2.6.27-11-generic
gnome 2.26.1

---

### Post by chellrose on 2009-05-07
[FONT=System]Are you getting an error something like

[/FONT][FONT=System]ERROR while getting interface flags: No such device

If so, I had the same problem when I upgraded too -- check out the posts
here: [http://kubuntuforums.net/forums/index.php?topic=3103547](http://kubuntuforums.net/forums/index.php?topic=3103547)[/FONT]

Let me know if you need more clarification on something though.  I just fixed this on my machine yesterday, so hopefully I can offer something helpful. :)

---

### Post by djk21108 on 2009-05-07
same here

---

### Post by phar0z on 2009-05-18
I've had the same problem like you but I've solved it.

Here's my chipset: (it's the same.)

> 7 root@linux $ lspci | grep Atheros
04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

Here you can see that I'm running Jaunty:

> 8 root@linux $ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 9.04
Release:        9.04
Codename:       jaunty

In the beginning I saw:

> 24 root@linux $ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.


When my upgrade was completed I've noticed that I didn't have a wireless device anymore. After failed efforts to get it all working with tools like madwifi, previous modules like ath_pci/ath_hal and ndiswrapper I was desperately looking for a solution.

I decided to download the newest kernel at [www.kernel.org](www.kernel.org). I've configured the kernel with **make menuconfig** whereby I enabled:

Networking support -> Wireless -> Generic IEEE 802.11 Networking Stack (mac80211)

I also enabled ath5xxx with make menuconfig, I remember I saw something like Device Drivers -> Wireless Lan -> ...

Then I've compiled my configured kernel according to the Debian-method. (so this is with make-kpkg ...)

[Here you can reed how to compile a kernel according to the Debian-method]("http://www.howtoforge.com/kernel_compilation_debian_etch").

Then I've downloaded a compat-wireless tarball [from this site]("http://www.orbit-lab.org/kernel/compat-wireless-2.6/2009/").

Then I've extracted the tarball with a **tar jxvf compat*.tar.bz2**, I entered the folder with **cd** and I installed it successfully with **make && make install**. 

Suddenly I was able to load the necessary ath5k module with **modprobe ath5k** and there my wlan0 appeared. After modifying my /etc/network/interfaces file to my needs and restarting it all with /**etc/init.d/networking restart** everything seems to be working.

Important note: I've tried to install several versions of compat-wireless on a default Ubuntu (generic) kernel, unfortunately errors while compiling made this impossible. That's why I've decided desperately to compile a new kernel. :)

> 24 root@linux $ iwconfig wlan0

wlan0     IEEE 802.11bg  ESSID:"dlink"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:15:E9:F5:62:58
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:A1B3-C5D7-E0   Security mode:open
          Power Management:off
          Link Quality=50/70  Signal level=-60 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

