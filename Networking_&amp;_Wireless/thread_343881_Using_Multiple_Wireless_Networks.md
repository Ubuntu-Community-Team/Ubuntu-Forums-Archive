---
title: "Using Multiple Wireless Networks"
date: 2007-01-22
forum: Networking &amp; Wireless
---

### Post by knichel on 2007-01-22
I have a laptop that I use for work and at home.  I have wireless network at home an work.  When I use Neworking to change networks (I have cretated different profiles), it take forever to switch.  I am not familiar with the command line to change network settings.  Is there a fast way to change the network settings from one network to the other?  I have tried netswitcher as well and that takes a very long time as well.  Is command line my best option?  If so, can you list the commands necessary to change ESSID, IP, Gateway, default route... I am not using any encryption.

TIA,
Mike

---

### Post by encompass on 2007-01-22
sudo apt-get install nm-applet-gnome
I think is the command to install network-manager-applet
Just got it working for me and it is great!

---

### Post by knichel on 2007-01-22
What about for kde?  Will this app work under kde?

---

### Post by encompass on 2007-01-22
Search in synaptic for things that start with nm-applet you will find the kde version of it there... same as the gnome version.

---

### Post by knichel on 2007-01-22
When I search synaptic, I find nothing starting with nm-  and only network-manager-gnome.  Do I need a special repository enabled?  I am using 6.06 LTS.

---

### Post by encompass on 2007-01-23
So sorry, yeah that is what it is called.... but you don't want the gnome version you want the kde version.  if it exists for 6.06.  I am not sure.  To my knowledge it is a fairly new program.

---

### Post by rmartz on 2007-01-23
I found Wifi-radar In the Synaptic Manager. I installed it and it works pretty easy to allow me to set up multiple wireless networks and can switch with just a click or two.

---

### Post by encompass on 2007-01-23
I used it for my lowend systems... but I still recommend network manager... it is very nice and easy to use.

---

