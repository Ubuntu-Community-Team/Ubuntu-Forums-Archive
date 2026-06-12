---
title: "Md5sum"
date: 2009-09-23
forum: New to Ubuntu
---

### Post by Nottawa on 2009-09-23
I downloaded the latest version of Ubuntu and the md5 was different than the one on the Ubuntu hash page.  So I got it again.  The sum was still different, but exactly the same as the first download.  Do I try again?  Try installing?  I have not yet burned to a cd, so this problem is just from my download.

---

### Post by mac9416 on 2009-09-23
I would suggest burning the disc, then booting it and choosing the "Check CD for defects" option in the bootup screen. If it doesn't find any errors, go ahead and to install.

Good luck

---

### Post by unutbu on 2009-09-23
mac9416, the md5sum is there to help prevent a hacker from being able to distribute a modified copy of Ubuntu. The hacker could make the "Check CD for defects" option return nothing.

Nottawa, can you post the url of the file you are downloading, and the md5sum that your are getting?

---

### Post by alphaniner on 2009-09-23
This is the second post I've seen with this issue.  Which version did you download (ie AMD64-desktop, etc.) and what was the hash?  I'd heed unutbu's advice and find out what is up before going any further.

---

### Post by LewRockwell on 2009-09-23
something is fishy

.

---

### Post by farsight on 2009-09-23
Have you tried downloading from a different mirror, for example the University of Kent as opposed to Canonical?

It may be an issue with the transmission from the mirror that is causing the md5sum to mismatch.

Try again at another download. I'd recommend not installing until you have a like-for-like sum value.

---

### Post by NightwishFan on 2009-09-23
I advise you use a torrent to download Ubuntu. They are listed, legal and supported. Torrent verifies downloads automatically.

[http://www.ubuntu.com/getubuntu/downloadmirrors#bt]("http://www.ubuntu.com/getubuntu/downloadmirrors#bt")


If you wish to direct download, use a download manager such as Mozilla Firefox, which has a built-in one. (Not downthemall, but the default downloader.)

If you get an iso from an official mirror, it is doubtful (though perhaps possible) that it is compromised somehow.

---

### Post by ranch hand on 2009-09-23
If you are talking about 9.04, do not try anything until you get a clean download.

If you are talking about 9.10, this is an alpha release and you do not want it on your box now at all.  It is very unstable and the Live CDs and the installer on them are both funky when you get one that has the right md5sum.  A bad md5sum is just not going to get it.

Those md5sums are handy, you have a good copy or you don't.  Don't use bad copies, they don't work.

---

### Post by Nottawa on 2009-09-23
Here is where I downloaded from:Download URL: [http://mirror.csclub.uwaterloo.ca/ubuntu-releases/jaunty/ubuntu-9.04-desktop-i386.iso](http://mirror.csclub.uwaterloo.ca/ubuntu-releases/jaunty/ubuntu-9.04-desktop-i386.iso)

Here is my check sum:bd7c6e72927dd71d8cdc60dcb4899f37 peter-robertss-macbook:~ drpeterroberts$ 

I hope this gives some one some ideas, but I will try a different mirror.

---

### Post by ranch hand on 2009-09-23
A different mirror would be a good place to start.

Are you downloading from one of the mirrors listed on;

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

or getting the link somewhere else?

---

### Post by unutbu on 2009-09-24
Just to check, I downloaded the ISO using 

```
wget -c http://mirror.csclub.uwaterloo.ca/ubuntu-releases/jaunty/ubuntu-9.04-desktop-i386.iso
```

The md5sum matched the expected value:

```

% md5sum ~/test/waterloo/ubuntu-9.04-desktop-i386.iso
66fa77789c7b8ff63130e5d5a272d67b  /home/unutbu/test/waterloo/ubuntu-9.04-desktop-i386.iso

https://help.ubuntu.com/community/UbuntuHashes
66fa77789c7b8ff63130e5d5a272d67b  ubuntu-9.04-desktop-i386.iso

```
So the ISO from waterloo seems fine.

---

### Post by dearingj on 2009-09-24
I'd suggest downloading the CD image via BitTorrent if you can. BitTorrent has built-in automatic hash checking, so when it says the download has finished, you know the .iso works properly. You can get the torrents from this page: [http://www.ubuntu.com/getubuntu/downloadmirrors#bt](http://www.ubuntu.com/getubuntu/downloadmirrors#bt)

---

### Post by freak42 on 2009-09-24
searching google with the "wrong" checksum above returns at least two more unique posts with the same problem:

[https://answers.launchpad.net/ubuntu/+question/74435](https://answers.launchpad.net/ubuntu/+question/74435)
and 
[http://forum.ubuntu-fr.org/viewtopic.php?id=341989](http://forum.ubuntu-fr.org/viewtopic.php?id=341989)

they are both discussing about macs, so either you also use a **mac **for this, or something is very wrong with the distributed images and/or checksums

---

### Post by Nottawa on 2009-09-25
I downloaded the iso again from a different server, also use Firefox and got a clean version to use.  Thanks for the help.

---

