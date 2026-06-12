---
title: "Linksys WUSB54G"
date: 2008-01-01
forum: Networking &amp; Wireless
---

### Post by Septenary on 2008-01-01
Hello,

I am, unfortunately, completely new to Ubuntu, and, admittedly, I have no idea what I'm doing (*yet*).  Sorry for my inexperience.  Anyway, for the past few days, I've been trying to get a network connection on 7.10 Gutsy through my Linksys USB Wireless, model WUSB54Gv4.

From what I've read, I needed to somehow install the drivers for the WUSB54G, through ndiswrapper - so, I attempted to do this, following these instructions: 
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

The driver seems to have installed fine through ndiswrapper (ndiswrapper lists it as installed) but, in the ndisgtk graphical interface, it says "Hardware not found." - which, I don't understand, because *lsusb* shows the hardware to be properly connected.  The driver's chipset ID matches, and I tried many different versions, but to no avail.  Am I doing this completely wrong?

Sorry once again for my newbishness, and thanks for your help!

---

### Post by Septenary on 2008-01-01
Here's where I think the problem is occurring?:

[IMG]http://img125.imageshack.us/img125/4793/screenshotwirelessnetwotp0.png[/IMG]

---

### Post by rightmind on 2008-01-03
If you have Dapper Drake like I do, this is what worked for me.

Getting the WUSB54Gv4 Linksys Wireless Adapter to work on Ubuntu Dapper Drake
These instructions are the culmination of several post by different members. The below is what initial work for me.
1.Black list the driver rt2570 by typing: $sudo gedit /etc/modprobe.d/blacklist
2.Enter at the bottom: lbacklist rt2570

save and restart. Check that after restart your wireless rausb0 disappears leaving only the modem in admin -> network.

3.Install ndiswrapper from synaptic package manager. Therefore I didn't have to deal with the make commands. You could use the make install method found in the &#8220;INSTALL&#8221; file within the ndiswrapper directory, but using synaptic made this install painless. 

I also installed &#8220;linux-headers 2.6.15-25, but that was so I could use make command. Not sure if this really helped in the end.

4.Get the WUSB54Gv4 driver from the cd that it came with, or download it. I made a directory called &#8220;WUSB54Gv4&#8221; and copied the driver WinXP driver files there.
5.Open terminal: cd to the WUSB54Gv4  directory.
6.Check if there are any ndis drivers: sudo ndiswrapper -l
If so, type: sudo ndiswrapper -e
7.Create ndis driver by typing: sudo ndiswrapper -i drivername.inf
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



Synaptic (In Ubuntu Dapper Drake is found in System>Adminstration>Synaptic Package Handler. I needed to hook up to the internet via hard line for the updates to download.

I hope this helps, good luck :)

---

### Post by rustybronco on 2008-01-03
if not, try this method.
[http://ubuntuforums.org/showthread.php?p=3609183#post3609183](http://ubuntuforums.org/showthread.php?p=3609183#post3609183)

---

### Post by onlineapps on 2008-01-03
One thing that worked for me was simply unplugging the dang wifi adapter and then plugging it back in. I have an older WUSB54G though.

---

### Post by Septenary on 2008-01-03
Thank you all very much for replying!  The link that rustybronco provided ended up working perfectly - and very quickly too.  I'm making this post from Ubuntu now.  Exciting.  :D

---

### Post by kevdog on 2008-01-03
Way to go Septenary and Rusty Bronco!!! Good team work!

---

