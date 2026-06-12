---
title: "WPA was working, now it's not..."
date: 2007-03-02
forum: Networking &amp; Wireless
---

### Post by tamman2000 on 2007-03-02
I am getting really confused here...

I am very new to Ubuntu; I installed edgy for the first time Monday...

I got online using WPA_supplicant and was happily using it for a few days (without any reboots).  Right after I got online I installed wifiradar, because I heard it makes wifi easier, and I would not always be on the same network.

Then, this morning I installed 915resolution, and had to restart to get the effects.  When it came back up, I couldn't connect to the wireless network.  
I tried to repeat the procedure I went through to get WPA supplicant working, no luck.
I removed wifi radar, and again retried...  still no luck.  

Now I don't know what to do.

I am somewhat limited in terms of how I can connect.  The wifi network in question is my landlords, so I have no control over the router.  I am writting on my windows laptop right now.  I don't have windows on the machine I am trying to fix.  I do have another wifi network (nonbroadcasting WEP) that I can connect to, but it isn't connected to the outside world, and I can not connect it to the outside world (I got rid of my cable modem when my landlord gave us free wifi).

So the summary, is...

WPA was working, either wifiradar, 915resolution, or a reboot seems to have broken it.
I know the card is working, because I can connect to a useless network.

Help,
Please,
Tamman2000

---

### Post by FIONEX on 2007-03-02
Follow these instructions, but when you get to the end DONT RESTART, just do the "/init.rc/dbus restart" command.  After you do that, run "nm-applet" and you're all good.
[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

WIFI radar is a POS.  I tried everything to get it working but no luck.  It seems to confuse the loopback as a connection.  Cuz I couldn't even connect to a non secured network with it.  Wireless really needs to be better integrated into ubuntu.  Some things are just standard, and the ubuntu network needs to realize that and just ship them preinstalled and working with the system.  Chop out GIMP and OpenOffice from the CD and put in a working wireless installation.

---

### Post by cookfromfrozen on 2007-03-02
You may want to install the "network-manager-gnome" package (if you're on GNOME) or "knetworkmanager" if you're on KDE.  You can use these to connect to a list of available networks and it supports WPA too.

This page may also be helpful too:

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

---

### Post by tamman2000 on 2007-03-14
I managed to get it on a wired connection for a while, and I was able to install networkmanager.

But that didn't solve my problems.  Network manager only has my wired network as an option.

How is networkmanager supposed to work?  Do I have to do something to add wireless networks?

---

### Post by Fitzcarraldo on 2007-03-14
Perhaps the following thread may help you:

[http://ubuntuforums.org/showthread.php?t=378179](http://ubuntuforums.org/showthread.php?t=378179)

---

### Post by tamman2000 on 2007-03-17
Fitzcarraldo,

Thank you!

It seems to have worked.  I says seems to have worked because I am still not sure everything is set up correctly, but I am online...

It didn't offer me a list of networks to connect to, I had to put in the SSID manually, even though it is a broadcasting network, and it isn't giving me a list of other networks I could connect to, while my windows machine shows 7 in the area, 3 of them with decent strength.   In other words, it doesn't seem to be scanning.

Any ideas on why that is, or should I start a new thread with a subject line that is indicative of my current situation?

Thanks again,
Tamman2000

---

### Post by Fitzcarraldo on 2007-03-17
I'm using Dapper, not Edgy, so I can't be sure what the precise situation is on your PC. Also, as you installed wifiradar and 915resolution, I don't know what effect they had on your configuration, even if you later unistalled them.

If you also have the Network Monitor icon (as distinct from the Network Manager icon) on your Panel, try disabling all the interfaces in Network Monitor. I can't recall the precise sequence (I'm not on a PC using ubuntu at the moment), but there is a tick-box for each interface. Then, also go back to the /etc/network/interfaces file and make sure it contains only the following two lines:

auto lo
iface lo inet loopback

If that does not work, you'll have to do a bit of searching and reading through the threads in the Networking & Wireless forum, as several people have reported Network Manager not seeing available networks that are broadcasting their SSIDs, and you may find one that is of help.

Here are a couple more threads that might be of some use:

[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

[http://www.ubuntuforums.org/showthread.php?t=156319](http://www.ubuntuforums.org/showthread.php?t=156319)

[https://wiki.ubuntu.com/DapperNetworkManager?highlight=%28wpasupplicant%29](https://wiki.ubuntu.com/DapperNetworkManager?highlight=%28wpasupplicant%29)

If you manage to crack the problem, post here to let us know.

---

