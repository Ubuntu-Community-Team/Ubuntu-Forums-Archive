---
title: "Basic nfs server setup"
date: 2006-12-01
forum: Networking &amp; Wireless
---

### Post by foldingthought on 2006-12-01
Hi there,

After scouring the threads and google and O'Reilly Linux books from the library, I could not find anything basic in relation to what I want to do - so I had to start my own. 

Basically, I am a n00b - so be kind. 

**Objective** to establish a headless nfs file server to share with os x 10.4.8

I have installed the recent server release of ubuntu on an old g4 Power Mac and I wish to connect to the server through an OS X Powerbook. I want the server to sit there and for me (and others - my xp users will have to work it out themselves) to mount my files on my mac. Basically I need to know the following;

How to set up an nfs server (including editing a file in vi) - with one collective read/write file

How to install another hard drive and create a RAID disk in the server in the OS

How to connect into this server - once established I hope this is the easyist part. 

How to manage this server through VNC/remote desktop/webmin... 

I have been an OS X user for 5ish years and no a limited amount of shell - "echo", "sudo" I think i am exhausted here. So without a point and click thing, I am struggling. Any walk through would be appreciated... 

Kind Regards,

Adam

---

### Post by dmizer on 2006-12-01
there's a fantastic howto on nfs sever/client here in the forums.  see the 4th link in my sig.

realize ... nfs will only work in linux based networks.  if you have a windows computer, (as far as i know) it cannot be configured to share files on an nfs network.  osx on the other hand ... can be configured to do so.

i set up a raid server once, but it was from install rather than after, and i'm not sure i'm qualified to give an acceptable howto.

---

### Post by foldingthought on 2006-12-01
Thanks dmizer...

Have had a look before, however, when i tried to edit the etc/export in vi I got lost. Hence not to sure what to do. Everything has worked well thus far. I have reinstalled and will have another look. 

As I am getting the hard drive this weekend, reinstall will be no problem. It is a matter of getting the things running smoothly...

---

### Post by dmizer on 2006-12-01
try using nano instead of vi ... the commands you need to use for nano are listed at the bottom.  it's significantly more user friendly in my opinion.

so if you run into a howto that says to use "vi" try using "nano" instead.  like so:
```
sudo nano /etc/exports
```

edit:
friendly hint ... in nano, "write out" means save

---

