---
title: "bcm4310 help"
date: 2007-10-18
forum: Networking &amp; Wireless
---

### Post by nickkov89 on 2007-10-18
Ok i got the driver for my broadcom card, 
this is what i get when I use ndiswrapper -l

bcmwl5 : driver installed
        device (14E4:4312) present (alternate driver: bcm43xx)


It doesnt work anyway however, anybody have an idea?

Thanks.

---

### Post by nickkov89 on 2007-10-18
bump
anyone?
I need wireless on here for  college, im desperate

---

### Post by nickkov89 on 2007-10-18
ok well im getting *somewhere*

when i type iwconfig i get:

lo        no wireless extensions.

eth0      no wireless extensions.

device    IEEE 802.11b/g  ESSID:"r"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid   
          RTS thr: off   Fragment thr: off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

so its detecting it, but its still not working what do i need to do?
i read somewhere i need the broadcom to be under wlan0 but its under driver, is that significant?

---

### Post by worldgnat on 2007-10-26
Try this: [http://www.stylesen.org/configuring_wireless_bcm4310_uart_card_in_debian_etch_amd64_using_ndiswrapper](http://www.stylesen.org/configuring_wireless_bcm4310_uart_card_in_debian_etch_amd64_using_ndiswrapper)

I'm working on it right now, I'll let you know how it goes.

EDIT: seems to work so far, I'm actually posting from the card right now. Good luck. 

-Peter

---

### Post by staticsage on 2007-10-26
Check out the sticky: [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

If you don't want to use his script, you can still grab the offline installer and use the bcm43 drivers included: [http://www.fileden.com/files/2007/9/16/1436371/bcm43xx-0.3.2-offline.tar.gz](http://www.fileden.com/files/2007/9/16/1436371/bcm43xx-0.3.2-offline.tar.gz)

I was having trouble getting ndiswrapper working with my bcm chipset, but using the drivers included in that package worked like a charm.

---

### Post by rosegarden78 on 2008-01-21
1) install bcm43xx package from repos
if you're off-line it might be included already
if on-line type
sudo aptitude install bcm43xx
or use a package manager like Synaptic

2) type in a terminal
sudo modprobe bcm43xx

3) then type
nm-applet

or if missing type
sudo aptitude install nm-applet
to install it

---

