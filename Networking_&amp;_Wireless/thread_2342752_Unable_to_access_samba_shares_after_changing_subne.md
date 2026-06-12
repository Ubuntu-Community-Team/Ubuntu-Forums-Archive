---
title: "Unable to access samba shares after changing subnet of network"
date: 2016-11-09
forum: Networking &amp; Wireless
---

### Post by Doggins on 2016-11-09
Hey Team!
I'm having a problem that is making me bang my head against the wall a little bit.

I recently changed my home subnet from 192.168.1.x to 192.168.8.x (Edit: mistakenly had this as 192.168.5.x), and everything seemed to go pretty smoothy.

My home network consists of the following:
PC1 - Windows PC - 192.168.8.99
PC2 - Ubuntu 'server' - 192.168.8.89
PC3 - Ubuntu HTPC - 192.168.8.88

Since the subnet change, I am having an issue accessing PC2 (Ubuntu server) shares via hostname from PC3. The windows PC can access these shares by hostname without issue.

Using 'Connect to Server' in nautilus:
1) smb://pc2/ shows 'no route to host' (previously this worked without issue)
2) smb://192.168.8.89 (PC2 IP) works fine

pinging the hostname 'PC2' from PC3 correctly shows the IP address of 192.168.8.89

Googling around all I can find for 'no route to host' is issues with SSH, and a [similar case]("https://www.experts-exchange.com/questions/21279670/Samba-NFS-gives-No-route-to-host-but-SSH-and-PIng-works-fine.html") that looks related to a firewall (?) however i'm skeptical to think this is the issue as it was previously working fine on the 192.168.1.x network.
Thanks for any help you can offer <3

---

### Post by TheFu on 2016-11-09
Is the 192.168.5.x above a typo?  That needs to be corrected first. Facts are important.

Can PC3 ping PC2?
Are all the /etc/hosts updated?
Was /etc/samba/smb.conf updated?
Are you running a firewall anywhere? Have those settings been updated for the new subnet?

---

### Post by Doggins on 2016-11-09
Hey thanks for the help -- 192.168.5.x is indeed a typo.

-PC3 can ping PC2, no issue with either hostname or IP address
-/etc/hosts has not been updated on either machine, but I had not previously made any changes
-/etc/samba/smb.conf is not updated, I checked PC3, but thinking about it now I suppose this would be configured more on PC2. I would suspect this is 'fine' if I can access the shares from windows, but I'll take a look at this
-No firewalls unless anything set up by default with Ubuntu, both are on the newest LTS release.

---

### Post by TheFu on 2016-11-09
Sorry if wasn't clear.  You should update ALL THOSE THINGS that I've listed.  I have no idea how your systems "find" each other if you didn't update /etc/hosts with the mapping to all the other local systems. Can you please explain how that works on your network?  I don't believe in magic. ;)

Also, if all the systems are not on the same subnet, you'll need a WINS server.

Also - rather than saying what is and isn't working, please post proof.  It isn't that we don't believe you, but history has proven over and over that we are often blind about issues on our systems.

The output on the samba server from the **testparm** tool would be handy too.

For all the output, please show both the command AND the output and please, please, please use *code tags* so things line up.

---

### Post by Doggins on 2016-11-09
Thank you again for the assistance TheFu,

once I got home from work today I tinkered with my settings for a bit. Ended up not changing anything but rebooting the router (my DNS), and all machines on the network. Everything is now working like a charm.
my apologies for no clean resolution though.

---

