---
title: "Samba being incredibly slow"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by trillex on 2009-04-11
Hello there,

I currently got a ubuntu server going. It's been a bit of a project to make it work and did so I could remove several things away from my other computers. It's at the moment functioning as a fileserver with lots of little things to it, that should help me out further down the road. It's meant to be a house server, nothing more. 

Currently it got this installed:

Torrentflux B4rt
Apache
Webmin
Samba
Postfix (plus ClamAV and Dovecot)
Apache got wordpress going but it's not something that is taking a lot of hits. 

I've run into a very annoying issue: Samba is very _very_ slow. I'm talking about 4.5 mb/s tops. This is a bit of an issue, as it is used to stream music to various puters as well as movies/series to my mediacenter. If a lot is going on at the same time, it will make everything stutter. 

Reason I'm not making it a sole Samba thread is because I do not think that Samba is the issue. I've tried a couple of various fixes to smbconf (Like socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192, which only gave me about 0.5 mb/s extra). I'm also seeing a bit of a huge load on the CPU. 

A brief look at top shows smbd to be the highest user of CPU. Load average is 2.47, 2.46, 2.30. 

I know that torrentflux is probably a culprit but I wonder if there are any kind of fixes, tweaks or other "fun" things I can play around with so I can get my samba speed up. It is probably the biggest factor in this server and the main reason I got it. Please do not suggest removing somethings, as I also need all the other ones. :)

It's a E6200 processor.

---

### Post by lfaraone on 2009-04-11
Seriously, unless you throttle down your torrenting there *isn't* a fix, other than to split it off to a separate box or upgrade your hardware.

---

### Post by MrWES on 2009-04-11
Samba is slow -- period.

If you have a lot of torrent leechin' going on you might look at your router and see if it offers QoS -- Quality of Service option. I run Tomato firware on my Linksys router and it helps, but Samba is still slow. Might look into mounting via cifs -- might be a tad faster.

Bill

---

### Post by lfaraone on 2009-04-11
> **MrWES said:**
> Samba is slow -- period.

If you have a lot of torrent leechin' going on you might look at your router and see if it offers QoS -- Quality of Service option. I run Tomato firware on my Linksys router and it helps, but Samba is still slow. Might look into mounting via cifs -- might be a tad faster.

Bill
Or you can use HTTP/anon-FTP if authentication isn't important.

---

