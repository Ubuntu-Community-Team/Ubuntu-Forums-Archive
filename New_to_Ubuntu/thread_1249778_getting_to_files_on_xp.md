---
title: "getting to files on xp?"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by happypizza on 2009-08-25
So, I installed Ubuntu on my laptop that has a whopping 16 gigs of storage. but im not ready to switch my desktop over until ive had more time with it, so can someone show me how i can gain access to my files on my external harddrive on my desktop? is it a matter of just enabling sharing and searching for it over my network? is there maybe a way to make it a mini server and access it onilne? what are my options. I just installed ubuntu last week, so im still a gaint newbie. thanx for any help guys!

---

### Post by infurnus on 2009-08-25
Few things you can do on your windows box (your desktop) to access from your linux machine (laptop).

You can install cygwin and use sshd then ssh in from your laptop into your desktop to access files.

You could also setup a samba share.

You could also install VNC on your windows machine and use xtightvncviewer to visually look at files. Also remote desktop would work.

I think the easiest would be samba but those are a few ideas. Look around on google. I've used all the above methods.

---

