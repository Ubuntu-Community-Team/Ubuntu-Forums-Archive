---
title: "how do i connect to my work server and printers?"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by gettinit on 2008-06-12
Out of the 8 printers in my office I can only connect to the one old laser jet in the back! Searched for it on the network, found it, got the driver works great..

The ones I really need are for a ricoh/savin but I can't find them in the list any ideas would be great..

Also how do I connect to the server in my office? 
Keep it simple Im still kinda new! 
Thanks!

---

### Post by cmnorton on 2008-06-12
As to printing, you can use smbclient from an X-term (conmand line).

smbclient -L your-domain-controller (either dns name or ip-address)

You'll probably want to pipe this into less, because a lot of stuff prints out

smbclient -L our-domain-controller | less

This link I found useful:

[http://learnlinux.tsf.org.za/courses/build/net-admin/ch08s02.html](http://learnlinux.tsf.org.za/courses/build/net-admin/ch08s02.html)

I have found using CUPS' web interface to be the most useful in configuring printers, though Ubuntu's printer config interface is quite good. If your printers are true print servers, the best way to get to them is by app jet direct, and giving a socket address. port 9100 is assumed, and most modern non-hp printers answer at that port.

As to connecting to your server, on your top menu there should be a pick called places or locations, and you can enter the string smb://your-domain-controller, a lot of interesting stuff should print out, and you can start finding available shares from there.

---

