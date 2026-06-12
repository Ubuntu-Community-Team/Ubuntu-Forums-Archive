---
title: "update roblem"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by il pepe on 2009-07-27
GPG-fout: [http://ppa.lanchpad.net](http://ppa.lanchpad.net) jaunty Release: De volgende ondertekeningen waren ongeldig: NODATA 1 NODATA 2Ophalen van [http://ppa.lanchpad.net/spring/ubuntu/dists/jaunty/main/source/Sources.bz2](http://ppa.lanchpad.net/spring/ubuntu/dists/jaunty/main/source/Sources.bz2) Subproces bzip2 gaf de foutcode 2 terug is mislukt
Ophalen van sommige indexbestanden is mislukt, deze zijn of genegeerd, of er zijn oudere versies van gebruikt.

I received this problem when i tried to update my ubuntu...
Any help?

It's in dutch, hope it's enough info...

---

### Post by Michael.Godawski on 2009-07-27
A little translating would be a blessing. ;)

---

### Post by Taylor13 on 2009-07-27
This looks like (roughly) the same error I get when I try to get updates, and in fact I was planning on posting it when it happened again. I'll get an English version if I can get it to happen again. :)

Until then, I remember that it was complaining about missing or invalid gpg files for those repositories.

---

### Post by Pepe Lebuntu on 2009-07-27
If it's like mine, it's like this:

> GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4874D3686E80C6B7Failed to fetch cdrom://Xubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Xubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/multiverse/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Xubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

I'm having a hard time doing my updating as well, obviously.

---

### Post by Pepe Lebuntu on 2009-07-27
and yes, I'm a little freaked that two "pepe's" are having the same problem...

---

### Post by plucky on 2009-07-28
@Pepe Lebuntu

> GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4874D3686E80C6B7Failed


Open a terminal and ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4874D3686E80C6B7
```

Should fix that error.For the other error > Failed to fetch cdrom://Xubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/multiverse/binary-i386/Packages Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Open **System > Administration > Software Sources** and un-tick the CDroms as a source.Then ```
sudo apt-get update
```


Good Luck

---

### Post by plucky on 2009-07-28
@il pepe


> [http://ppa.lanchpad.net](http://ppa.lanchpad.net) jaunty Is that a typo or what?

Open a terminal and post output of ```
cat /etc/apt/sources.list
``` I don't think that location is valid.

Good Luck

---

### Post by il pepe on 2009-07-28
What do you mean a typo?
I have these lines following the code you gave me... So i guess there is problem with my spring software?

deb [http://ppa.launchpad.net/spring/ubuntu](http://ppa.launchpad.net/spring/ubuntu) jaunty main
deb-src [http://ppa.lanchpad.net/spring/ubuntu](http://ppa.lanchpad.net/spring/ubuntu) jaunty main

---

### Post by plucky on 2009-07-28
> **il pepe said:**
> What do you mean a typo?
I have these lines following the code you gave me... So i guess there is problem with my spring software?

deb [http://ppa.launchpad.net/spring/ubuntu](http://ppa.launchpad.net/spring/ubuntu) jaunty main
deb-src [http://ppa.lanchpad.net/spring/ubuntu](http://ppa.lanchpad.net/spring/ubuntu) jaunty main


Check the spelling of the second line.


Good luck

---

### Post by Pepe Lebuntu on 2009-07-28
> **plucky said:**
> 
			@Pepe Lebuntu

 	Quote: GPG error...

 Good Luck

Thanks mate, that worked a treat!

---

### Post by il pepe on 2009-07-29
> **plucky said:**
> Check the spelling of the second line.


Good luck
haha (laughing at myself)

it indeed did the trick and it was indeed a stupid typo....

Thanks alot!!

---

