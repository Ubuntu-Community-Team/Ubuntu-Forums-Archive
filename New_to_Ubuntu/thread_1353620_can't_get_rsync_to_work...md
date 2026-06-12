---
title: "can't get rsync to work.."
date: 2009-12-13
forum: New to Ubuntu
---

### Post by maciekmn on 2009-12-13
It all started by simply trying to get dvd iso image of CentOS.. I use Ubuntu for everything.. but I may need red-hat experience for jobs.. so I'm trying to get used to it too..

They don't have torrents available for Centos dvd (working ones).

I've had ridiculous problems trying to download image from few servers that have it.. 

1. several times my downloads were not completeing..

2. i used wget gui to make sure I can resume downloads.. hurray it completed.. 
   but then the image was 6GB in size instead of 3.4..

3. I was trying to use rsync to hopefully quickly fix the image:

This info showed how to use rsync to resync file (image)
  [https://help.ubuntu.com/community/RsyncCdImage](https://help.ubuntu.com/community/RsyncCdImage)

Here's list of mirrors that support rsync / the ones which have dvd iso:
  [http://www.centos.org/modules/tinycontent/index.php?id=30](http://www.centos.org/modules/tinycontent/index.php?id=30)

This is what i tried.. going to the folder where I have corrupted iso, I ran:

rsync -zhhP rsync://mirrors.kernel.org/centos/5.4/isos/x86_64/CentOS-5.4-x86_64-bin-DVD.iso .

I tried that for many mirrors.. I keep getting this (after few MINUTES)
rsync: failed to connect to mirrors.kernel.org: Connection timed out (110)
rsync error: error in socket IO (code 10) at clientserver.c(122) [receiver=3.0.3]

I tried just getting some small directories etc. I couldn't get anything to work..

I'm extremely frustrated.. 

I also thought it could be some firewall issue.. but I'm just connecting to server that accepts rsync connections (I suppose)..

I'm new rsync user.. so I may be goofing something up..

---

### Post by Temposs on 2009-12-13
Aren't you just trying to get an ISO of CentOS? Why all this complicated stuff? The CentOS download page is here:
[https://www.centos.org/modules/news/article.php?storyid=71](https://www.centos.org/modules/news/article.php?storyid=71)

Just download the DVD ISO again using the torrent from this link(you can use the Transmission program included with Ubuntu):
[http://mirror.centos.org/centos/4/isos/i386/CentOS-4.0-i386-bin.DVD.iso.torrent](http://mirror.centos.org/centos/4/isos/i386/CentOS-4.0-i386-bin.DVD.iso.torrent)

A torrent is the fastest way to download a file as long as their are a number of seeders.

When the file is finished downloading, run the md5sum command on the file, something like this:
```
md5sum CentOS-4.0-i386-bin.DVD.iso
```

Check the resulting md5sum against the gold standard(also found on the download page):
243d0d726a61681cee52f9aaf22b771f

If it matches, then you have a good file. Burn it to a DVD with Brasero, or to a USB drive with the USB Startup Disk Creator program. Then you should be good to go.

---

### Post by maciekmn on 2009-12-14
Temposs,

Thanks for your help.. for some reasons the torrents don't work on that centos iso..

I finally downloaded the image doing regular download on windows machine..  with small download manager..

Right now I'm still intrigued though why the rsync wouldn't work..

Anyone knows why rsync doesn't work for what was trying to do?
How do I troubleshoot rsync connection?

Thanks..

---

### Post by ephmanjmm on 2009-12-14
You might need to include where to store the downloaded file, i.e., /home/myhomedir

---

