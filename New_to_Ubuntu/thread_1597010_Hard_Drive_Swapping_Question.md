---
title: "Hard Drive Swapping Question"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by john wagner on 2010-10-14
I am currently running Ubuntu 9.04 on my Pavillion (refurbished, contents are NOT what was claimed...) Notebook computer.  

I swapped in a Seagate Momentus 5400.3 ST9160821AS 160GB 5400 RPM 8MB Cache 2.5" SATA 1.5Gb/s HD (about 3 years ago).  Well, it's full now.  Even with dumping old files, moving stuff over to external drives etc....  I have 6 gig left.

My question is thus, can I install one of these:

SAMSUNG SpinPoint MT2 HM100UI 1TB 5400 RPM 2.5" SATA 3.0Gb/s Internal Notebook Hard Drive -Bare Drive

or one of these others: 

[http://http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007605%20600030600&IsNodeId=1&name=1TB]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007605%20600030600&IsNodeId=1&name=1TB")

And expect the 3.0Gb/s to work in my 1.5  Gb/s HD?  No problem, right?

(2gig ram, 160 HD, Intel CPU, T2050 1.60 GHz).

Thanks in advance,
john

---

### Post by jquis8411 on 2010-10-14
I don't see any problems, Were you concerned about the transfer speeds? worst comes to worst you wont be able to take full advantage of 3GB/sec, but it wont hurt any either. And the linux kernal can handle huge hard drives.

---

### Post by john wagner on 2010-10-14
> **jquis8411 said:**
> I don't see any problems, Were you concerned about the transfer speeds? worst comes to worst you wont be able to take full advantage of 3GB/sec, but it wont hurt any either. And the linux kernal can handle huge hard drives.

That's more of what I as worried about.  If the kernal would handle the huge drive.

Thanks!  It may be slow (relatively speaking) and the monthly drive check will take FOREVER, but it'll be big and built in!

A terabyte will take a while to fill!

john

---

### Post by srs5694 on 2010-10-15
I don't know what the kernel's limit is on drive size. The limit that's closest to being an issue today is the Master Boot Record (MBR) partitioning scheme's limit. MBR uses 32-bit pointers to identify partition start points and sizes. Combined with the near-universal 512-byte sector size, this works out to a 2 TiB limit. (If you push things, you could start the last partition at just under 2 TiB and make it 2 TiB in size, for a 4 TiB limit; but most OSes flake out when they see that.) Future drives may use larger sector sizes, which would push the limit higher. In any event, the drive size you're talking about is still only half the MBR limit.

If you got a 3 TiB drive (drives of this size are just starting to appear, but not in 2.5-inch format), you'd need to switch from MBR to the newer GUID Partition Table (GPT) format, which uses 64-bit pointers. This should hold us for at least another couple of decades, assuming the rate of drive-size increase we've seen for the past couple of decades holds. Fortunately, Linux is well-prepared for GPT, although there are a few wrinkles -- mostly benefits, really. GPT does away with the primary/extended/logical distinction, for instance.

---

