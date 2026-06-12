---
title: "[SOLVED] ubuntu server &amp;amp; wireless"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by anewguy on 2008-12-20
I want to play around a little with the server addition, so to get started I want to follow these instructions (using the current release of course):

[http://www.howtoforge.com/ubuntu-home-fileserver]("http://http://www.howtoforge.com/ubuntu-home-fileserver") 

to just get started with some simple things.

I don't have the cable currently to connect that box to one of the ports on the back of my wireless router.  I do have a USB stick wireless adapter that works fine in Ubuntu.  Will I be able to access the server box via http from a box that is hard wired to the wireless router (ie., if I set address as static for the server at xxx.xxx.xx.xxx, will I be able to get to it via [http://xxx.xxx.xx.xxx](http://xxx.xxx.xx.xxx)).  

Any help would be appreciated!

dave :)

---

### Post by Carl Hamlin on 2008-12-20
> **anewguy said:**
> I want to play around a little with the server addition, so to get started I want to follow these instructions (using the current release of course):

[]("http://www.howtoforge.com/ubuntu-home-fileserver")  

to just get started with some simple things.

I don't have the cable currently to connect that box to one of the ports on the back of my wireless router.  I do have a USB stick wireless adapter that works fine in Ubuntu.  Will I be able to access the server box via http from a box that is hard wired to the wireless router (ie., if I set address as static for the server at xxx.xxx.xx.xxx, will I be able to get to it via [http://xxx.xxx.xx.xxx](http://xxx.xxx.xx.xxx)).  

Any help would be appreciated!

dave :)

-----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

I've currently got two Ubuntu servers running on my home network. Neither of them were ever able to see wireless, be it PCI, XPCI, or USB. However, they were able to detect and use ethernet via the onboard ethernet ports right away.

It's always possible that your experience might be different, however, and if it is, I'd be interested in hearing about it.

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAklNhQwACgkQyLm4ydrABvdxGgCfSEPOPd4WtOnWU8AJnhJ249Yo
6o8AoIyAsvVm7PDwvmVNnwPm0dthEeCr
=Uhci
-----END PGP SIGNATURE-----

---

### Post by albinootje on 2008-12-20
> **anewguy said:**
> 
I don't have the cable currently to connect that box to one of the ports on the back of my wireless router.  I do have a USB stick wireless adapter that works fine in Ubuntu.  Will I be able to access the server box via http from a box that is hard wired to the wireless router (ie., if I set address as static for the server at xxx.xxx.xx.xxx, will I be able to get to it via [http://xxx.xxx.xx.xxx](http://xxx.xxx.xx.xxx)).  


If your own box, the router and your Ubuntu-server all use the same network-range (For example 192.168.1.0/24), then they should be able to talk to each other.

---

### Post by anewguy on 2008-12-21
I'm thinking here I may even be dumber than I thought, so let me ask - if I want a NAS to store both Linux and Windows files on, and be available across my wireless network (the main Windows box is directly connected to a port on the back of the router for legal reason for my part time work).  I have a cable modem as the first box in, then a Vonage box as 2nd, and finally from the Vonage box to a wireless router.  The wireless router currently has 1 Windows box directly connected to one of it's wired ports.  I have another older machine I want to use as the NAS, and a 3rd box with Ubuntu on it.  I'm thinking now I may need to hook up my PC's differently from what I was thinking:  can I use a network hub, hook up the direct link to my router to it, and hook up both of my other computers to it, then access the internet via 2 machines and leave the 3rd as NAS?

Any thoughts on this and how to do it in Ubuntu would be greatly appreciated!!

Thanks for your time!
dave :)

---

### Post by superprash2003 on 2008-12-21
well.. most probably you wouldnt need to do any changes with the current setup if all the machines are getting an ip from the same gateway.. in your windows pc type ipconfig in the command prompt and in the liinux pc type ifconfig in the terminal.. you would get information on the machine's ip and its gateway . post ip info of all machines and its gateway ip .. 
  for file sharing you could use samba.

---

### Post by BDNiner on 2008-12-21
That would work so long as there is only one device handing out IP addresses on the network. The wireless router would be the one doing that in your case. You will not be able to browse to [http://x.x.x.x](http://x.x.x.x) until you get some kind of http server setup like apache. You will be able to setup network shares using samba and browse to them using smb://x.x.x.x which would be the correct protocol in this case.

---

### Post by anewguy on 2008-12-21
Thanks for all the replies!!  So, should I install the server edition then?  Also, any ideas on how to get wireless working on the server?  I know with the desktop version it just automatically rfound it(I got lucky or they've really improved wireless detection and support!!), but the server edition, at least so far, doesn't see it.  I've been following the instructions on the site I linked to in my initial post, and now I'm at the point where it is supposed to get on the net but I can't get there since the wireless isn't working.  Is there a way to do this all through the command line?  Does the server need to make an "outbound" connection to the router somehow (when it does work) or do I need to turn on some sort of port forwarding in my router and then requests from other PC's will get wirelessly routed to the server?

I have been following this link and got down to where it wants me to access the internet and now I'm stuck.  I seem to need to be able through the command line to see if my wireless is even detected for use (it shows on lsusb, but that doesn't mean much), how to be sure the driver for it is installed and working, and then how to manually set up the information for wap, etc., so I can connect to the router.

[http://http://www.howtoforge.com/ubuntu-home-fileserver]("http://http://www.howtoforge.com/ubuntu-home-fileserver")

I know that's a lot of questions, and rather disjointed.  As you can tell, my knowledge here is very limited.  Any servers we did at work (and I haven't worked since 1996) were Windows and obviously all hard-wired, so this is just as good as starting from scratch for me.  I feel a little stupid, but hey - I gotta learn somehow, right?  ;)

