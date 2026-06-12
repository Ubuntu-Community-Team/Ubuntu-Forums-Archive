---
title: "run script when wwan0 interface obtains IP address"
date: 2014-12-16
forum: Networking &amp; Wireless
---

### Post by marchello_lippi2 on 2014-12-16
Hi all, 

My need is to run script when wwan0 interface obtains IP address. 
How do I perform it? 
Thanks ahead.

---

### Post by marchello_lippi2 on 2014-12-16
less /etc/network/interfaces
> 
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
auto eth0
allow-hotplug wwan0
iface wwan0 inet dhcp
post-up /etc/network/if-up.d/wwan0_is_up
/etc/network/interfaces (END)


less /etc/network/if-up.d/wwan0_is_up
> 
#!/bin/sh

echo "wwan0 is up"
aplay /home/ymarkiv/Dropbox/music/wav/bird.wav
xmessage -nearmouse -buttons continue:0,stop:1 "wwan0 is up"
/etc/network/if-up.d/wwan0_is_up (END)


Yes, I performed 
sudo chmod +x /etc/network/if-up.d/wwan0_is_up

But script doesn't run after wwan0 interface obtains IP address. 
What else should I do to make it work? 
Thanks ahead.

---

### Post by Ersin Kandemir on 2014-12-16
I wrote a post on my blog about similar issue:[ Run/Trigger Something on Wireless Dis/connection With Bash ]("http://ersinkandemir.cf/posts/243528")

---

