---
title: "DNS entry shuffling"
date: 2007-09-09
forum: Networking &amp; Wireless
---

### Post by robot6868 on 2007-09-09
I was having a problem with Ubuntu being abysmally slower than windows
when it came to web browsing and ssh, etc. 

But I noticed that ssh and aMSN, etc were performing alright after
that super slow initial connection, so I figured it was a DNS issue.

Using this very end of this thread, 
[http://ubuntuforums.org/showthread.php?t=546566&highlight=dns+slow](http://ubuntuforums.org/showthread.php?t=546566&highlight=dns+slow)

I determined that moving the last DNS entry up to the top of
/etc/resolve.conf  
solved the problem and web browsing, etc became speedy again.

However, when I reboot, the order of the DNS entries goes back to
what it was originally, so I have to edit the file every time.

Is there a way I can keep that fast DNS IP at the top?

---

### Post by noob12 on 2007-09-09
Yes, the answer lies in your settings in **/etc/dhcp3/dhclient.conf** (see **man dhclient.conf** for the whole story).

You can supersede the name servers there using a line of the form

```

supersede domain-name-servers your.first.nameserver.ip, your.second.nameserver.ip;
 
```

You can also prepend to the name servers there.
```

prepend domain-name-servers your.first.nameserver.ip, your.second.nameserver.ip;
 
```

The list is comma-separated and ends with a semi-colon.

Of course if you control your own router/DHCP server, then you can usually control this for all clients in that configuration.

You may also find this thread helpful:  [http://ubuntuforums.org/showthread.php?t=543659](http://ubuntuforums.org/showthread.php?t=543659)
for additional tips.

---

### Post by robot6868 on 2007-09-10
Thanks alot, man.

That was a speedy reply, and my troubles are over!
That man page is fairly reasonable too if you search for
key phrases rather than try and read it all at once.

---

