---
title: "XUbuntu 7.10 64Bit - cannot connect to wlan router with steps in howto"
date: 2008-03-19
forum: Networking &amp; Wireless
---

### Post by GordonFreeman on 2008-03-19
Hi,
I'm running XUbunt 7.10 64Bit version on my Dell XPS M1530 notebook.
It has a PRO/Wireless 4965 AGN network connection.
The command "sudo lshw -C network" lists this device and its driver iwl4965 which is the correct driver.
As logical name it show "wmaster0" but with iwconfig and the Network Manager I get a wlan device called
wlan0 and when following the steps from the "Howto withouth NetworkManager for WEP" I have to use this
device since wmaster0 does not support ifconfig up and iwconfig essid (I suppose other commands too but
on these I got an error).
Using wlan0 all configuration steps are working fine only when doing the last step, calling sudo dhclient wlan0
it cannot find the dhcp server.
And the NetworkManager cannot access the wlan network, too although it finds my wlan network (it shows even the name
although the roude has the essid hidden). But when trying to connect it tries for a long time and then just prompts
again for the WEP key.

Have you any clue why it is not working?

btw. my wlan router is set up correctly since I can connect on the same notebook using windows vista and I'm writing
this posting from my other notebook which runs Fedora 8 and is connect wireless.

---

### Post by kufra on 2008-05-05
i have the same problem. the command lshw -C network gave me "product: PRO/Wireless 4965 AG or AGN" so i suppose it's the same driver. i can connect to a non crypted wlan accesspoint. but as it comes to wep and those stuff (kinda noob so) it does not work. but i find this post, might be intresting for you aswell.
[http://ubuntuforums.org/showthread.php?t=419806&page=1]("http://ubuntuforums.org/showthread.php?t=419806&page=1")
i use gnomes "network manager" and when i try to connect (it's the same i can see the names of the networks) i only get one green light.

btw, im total new to linux.

//kufra

---

