---
title: "dodgy wireless after wired"
date: 2007-09-25
forum: Networking &amp; Wireless
---

### Post by petay on 2007-09-25
Hi  all

I am a keen user of ubuntu and i have a dell Latitude D500 with just ubuntu on there. Everything works and i insalled an intell wifi card which worked perfectly.

I have since started a new job and am using my lappy for work as well as pleasure, but i am connecting to the network via the wired network.

Ever since I have started using the wired net connection, my wireless has started going strange, with it working for the first 5 min and then it stops!! i have tried rebooting my router which has made no difference, but when i have been unable to access things like the internet and email, other things like messenger and torrent downloads are still working.

The settings for firewalls have not changed from when things used to be ok, and i fired up puppy linux from a live cd the other day and the wireless worked for hours on there.

maybe ubuntu is trying to use the wired net connection when it should be using the wireless???

Anyone got any ideas??

Thanks in advance

Pete

---

### Post by noob12 on 2007-09-25
Are you using (the default) NetworkManager ?   

My suggestion is to remove all stanzas from your **/etc/network/interfaces** file except the one for loopback.  You can make a backup copy in case you want to go back.

---

### Post by petay on 2007-09-25
what better backut than posting it here ;)
> 
petay@lappy:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


i dont know where the ath0 has come from!!!

i am using the standard NetworkManager Applet 0.6.4 and i have 1xethernet 1xwireless adaptors

i shall clear all bar the loopback and reboot and see what happens!!

---

### Post by petay on 2007-09-25
well so far so good!!!!

maybe the extra interfaces in the file were confusing things!!

Thanks very much noob12

I now have a flawless ubuntu system again :D

---

