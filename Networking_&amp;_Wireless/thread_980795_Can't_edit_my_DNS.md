---
title: "Can't edit my DNS"
date: 2008-11-13
forum: Networking &amp; Wireless
---

### Post by I_love_Life on 2008-11-13
Hello, i tried to edit my DNS server but whatever I do it remains the default.

I tried via the graphical uses interface - it doesn't work

I tried via "sudo gedit etc/resolv.conf" - it doesn't work

I tried to change permissions via "sudo chmod "0660 etc/resolv.conf" and then "sudo gedit etc/resolv.conf" - it doesn't work

I tried after I edited to change to "sudo chmod "0440 etc/resolv.conf"- it doesn't work

However I edit the address it always keeps coming back to the same settings :( can someone give me an idea pls ?

---

### Post by superprash2003 on 2008-11-13
[http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by Iowan on 2008-11-13
I'll throw in my nickel's worth (2 cents - before inflation). Your resolv.conf file may be getting updated (or put back) by dhclient.  By using the **prepend** mentioned in the link, your information gets put in resolv.conf.  Now, I hope my nickel isn't wooden...

---

