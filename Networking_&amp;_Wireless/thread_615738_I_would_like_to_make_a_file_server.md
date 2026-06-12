---
title: "I would like to make a file server"
date: 2007-11-17
forum: Networking &amp; Wireless
---

### Post by niw_uk1964 on 2007-11-17
I would like to make a file server to stream audio/video etc to other pc's on my network running a variety of windows and linux os's.

What version of Ubuntu would be right for this and is there a link to a how-to for this? I'm a Linux networking newbie!

TIA.


Nige.

---

### Post by jetsam on 2007-11-17
I found this link useful as a jumping off point for setting up a home server:

[http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/]("http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/")

It was written for Feisty, but works with Gutsy.  

Hurdles I had while setting up:
--Network Manager was causing problems and leaving warnings in my Syslog.  Since I have a simple wired network, I just uninstalled Network Manager and set my wired connection to use DHCP under Applications-->System-->Network in the Xubuntu control panel.  

--Samba was a bit tricky.  I wanted to use SWAT to configure it.  To use SWAT fully, you need to install it through Synaptic, then enable the root account password on your server and log into the SWAT webpage at localhost:901 with user root and your password.

--Mounting the Samba shares on Ubuntu through cifs  took some time to figure out.

You have a ton of options, but this setup has worked well for me for about a week.  I serve audio just through Samba and use Amarok as a client on Ubuntu and Media Monkey on WIndows (it's free as in beer, but not as in speech, but it plays .ogg files natively).  There are a lot of possibilities for more elaborate  dedicated streaming, but I haven't found the need to look into them yet.  

The only option you probably shouldn't use is the Ubuntu server edition.  It's a bare bones Ubuntu install intended for experienced server administrators,  and you would likely find yourself in over your head.

---

### Post by niw_uk1964 on 2007-11-17
Thanks very much for the help. I was thinking of buying a NAS hdd, but I have some old pc hardware knocking around and thought a dedicated media server would probably work better and, I might learn something from the exercise too. Cheers!

---

### Post by HermanAB on 2007-11-17
TO set up Samba, go to the samba web site.  All the info you need is right there.  BTW, there is a new version of Samba coming out on Monday.

---

