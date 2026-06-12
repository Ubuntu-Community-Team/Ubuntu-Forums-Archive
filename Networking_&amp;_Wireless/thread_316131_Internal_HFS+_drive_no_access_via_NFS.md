---
title: "Internal HFS+ drive: no access via NFS"
date: 2006-12-10
forum: Networking &amp; Wireless
---

### Post by thorix on 2006-12-10
Hello everyone!

I&#8217;ve just recently bought an old Windows-PC, wiped off W2k and installed Ubuntu 6.10.
The purpose of this machine is to serve my 200GB, formerly external hard drive for my Mac network.

Installing hfstools, mounting and accessing the drive was no problem.

Setting up NFS shares and accessing them from my Macs is almost no problem, but: the fstab-mounted, freely accessible HFS+ (nonjournaled ;) ) drive shows up in the NFS share on my Mac, but i can&#8217;t access its contents!

Meanwhile i helped out with Netatalk, but this seems to be slow and doesn&#8217;t respect permissions - i&#8217;m still working on it. Samba won&#8217;t let me write - i&#8217;m also working on it.

My favourite sharing protocol is NFS but i can&#8217;t get it to work in this case ](*,) 

Is there any geek outside who knows the trick?

/etc/fstab:
```
/dev/hdb10 /media/hartscheibe hfsplus defaults 0 0
```

/etc/exports:
```
/media *(rw,sync,insecure)
```
Note that the /media share was formerly /media/hartscheibe, but so i can see if i am really connected and seeing not the dummy folders created locally. I see &#8220;hartscheibe&#8221; in /media, but can&#8217;t get behind.

---

### Post by thorix on 2006-12-11
Update

After having problems with the read-only HFS+ issue i quit this nasty buisiness. I will eventually bargain a harddrive that i could build into the Ubuntu box, formatted as ext3.

---

