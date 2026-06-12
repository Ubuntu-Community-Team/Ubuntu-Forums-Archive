---
title: "How do I move/resize the extended partition of a drive?"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by Rossta on 2009-09-12
Having sorted out the problems I was having with GParted I have now come across another issue...

When I went to resize my partitions I found that I could very easily shrink the size of my old NTFS partition, but was then unable to expand the Ext3 Filesystem as it was contained within the extended partition which could not be adjusted in any way.

For those who did not read my first problem, I am unable to download anything as I am told that there is 0kB free in the "/" directory.

Here's hoping I get this sorted soon as my GF is trying to get me to go back to Windoze already.  (2 days in... not good)

Thanks in advance

Ross.

---

### Post by drs305 on 2009-09-12
If you are using gparted, the *trick* is you have to expand the extended partition first. Select the extended partition (light blue border) f*rom the bottom panel*. If you are really precise, you can click on the thin light blue border but that is a bit more difficult. ;-)  Then select Partition, Move and move it to occupy the unallocated space to the left. Once you have executed this, you will be able to expand the logical partitions to the left as well. Of course, your logical partitions will need to be unmounted, so you will probably have to use the LiveCD or a rescue CD.

I wrote a guide about resizing the / partition which may explain things or offer tips of use in your situation.[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by Rossta on 2009-09-12
> **drs305 said:**
> 
I wrote a guide about resizing the / partition which may explain things or offer tips of use in your situation.[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

Thanks for that.  It is precisely the problem I am having.

However there is one problem I am still having and that is that when I select the extended partition the option to move or resize is not avaliable

I did take a screenshot to show you what I mean, but was unable to complete the save anywhere :(

Any more ideas?

---

### Post by drs305 on 2009-09-12
> **Rossta said:**
> Thanks for that.  It is precisely the problem I am having.

However there is one problem I am still having and that is that when I select the extended partition the option to move or resize is not avaliable

I did take a screenshot to show you what I mean, but was unable to complete the save anywhere :(

Any more ideas?

Having a screenshot would certainly make things easier. Are your partitions unmounted? In the lower panel, any partition you are working with must be unmounted. Mounted partitions have a "keys" symbol next to them. 

Are you working from within the LiveCD Desktop? That is one way to ensure your partitions can be unmounted. Also, even with the LiveCD, you have to unmount the swap partition (highlight it, the Partition, Swapoff).

---

### Post by Rossta on 2009-09-12
> **drs305 said:**
> Having a screenshot would certainly make things easier. Are your partitions unmounted? In the lower panel, any partition you are working with must be unmounted. Mounted partitions have a "keys" symbol next to them. 

Are you working from within the LiveCD Desktop? That is one way to ensure your partitions can be unmounted. Also, even with the LiveCD, you have to unmount the swap partition (highlight it, the Partition, Swapoff).

:PWe have actually solved the problem here now.:P

The partition was indeed mounted and I completely missed the keys icon that was beside the swap partition....  My GF on the other hand looked at your screenshots and pointed out that there were keys in ours, but not in yours.  When I asked "Where?" I got the reply "Next to the pretty turquoise box"  and upon ReBootinbg again with the LiveCD found her to absolutely correct.

I'm not going to here the end of this for a while.:(

In happier news she now want to know when we can nuke the WinXP partition. :D:D

---

