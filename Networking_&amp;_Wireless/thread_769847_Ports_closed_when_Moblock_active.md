---
title: "Ports closed when Moblock active?"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by Tibco on 2008-04-26
I just tried this and im a bit confused. I added a torrent with moblock disabled and it went at an amazing speed. When i turned on moblock, my speed went down drastically to less than 20 KiB. Iam using Ubuntu 8.04...i tried activating moblock and then going to terminal and typing
" sudo iptables -A INPUT -p tcp --dport 6881 -j ACCEPT "
didn't really help, the download speed was still slow.
Also, I KNOW the port gets closed because ubuntu shipped with Transmission and it lets you see when ports are cloesd and open, and i used it to SEE that the port got closed. Iam a linux newbie, and i really like Ubuntu so far, it would be great if i could use it!
Anyone have any idea on what to do?

PS: If this is the wrong forum, please move it, i wasnt sure where to put it...

---

### Post by Tibco on 2008-04-27
Can someone help me? I really dont want to have to go back to windows! Ive looked at some other threads, and it seems like i could whitelist the port that Transmission uses, but that would be stupid because there is no use for Moblock then right?

---

### Post by nullmind on 2008-04-27
I used MoBlock, and I enjoy the concept, but it simply doesn't work well. It blocked google.com and I could only find areas where I could whitelist domains and I didn't like working in the direction it's configuration files where forcing me.

Cheers,
Kris

---

### Post by Tibco on 2008-04-27
can someone else help me figure this out?

---

### Post by Moop on 2008-04-27
> **Tibco said:**
> Can someone help me? I really dont want to have to go back to windows! Ive looked at some other threads, and it seems like i could whitelist the port that Transmission uses, but that would be stupid because there is no use for Moblock then right?

You need to have a port open for torrents to run correctly. Moblock is for blocking IP's or a range of IP's. Those IP's will still be blocked even from a open port. Deluge has a plugin for doing the same thing if you want another option. 

There is also Mobloquer that is a gui frontend for moblock. [http://mobloquer.foutrelis.com/](http://mobloquer.foutrelis.com/)

---

### Post by zeronothing on 2008-04-27
yes I will say moblock used to be something I used but all the settings right off the back block all traffic. which I thought was really weird. I will say I like to use "iplist" instead of moblock. check it out if don't end up getting it functioning properly. I believe you can download it from sourceforge and it comes in a .deb package which makes for an easy installation.

---

### Post by Tibco on 2008-04-27
> **Moop said:**
> You need to have a port open for torrents to run correctly. Moblock is for blocking IP's or a range of IP's. Those IP's will still be blocked even from a open port. Deluge has a plugin for doing the same thing if you want another option. 

There is also Mobloquer that is a gui frontend for moblock. [http://mobloquer.foutrelis.com/](http://mobloquer.foutrelis.com/)

I use mobloquer already, but i dont understand what you mean i can open ports. If i, for example, whitelist HTTP, it ignores that port, irregardless of the IPs that pass through it. I can't access google with http blocked, but i can access it with http ignored. So it wont do me much good to have my torrent port ignored, because even though that would open the port for me, it would leave me defenseless.


I have tried IPlist also, and it has the same problem, but i feel more safer with MOblock, because its tested, while iplist is in alpha stage.
thanks for the replys!

---

### Post by Moop on 2008-04-27
> **Tibco said:**
> .....So it wont do me much good to have my torrent port ignored, because even though that would open the port for me, it would leave me defenseless.


Leave you defenseless against what? 

Moblock is for blocking certain hosts from connecting to your IP address. Normally you get a list of hosts you want to block by downloading a "blocklist". So if google is on the blocklist you won't be able to connect to google even if you have http open or any other port open. Programs like moblock are for blocking hosts from any open port on your pc. If you don't have any open ports then there isn't anything to block.

---

### Post by Tibco on 2008-04-27
thats not how its working for me...google IS on my blocklist, but when i say http ignored, i can access google through firefox, but when http is closed, i cant.

---

### Post by Moop on 2008-04-27
I guess I'm not familiar enough with how moblock works. Allowing http is opening port 80 and maybe it allows all connections from port 80. I don't know. 

Open up a port and download a torrent and then look at your logs for blocked IP's. I think there is a log in moblock that keeps a list. That should tell you if it's working.

---

### Post by jre on 2008-04-30
Same discussion here: [http://forums.phoenixlabs.org/showthread.php?t=16688](http://forums.phoenixlabs.org/showthread.php?t=16688) , unfortunately no answer ...

Have a look at /var/log/moblock.log to see if there are many blocks - if yes, then moblock is just doing it's job and is working as it is designed to do.
Whitelisting ports (which does mean that MoBlock will not check/block traffic on these ports) does indeed not help with this problem.
Instead it might make sense to change the preconfigured blocklists. Have a look at /etc/moblock/blocklists.list and /usr/share/doc/moblock/README.blocklists.gz.
E.g. only using the level1 list might be good.
Otherwise I still think you have a bad torrent if MoBlock has such a huge impact on it.

---