Thanks again for all the replies!

Dave :)

---

### Post by anewguy on 2008-12-22
Okay, I'm still stuck.  I manually (via lwconfig) set the password and session id of my wireless adaptor, then did a if-up on wlan0, then started dhclient3 on wlan0.

Following the example in the aforementioned link I am following, I set my host name to server1.  On the router, I can see and add server1 and it's MAC address to the MAC filtering (the router does show it and I just clicked "add" and "apply").

It would seem that is all I can do though.  I've tried a ping to yahoo (also tried google) and it always comes back saying unknown host [www.yahoo.com](www.yahoo.com), so I assume that the server, via the wireless connection, is not getting to the DNS servers.  It also fails when I try to ping my Windows computer that is hard wired to a port on the back of the router, but I can only assume that's because of something like the workgroup name or not even having enough packages installed to be able to do anything yet.

I am at the point, on page 3 of the instructions in the link, where it wants to go online and grab a bunch of stuff.  If I can't even ping yahoo, I know that the apt-get will fail since it is just using named addresses as well.

My /etc/network/interfaces file is kind of a mess (it doesn't even work) and it doesn't have anything for wireless in it yet.  I do need help knowing what that should look like.  I've done some searching, and I find pages that say I need to put in wlan0 obviously, but also things like wireless-ssid, etc., and I just really don't understand enough of what's going on to set that all up.  If I can get my wireless defined correctly and have it start automatically /etc/init.d/networking then I think things would work.

Right now all I know is this:

for the server:

[LIST]
[*]the hostname of the server is "server1"
[*]the wep key is 10 regular numeric digits
[*]I did not assign an IP address to the server yet as I don't know how that works
[*]the server at some level, with my manual entries noted above, does connect to the router at some level as it gets an IP address assigned to it from the router and lshw -C network shows the corresponding IP address
[/LIST]

for the router:

[LIST]
[*]I reset the security down from wpa2-psk(aes) to wep
[*]I reset the wep key (shows as key1) to the same 10 regular numeric digits I specified in the server definition of the wireless adaptor.
[*]The router "sees" the server at some level, as it shows in the MAC filtering setup (I just simple clicked "add" and "apply")
[*]The router assigns an IP address to the server
[/LIST]

in general from the server:

[LIST]
[*]If I ping a named address such as yahoo, ig comes back with the error "ping: unknown host www.yahoo.com" (same for google)
[*]If I ping my Windows PC by name I get the same type error
[*]If I ping my router or my Windows PC by IP address I get the error "From 192.168.1.200 icmp_seq=xx Destination Host Unreachable".  This seems weird to me, as 192.168.1.200 was the address I assigned the server when in installation, and it went on eth0 - the internal adapter card, not the wireless.  eth0 also has addresses specified for network, broadcast, gateway and dns-nameservers, all pointing to a port on my router.
[/LIST]

I don't know if any of what I have here makes any sense or if it's enough for someone to help me.  I assume that if I can get wireless up on the server, then do whatever (I have no clue for Linux) to set my workgroup (and domain?) the same as what my Windows box is, that I will be able to get this to work.

Help??

Thanks!
Dave :confused:

---

### Post by anewguy on 2008-12-23
> **Carl Hamlin said:**
> -----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

I've currently got two Ubuntu servers running on my home network. Neither of them were ever able to see wireless, be it PCI, XPCI, or USB. However, they were able to detect and use ethernet via the onboard ethernet ports right away.

It's always possible that your experience might be different, however, and if it is, I'd be interested in hearing about it.

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAklNhQwACgkQyLm4ydrABvdxGgCfSEPOPd4WtOnWU8AJnhJ249Yo
6o8AoIyAsvVm7PDwvmVNnwPm0dthEeCr
=Uhci
-----END PGP SIGNATURE-----

Just FYI - I did get wireless working on the server.  I had to set up the /etc/network/interfaces file correctly (someone gave me a LOT of help!).  Now the only network connection to the server is wireless.  My Windows PC sees the server and sees the disk I want to share, so that part is working.  I just have a small permissions problem right now that won't let me actually open the disk.  If you would like more info, PM me and perhaps we could get your servers working wirelessly as well?

Dave :)

---

### Post by Carl Hamlin on 2008-12-23
> **anewguy said:**
> Just FYI - I did get wireless working on the server.  I had to set up the /etc/network/interfaces file correctly (someone gave me a LOT of help!).  Now the only network connection to the server is wireless.  My Windows PC sees the server and sees the disk I want to share, so that part is working.  I just have a small permissions problem right now that won't let me actually open the disk.  If you would like more info, PM me and perhaps we could get your servers working wirelessly as well?

Dave :)

-----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

That would be great. If we get them working, I'll post the involved steps here so everyone else can benefit as well.

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEUEAREDAAYFAklRFDEACgkQyLm4ydrABvcP+wCYrAa91jkvZZXGh05fOS6wcLGc
dACgug3BUMy8hfxApFRrdkoY/yAT2NM=
=MY8n
-----END PGP SIGNATURE-----

---

