---
title: "PC seems firewalled, but I didn't install a firewall!"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by theschles on 2007-04-25
I just set up xubuntu 6.10 on a P3 laptop.  I originally tried krfbserver with UltraVNC as a client from my windows laptop, but in terminal windows, it sometimes thought I was holding down the enter key for no apparent reason.

So I tried installing vnc4server, tightvncserver, and then x11vnc with no luck.

Then I stumbled across this post on vnc4server:
[http://grumpymole.blogspot.com/2006/12/xubuntu-remote-desktop-with-vnc4server.html](http://grumpymole.blogspot.com/2006/12/xubuntu-remote-desktop-with-vnc4server.html)

Trying a local loopback wouldn't work, so then I tried this post on x11vnc:
[http://www.ubuntuforums.org/showpost.php?p=771174&postcount=61](http://www.ubuntuforums.org/showpost.php?p=771174&postcount=61)

Now I could get local loopback.

So I went back to my windows laptop and tried to vnc into the xubuntu laptop.  No dice.  

I then tried pinging it.  No dice.

iptables reports no rules whatsoever:
[http://paste.ubuntu-nl.org/17540/](http://paste.ubuntu-nl.org/17540/)

I can surf from this xubuntu PC, and can use smb4k to browse the home network.  Everybody's on the same subnet (i.e. 192.168.x.y where the x's are the same and y's are .100 and .101).

What's going on??????  Help???

---

### Post by grumpymole on 2007-04-25
theschles,

What is the IP address of the gateway on your network?  netstat -nr and check for gateway address for the flags entry that has UG.  Can you ping that?  Normally, it's 192.168.x.1 or something similar.

The other thing that keeps coming back to me is that I have sen the Connection Refused (111) error before and it wasn't a networking issue.  Even though the message sounds like one.

You say that the Xubuntu machine can see the SMB network, which makes me think that there must be some connectivity between the machines.  Are you able to try and ssh into the Xubuntu machine?

I'll look for you in #xubuntu  again.  I'd like to find out the end result of your problem.

Cheers

Warren

---

### Post by dreadlord_chris on 2007-04-25
Just so you know - Ubuntu comes with a *firewall* already installed - it's called iptables
There are a number of GUI's for iptables - with Firestarter probably being the easiest for new users.

---

