---
title: "Internet Connection Sharing"
date: 2007-03-31
forum: Networking &amp; Wireless
---

### Post by chamberlain2006 on 2007-03-31
Hi, i need to share my wireless connection through my ethernet connection.  My wireless card (wlan0) is connected to my wireless network and the internet, and my ethernet device (eth0) is connected to a hub and other computers which need internet.  How can I share the internet connection?

---

### Post by jorno on 2007-04-02
Setting up a DHCP daemon, you'll give the other computers on your hubbed network an IP-address.

By playing a little with IP-tables, you could "open the connection-sharing". Try googling for "iptables masquerading".

I'm a bit disapointed that I can't seem to find such a howto within the Ubuntu Wiki. But I know there are lots of documents explaining this out there...

EDIT: However, I did find something in these exact forums...
[http://www.ubuntuforums.org/showthread.php?t=91370](http://www.ubuntuforums.org/showthread.php?t=91370)

I'm new to these forums, but from what I've seen so far, I bet you could find hundreds of others in the same situation as you (almost), who's gotten good help. Try searching this forums, and if you can't seem to find anything, please tell me - and I'll try helping you a bit more.


Good luck from Norway.

---

### Post by chamberlain2006 on 2007-04-03
Phenomenal!  I finally got this figured out.  It needed some configuration of dhcp3-server, but eventually I got it all worked out, and now I can have another computer and XBOX using the connection!

---

### Post by jorno on 2007-04-04
Nicely done! Congratulations :D It's fun when it's all rolling... =)

---

