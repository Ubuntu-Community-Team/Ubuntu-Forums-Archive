---
title: "Problem connecting to the Internet, but not with Firefox"
date: 2007-03-10
forum: Networking &amp; Wireless
---

### Post by Cilionelle on 2007-03-10
Hi! Just started using Edgy, liking the look and feel of it, but my resolution is stuck at 640x480.  After some talking back and forth, seems I can download a programme to help me out, and I have a connection to the internet via Firefox, but no connection to the Ubuntu update-y sites to download these new bits and bobs.

I have had a little trouble using Edgy to get a connection in the past, until someone recommended disabling IPv6 (which I have no idea about!).  I did this in Firefox, and it is working, but not elsewhere.  How do I generally disable IPv6, or will that not solve my problem.

I am running my internet connection through a Wireless Firewall Router, but using a cable, to a D-Link modem.  Ta!

---

### Post by Cilionelle on 2007-03-11
Still no luck with this.  I've gotta say, such a small screen is really painful.  Can anyone help me restore full connectivity.  Oh, and it's not the IPv6 thing either.  I've tried a couple of disabling things and none of it has worked.  Even a good strong shove in the right direction would be appreciated at the moment!

---

### Post by Mr. C. on 2007-03-11
Show output of :

ifconfig -a
cat /etc/resolv.conf

and the IP address, netmask and broadcast address you have configured in your router for your LAN.

MrC

---

### Post by mrmonday on 2007-03-11
have a look  at the 8th post [here]("http://www.ubuntuforums.org/showthread.php?t=358749#post2226758").

Hope this helps.

---

