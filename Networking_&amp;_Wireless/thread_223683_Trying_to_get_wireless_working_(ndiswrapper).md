---
title: "Trying to get wireless working (ndiswrapper)"
date: 2006-07-26
forum: Networking &amp; Wireless
---

### Post by Morca007 on 2006-07-26
So, I am a complete *nix noob, and am trying to setup my wireless card in ubuntu 6.06.

Card - D-link DWL-520  (device manager claims a prism 2.5 chipset)

D-link has not released linux drivers for this model, so I was reccomended to try using ndiswrapper. But even with some hand-holding from a friend, I cannot seem to get it to work.

This is what I have done so far (instructions friend gave me)- installed ndiswrapper
copy the driver from wherever it is currently located to your home directory (to make things simpler) 
type sudo ndiswrapper -i NETPRISM.inf 
open up device manager System>admin>device manager 
Scroll down till you find your wireless card 
Click the advance tab 
Scroll till you see pci.linux.sysfs_path 
look at the last 8 numbers in the line 
sudo ndiswrapper -l
then type sudo ndiswrapper -d "the last 8 numbers" "output of -l"
then sudo ndiswrapper -m 

When I do "sudo ndiswrapper -l" It gives me the message: "invalid driver"

I hope I'm not leaving out important info.

---

### Post by slaiyer on 2006-07-27
Ah....dont worry, we are on the same train...i am also getting the same error, except that i am using a D-Link DWL-122 card...

---

### Post by ion9 on 2006-07-27
do this 

sudo gedit /etc/modprobe.d/blacklist

and this line 

blacklist prism2_usb

save and close.

sudo ndiswrapper -e netprism
sudo ndiswrapper -i ~/NETPRISM.inf
sudo ndiswrapper -m
sudo gedit /etc/modules

add this line 

ndiswrapper 

( i'd use NetworkManager ) 
sudo apt-get network-manager-gnome

---

