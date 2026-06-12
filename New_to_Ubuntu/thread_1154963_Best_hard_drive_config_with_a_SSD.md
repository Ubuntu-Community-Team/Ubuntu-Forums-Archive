---
title: "Best hard drive config with a SSD"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by madu on 2009-05-10
Hey guys,

I have been having a persistent problem with Firefox. I have two hard disks and during installation I put '/' in one hdd and '/home' in another hard disk drive. I did because I used to have the problem of not being able to work on FF while I am (un)raring files, which I do quite often. But this setup doesn't seem to help either. I still have the problem.

I am going to do some work on my system, so as part of that, I want to change my existing hard disks. I am planning on better, preferably Wester Digital Raptor hdds.

What I want to know is, what is the best configuration for a faster/responsive system? 
I do a lot of raring so how to config the hard drives so that wont affect my other apps?

Also, I am considering the idea of buying a 32GB SSD. But is it worth it?
If so, how should I use it, i.e. what partition should I put in that?

Thank you very much.

---

### Post by madu on 2009-05-10
Nobody? :confused:

---

### Post by blueridgedog on 2009-05-10
You may be able to salvage your current situation.  If you save the archives on one drive, then unrar to another, you should get be best performance.  Unrar'ing from and too th same drive may create a bottleneck.

If you do re-partition, you could create one drive with / and /downloads and another with /home, so you would always use one to read and one to write during an urar operation.

I have no comment on the ssd, as I can't see it helping your setup.  I also suspect that the rar issue may be CPU related.  I have a quadcore chip (2.8Ghz) and generally can multi-task when unraring.

---

### Post by albinootje on 2009-05-10
> **madu said:**
> 
What I want to know is, what is the best configuration for a faster/responsive system? 
I do a lot of raring so how to config the hard drives so that wont affect my other apps?


The Firefox binary is loaded into RAM I think, but e.g. cache files and history are written to your /home directory.
Were you working on your files in / or in /home ?
Is your swap being used, and on which disk is your swap partition ?

You can use the "nice" command to give priority to certain programs. See "man nice", and also "man top" -> "r" (renice).

---

### Post by madu on 2009-05-10
> **blueridgedog said:**
> You may be able to salvage your current situation.  If you save the archives on one drive, then unrar to another, you should get be best performance.  Unrar'ing from and too th same drive may create a bottleneck.

If you do re-partition, you could create one drive with / and /downloads and another with /home, so you would always use one to read and one to write during an urar operation.

I have no comment on the ssd, as I can't see it helping your setup.  I also suspect that the rar issue may be CPU related.  I have a quadcore chip (2.8Ghz) and generally can multi-task when unraring.

Thank you.
I don't think it is CPU/RAM related as I run a Q9550 with 4GB ram.
I think the problem is because I read and rar to the same drive as you said.
When you say create one 'drive' with / and one with /home, do you mean seperate hdd's or seperate partiotions on the same hdd? seperate hdd's would give better performance, right?

---

### Post by madu on 2009-05-10
> **albinootje said:**
> The Firefox binary is loaded into RAM I think, but e.g. cache files and history are written to your /home directory.
Were you working on your files in / or in /home ?
Is your swap being used, and on which disk is your swap partition ?

You can use the "nice" command to give priority to certain programs. See "man nice", and also "man top" -> "r" (renice).

Thank you. My files are in /home. I guess thats whats freezing the FF.
I think the best option is to have a seperate hdd for my files.

BTW, is it possible to create a seperate partition called, say /myFiles at the Ubuntu installation or I have to do it later?

Cheers.

---

### Post by albinootje on 2009-05-11
> **madu said:**
>  BTW, is it possible to create a seperate partition called, say /myFiles at the Ubuntu installation or I have to do it later?

Cheers.

I assume you have / on one disk, and /home on the other disk ?
Then create /myFiles (and do a "sudo chown 1000:1000 /myFiles), and test it.

---

### Post by starfry on 2009-05-11
If you are going to buy an SSD,the only one worth buying at the moment is the INTEL X25-M. All others have performance issues that are well discussed on the internet. The INTEL is a little more expensive but at least you buy in some longevity. I have an X25-M that I am about to install. I haven't yet because there is some optimising at a format level that I want to try but it's new to me so I need to do some research first.

---

### Post by madu on 2009-05-11
> **albinootje said:**
> I assume you have / on one disk, and /home on the other disk ?
Then create /myFiles (and do a "sudo chown 1000:1000 /myFiles), and test it.

Thank you albinootje.
I was thinking putting /myFiles in a seperate hdd, not a partition. Since drives are quite cheap I guess it's much better.
That is possible, is it not?

---

### Post by madu on 2009-05-11
> **starfry said:**
> If you are going to buy an SSD,the only one worth buying at the moment is the INTEL X25-M. All others have performance issues that are well discussed on the internet. The INTEL is a little more expensive but at least you buy in some longevity. I have an X25-M that I am about to install. I haven't yet because there is some optimising at a format level that I want to try but it's new to me so I need to do some research first.

Thankyou Starfry.
Intel ssd's are out of my price range :(. I was thinking about a 32GB one I can get for around ~$120. But I guess its not much worth.

---

### Post by albinootje on 2009-05-11
> **madu said:**
> Thank you albinootje.
I was thinking putting /myFiles in a seperate hdd, not a partition. 
Since drives are quite cheap I guess it's much better.
That is possible, is it not?

Yes, it's possible.
Just make sure that /myFiles is the mountpoint for the partition on the seperate hdd that you will use for it.
Think link could be useful for that :
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

---

### Post by madu on 2009-05-11
> **albinootje said:**
> Yes, it's possible.
Just make sure that /myFiles is the mountpoint for the partition on the seperate hdd that you will use for it.
Think link could be useful for that :
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

Thank you very much albinootje.
That how to was what I was looking for.
Thanks again.

---

