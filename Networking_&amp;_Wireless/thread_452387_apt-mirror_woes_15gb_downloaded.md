---
title: "apt-mirror woes 15gb downloaded"
date: 2007-05-23
forum: Networking &amp; Wireless
---

### Post by andytof47 on 2007-05-23
Hi I have just downloaded about 15GB from a local server:D (impressive I thought):popcorn:

It was a sacrifice I was willing to make if it meant I could do network installs ..........

I'm using apt-mirror to pull down the mirror from my ISP

so Here is what I did

```
gedit /etc/apt/mirror.list
```

I inserted these lines into mirror.list
```
deb http://filer-1.filearena.net/pub/ubuntu feisty restricted multiverse universe main

```

I assumed these were what was needed to get these directories mirrored... then I ran apt-mirror

Hours later I begin a Network install and I can't because apt-mirror hasn't made a mirror of the directories..... I get an error from the ubuntu installer on the clients

and this is a snippet of the apache logs

```
[Wed May 23 22:26:08 2007] [error] [client 192.168.2.98] File does not exist: /var/www/ubuntu//dists/feisty/restricted/debian-installer/binary-i386/Packages
[Wed May 23 22:26:09 2007] [error] [client 192.168.2.98] File does not exist: /var/www/ubuntu//dists/feisty/main/debian-installer/binary-i386/Packages.gz
[Wed May 23 22:26:09 2007] [error] [client 192.168.2.98] File does not exist: /var/www/ubuntu//dists/feisty/main/debian-installer/binary-i386/Packages
[Wed May 23 22:26:09 2007] [error] [client 192.168.2.98] File does not exist: /var/www/ubuntu//dists/feisty/restricted/debian-installer/binary-i386/Packages.gz
[Wed May 23 22:26:09 2007] [error] [client 192.168.2.98] File does not exist: /var/www/ubuntu//dists/feisty/restricted/debian-installer/binary-i386/Packages
[Wed May 23 22:32:11 2007] [error] [client 192.168.2.98] File does not exist: /var/www/ubuntu//dists/feisty/main/debian-installer/binary-i386/Packages.gz
[Wed May 23 22:32:11 2007] [error] [client 192.168.2.98] File does not exist: /var/www/ubuntu//dists/feisty/main/debian-installer/binary-i386/Packages
[Wed May 23 22:32:11 2007] [error] [client 192.168.2.98] File does not exist: /var/www/ubuntu//dists/feisty/restricted/debian-installer/binary-i386/Packages.gz
```

Only after I have downloaded 15gb and began to receive errors did I realise that I didn't have a deb-src line in the mirror.list file so I added
```
deb-src http://filer-1.filearena.net/pub/ubuntu feisty restricted multiverse universe main
```
hoping it would pick up the files it missed however it wants to download about 16gb this time


surely there is a way of just getting the files I missed????????/? without re doing the whole excercise


PLEASE SOMEONE HELP MEEEEEEEEE


Cheers

---

### Post by andytof47 on 2007-05-23
bump!!! Please someone help a brother out --- I can't believe no knows how to help and I wouldn't think that no one wants to help ???? come on Ubuntu gurus!!!!!!!

Please:(

Cheers

---

### Post by andytof47 on 2007-05-23
Hey these forums are here so people can get help......

come to the party guys pleeeeeeeaaaassssseeeee




:(:(:(

---

### Post by chris.zeman on 2007-10-21
I'm having the same problem, but there may be multiple steps to solve this.

```
ubuntu//dists
```
should be
```
ubuntu/dists
```

Change
```
/ubuntu/
```
to
```
/ubuntu
``` in your config file.

I had the same thing happen, and that was an easy fix. My other problem is that apt-mirror never downloaded the debian-installer directory. I am going to start a new thread about this.

---

### Post by Dryw Paulic on 2007-12-13
Hi Andy,

This is a bit late, but an I do have an explanation for apt-mirrors behavior. First off, like Chris stated the clients are looking in the wrong place - - one too many slashes "ubuntu//dists/".

However, if you still have problems after you do that check to see if the package list files are actually there. If they do not show up in mirror/dists/ you can go into the skel/dists/ directory and check if those package files are present . If they exist in skel but not in mirror, just copy skel/dists to /mirror/dists and that will clear up the "package list missing" errors.

As for having to download an extra 16 GB, that's because you specified:

```
deb http://filer-1.filearena.net/pub/ubuntu feisty restricted multiverse universe main
deb-src http://filer-1.filearena.net/pub/ubuntu feisty restricted multiverse universe main
```

Which will download all the deb packages for the restricted, multiverse, universe and main feisty repos. This comes out to about 15 GB by itself. Specifying deb-src will download all of the source for those debs, which adds an additional 15 GB or so.

Hope this helps!

-Dryw

---

