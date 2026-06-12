---
title: "wireless laptop problem"
date: 2007-10-27
forum: Networking &amp; Wireless
---

### Post by evilfootware on 2007-10-27
Evening all,

I have a Avent 8315 laptop and just installed the latest version of ubuntu. When I completed the installation, it asked me, wether it was ok to enable the restricted-module for my wireless Intel card (pro/wireless 3945 abg), I clicked ok.

I am having major troubles getting the wireless to work. The card is enabled, and when I click the network icon in the top right hand corner, I clicked my orange livebox (wireless router from my isp) from the dropdown menu, and enter my WEP key, and nothing seems to happen, just hangs for a short while and a box appears asking to enter the WEP key again.

I looked a bit further and the wireless card seems to be using the ipw3945 module. I read someone that if I dissable that module and enable iwl3945 module, it might work.

How do I disable the module and enable the other one? Or does anyone have a ideal on how to solve this?

Thanks

Kevin

---

### Post by kevdog on 2007-10-27
Im not really sure about your problem, but lets first check that you have the two kernel modules in your system.

What the results of: (Type at command line)
modinfo ipw3945
modinfo iwl3945

---

### Post by evilfootware on 2007-10-27
Hi,

thanks for the reply, this is what I got when I typed those commands

[HTML]altern8@altern8-laptop:~$ modinfo ipw3945
filename:       /lib/modules/2.6.22-14-generic/ubuntu/wireless/ipw3945/ipw3945.ko
license:        GPL
author:         Copyright(c) 2003-2006 Intel Corporation
version:        1.2.2mp.ubuntu1
description:    Intel(R) PRO/Wireless 3945 Network Connection driver for Linux
srcversion:     04FD04D6570525365D93930
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*
alias:          pci:v00008086d00004222sv*sd*bc*sc*i*
depends:        ieee80211
vermagic:       2.6.22-14-generic SMP mod_unload 586 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           associate:auto associate when scanning (default 0 off) (int)
parm:           auto_create:auto create adhoc network (default 1 on) (int)
parm:           led:enable led control (default 1 on)
 (int)
parm:           channel:channel to limit associate to (default 0 [ANY]) (int)
parm:           rtap_iface:create the rtap interface (1 - create, default 0) (int)
parm:           mode:network mode (0=BSS,1=IBSS,2=Monitor) (int)
altern8@altern8-laptop:~$ modinfo iwl3945
filename:       /lib/modules/2.6.22-14-generic/ubuntu/wireless/iwlwifi/iwlwifi/origin/iwl3945.ko
license:        GPL
author:         Copyright(c) 2003-2007 Intel Corporation
version:        1.1.0
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     B019B21F27D52A5DCDDA000
depends:        iwlwifi_mac80211
vermagic:       2.6.22-14-generic SMP mod_unload 586 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           hwcrypto:using hardware crypto engine (default 0 [software])
 (int)
parm:           debug:debug output mask (int)
parm:           disable_hw_scan:disable hardware scanning (default 0) (int)
parm:           queues_num:number of hw queues. (int)
parm:           qos_enable:enable all QoS functionality (int)
altern8@altern8-laptop:~$ 
[/HTML]

Hope that helps

Kevin

---

### Post by kevdog on 2007-10-27
Ok -- I dont know if switching drivers will help.  I here only how to tell you to switch kernel modules.  Hopefully it will help since I dont have an intel wireless device.

sudo ifconfig <interface> down  <---<interface> = wlan0, eth0, etc.
sudo modprobe -r ipw3945
sudo depmod -a
sudo modprobe iwl3945
sudo ifconfig <interface> up

Ok you can no try connecting via your interface of choice.  If you are using network manager you may need to do:
sudo /etc/init.d/networking restart
or
sudo /etc/init.d/dbus restart

Try without the above commands 2 commands for right now.

Good luck.

---

### Post by evilfootware on 2007-10-28
Hi again,

Thanks for you help. I tried to do what you said, but somewhere I messed up and got some errors. So this morning, I reinstalled it all, so I am back to square one, so to speak.

I had a fiddle around and still no good, So I have taken a screenshot of what I have. Maybe of some use. When I connect the ethernet cable, works fine. But as soon as I try the wireless, nothing work. What it appears to me anyway, is that when I enter the WEP key, the livebox seems to ignore it. I know its the right key, as I have a windows laptop that uses the same key.

Maybe you have an idea. 

[http://img137.imageshack.us/my.php?image=screenshotur0.jpg]("http://img137.imageshack.us/my.php?image=screenshotur0.jpg")

Thanks

Kevin

---

### Post by evilfootware on 2007-10-28
Have made a little more progress. Got the laptop connecting to the livebox. But for some reason, it is not getting an IP address. Not sure why this is, so how to solve it. Have made another screenshot to show.

[http://img248.imageshack.us/my.php?image=screenshotpv8.png]("http://img248.imageshack.us/my.php?image=screenshotpv8.png")


thanks

Kevin

---

### Post by kevdog on 2007-10-28
Make sure you can "see" your router

iwlist scan  <-- This should give you a list of the routers in your area.

You cant use wired and wireless at the same time unless you put them on different subnets, or use bonding, etc.  Basically if you had the wired connectrion running and you wanted to use wireless type this:

sudo ifconfig eth0 down
sudo ifconfig eth1 up
sudo iwconfig eth1 essid "ESSID_NAME_OF_ROUTER_IN_QUOTES"
sudo dhclient eth1

See if this works for you!


There is a link in my signature that tells you how to connect manually.  Its good for troubleshooting initially just to confirm everything is capable of being up and running.

---

### Post by evilfootware on 2007-10-28
Kevdog, your're a star. Finally got the laptop working wireless. Not sure what I did exactly, but with your expert help, got it working. Read your guide in the your sig, very cool stuff.

Thanks for your help.

Kevin

---

