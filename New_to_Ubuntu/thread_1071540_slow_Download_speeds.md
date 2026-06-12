---
title: "slow Download speeds"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by som1special2 on 2009-02-16
I have been using Hardy for over 6 months. My wife still uses Vista, (for her own reasons) and I have noticed ONE thing that Vista does better than my Hardy... Download large files. 

We essentially use the same equipment and I have tried several download scenarios with no result. She downloads a 600mb file in 15 minutes and it takes me over an hour! Is it the filesystem I use? JFS... OR is there something I can do internally to speed up downloads???

Thanks for any help

---

### Post by superprash2003 on 2009-02-16
you could try disabling ipv6 to improve speeds [http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html](http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html) .. also in the terminal type **ifconfig** and post output..

---

### Post by mike555 on 2009-02-16
You can also try "tweak network" extension for Firefox , and also "DownthemAll"  downloader extension .....

---

### Post by benny bronx on 2009-02-16
> You can also try "tweak network" extension for Firefox , and also "DownthemAll" downloader extension .....

+1 for Downthemall.  While tweak network is a cool extension to make it easy to play around with the network settings, the power setting raises the max-persistent-connections to 16.  Mozilla states that anything above 10 is excessive.  See:

[http://kb.mozillazine.org/Network.http.max-persistent-connections-per-server]("http://kb.mozillazine.org/Network.http.max-persistent-connections-per-server")

It also raises pipelining to the maximum of 8.  In my experience, while this causes some sites to load faster, it can have the opposite effect on others.

---

### Post by joopbraak on 2010-05-17
downthemall is a piece of ****. The GUI is totally illogical and user-unfriendly, and if you download a few large files you are then unable to browse anymore in Ubuntu (I have Lucid), even though your internet connection is not saturated.

---

### Post by zeekoman on 2010-05-17
Is it possible that [LIST]
[*](if using wifi) your signal might be weaker?
[*]both you and your wife are downloading at the same time, so your speeds are slower?
[*]you have a cap on your download speed? 
[/LIST]

Otherwise.. try as the above suggested, ie. disable IPv6, change settings etc. 

As for the filesystem.. JFS is one of the fastest/best filesystems.

---

