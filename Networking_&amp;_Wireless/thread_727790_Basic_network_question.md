---
title: "Basic network question"
date: 2008-03-18
forum: Networking &amp; Wireless
---

### Post by troykm on 2008-03-18
i have two laptops running ubuntu 7.10.  i have my music library on one and want to access it from my other laptop via a network. how do i do this? i have no idea how to connect 2 pc's together 

any help appreciated 

thanks

---

### Post by yeats on 2008-03-18
Are you already using a wireless router or other access point?  You'll probably want to give as many specifics about your current setup as possible, as well as your knowledge/experience about networking in general, so when people start throwing terms like "DNS", "TCP/IP" and "lookback" at you they'll know how to phrase it.

---

### Post by troykm on 2008-03-18
i am using a cable wifi modem to access internet. i have very limited knowlage but can learn. both laptops have wifi builtin

---

### Post by superprash2003 on 2008-03-18
its very simple... you need to install samba.. there is a tutorial available at [http://ubuntuguide.org](http://ubuntuguide.org)

---

### Post by Eiríkr on 2008-03-18
Some other thoughts to consider.  Let's call these two machines A (with the music) and B (your laptop).

When you say you "want to access [your music library] from [your] other laptop via a network", do you mean that you want to access the files on A directly from B, for moving them around, adding, deleting, and such?  If so, Samba might be overkill, as it can be extremely complex to set up, and is really much more oriented towards Lin -> Win sharing rather than Lin -> Lin.  The generally easier approach that would give you access both to A and to B would be to install the [font=courier]**ssh**[/font] package on both machines, and then in your file browser you'd be able to type [font=courier]sftp://IP.ADD.RES.S[/font] to log into one or the other.  (You can use hostnames instead of IP addresses if you have a DNS server set up on your LAN {the complex route}, or if you add your LAN hostnames and matching IP addresses to the [font=courier]/etc/hosts[/font] file {the simple route}.)

If instead you mean that you only want to *listen* to the music library when using B, and you don't need to access B's filesystem directly, you might want to consider setting up a music server, such as [Firefly]("http://onlyubuntu.blogspot.com/2008/01/howto-setup-itunes-compatible-media.html"), [GnuMP3]("http://onlyubuntu.blogspot.com/2007/04/streaming-media-server-in-ubuntu.html"), or [thread=555241]SlimServer[/thread].  

Cheers,

Eiríkr

---

