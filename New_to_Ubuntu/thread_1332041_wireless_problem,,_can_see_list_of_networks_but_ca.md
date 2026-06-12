---
title: "wireless problem,, can see list of networks but can't connect"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by vxice on 2009-11-19
OK, read through many posts, google searches etc.  I have a compaq r4000 wuith xubuntu 9.04 64bit with the broadcom stuff installed with ndiswrapper.  currently sudo iwlist scan shows the wireless networks all of the wireless networks available.  I have wpa_supplicant correct for the network, it is at a college and they provide the .conf, the provided by the school tech support command doesn't work to update supplicant which is 
sudo wpa_supplicant -Bw -c/etc/wpa_supplicant.conf -iwlan0 -dd
output
ioctl[SIOCISIWPMKSA]: Invalid argument
ioctl[SIOCISIWPMKSA]: Invalid argument

in another tutorial a different set of arguments was given to supplicant which was -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -iwlan0 which outputs lots of text.  currently using another computer here on campus to read posts.

---

### Post by vxice on 2009-11-20
ok got it worked out, because I used xubuntu i couldn't figure out how to get network manager to work so i uninstalled it and used wicd instead.  now I just got to get encrypted working.  i used xubuntu because i was having trouble installing ubuntu, turns out I needed to use a crt monitor to work with the poor default settings for the display.  now i just need to get flash working on 64bit processor.

---

