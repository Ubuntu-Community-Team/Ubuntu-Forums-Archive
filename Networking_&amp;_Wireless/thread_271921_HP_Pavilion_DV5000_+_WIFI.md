---
title: "HP Pavilion DV5000 + WIFI"
date: 2006-10-05
forum: Networking &amp; Wireless
---

### Post by kaurxxl on 2006-10-05
I wanted to try linux, and I Downloaded Ubuntu 6.06.1 64 ADM version.
Now evrything is working fine, but I can't use wireless internet.
Only way to use internet is to use wire wich I don't like.
I have downloaded ndisgtk and installed my WIFI card drivers.
It shows that hardware is present, now I dont get how to connect to Wireless Area.
I also downloaded NetworkManeger Applet 0.6.2 ([http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/))
I can't connect with this also.

Sorry for my bad grammar but if anyone can help then please do.
Thank you!

---

### Post by willca on 2006-11-05
If you run a few of these commands what does it tell you?

Here is my output.

willca@uberwca:~$ sudo iwconfig
Password:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"joeblow"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:A5:93:68:C4   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:100/100  Signal level:-62 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

If you got a similar output as such then you have your wifi card at least recognizable. 

You can configure it by editing /etc/network/interfaces. 

For example:

willca@uberwca:~$ sudo cat /etc/network/interfaces
auto lo
iface lo inet loopback

iface eth1 inet dhcp
wireless-essid joeblow

Then you can enable / disable your interface (for me its eth1)

$ sudo ifdown eth1
some output....

$ sudo ifup eth1
some output which will confirm if its gotten connected with an IP

HTH
-W

---

### Post by A. J. Rimmer on 2006-11-05
I also have an HP Pavilion dv5000-series laptop.  However, mine has an Intel processor and Intel 3945 WiFi adapter, which works well with Ubuntu.  

I believe that the AMD processor versions of this computer use the Broadcom WiFi adapter, which can be made to work, but which requires a few extra steps.

I don't have any experience with this so I can't answer your question directly, but if you search the forums for "Broadcom" and "ndiswrapper" I'm sure you will find some helpful information.

---

### Post by d-E-a-D on 2006-11-21
I use dv5000 with a broadcom wireless, after a fresh install all i have to do  in Ubuntu Edgy is:
```
sudo aptitude install bcm43xx-fwcutter
sudo /usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh
```
And voila! it starts to work!
Hope this helps, if don't send me some pm.
Does anyone can install Ati 200m on this laptop? if so please pm me! :(
Thanks

---

