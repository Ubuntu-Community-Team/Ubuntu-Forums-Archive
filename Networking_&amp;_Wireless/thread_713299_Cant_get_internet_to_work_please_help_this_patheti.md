---
title: "Cant get internet to work please help this pathetic newb"
date: 2008-03-02
forum: Networking &amp; Wireless
---

### Post by EricSul on 2008-03-02
Hi. First off let me say I've looked at other threads and have been trying to fix this on my own for like 5 hours and I can't get it to work. I previously had my laptop dual booted with ubuntu 6.10 and xp but I never used the ubuntu as i couldn't get any of my internets to work (among other things). Then I came across 'Ubuntu Ultimate', for those who don' know, is a distro that has, from what i'm assuming, is pretty much everything you need for ubuntu pre-installed.

After downloading and burning, I ran the live CD and explored. I came accross 'Wireless Assistant', it saw and was able to connect to my wireless network so I wiped clean and installed ubuntu ultimate gamers ed.

Now I can't get an ethernet connection or a wireless connection. I'll start with showing what I've tried to do and the errors that I'm getting for my ethernet connection and then I'll move on to the wireless.


ETHERNET:
So i plug my ethernet cable in and the 'NetworkManager Applet' goes to work connecting, after which it says its connected. So i right click on it, go to connection information and get an error that it couldn't find resources (the glade file).

So I open 'Network Monitor' and see that it has a connection "eth0:avahi" but my status is error. I read the error "could not find information on interface 'etho:avahi" in /proc/net/dev". the support tab reveals I have an active Address and Broadcast

So I run HardInfo and Sysinfo from System Tools and everything seems to be fine so after I typed 'lshw -C network' in the terminal it comes up as 'network:1' with the logical name of 'eth0' all other values show that it is recognized by the system with drivers installed.


WIRELESS:
I run Wireless Assistant and I get an error "you might have insufficient permissions for Wireless Assistant to function properly, did you run it using sudo?" well all the programs I run from the GUI that need to run as sudo always prompt me for a password.

So I try like 5 of the pre-installed programs that should let me connect to my wireless manually network but none of them connect.

typing 'lshw -C network' in the terminal shows 
Network:0 DISABLED
physical ID 2
Logical Name: eth1

Also I should note: My laptop is a COMPAQ Presario v5000 with broadcom wireless. the package is already pre-installed and the system sees both the wireless cards and the drivers.

Please Help!!! I want to learn to use linux more but its quite hard when you can't use the internet

---

### Post by xc3RnbFO8P on 2008-03-02
Did you try this:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")

---

