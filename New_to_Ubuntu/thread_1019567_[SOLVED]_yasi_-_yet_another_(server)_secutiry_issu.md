---
title: "[SOLVED] yasi - yet another (server) secutiry issue (question)"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by anewguy on 2008-12-23
I just installed and got working the server edition as a very simple server so that I share a disk drive on the server - basically a NAS I guess.  My server connects to the network wirelessly, my Windows PC via hard-wire to the back of the wireless router, and a soon arriving dedicated Ubuntu desktop box will be running wireless.  I have MAC filtering on my router, but only WEP (I couldn't get WPA2-PSK(AES) figured out again using iwconfig on the server).

I have 2 security questions:

(1) The link I followed had me enable the root account on the server as I was setting it up.  After I got all done I think it all could have been done with just sudo.  Is there a way to disable the root login again?

(2) Given my simple setup, is there anyway someone can get from the net through my router to the server, or is it secured?  The server has an assign IP address at the router.

Thank you in advance! (and thanks for letting an old guy ask another one of his zillion questions!!)

Dave :)

---

### Post by wizard10000 on 2008-12-23
Hi, Dave -

1.  To disable root logins do this -

sudo passwd -l root

:)

2.  If your server is on a private network it's inaccessible from the internet unless you've got some ports forwarded to the machine on your router - so if the server's IP address is on the 10.x.x.x, 192.168.x.x or 169.254.x.x networks it has a nonroutable IP address and can't be seen from the internet unless you've done something on the router to make the server visible.

Hope this helps -

---

### Post by anewguy on 2008-12-23
Thanks!!

Dave :)

---

