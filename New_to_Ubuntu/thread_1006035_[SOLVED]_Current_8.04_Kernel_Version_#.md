---
title: "[SOLVED] Current 8.04 Kernel Version #?"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by kansasnoob on 2008-12-08
As you can see here:

[http://ubuntuforums.org/showthread.php?t=934230](http://ubuntuforums.org/showthread.php?t=934230)

I've had an old 30gb testing hard drive installed since the end of September. Hey, don't laugh! Intrepid (and Mint 6) have just been working so well I had no need to change back. 

And I store all important data on external drives that I keep in Tupperware in my fireproof gun safe! Again, don't laugh! I've lost data due to fire, flood, and a malicious ex-wife so I'm paranoid!

Anyway I decided to reinstall my normal hard drive that's triple boot: Win XP, Ubuntu 8.04.1, and Mint 5. I started by updating everything in Windows. That took about two hours and there's a serious glitch in the HP printing software. No surprise - (((sigh)))!

Of course there were over 100 Ubuntu updates but I was a dummy and didn't make note of the newest kernel update. It shows that I'm running 2.6.24-19.

Is 2.6.24-19 the newest kernel version in Hardy?

I'm using Mint's Grub so it's possible that the Mint Grub didn't pick up the new kernel version. I know how to fix that and come to think of it I could just look at synaptic, but I'd appreciate someone checking their current kernel version in 8.04.

---

### Post by kansasnoob on 2008-12-08
OK, looking at synaptic I should be running -22. Is that right?

---

### Post by egalvan on 2008-12-08
> **kansasnoob said:**
> As you can see here:

[http://ubuntuforums.org/showthread.php?t=934230](http://ubuntuforums.org/showthread.php?t=934230)

I've had an old 30gb testing hard drive installed since the end of September. Hey, don't laugh! Intrepid (and Mint 6) have just been working so well I had no need to change back. 


Is 2.6.24-19 the newest kernel version in Hardy?



from my desktop:
```

ernest@gx280:~$  uname -r
2.6.24-21-generic

```

And I'd never laugh at older hardware. I use it all the time.

P-III with 10G drives...

---

### Post by kansasnoob on 2008-12-08
Thanks, I haven't been into Mint yet. I'll boot it and run update-grub and see what happens.

Something odd, but pleasant, is that I've *never* been able to get the "button graphic" to work in Flashblock on 8.04 and it's working!

I'd forgotten how quiet this box could be!

I have some old 6 gb drives that sound like a train going by!

---

### Post by sdennie on 2008-12-08
From the normal repos, it should be -22:

```

$ apt-cache show linux-image | head
Package: linux-image
Priority: optional
Section: metapackages
Installed-Size: 52
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux-meta
Version: 2.6.24.22.24
Depends: linux-image-generic (= 2.6.24.22.24)
Filename: pool/main/l/linux-meta/linux-image_2.6.24.22.24_i386.deb
$ grep proposed /etc/apt/sources.list
$

```

---

### Post by kansasnoob on 2008-12-09
Well, since I planned on dumping Mint anyway (they're simply too slow with security updates, but I love Clem's work) I just restored Grub to the Ubuntu partition.

And, yep, it's 2.6.24-22!

Now, if I could figure out why the buttons show the way they should using Flashblock I'd be a happy camper! They worked perfectly in Intrepid anyway and I'll likely upgrade to Intrepid anyway but it's interesting.

Thank you all very much!

---

### Post by igknighted on 2008-12-09
> **kansasnoob said:**
> Well, since I planned on dumping Mint anyway (they're simply too slow with security updates, but I love Clem's work) I just restored Grub to the Ubuntu partition.

And, yep, it's 2.6.24-22!

Now, if I could figure out why the buttons show the way they should using Flashblock I'd be a happy camper! They worked perfectly in Intrepid anyway and I'll likely upgrade to Intrepid anyway but it's interesting.

Thank you all very much!

... not that i care about Mint, but they use almost entirely the same repo's as Ubuntu (and all major apps are drawn from there), so they aren't any later than Ubuntu is...

---

### Post by egalvan on 2008-12-09
> **vor said:**
> From the normal repos, it should be -22:

```

$ apt-cache show linux-image | head
Package: linux-image
Priority: optional
Section: metapackages
Installed-Size: 52
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux-meta
Version: 2.6.24.22.24
Depends: linux-image-generic (= 2.6.24.22.24)
Filename: pool/main/l/linux-meta/linux-image_2.6.24.22.24_i386.deb
$ grep proposed /etc/apt/sources.list
$

```

Being the curious type, I ran that code, and got EXACTLY the same output...

So now I wonder why ```
uname -r
``` shows ```
2.6.24-21-generic
```

What is wrong with the update on the kernel?

---

### Post by igknighted on 2008-12-09
> **egalvan said:**
> Being the curious type, I ran that code, and got EXACTLY the same output...

So now I wonder why ```
uname -r
``` shows ```
2.6.24-21-generic
```

What is wrong with the update on the kernel?

1) if you are running multiple distros, did grub update to the new kernel?

2) have you installed the latest?  (for kernel, use sudo apt-get dist-upgrade)

---

