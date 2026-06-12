---
title: "Stopping wired conection stops wireless connection (Ubuntu server)"
date: 2008-06-02
forum: Networking &amp; Wireless
---

### Post by karto on 2008-06-02
The issue was resolved. Apparently I hadn't been following the instructions in the [sticky](http://ubuntuforums.org/showthread.php?t=571188) properly, so you can ignore the below post.



I am setting up a file/print server with Ubunu server. It will be used with a wireless connection, but because I didn't know how hard/easy it was going to be, I initially configured it using a wired connection, and it runs with no problems (samba, webmin, torrentflux b4rt etc...).

I then added and configured the wireless adapter (Linksys wusb54gs v. 2.1) using the instructions on [http://ndiswrapper.sourceforge.net/]("http://ndiswrapper.sourceforge.net/"), and it works flawlessly with my WPA encrypted network. I can use webmin, torrentflux etc. over the wireless just by accessing the relevant IP.

**Now the problem: Whenever I disconnect the cable from the wired connection or bring the connection down (sudo ifconfig eth0 down) I loose the wireless connection to the server as well.**

I have tried:
[LIST]
[*]Configuring only the wireless (and loopback) interface to come up at boot.
[*]Restarting networking (sudo /etc/init.d/networking restart)
[*]Bringing the wireless down and up again (sudo ifconfig wlan0 down | sudo ifconfig wlan0 up)
[*]Restarting wpa_supplicant from wpa_cli
[*]Both DHCP and static IP configurations
[*]Taking eth0 down from webmin (I don't know how it does it, but I assume it simply runs ifconfig eth0 down as well)
[*]sudo ifdown -a | sudo ifup -a
[*]... probably some more ...
[*]... and pretty much any combination of the above
[/LIST]

It seems really weird to me. Why does unplugging the ethernetcable stop the wireless adapter from working? The only sensible explanation I can come up with would be that DNS lookups are using the wired connection, but /etc/resolv.conf doesn't change...

Any help would be welcome. I searched google and these forums with no result. Apologies if I missed the answer.


My setup:
[list][*]*Linux:* **Ubuntu Server, kernel 2.6.24-17-server**
[*]*Wired networking:*Onboard connection (MCP integrated nVIDIA MAC +** Realtek 8201BL PHY** on an Asus A7N8X-X motherboard)
[*]*Wireless networking:* USB adapter **Linksys WUSB54GS** using NDISwrapper 1.52 (standard version from the ubuntu repositories) with the bcmrdnis driver as per instructions on the NDISwrapper site
[*]*Wireless AP:***Linksys WRT54GC** running in mixed mode on channel 6 with broadcasting enabled[/list]

---

