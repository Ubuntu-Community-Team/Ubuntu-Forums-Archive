---
title: "Partition Info"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by Don1500 on 2009-06-05
I don't really have a problem, just would like an answer.

I have Intrepid installed on a single partition hard drive, 500 gig, (with about 5 gig for swap). As soon as I set it up this way I read that it is a good idea to put /root on one partition, I guess 10 gig would do, and put /home on a separate, larger, partition (in this case it woould be about 480 gig). Can I just use g-parted to make the single partition smaller then add the second partition and move /home over to it? Or do I need to reinstall from the start? :?:

---

### Post by Tibuda on 2009-06-05
Yes, you can using Gparted from the LiveCD, because you can't resize a partition if it is already mounted. I recommend you to backup your files before resizing it.

---

### Post by Don1500 on 2009-06-05
Thanks, I have a live CD of g-parted(only) I would use that. But when I move /home will it be recognized as it is now, or do I have to point to it some how?

---

### Post by Tibuda on 2009-06-05
Hmmmm.... Not sure, you better move everything from the /home folder in the root partition to the home partition before leaving the LiveCD. And I forgot to tell you have to edit your fstab to mount your home partition everytime.

EDIT: Psychocats rocks. See instructions on how to create a home partition from a already working ubuntu: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Miljet on 2009-06-05
Here is an excellent guide to do exactly what you want:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Don1500 on 2009-06-07
> **Miljet said:**
> Here is an excellent guide to do exactly what you want:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
I usually have no problem with following directions on these forums. I didn't do it this time. Somehow I screwed up. Had to reformat everything, All is well though I keep the important stuff on a separate drive. Now all my partitions are correct, 50 gig root, 445 gig /home and 5 gig swap (These numbers are not exact.)

):P Thanks for the help, even if I did have to re-install.

---

