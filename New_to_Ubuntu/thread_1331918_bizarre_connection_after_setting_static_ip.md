---
title: "bizarre connection after setting static ip"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by maja_z on 2009-11-19
OK, I've posted this here, because I really have no idea what I'm doing :)

I'm on ubuntu 9.10. 64bit

I've been trying to set up a static ip address to port forward from utorrent over wine..

I tried the terminal way, editing /etc/network/interfaces, but that didn't work.

So I tried simply adding a new profile by right clicking on the network icon and adding a new one, changing the IPv4 settings and setting it to connect automatically and setting eth0 not to do so.

So far so good, ifconfig shows the correct ip. (don't ask about the portforwarding, still doesn't work, but that's a topic for a different thread).

The bizarre part is this: now that I'm on this new connection, I'm still "somewhat connected to the internet" but by somewhat I mean that opening a new page in firefox  will give me a "server not found" error, and the same if I click on the "try again" button. BUT if I double click on the "try again" button, then the page loads. !? 

It's completely weird? I can go back to eth0 and all is normal, and the only difference between the connections is that one has DHCP enabled and the other's method is set to Manual. 

Any ideas?

Thanks!

maja.

---

### Post by skatinjj on 2009-11-19
Can you post the contents of your /etc/network/interfaces?

Also, did you restart the network daemon after updating interfaces:

```
sudo /etc/init.d/networking restart
```

---

### Post by maja_z on 2009-11-19
I reverted /etc/network/interfaces back to the way it was:

```
auto lo
iface lo inet loopback
```Not sure who/what the daemon is, but after I added the new connection I switched to it by clicking on the networkign icon and simply selecting the new connection.

If I try  restarting it (under either connection) I get this: 

```
me@here~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          
Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]
```

Hope this helps!

m.

---

### Post by skatinjj on 2009-11-19
[This]("http://ubuntuforums.org/showthread.php?t=1309835") thread should be what you need.

---

### Post by maja_z on 2009-11-19
Thanks skatinjj!

OK, so I've uninstalled the network manager:

```
sudo apt-get remove network-manager network-manager-gnome
```then edited /etc/network/interfaces to:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.10
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1
```ifconfig shows the ip to be 192.168.1.10, so that's fine.

but restarting the 'dameon' gives:

```
me@here:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          
SIOCADDRT: File exists
Failed to bring up eth0.
                                                                         [ OK ]
```

---

### Post by skatinjj on 2009-11-20
If the IP address you have now is the one you were using with DHCP (or when you got the screwy internet connetion) try changing to another IP address and that should work.

---

### Post by maja_z on 2009-11-20
[SIZE=1]Cool, thanks!

A changed /etc/network/interfaces to 192.168.1.100 and changed the router DHCP settings to only assign up to .99.

A couple of reboots later, it seems to be working fine! The static ip that is. 

I've set up the port forwarding on the router port 6881 to 192.168.1.100 and in the terminal typed 

```
sudo ufw allow 6881
```and for the first time ever utorrent has a nice little green icon saying "your network is working like it should"! Hooray!

However... [http://www.canyouseeme.org/](http://www.canyouseeme.org/) keeps giving me this error:

[/SIZE]       [SIZE=1][COLOR=red]Error:[/COLOR][/SIZE][SIZE=1] I could **not** see your service on **78.148.244.170** on port (**6881**)
Reason: Connection timed out

[/SIZE]  [SIZE=1][SIZE=1]And (possibly a matter for another thread) the torrents are not actually connecting - all of them have seed and peer readings like 0(299), 0(234) - so many seeds and peers in the swarm, but none connected.

So I'm not sure if the port is actually open correctly or if this is some other issue?

Thanks again for this!

m.[/SIZE]   
[/SIZE]

---

### Post by skatinjj on 2009-11-20
Not sure why you really want to stick with Utorrent, I use Deluge and it works like a charm (never had this issue and with UpnP enabled, I don't have to forward the port manually).

Also, do you have UpnP enabled in Utorrent (if your router supports UpnP)?

---

### Post by maja_z on 2009-11-20
I've tried with both UpnP enabled and disabled, and haven't found any difference.

The utorrent preference is due to the fact that I'm currently still dual booting and am sharing the torrent folders with windows7, although that is probably not reason enough..

---

### Post by skatinjj on 2009-11-21
You can still use a program outside of wine like Deluge. Since its a torrent, the file type downloaded is staying the same.

I like using utorrent on Windows, not linux.

Also, the WINE HQ site shows a bug in utorrent (think version 8 ) where torrents will not connect.  Might want to check that out for yourself to see if it pertains to your version of utorrent.

---

### Post by maja_z on 2009-11-21
Thanks!

I've now reinstalled wine (I had 1.0.1, now 1.1.33) and utorrent (from 1.8.2 to 1.8.5).

This was also based on another thread I started on a utorrent forum [http://forum.utorrent.com/viewtopic.php?id=64450](http://forum.utorrent.com/viewtopic.php?id=64450)

The static ip seems to work OK, but now, with the new re-installation, I think the portforwarding is not working any more. The utorrent icon is now red, although I'm getting amazing download speeds (see the linked thread for screen-shots).

I think I would prefer to stick with utorrent, only because I've found some advanced settings tweaks that get my downloads to ridiculous heights. I'm sure deluge is great, but if I got this far with utorrent, I would hate to loose all this work :)

---

### Post by skatinjj on 2009-11-22
From the linked thread it seems utorrent is trying to bind the port with the IP:0.0.0.0

So you should start googling around for a solution to that.

I will try if I have time but good luck.

---

### Post by skatinjj on 2009-11-22
looks like the binding problem is an issue with winsocket.

Not sure how that is tied into wine, I would try a port you haven't used yet and see if that helps with the connection at all.

---

