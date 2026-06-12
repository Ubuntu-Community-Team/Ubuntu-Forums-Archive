---
title: "[Wireless] 3945ABG, Edgy Eft, wifi-radar"
date: 2006-12-10
forum: Networking &amp; Wireless
---

### Post by Snakiej on 2006-12-10
Hi there :)

I'm running in some problems using my WPA-secured wireless network at home.

I use wifi-radar, but whatever driver I use in the WPA section, I can't connect. The key IS correct, the network shows up perfectly. In Windows XP it works 100%. The drivers I tried are: test, madwifi, wext. ( all the ones that show up @ wpa_supplicant ).

This link works perfectly [http://www.ubuntuforums.org/showthread.php?t=263136](http://www.ubuntuforums.org/showthread.php?t=263136)

BUT I have to use differant profiles for my network, because I am at differant locations ( home, school, my girl ).

Anyone know which driver I have to use?

Thanks

---

### Post by n00b@linux on 2006-12-11
I too have an Intel Pro/Wireless 3945 network adapter.
I too am trying to connect to my network with WPA.
I too am experiencing problems.
I have followed the [Ubuntu WPA HowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo) and in it is a link to the wpa_supplicant web site.  That web site lists the supported wireless network adapters.
I could not see the Intel Pro/Wireless 3945 (ipw3945) listed so I am presuming that it is not supported by wpa_supplicant, ie. don't bother with wpa_supplicant as it won't work.
I am still trying to find information on configuring WPA without wpa_supplicant....

---

### Post by Lowfront on 2006-12-12
I'm getting this card very soon with my notebook..


How does it do connecting to a unsecured network?  My house in the woods so it doesn't matter

---

### Post by fredj on 2006-12-12
Install network-manager and network-manager-gnome.
Then edit the /etc/network/interfaces file and comment out the lines
which refer to your wireless card. Then restart and configure your wpa
network(s) using the new systray network icon.
All the above will be much easier if you have the DVD version of Ubuntu
which already contains network manager, I don't think its included on the
CD version.

---

