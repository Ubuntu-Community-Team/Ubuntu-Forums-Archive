---
title: "Best configuration for a SSD in Ubuntu 10.04"
date: 2010-07-10
forum: New to Ubuntu
---

### Post by razorj7 on 2010-07-10
Hello everyone,

I have Ubuntu Netook Edition 10.04 with an Intel SSD on a HP Mini 2140 netbook.

My question is: What is the best configuration to take full car and advantage of my SSD? I have been Googling this all night, but I can't seem to find a "noob friendly" guide.

Please help =)

Thanks to all in advance!

---

### Post by audiomick on 2010-07-10
Hallo.
In what respect  do you mean "configuration"? I you elaborate a bit, I think you will get help more quickly.

---

### Post by bumanie on 2010-07-10
As of kernel 2.6.33, trim will be (as far as I understand things), an automatic process. Thus you can use a development kernel (presently  and trim should keep your ssd in top order. Alternatively you can go [here]("http://sourceforge.net/projects/hdparm/") and [here]("http://sourceforge.net/projects/hdparm/files/wiper-2.7.tar.gz/download") and download hdparm and washer.sh which will do the trim for you and [here]("http://sourceforge.net/projects/disktrim/files/") is a gui to help if you wish. You need hdparm 2.20 or above and wiper.sh 2.1 or above. Hope this helps a bit.I would probably go the a later dev kernel if it were me, but it is up to you. Ubuntu will have the trim function in the next release.

---

### Post by Paqman on 2010-07-10
Gparted can align the partitions on the drive for you. Just put a 1MB gap in front of any primary or logical partitions and uncheck "round to cylinders".

If you're using swap i'd wind the [swappiness]("https://help.ubuntu.com/community/SwapFaq#What is swappiness and how do I change it?") way down to prevent the system writing to your swap excessively. If you've got enough RAM there's no reason why you shouldn't set swappiness down to 10 or 0.

Other than that the only thing you need is a newer kernel that does TRIM on Ext4. You'll have to wait for Maverick to be released in October for that unless you want to go installing non-Ubuntu kernels.

---

### Post by stmiller on 2010-07-10
Trim is not automatic in 2.6.33 and later.

You have to manually specify the option 'discard' in your /etc/fstab 

Ex:

```
/dev/sda1 / ext4 defaults,noatime,discard 0 1
```

Also trim is ext4 only.

---

### Post by oldfred on 2010-07-10
Herman usually has lots of detail, while for Karmic settings general would be the same for Lucid:

Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)

---

