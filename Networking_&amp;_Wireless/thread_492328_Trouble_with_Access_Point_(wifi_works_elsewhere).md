---
title: "Trouble with Access Point (wifi works elsewhere)"
date: 2007-07-04
forum: Networking &amp; Wireless
---

### Post by equant on 2007-07-04
I have a thinkpad 42 with working wireless.  That is, working when I'm at my home network, and several public access points.
 
I am at a hotel in Denver, and can not get it to work.  If I run windows, the wireless works just fine, so I think the access point is ok.  When using linux, dhcp returns an IP, and it works for about one or two webpages before dying.  Then I can't ping anything.  If I try to release and renew my dhcp lease, I get no reply.  iwconfig shows the correct essid, and a strong signal. 
 
If I change the essid to something that doesn't work, do dhcp, let it time out (it gets nothing of course) change the essid back to the ap I'm wanting, and run dhcp again, I'll get the same IP that I got the first time, but not be able to get any network activity. 
 
Some things I've noticed...
 
There are a lot of access points from my hotel room.  I think around 9.  Only windows can give me a list.  I can't get a list (or don't know how) from the linux side of things.
 
eth0:avah sometimes shows up with an IP, but eth0 is not my wireless card (it's eth1).  Also, the IP it has isn't a valid IP for the A.P. I'm trying to use.
 
I'm using xubuntu.  recent.  6.10 or newer.  Don't remember off hand.
 
Any ideas?
 
Also, how do I dissable avahi from running at startup?
 
Thanks,
Nathan
Tucson, AZ USA
[http://retards.org/](http://retards.org/)

---

### Post by ubuntu.daemon on 2007-07-04
lol ive had your problem!  leave avahi alone bc what that does i believe is gives you an ip if you cant connect to a wireless signal, so loading goes faster, instead of waiting forever for it to time out.  Install wifi-radar bc that seems to works best for xubuntu honeslty, oh and btw im using a x31 =]  ,  and what wireless util are you ising for windows??  bc even the one that comes standard should give you a list i believe.  and the windows on might not be connecting to the one your linux one is connecting too, oh and that might be a trap, especially in a hotel ><  ive seen those in airports, it will say free public wifi!  but you will have to have file sharing for it to work, so basically the wap probably wont work bc your using linux and the user who has the wap cant get into your files. SO BE CAREFUL!!!

hit me back:popcorn:

---

### Post by equant on 2007-07-04
I've left avahi alone, but it's odd that it's creating eth0:avah with an IP address that shouldn't be coming from anywhere.  It's a 192.167.200.x address when the hotel's AP ('stayonline') only gives out 192.167.50.x ips, and the only place I ever use eth0 has .1.x or .11.x addresses.

I double checked that in Windows and linux the wireless is connected to the same access point 'stayonline'.

Thanks,
Nathan

---

### Post by ubuntu.daemon on 2007-07-04
like i said it just creates one till you connect to a wireless or wired internet, but if linux wont connect and windows does, i wouldnt use it honestly,  do you have file sharing enabled in windows?  Just ask the clerk at the desk if they have free wireless and what it is and use that, grab wifi-radar, if your going use windows, i really wouldn't use that connection,

---

