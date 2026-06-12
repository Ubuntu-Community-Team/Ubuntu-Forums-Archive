---
title: "Can't browse any Samba shares anymore"
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by hansjs on 2008-02-20
First, I am still quite a noob...but...

I had everything working fine. When i went to Places/Network    I saw my network storage and all my windows shares. I was even able to mount my network drives....but...

I rebooted and now I can't see any of my shared folders. I checked etc/fstab and the mount entries are still there....but i can't browse anything.

I can browse my netwrok drive web browser (ip address/network drive name)..so I know that it is still connected.

Can anyone help me get this working again? I was thrilled to have it all working so good and now frustrated that its not....

---

### Post by Iowan on 2008-02-21
I'll give your thread a bump...
Dunno how you were mounting network drives, etc.  You might try **smbtree** to see what (if anything) pops up.  You can also check **man net** to see if there's anything there to use in debugging.

---

### Post by hansjs on 2008-02-21
I mounted by creating folder in mnt directory called "movies" and "nas", then entered the following in fstab:

```

//NAS/OneTouch_b /mnt/movies smbfs username=my ubuntu acct name,password=my ubuntu acct p/w,umask=022 0 0
//NAS/HDD_a /mnt/nas smbfs username=my ubuntu acct name,password=my ubuntu acct p/w,umask=022 0 0
```

That worked great at first. But now for some reason none of my network shares show up. I don't think it's a mount issue. It's more that I can't see any files or folders on my netwrok now when I could see everything fine yesterday.

---

### Post by Iowan on 2008-02-21
Do they show up under Places>Network or Places>Connect to Server?

---

