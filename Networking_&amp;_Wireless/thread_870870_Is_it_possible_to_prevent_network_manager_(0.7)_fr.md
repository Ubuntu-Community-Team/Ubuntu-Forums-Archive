---
title: "Is it possible to prevent network manager (0.7) from replacing the default route?"
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by motin on 2008-07-26
At home, I share my 3g internet with another computer on a local LAN. 

However, every time I connect to the LAN using network manager the computer seems to think that it is supposed to access internet through the wireless network, which is wrong... ppp0 should this be used for internet. Using dhcp or not doesn't matter.

If I disconnect my 3g connection and reconnect - internet works as expected. I would prefer not have to perform this reconnect everytime I connect to my LAN...

I have configured the connection as a static connection with:

Ip 192.168.111.1
Netmask 255.255.255.0
Gateway 192.168.111.1 (...or 127.0.0.1 - it doesn't matter - and I am not allowed to leave this field empty!)

PS In the long run, I guess it would be better to use Network Manager 0.7 directly to connect to the 3g network, but [I have yet to understand how to do this]("http://ubuntuforums.org/showthread.php?p=5462046#post5462046")...

---

### Post by tiger74 on 2008-08-06
I wonder the same thing.
How to prevent dhcp to create a default route?

---

### Post by motin on 2008-08-11
Got some more hints from tambeti in #nm @ irc.freenode.net:
> 
<motin_0_> I have the following question: Is it possible to prevent network manager (0.7) from replacing the default route? - summarized in a forum post: [http://ubuntuforums.org/showthread.php?p=5539357#post5539357](http://ubuntuforums.org/showthread.php?p=5539357#post5539357)    I'd love it if you know how to achieve this... thanks!
<tambeti> you can edit the connection's ip4 settings and add the default route there
 but you'll need a very recent NM for that
<motin_0_> tambeti: thanks I have a very recent nm, but it doesn't work if I set the default route to the local ip address
 I use ppp for internet access
 so what default route should I then set for it to work?
<tambeti> oh, you don't use NM for all the devices...
 so how do you set up the wthernet device (which gets the default route)?
 if it uses DHCP and the DHCP server sets a default route, NM uses it
 oh... I guess the problem is that NM flushes the existing routes first
 so the only way for your setup to work is to use NM for all the devices, including the 3g device
<motin_0_> tambeti: that's a pity, since currently my 3g device doesn't work with nm...
 tambeti: but thanks for the pointers - maybe I can prevent nm from flushing the existing routes in some way?
<tambeti> you can't do that
<motin_0_> tambeti: do you know the commands used to flush existing routes?
 there must be a way for me to save the routes, let nm flush them, and then restore them
 tambeti: actually - I'd prefer to use nm to handle my 3g connection, but currently I don't understand how that would be possible. all summarized in forum post here: [http://ubuntuforums.org/showthread.php?t=870862](http://ubuntuforums.org/showthread.php?t=870862)
<tambeti> yes, I read that. does nm-tool list your 3g device?
 flusing the routes is done in src/NetworkManagerSystem.c:nm_system_device_flush_ip4_routes_with_iface()
 or if you were just wondering how, then using libnl
<motin_0_> tambeti: actually nm-tool is broken currently
 using svn20080720t224551
 I'll get a more recent snapshot and try again
<tambeti> svn20080720 doesn't have the UI for setting/overriding routes either
<motin_0_> tambeti: aha, I am confusing routes with the default gateway...
 tambeti: thanks


So, we should get an even more recent snapshot of Network Manager 0.7 to even be able to override routes, but more likely we might have to find a way to save the routes after we are connected using ppp, and have a script restore them after nm has connected to a network. 

Or, we could just try to get NM to handle the 3g connection, but as I said above I haven't got that figured out, see [http://ubuntuforums.org/showthread.php?t=870862](http://ubuntuforums.org/showthread.php?t=870862)

---

