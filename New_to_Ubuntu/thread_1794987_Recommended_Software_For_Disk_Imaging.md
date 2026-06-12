---
title: "Recommended Software For Disk Imaging"
date: 2011-07-01
forum: New to Ubuntu
---

### Post by tb75252 on 2011-07-01
I am using Ubuntu 11.04, 32-bit.

When I was on Windows XP I used Macrium Reflect (Free Edition) to create disk images on DVDs.  Is there something similar that I can use with Linux?  (Would prefer something GUI based...)

I have done some research on this subject, and here are my observations:
1)  Partimage:  I don't think that I can use it because it does not support the ext4 filesystem.  (Ubuntu 11.04 default install uses ext4, correct?)
2) Clonezilla: I am not sure that it can image a partition (or an entire HD) to a DVD.  The interface looks intimidating!
3) GParted:  I don't think that it does disk imaging.  The program allows to do copy/paste of partitions but that is not the same as imaging.

Thanks for your suggestions!

---

### Post by wolfen69 on 2011-07-01
Checkout [Ultimate Boot CD]("http://www.ultimatebootcd.com/"). It has several tools for cloning.

---

### Post by spcwingo on 2011-07-02
One word: Remastersys :)

[http://www.geekconnection.org/remastersys/]("http://www.geekconnection.org/remastersys/")

This will create a live ISO image of your install.

---

### Post by jtarin on 2011-07-02
> **spcwingo said:**
> One word: Remastersys :)
That's three words. :P

I alway dual boot and have used Paragon Partition Manager on a USB flash (Linux based) to do all my hard drive work. Imaging included. The newest free version 11 has more options than you can shake a stick at.(I've been wanting to use that phrase all day) :P

---

### Post by spcwingo on 2011-07-02
> **jtarin said:**
> That's three words. :P

You caught me.  :lolflag:

---

### Post by tb75252 on 2011-07-03
> **jtarin said:**
> That's three words. :P

I alway dual boot and have used Paragon Partition Manager on a USB flash (Linux based) to do all my hard drive work. Imaging included. The newest free version 11 has more options than you can shake a stick at.(I've been wanting to use that phrase all day) :P

...and you are sure that it does disk imaging (as opposed to disk cloning), right?

---

### Post by jtarin on 2011-07-03
> **tb75252 said:**
> ...and you are sure that it does disk imaging (as opposed to disk cloning), right?
And your understanding of these terms is what?

---

### Post by tb75252 on 2011-07-03
> **jtarin said:**
> And your understanding of these terms is what?

My understanding is that disk imaging creates a compressed file only of those sectors on the HD that are actually used.  Disk cloning copies all the sectors on the HD, whether or not they are used.

Therefore, in theory, one could image a HD on a DVD or a set of DVDs (disk spanning).  Disk cloning would require the receiving media to also be a HD (internal or external) of equal or greater capacity. It would not be practical to use DVDs with disk cloning because of the large number of DVDs required.

I got this understanding when I was using Windows XP and backing up my HD with Macrium Reflect (Free Edition).  To be honest, I never had to restore the HD when I was using Windows, so it is entirely possible that I am making some confusion.

In any case, I do not own a second HD (whether internal or external) so I want to find a way to copy my HD on DVDs, and disk imaging appears the way to go.

---

### Post by jtarin on 2011-07-03
Then for your purposes this would be imaging.

---

