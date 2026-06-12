---
title: "iwl3945 with Hardy"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by nwadams on 2008-04-28
hey
my intel wireless card does not work with the new iwl3945 drivers. Worked perfectly with the ipw 3945 drivers before. 
please help. And would it help if i posted my iwconfig and my ifconfig, and what other commands should i post too. 

Thanks

---

### Post by azwan on 2008-04-28
there's solution i found when search at google but i can't recall what is the site
but try this forum thread
[http://ph.ubuntuforums.com/showthread.php?t=748218](http://ph.ubuntuforums.com/showthread.php?t=748218)

edit /etc/udev/rules.d/70-persistent-net.rules

comment line that show 
# PCI device 0x8086:0x4222 (iwl3945)
#SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="xx:xx:xx:xx:xx:xx", ATTR{type}=="1", NAME="eth1"
add this line
SUBSYSTEM=="net", DRIVERS=="?*", ATTR{address}=="xx:xx:xx:xx:xx:xx",ATTR{type}=="1", NAME="wlan0"

replace xx:xx:xx:xx:xx:xx with your original mac address

reconfigure your /etc/network/interface setting to use wlan0 instead of eth1 for wifi
(you must use wlan0 because from my experience i can't use eth1.. it will give you error(s) when starting the network)

then add this to you /etc/modprobe.d/blacklist
blacklist ipw3945
blacklist ieee80211
blacklist ieee80211_crypt

and.. load iwl3945 module by adding this 2 line into /etc/modules file
iwlwifi_mac80211
iwl3945

reboot... and your wifi should work.. you can ping and access any pc in your lan/network range
but this solution is not complete since i also didn't what else seem to be the problem since i can't access the internet. i can't ping my modem WAN ip address. it's like the pc can't communicate with ip that's in not in your network range. ( sorry, i don't know how to explain this properly)

added: you also will get errors when restarting network service and must reload iwl module back by
$modprobe -r iwl3945
$modprobe iwl3945

the wifi will be FINE, it just can't access to internet..look like it's still buggy

---

### Post by Everywhere_at_Once on 2008-04-28
I'm having the same trouble with this stupid 3945.

I tried using compat-wireless-2.6, but at first it would work, then upon reboot it was back to square 1.

Now, when i run compat-wireless, it won't even work at all.


and as for your solution, it is better than nothing, i will give you that, but it can't access the internet?

---

### Post by chili555 on 2008-04-28
With all due respect to my esteemed colleague azwan, I don't think that's the best solution. There have been several threads here, and the working solution seems to be here: [http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/](http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/) It worked for mine!

---

### Post by azwan on 2008-05-02
thanks for that information but i already tried installing backport module
before this, unfortunately it just work for a while then error occur.
since wifi is my main internet connection, i can't afford to try something else that would break my connect, maybe when i'm back home i'll try to make it work again.
now i'm using old kernel from previous gutsy installation.

---

