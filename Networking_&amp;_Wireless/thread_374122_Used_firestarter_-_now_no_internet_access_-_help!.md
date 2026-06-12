---
title: "Used firestarter - now no internet access - help!"
date: 2007-03-02
forum: Networking &amp; Wireless
---

### Post by graham_reynolds on 2007-03-02
I'm a newbie - please help.
My PC is connected to a router - both a wired connection (eth1), and via a USB wireless card (RAUSB).  Router is 192.168.1.1, IP is 192.168.1.3.  There is also an eth0 not connected to anything.  

I was playing around yesterday with firestarter - before use I had full internet connection, after use I had nothing.  I have tried
a) logging in and out - no joy
b) rebooting - no joy
c) using firestarter to 'disable firewall' - no effect
d) running the firestarter wizard to select first 'rausb' as my primary internet connection, then  'eth1' - neither worked.

I'm not using internet connection sharing.  My incoming connections is set to allow bittorrent.  I get no connection whether the outgoing setting is permissive or restrictive.  If restrictive it is set to allow common services (FTP, HTTP, HTTPS, NFS, Samba, etc).

What have I done wrong?  I can usually fix problems but this is tempting me to reinstall - which I shouldn't have to do - Ubuntu (i'm using 6.10) is otherwise pretty high quality software.

Any help appreciated?
Is there a way to reset my IPTables back to default?  if so, how?

---

### Post by zvacet on 2007-03-02
I think you have to tell to Firestarter witch port you use and open it.Don´t reinstal all OS because of one problem.Simplier solution is to uninstall Firestarter,don´t you think?I don´t know if any of this is helpfull to you.

---

### Post by dannyboy79 on 2007-03-02
please post the output from 

sudo iptables -L

DON'T reinstall, please. This and almost every single problem you'll have is fixable. Never reinstall, you won't learn anything!

---

### Post by dannyboy79 on 2007-03-02
to delete all your rules would be 

sudo iptables -F

if you ever want to know how to do something you can always read the man pages. I have learned so much from reading them. So whatever the program is called, it this case, iptables, you would do 

man iptables

then it takes you to the manual for iptables. this works for every command, almost. Not like custom software, like sbackup and things like that.

---

### Post by graham_reynolds on 2007-03-02
Thanks for the ideas guys.  I feel a bit stupid now - when I came home from work the first thing I thought I would try was to remove the usb wireless card (as superflous anyway) - the network then came up on boot.

at least I didn't reinstall.

---

### Post by dannyboy79 on 2007-03-02
not sure how this had anything to do with firestarter or iptables but I am glad you got it working.

---

