---
title: "wlan drops after maybe 10 minutes"
date: 2006-11-26
forum: Networking &amp; Wireless
---

### Post by falkenberg_cph on 2006-11-26
Hi
My wireless have been working fine in edgy for awhile now, untill suddenly today it disconnects after about 10 minutes. What is wrong.
Yesterday i tested firestarter, but i decided not to use it.
I also tried running Ekiga. Dont use that today either.
I had the computer automatically uninstall unneeded software - ndiswrapper 1.1 was part of this. I reinstalled ndiswrapper 1.1, i allready have ndiswrapper 1.8.

When i write the address of my router in firefox, it cannot connect :confused: - this is strange, this also happens when the internet is up and running. I cannot really give any more info, except maybe:
Router: linksys wrt54g
Driver: windows driver bcmwl5

Hope someone can help me
Thanks
/Carsten

---

### Post by rigol on 2006-11-26
I have the same problem, but with Dapper... see here for details: [http://www.ubuntuforums.org/showthread.php?t=306569](http://www.ubuntuforums.org/showthread.php?t=306569)

---

### Post by falkenberg_cph on 2006-11-26
Oh ok, hadnt found your post.
So what do you think could be wrong.

Can you connect to your routers login page?

/Carsten

---

### Post by falkenberg_cph on 2006-11-26
[EDIT]: Sorry i thought i had figured something out. But i hadnt - so please ignore this exact post. But not the other

---

### Post by AndyC_772 on 2006-11-26
Also check out [http://www.ubuntuforums.org/showthread.php?t=290873](http://www.ubuntuforums.org/showthread.php?t=290873) - I, among others, have a problem with Edgy (new, wasn't in Dapper) whereby the wireless connection works OK as long as I keep actively using it, but drops out if I leave the machine or stop accessing the net for a while.

---

### Post by falkenberg_cph on 2006-11-26
figured my problem out. Maybe this can help others.
It turned out that i had only setup ndiswrapper partly. Leaving out broadcast and dns-nameserver

> sudo gedit /etc/network/interfaces

Mine now looks like this:
> 
auto eth1
iface eth1 inet static
address 192.xx.x.xxx
netmask 255.255.255.0
broadcast 192.xx.x.255
gateway 192.xx.x.xxx
dns-nameservers xxx.xx.xxx.xx
pre-up wpa_supplicant -Bw -Dwext -ieth1 -c /etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant


Of cause with numbers instead of xxx

Strange enough it had been able to connect for quite a while now without problems. So i dont know what happened since yesterday

/Carsten

---

### Post by AndyC_772 on 2006-11-26
Are you using DHCP though? My /etc/network/interfaces looks like this:

> 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

iface eth1 inet dhcp
wireless-essid xxxxxxxx
wireless-key 0123nnnnnnn...nnnn

auto eth1


It did also include a duplicate of the wireless configuration, under the name wlan0 - I've removed those lines to see if it makes any difference. It certainly doesn't seem to have done any harm.

There's nothing about broadcast addresses or dns servers, though - they shouldn't be needed with DHCP (I wouldn't have thought...)

---

### Post by falkenberg_cph on 2006-11-26
I use static ip. because of azureus and stuff.
I cant really help you further. Eventhough i have managed to setup wireless wpa-psk, doesnt mean i know im doing :)

However, this was the thread that helped me, maybe it can help you:
 [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

/Carsten

---

### Post by AndyC_772 on 2006-11-26
Hm... I just left my PC on while I went for dinner - came back and it's still working :)

---

### Post by falkenberg_cph on 2006-11-26
what did you do? Nothing?

---

### Post by AndyC_772 on 2006-11-26
> **falkenberg_cph said:**
> what did you do? Nothing?

Last thing I did was I removed the duplicate entries from the /etc/network/interfaces file.

---

