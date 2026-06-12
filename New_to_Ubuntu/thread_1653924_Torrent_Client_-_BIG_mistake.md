---
title: "Torrent Client - BIG mistake ???"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by mistypotato on 2010-12-27
Hiya !

Today was the first time I used a Torrent client (K-torrent) to download a software package and as soon as I connected to begin downloading, my firewall lit up like a Christmas tree and hasn't stopped since.  I have an advanced firewall with a monitoring station similar to what hosting centers would use and so I can see every IP connection In or Out.

What I mean is that suddenly my server is under attack by IP addresses from Italy, Russian Federation, China, Turkey, Brazil and so forth (all the KNOWN major hacking centers).

This started as soon as I connected the torrent to the URL targe and continues now, over an hour later).  I'm seeing maybe 6,000 - 9,000 malicious hits per hour.   Before, I saw may 10 - 20 per hour.

So, it appears using this torrent client broadcast my IP address to a lot of bad servers.

Is this just a fact of using torrent clients or did I just go to a bad site?

OR...............................

Am I just not aware of how Torrents work and all these "residual" connection attempts from all these places are just friendly computers trying to see if they could help with my download in any way ?

---

### Post by 3rdalbum on 2010-12-27
Torrents not only download the file you want, they also send it to others who want the file. This is why you are noticing incoming connections - your computer has been advertised as having the file.

These incoming connections are not "malicious", they are just ordinary people doing exactly what you were doing, downloading the file.

In a couple of hours the torrent tracker will realise that you aren't running the client anymore, and will stop directing downloaders to your computer.

If someone tries to connect to your computer and you are not running any software that is listening for connections, then they simply can't connect. If all you are running is a torrent client, then all they can do is start downloading a torrent from you.

I suggest you stop looking at your firewall logs if you don't understand firewalls. Honestly, firewall logs are scary until you realise that "The firewall is blocking all these connections" and "I have nothing listening to these ports anyway".

In short, stop worrying about it. Incoming connections are normal when you are using torrents, and they are perfectly innocent.

---

### Post by mistypotato on 2010-12-27
> **3rdalbum said:**
> Torrents not only download the file you want, they also send it to others who want the file. This is why you are noticing incoming connections - your computer has been advertised as having the file.

These incoming connections are not "malicious", they are just ordinary people doing exactly what you were doing, downloading the file.

In a couple of hours the torrent tracker will realise that you aren't running the client anymore, and will stop directing downloaders to your computer.

If someone tries to connect to your computer and you are not running any software that is listening for connections, then they simply can't connect. If all you are running is a torrent client, then all they can do is start downloading a torrent from you.

I suggest you stop looking at your firewall logs if you don't understand firewalls. Honestly, firewall logs are scary until you realise that "The firewall is blocking all these connections" and "I have nothing listening to these ports anyway".

In short, stop worrying about it. Incoming connections are normal when you are using torrents, and they are perfectly innocent.

Thank you very much.  That makes sense now that I understand torrents.  I didn't realize I was also advertising that I was sharing the file.  I have to admit I was worried there for a while.
I'm a Torrent Noob :redface:

---

### Post by ikt on 2010-12-27
> **mistypotato said:**
> Italy, Russian Federation, China, Turkey, Brazil and so forth **(all the KNOWN major hacking centers).**


huh?

Source?

---

### Post by mistypotato on 2010-12-27
> **ikt said:**
> huh?

Source?

Correct.

I didn't just make that up.

LOTS of sites like Spamhaus,CountryIPBlocks.net etc that list the top countries from which hacking originate.
The US has also risen to the top.....I just forgot to list it....the list changes.

---

### Post by mysteriousdarren on 2010-12-28
I would use software such as moblock to protect yourself at least a little from all the bad out there in torrents.

---

### Post by ikt on 2010-12-30
> **mistypotato said:**
> Correct.

I didn't just make that up.

LOTS of sites like Spamhaus,CountryIPBlocks.net etc that list the top countries from which hacking originate.
The US has also risen to the top.....I just forgot to list it....the list changes.

I don't get it, are you saying you block entire countries ip ranges?

---

