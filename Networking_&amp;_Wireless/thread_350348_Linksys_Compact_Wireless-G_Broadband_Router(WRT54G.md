---
title: "Linksys Compact Wireless-G Broadband Router(WRT54GC) - It's Alive!"
date: 2007-01-31
forum: Networking &amp; Wireless
---

### Post by merecats on 2007-01-31
Hello everybody.  

This is my first post as a Linux user....in a Linux forum....running a Linux distro!  

Over the past few weeks I've been trying to get my wireless connection running at home.  Nothing fancy, just a tidy little Linksys Wireless broadband router and a standard Toshiba laptop - all straight out of the box.  

This 'network' had been running fine under Windows XP Home (same hardware) but failed to work at all under Ubuntu Dapper.  There was lots of tweaking, head scratching, and mumbled expletives, and many an hour spent booting Windows checking the web then rebooting linux with new ideas - good fun.  

My first attempt was plugging the laptop into the router with the cable.  Without doing anything Ubuntu recognised the network and logged me in.  Then came the wireless attempt which failed straight away.  My next big step was to find that if I disabled the network key Ubuntu would connect to the wireless network without pressing any buttons!  But, with the key renabled No Joy.  

I tried many 'iwconfig' and'ifconfig' commands (without knowing what I was doing).  Also, running the various network managers to no avail.  

To cut to the chase, the following few simple steps got my connection running and I thought I would share this with anyone that happens to find themselves in my past condition: 

Within a Terminal:
Change the default policy context in both the following files so that it says 'allow' instead of 'deny'
  
$ sudo gedit /etc/dbus-1/system.d/NetworkManager.conf
$ sudo gedit /etc/dbus-1/system.d/nm-applet.conf

	<policy context="default">
		<allow own="org.freedesktop.NetworkManager"/>
		<allow send_destination="org.freedesktop.NetworkManager"/>
		<allow send_interface="org.freedesktop.NetworkManager"/>
	</policy>

Then restart the dbus
```
sudo /etc/init.d/dbus restart
```
and launch the applet
```
nm-applet
```



Back on the desktop, near the system clock, double click the network icon (two monitors) and select your network.  The network icon changes and a dialog opens.  In this dialog enter your network key.  Another dialog will open asking for you to enter a ring password (HELP: I'm not sure, yet, what this is but entered one anyway).  The icon then changed to a wireless connection power bar and that was it!  

Please feel free to explain any of this (I obviously stumbled into this!).  HTH someone, 

Merecats

---

### Post by l951b951 on 2007-01-31
> **merecats said:**
>  Another dialog will open asking for you to enter a ring password (HELP: I'm not sure, yet, what this is but entered one anyway). 
Merecats

**Disclaimer**:  I am also a newbie.  I could be dead wrong about anything I say.
In this instance, the keyring holds your network keys securely.  Whenever you boot up, nm-applet will request your keyring password.  It uses the keyring password to unlock the keyring, from which it gets your network key.  I'm not sure if there are other uses for the keyring (i'm sure there are because I believe it is a gnome component not a nm-applet component).  I'm also on the nm-applet mailing list (as a lurker, most of the posts are over my head), and I have read a post or two saying that future versions of nm-applet will store the keyring password and you will only have to enter it at installation once instead of entering it at every boot-up.  But I can't guarantee that, it's just the word on the mailing list. 

I am posting using my Ubuntu Dapper laptop (converted 1 month ago).  So, again, my post is from relatively little experience.

---

