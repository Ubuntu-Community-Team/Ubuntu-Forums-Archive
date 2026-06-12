---
title: "Getting the WUSB54Gv4 to work on Ubuntu Dapper Drake"
date: 2007-12-15
forum: Networking &amp; Wireless
---

### Post by rightmind on 2007-12-15
Getting the WUSB54Gv4 Linksys Wireless Adapter to work on Ubuntu Dapper Drake
These instructions are the culmination of several post by different members. The below is what initially work for me.

1.Black list the driver rt2570 by typing: $sudo gedit /etc/modprobe.d/blacklist
2.Enter at the bottom: blacklist rt2570

save and restart. Check that after restart your wireless rausb0 disappears leaving only the modem in admin -> network.

3.Install ndiswrapper from synaptic package manager. Therefore I didn't have to deal with the make commands. You could use the make install method found in the &#8220;INSTALL&#8221; file within the ndiswrapper directory, but using synaptic made this install painless. 

I also installed &#8220;linux-headers 2.6.15-25, but that was so I could use make command. Not sure if this really helped in the end.

4.Get the WUSB54Gv4 driver from the cd that it came with, or download it. I made a directory called &#8220;WUSB54Gv4&#8221; and copied the driver WinXP driver files there.
5.Open terminal: cd to the WUSB54Gv4  directory.
6.Check if there are any ndis drivers: sudo ndiswrapper -l
If so, type: sudo ndiswrapper -e
7.Create ndis driver by typing: sudo ndiwrapper -i drivername.inf
Please remember the inf extension. In my case the drivername is rt2500usb.inf
8.Entering these three lines allowed (below) the driver to show in the network config, and connect after I configured the IP, Gateway, and DNS. I connect via static, but will work with DHCP as well.

sudo depmod
sudo modprobe ndiswrapper
sudo ndiswrapper -m

9.Restart
10.Done! Open your network config or iwconfig. My driver is called wlan0. 

I hope this helps. Thanks to g3r41d, mattoman, and kewldude606.
You may view the post here: [http://ubuntuforums.org/showthread.php?t=192588](http://ubuntuforums.org/showthread.php?t=192588)
It may have a step that your system may need.

Again, thanks all. Because fo your collective input I am posting this from my WUSB54Gv4 wireless adapter. :guitar:

---

