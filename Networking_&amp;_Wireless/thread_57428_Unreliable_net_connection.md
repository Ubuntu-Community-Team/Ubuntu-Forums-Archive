---
title: "Unreliable net connection"
date: 2005-08-16
forum: Networking &amp; Wireless
---

### Post by cenithx on 2005-08-16
Ok i'm pretty new to all this but here goes..

2 weeks ago installed Ubuntu, very very happy with it. Only problem I had is the router-issue everyone seems to be having.. didn't understand the big tutorial about installing new dhcp stuff? but found a way around it by putting in the DNS servers of my ISP into the resolv.conf then locking the file. Seems to work fine for the last 2 weeks EXCEPT:

Net is unreliable. Gaim (just using the MSN part of it) drops out every night without fail while i'm asleep.. I get to the pc in the morning and it just says "Connection lost"

Net speed fluctuates wildly.. network is setup by me with absolutely no networking experience (hey at least i'm willing to try, and learn on the way!).. at the moment I have this PC just with ubuntu on it, and another PC with XP Pro on it (gf's).. they both go into a Netgear MR314 wireless router (via the wired ports, not using wireless atm).. which also has 2 xbox's into it, which also get fluctuating speeds (aka laaag!).. so definitely my network setup somewhere is wrong.. 

The router goes to a no-name ADSL modem provided by my ISP. By playing around with the router settings and both PCs I managed to get net working.. but as I said, having issues with reliability. 

Wondering if anyone knows of a good start-to-finish tutorial for this kind of setup to make sure I haven't stuffed anything up, or if someone is willing to step me through checking it all to make sure everything is right? as far as router settings, ubuntu network settings, etc.



Thanks.

---

### Post by cenithx on 2005-08-17
Ok it's getting worse.

Programs that need a persistant connection like IRC, IM apps, FTP, etc.. all seem to stuff up if they're on for prolonged periods of time. Even for shorter periods of time I get timeouts, failed download/uploads (in ftp) etc.

What could be regularly interfering with net?

Is there something maybe trying to access the resolv.conf and by me locking it, its creating freezes with my net? That's the only thing I can think of. Apart from that this is a raw install of ubuntu.

---

### Post by heimo on 2005-08-17
One thing to try is disabling ipv6:
```
sudo gedit /etc/modprobe.d/aliases
#change 
alias net-pf-10 ipv6
#to
alias net-pf-10 off

```
reboot.

---

### Post by nverhaar on 2005-08-22
Im having a similar problem. Ive setup Ubuntu as a server to provide web/mail/internet access to all machines at work.

For the life of me I cannot figure out why, but the machine appears to randomly drop ALL network activity for a period of around 10 seconds several times throughout the day for no apparent reason. It kills all internet activity, SSH/FTP connections to the box, basically anything that requires network activity.

I tried disabling IPV6 as detailed above, and while I thought it had been fixed, within several hours it started reoccurring again. The machine is a brand new Dell Dimension 3000, and I have tried several different network cards trying to work out the cause.

Any ideas?!

---

### Post by nverhaar on 2005-08-23
GRRRRR!! Im still havin this problem, and its getting really annoying.

Any ideas?!

---

### Post by nverhaar on 2005-08-23
I have checked every log I can think of, but nothing seems to report any problems.

Could it be that maybe the hotplug system is dropping and reconnecting the network connection/device by mistake, or some other process causing a similar effect?

Im stumped!!

---

