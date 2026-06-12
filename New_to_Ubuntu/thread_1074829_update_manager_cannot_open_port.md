---
title: "update manager cannot open port???"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by tubaking182 on 2009-02-19
i did some searching and i cannot find the answer to my prayers, i was at home where i had to access the internet through a socks5 proxy via my G1, but i was unable to use apt-get or the update manager through the proxy. i searched all night and was unable to find any settings that worked to get my installs from apt-get or update manager. so i gave up finally and and went to a buddy's house where i am at this very moment, now that i am not trying to use a proxy, the computer is trying to use a proxy. i went into system>preferences>network proxy and changed to direct internet connection, and hit apply system wide, and disabled my proxy settings in firefox, but still now dice.

when i try to install my updates from update manager i get the following error:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcups2_1.3.9-2ubuntu7_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcups2_1.3.9-2ubuntu7_i386.deb)
  Could not connect to localhost:1080 (127.0.0.1). - connect (111 Connection refused)

is there an easy setting that allows me to tell it to stop trying to go through the proxy? i need to get these updates because my system has been freezing and i have been told these should help

i am currently running ubuntu 8.10 on my P.O.S. gateway notebook. if you need more info i can get it for you. i am not a n00b, been running ubuntu since 7.10, almost two years and i know for the most part what i am doing.
thanks in advance for the help

---

### Post by cariboo on 2009-02-19
Did you restart networking after making the change? You can simply reboot, or open an Applications-->Accessories-->Terminal and type:

```
sudo /etc/init.d/networking restart
```

Jim

---

### Post by IwarV on 2009-03-04
Having a similar problem I hope someone can help me with.

I replaced my Netgear RP614 router with the DLink DIR-655 yesterday, because she-who-must-be-obeyed bought herself a netbook and needed wireless.
Long story short; got wired connections working, wireless working, we can both surf and do e-mail.

But for some strange reason the OOTB router won't allow Ubuntu updates.
Obviously, I need to flay this thing into shape.

Did a lot of googling and a lot of articles/posts with similar issues, but none with constructive replies.

The only noticable thing is that the new router issues IP addresses to attached machines from 192.168.0.199 downwards, whereas the Netgear issues them from 192.168.0.1 onwards.

Any boffins out there that can shed a light?

---

### Post by civillian on 2009-03-04
Not sure how/if this can help, but synaptic/apt-get runs through the same port as the browser (or it can...).

I got similar messages to yours (> W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...untu7_i386.deb](http://us.archive.ubuntu.com/ubuntu/...untu7_i386.deb)
Could not connect to localhost:1080 (127.0.0.1). - connect (111 Connection refused)
) when synaptic was trying to connect directly, not through the proxy server I use. (wwwcache.uni.ac.whatever)
If your directing your web browser through a proxy & specific port, you can tell synaptic to use the same proxy address and portn nunber, and it ought to start working.
(I had this issue at my uni and only just figured it out *'_'*

I know it doesnt address the issue of routers but its a possible fix.

---

### Post by IwarV on 2009-03-04
Fixed it I think.
When I googled "synaptic manager problems connecting" I was linked to this ([http://ubuntuforums.org/showthread.php?t=241110](http://ubuntuforums.org/showthread.php?t=241110)) forum thread.

Turns out, I just needed to copy the DNS addresses that the DLink router had into my /etc/resolv.conf. Problem solved!

Why I never had any problem connecting to (other-) websites without these is a mystery to me. Go figure.

Thanks for reading / helping.

---

### Post by civillian on 2009-03-04
mark as solved then?
Glad your sorted out :D

---

### Post by civillian on 2009-03-04
mark as solved then?
Glad your sorted out :D

---

