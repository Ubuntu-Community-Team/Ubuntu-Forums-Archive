---
title: "Wireless Internet to wired bridge troubles"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by brw02005 on 2008-04-28
Ok have gutsy going great but having trouble getting internet to xbox with static IP.  Want receive the wireless as I'm currently doing with my atheros chipset wifi card and bridge it with my ethernet. I also want other services such as windows file shares to pass through not just internet since I'm running XBMC on my xbox.  I originally had this set up with windows comp but am trying to save electricity.  The first problem I'm running into is that I can only get either wifi or ethernet working never both so this has made it impossible for most of the suggestions I've heard to work.  I think it may have something to do with network manager but I'm not disabling it on a hunch.  Thank you for whoever takes the time to answer this question.

---

### Post by amohanty on 2008-04-29
It _is_ because of NetworkManager. It is a bit feature limited - good critique here (though a bit outdated) [http://wiki.mandriva.com/en/Projects/EasyWifi/Development/NetworkManagerCritics](http://wiki.mandriva.com/en/Projects/EasyWifi/Development/NetworkManagerCritics)

You can simply remove it and revert back to the /etc/network/interfaces solution. 
man interfaces 
for configuration information.

HTH
AM

---

### Post by brw02005 on 2008-04-30
Removed it from synanaptic and the second I bring the ethernet up the wireless goes down.  I don't get it.

---

### Post by coheed on 2008-04-30
I'm having the exact same problem

New to linux, but am very quickly being scared away...

Just installed Ubuntu 8.04...

I'm trying to bridge my wireless network connection to my wired ethernet adapter so that I can use my computer as a means to provide internet to my xbox. 

I've done in successfully in Windows, but can't get this to work in Linux...

I've tried searching EVERYWHERE, and everyone's articles/tips either don't work, are outdated, or don't make sense. Seems like theres a million ways to do it and not one works. 

I can't imagine there isn't a definitive way to bridge network connections...

Furthermore... If bridging doesn't work, is Linux capable of simple network connection sharing (basically the same thing except through Connection Sharing my computer does not act as a dhcp client to the shared connection, it shares the same ip address as my laptop)

---

### Post by amohanty on 2008-05-01
so did you 'completely remove' the the "network-manager" package from synaptic ??

Can you post the output of right after you bring up the wired interface (and after the wireless goes down):

sudo ifconfig -a
dmesg | tail -n 100
contents of your /etc/network/interfaces file

AM

---

### Post by coheed on 2008-05-01
I haven't removed Network-Manager

Right now nothing is bridged. I couldn't get any of the suggestions/tutorials I read to work.

Care to start from scratch with me? I promise I'm a good listener! :-)

---

### Post by superprash2003 on 2008-05-01
read this - [http://wiki.steenbe.nl/?p=29#more-29](http://wiki.steenbe.nl/?p=29#more-29)

---

### Post by coheed on 2008-05-01
superprash, will do it right now and advise as to how it goes. Thanks for your link, it's definitely one I haven't came across yet.

---

### Post by coheed on 2008-05-01
Okay superprash...

Followed your instructions, all seemed to go well. Maybe I should have elaborated a bit more on my setup...

I have 2 network adapters. One built-in wireless, and one USB Hi-Gain wireless to get a better signal from my house (office is in the garage). 

Built-In wireless = wlan0
USB wireless = eth1
wired ethernet = eth0

Once this was all done, my USB wireless no longer can receive signals. I can't connect to a network through it, it keeps defaulting back to my built-in wireless.

I tried ifconfig wlan0 down, and iwconfig wlan0 txpower off and neithr of those would shut down my built-in wireless.

So I'm assuming this is why I'm not getting data out of eth0... 

Any suggestions?


eth0 is the ethernet connection I want to supply my Xbox with
eth1 is the wireless network providing the internet signal.

---

### Post by superprash2003 on 2008-05-01
firstly consider using only one wifi, either usb or wifi..have you changed the command according to your setup.. if there is a command like iptables eth0..... it need not be eth0 in your case.. it could be wlan0 .. have you done it accordingly??

---

### Post by coheed on 2008-05-01
I have set it up accordingly, and I would like to use only USB. 

I just can't figure out how to completely disable my wifi card inside my computer....

---

### Post by jimv on 2008-05-01
Check your BIOS settings.  THere's probably an option in there to disable your onboard wifi.

---

### Post by coheed on 2008-05-01
Right but then it's useless in Windows... Anyway to do it strictly in linux?

---

### Post by amohanty on 2008-05-01
Try commenting out the line in /etc/network/interfaces that refers to your built-in card ie wlan0.

Then in a terminal try:
sudo /etc/init.d/networking restart

HTH
AM

---

### Post by coheed on 2008-05-01
amohanty, there's nothing in there about wlan0... Here's the contents of my interface file:

auto lo
iface lo inet loopback


# The extended interfaces
auto eth0
iface eth0 inet static
address 192.168.10.1
netmask 255.255.255.0

# The primary network interface

iface eth1 inet dhcp
pre-up iptables-restore < /etc/iptables.rules
post-down iptables-save > /etc/iptables.rules
wireless-essid linksys

---

### Post by kevdog on 2008-05-02
Something like this?:
[http://ubuntuforums.org/showthread.php?t=733868](http://ubuntuforums.org/showthread.php?t=733868)

---

### Post by ninetailfox97 on 2010-12-31
try this out:

[http://davidzhang.webs.com/apps/blog/](http://davidzhang.webs.com/apps/blog/)

this trick seems like it might work

---

