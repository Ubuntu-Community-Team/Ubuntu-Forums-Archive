---
title: "NFS write speeds"
date: 2016-02-06
forum: Networking &amp; Wireless
---

### Post by cranerja on 2016-02-06
While writing to an NFS drive with nautilus I am obtaining a write speed of 27 kB/sec. The drive is capable of 131 MB/sec. When I test write speed of the drive from the client with dd, I get 47.2 MB/sec.

What would be causing this hit on performace? Is it with nautilus?


/etc/exports :
```
/drives/main/share      192.168.1.0/24(rw,sync,no_root_squash)
```

/etc/fstab :
```
192.168.1.1:/drives/main/share	/networkdrive	nfs	rsize=8192,wsize=8192,timeo=14,intr 	0	0
```

Thanks in advance!

---

### Post by cranerja on 2016-02-11
After having experimented more with this, dd is the only command that runs at a reasonable speed. Tools such as gcp also share the decreased speed.

---

### Post by SeijiSensei on 2016-02-11
You're moving the files over the network, right?  Your performance will be limited by the network speed.  Are you using Gigabit Ethernet or something slower like 100BT or, worse, wifi?  It doesn't look like you're using TCP for the NFS transport, but if you are, you'll have the additional overhead of reply packets (ACKs) being sent upstream by the client.  UDP should just blast the data as fast as it can.

Wifi is an especially poor conduit as it uses [half-duplex]("http://www.makeuseof.com/tag/what-is-half-duplex-and-full-duplex-operation-and-how-does-it-affect-your-router/").  That means it has to "turn the line around" periodically.

---

### Post by cranerja on 2016-02-11
> **SeijiSensei said:**
> You're moving the files over the network, right?  Your performance will be limited by the network speed.  Are you using Gigabit Ethernet or something slower like 100BT or, worse, wifi?  It doesn't look like you're using TCP for the NFS transport, but if you are, you'll have the additional overhead of reply packets (ACKs) being sent upstream by the client.  UDP should just blast the data as fast as it can.

Wifi is an especially poor conduit as it uses [half-duplex]("http://www.makeuseof.com/tag/what-is-half-duplex-and-full-duplex-operation-and-how-does-it-affect-your-router/").  That means it has to "turn the line around" periodically.

Naturally, and I am on gigabit with CAT5e and with dd I am getting 50 MB/s. When I was using samba I had nearly 100 MB/s. I had NFS at that speed for about a week but now it is slow again.

---

### Post by SeijiSensei on 2016-02-11
Things don't slow down on their own.  Is there other network traffic that might be consuming the server's connection?  I'm running out of ideas here.

---

### Post by cranerja on 2016-02-11
> **SeijiSensei said:**
> Things don't slow down on their own.  Is there other network traffic that might be consuming the server's connection?  I'm running out of ideas here.

Yeah I know what you mean, I have been scratching my head over this for a while. This server also acts as my router using dnsmasq, but it has been doing that since the beginning so I don't imagine it would bring it to that much of a crawl. 

One of the drives in the RAID (in the server) failed and I thought it was that causing it, but it was not.

---

### Post by cranerja on 2016-02-14
I just noticed that when copying normal files I get the desired speed but when I copy steam game files, it goes slowly. Why is it that steam game folders cause it to run slowly? Is it all the soft linking?

---

### Post by lensman3 on 2016-02-15
Could the "sync" option in exports slow things down.  Does the client/server have to wait until a block is written before the next block is sent.  async may work better.  

You mentioned that copying normal files is fast.  Could there be a compression happening?  nfs4 has encryption (that needs enabled), is encryption running?  Steam game files are compressed images aren't they?  Is there a way of removing compression on jpegs  etc, since images are already compressed.  rsync has a file that stops compression on image files, does nfs have the same?

---

### Post by cranerja on 2016-02-15
> **lensman3 said:**
> Could the "sync" option in exports slow things down.  Does the client/server have to wait until a block is written before the next block is sent.  async may work better.  

You mentioned that copying normal files is fast.  Could there be a compression happening?  nfs4 has encryption (that needs enabled), is encryption running?  Steam game files are compressed images aren't they?  Is there a way of removing compression on jpegs  etc, since images are already compressed.  rsync has a file that stops compression on image files, does nfs have the same?

I'll try the async, but I do not have encryption and the steam files may contain some compressed images but I do not think that would slow it down so much. And I do not understand what you mean with the rsync file.

Thanks for the answer and I will try it when i get the chance!

---

### Post by lensman3 on 2016-02-15
rsync is a network backup program.  It has a file that is read when it is compiled that specifies which files are NOT to be compressed during file transfer.  So a gif or tiff, which are already heavily compressed, should not compressed again resulting very little benefit.   For example, "sftp" compresses some files as it transfers them for faster throughput.  But if a file is already compressed, compressing it again can actually make it bigger.

---

### Post by cranerja on 2016-02-16
> **lensman3 said:**
> rsync is a network backup program.  It has a file that is read when it is compiled that specifies which files are NOT to be compressed during file transfer.  So a gif or tiff, which are already heavily compressed, should not compressed again resulting very little benefit.   For example, "sftp" compresses some files as it transfers them for faster throughput.  But if a file is already compressed, compressing it again can actually make it bigger.

Okay so I changed the sync to async in the exports file and while it was intermittently fast, it is now working as fast as other transfers!! Thanks so much!

I must have been following an outdated guide to have suggested sync.

---

