---
title: "New user needs help with ndiswrapper and Broadcom wireless"
date: 2008-09-01
forum: Networking &amp; Wireless
---

### Post by micky manymoons on 2008-09-01
Hello everyone, I'm new to Ubuntu and fairly new to Linux (once looked at a redhat distribution when in College). I have read a few of the post's and tried a few things but still cant get the wireless network to work  
here are a few reports I've had back from a few commands I got off some post's
mike@mike-desktop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

mike@mike-desktop:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)
mike@mike-desktop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: nForce2 Ethernet Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: a1
       serial: 00:0c:6e:fd:23:ee
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.60 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network DISABLED
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:01:07.0
       logical name: eth1
       version: 03
       serial: 00:11:50:0b:b4:ee
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=64 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g

seems to be telling me that the wireless card is disabled.  How can I Enable the wireless and disable the nvida nForce2 Ethernet Controller which I think must be the motherboard network Controller and of no use to me as I have no means of pysicaly running a cable. I would be very gratefull for any help

---

### Post by caljohnsmith on 2008-09-02
> **micky manymoons said:**
> 
mike@mike-desktop:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4320) present ([COLOR="Red"]alternate driver: bcm43xx[/COLOR])
mike@mike-desktop:~$ lshw -C Network
...
  *-network DISABLED
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:01:07.0
       logical name: eth1
       version: 03
       serial: 00:11:50:0b:b4:ee
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=64 [COLOR="Red"]module=bcm43xx[/COLOR] multicast=yes wireless=IEEE 802.11b/g

From above, it appears Ubuntu is using the old bcm43xx module to try and run your wireless card. To fix it, you have to "blacklist" that module so that Ubuntu won't use it. Also, there a few more modules you should blacklist, but first open:
```
gksudo gedit /etc/modprobe.d/blacklist
```
And at the bottom add:
```
blacklist b43
blacklist bcm43xx
blacklist b43legacy
```
Reboot, and you should be using ndiswrapper now. Let me know how it goes or if you need any more details/info.

---

### Post by Ayuthia on 2008-09-02
> **caljohnsmith said:**
> From above, it appears Ubuntu is using the old bcm43xx module to try and run your wireless card. To fix it, you have to "blacklist" that module so that Ubuntu won't use it. Also, there a few more modules you should blacklist, but first open:
```
gksudo gedit /etc/modprobe.d/blacklist
```
And at the bottom add:
```
blacklist b43
blacklist bcm43xx
blacklist b43legacy
```
Reboot, and you should be using ndiswrapper now. Let me know how it goes or if you need any more details/info.

In some cases you might also have to add ndiswrapper to /etc/modules.  You will need to edit /etc/modules by:
```
gksudo gedit /etc/modules
```and just add the word ndiswrapper to the end of the file.

You can try and see if you can connect by trying the following:
```
sudo modprobe -r bcm43xx
sudo modprobe ndiswrapper
```

---

### Post by micky manymoons on 2008-10-12
I'm Replying to this from Ubuntu!!!  Thank you Very much .. Blacklisting the unwanted drivers worked, I did have a little trouble editing /etc/modprobe.d/blacklist using sudo gedit .. It kept saying I didnt have permision to edit the file .. So I used sudo tee -a /etc/modprobe.d/blacklist
and typed the code in from a terminal  That did the trick .. Thanks again .. I'm looking forward to properly exploring ubuntu now  Oh one last thing is there a config file that i can add sudo modprobe ndiswrapper , to ? I have to type it in at a terminal after boot up at the moment

---

### Post by caljohnsmith on 2008-10-12
> **micky manymoons said:**
> I'm Replying to this from Ubuntu!!!  Thank you Very much .. Blacklisting the unwanted drivers worked, I did have a little trouble editing /etc/modprobe.d/blacklist using sudo gedit .. It kept saying I didnt have permision to edit the file .. So I used sudo tee -a /etc/modprobe.d/blacklist
and typed the code in from a terminal  That did the trick .. Thanks again .. I'm looking forward to properly exploring ubuntu now  Oh one last thing is there a config file that i can add sudo modprobe ndiswrapper , to ? I have to type it in at a terminal after boot up at the moment
Gosh, haven't heard from you in a long time! :) Glad you've at least got wireless working. If you are using sudo/gksudo, you shouldn't be getting permission errors when modifying files. Also, if you can do as Ayuthia suggested and add the line "ndiswrapper" to the end of your /etc/modules file, that will automatically load ndiswrapper on start up so that you don't have to manually "modprobe" it every time you log in. So can you do:
```
gksudo gedit /etc/modules
```
Or does that return an error? Post the exact error if you get one.

---

### Post by micky manymoons on 2008-10-13
Thanks for such a speedy reply!
Well   gksudo gedit /etc/modules  Works fine .. in as much as it edits and saves the file, I added .. modprobe ndiswrapper to the end of the file But it dosent seem to load until I type it into a terminal after boot up, I'm not seeing any error messages So it's no hardship really,  I was wondering if I should be looking into firewalls? I think i read that ubuntu has one built in but didnt understand properly how to configure it

---

### Post by Ayuthia on 2008-10-13
> **micky manymoons said:**
> Thanks for such a speedy reply!
Well   gksudo gedit /etc/modules  Works fine .. in as much as it edits and saves the file, I added .. modprobe ndiswrapper to the end of the file But it dosent seem to load until I type it into a terminal after boot up, I'm not seeing any error messages So it's no hardship really,  I was wondering if I should be looking into firewalls? I think i read that ubuntu has one built in but didnt understand properly how to configure it

It should be ndiswrapper instead of modprobe ndiswrapper in /etc/modules.  So if you go into /etc/modules and remove the word modprobe, it should load up for you.

---

### Post by micky manymoons on 2008-10-13
Thanks Ayuthia !  That worked a treat .. the network loads at boot up now.

---

