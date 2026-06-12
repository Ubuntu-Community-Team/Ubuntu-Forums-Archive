---
title: "Disk Defrag"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by smithdrumm on 2009-01-22
Hi All!,

Does anyone know if there is a disk defrag program that will work with ubuntu? If so, please advise. Thanks to all who can help!

smithdrumm

---

### Post by deanjm1963 on 2009-01-22
There are quite a few posts regarding defragmenting ubuntu drives.

The short story is, no, there is no disk defragmenter for ubuntu, as linux file systems do not need to be defragged the way windows file systems do.

There are scripts available that automate the process of moving files to one location and back again to remove any fragments, but unless your drive is more than 80% full, there is no need.

Hope this helps.

---

### Post by Crafty Kisses on 2009-01-22
You don't really have to defrag in Linux, the file system is organized and stored more efficiently than a Windows box. If you really want to then I can
suggest you go to something like Google and search "Linux defrag" or something and grab a utility, they do exist, but unnecessary.

There is an option to "clean" though, just run this command in Terminal:
```
sudo apt-get clean
```

---

### Post by WASHAD on 2009-01-22
I know that this response won't be terribly poplular, but the reading I've done suggests that defrag is pretty silly anyway. The reason for this is because modern drives (the last 10 years or so) have pretty sophisticated algorithms that place data on the drive in the most optimum way. 

What the operating system "sees" in terms of storage is actually not the way data is stored at all, but wrather a lookup table provided by the drive.

I may be terribly wrong on the subject, but that is what I've read :)

Stevej

---

### Post by bsmith1051 on 2009-01-22
Nope, no defrag.  And don't believe the claims that it's not needed.  We just have to wait for the newer EXT4 partition-type to support defrag.

Personally, I replace my hard drives every 2 years (or sometimes sooner) and make a point of copying all my files across so that they're defragged.  That's secondary, actually -- the main reason is that I don't trust drives for more than about 2 years and they're relatively cheap.

---

### Post by jrusso2 on 2009-01-22
There are defrag tools for Linux and all drives get fragmented.  Some file systems are just worse then others at it.

[http://ubuntuforums.org/showthread.php?t=169551&page=2](http://ubuntuforums.org/showthread.php?t=169551&page=2)

Pyfrag is just one of them.

Personally I think its over done and probably not necessary.  At one time NT came without one too cause NTFS does not need defrag according to Microsoft.

It might be more trouble then its worth on Linux.

---

### Post by blackmail on 2009-01-22
I know that I will not add a lot to the topic but i think that i still will help a litle, here you can see a method for defrag but it is rather unorthodox and it is unecesarry: [http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)
Hope i was of some help.

---

### Post by binbash on 2009-01-22
you don't need it but you can give pyfrag a try.It is good

---

### Post by smithdrumm on 2009-01-22
> **Codename said:**
> You don't really have to defrag in Linux, the file system is organized and stored more efficiently than a Windows box. If you really want to then I can
suggest you go to something like Google and search "Linux defrag" or something and grab a utility, they do exist, but unnecessary.

There is an option to "clean" though, just run this command in Terminal:
```
sudo apt-get clean
```
Thanks Codename!

---

### Post by smithdrumm on 2009-01-22
> **jrusso2 said:**
> There are defrag tools for Linux and all drives get fragmented.  Some file systems are just worse then others at it.

[http://ubuntuforums.org/showthread.php?t=169551&page=2](http://ubuntuforums.org/showthread.php?t=169551&page=2)

Pyfrag is just one of them.

Personally I think its over done and probably not necessary.  At one time NT came without one too cause NTFS does not need defrag according to Microsoft.

It might be more trouble then its worth on Linux.
Thanks jrusso!

---

### Post by hyper_ch on 2009-01-22
> Modern Linux filesystem keep fragmentation at a minimum by keeping all blocks in a file close together, even if they can't be stored in consecutive sectors. Some filesystems, like ext3, effectively allocate the free block that is nearest to other blocks in a file. Therefore it is not necessary to worry about fragmentation in a Linux system.
[http://tldp.org/LDP/sag/html/filesystems.html](http://tldp.org/LDP/sag/html/filesystems.html) --> 5.10.11

---

### Post by bsmith1051 on 2009-01-22
> **deanjm1963 said:**
> unless your drive is more than 80% full, there is no need.
As long as you never get anywhere near filling a drive, you're ok.  Most of us, I suspect, occasionally max our drives even if just temporarily.

---

### Post by jerome1232 on 2009-01-22
Also if you're curious about the level of fragmentation on your drives fsck tells you. Boot from a live cd and run fsck, it'll report on non-contigous files (fragmented files)
```
sudo fsck -f /dev/sdxx
```

---

