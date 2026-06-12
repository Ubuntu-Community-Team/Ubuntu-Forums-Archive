---
title: "Importing NTFS - EFS files"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by MattTL on 2009-10-01
I have made a dual boot system - Ubuntu / Windows XP.  XP has EFS enabled in NFTS.

Windows became corrputed during the installation and no longer boots.

I can see my windows partition from Ubuntu (which boots fine, thank you!).  But the files will not open- I get a permissions error.  From reading the forums /posts I gather this is because the windows files are encrypted within EFS.  

I know the password for my Windows installation.

Is there anyway I can enable Ubuntu to open the EFS encrypted files on the NTFS volume?

Thanks for any help you can offer.

Regards


Matt

---

### Post by Mark Phelps on 2009-10-01
Hate to ask, but did you use Ubuntu to shrink the encrypted MS Windows volume to install Ubuntu? If so, that's probably what corrupted it.

If the whole volume was encrypted, then even if you had an XP CD, and could boot using that, you most probably wouldn't be able to run fixboot or fixmbr.

I don't believe that you can bypass the encryption from inside Ubuntu -- but this is not my area of expertise and I defer to others who know far more about this than me.

---

### Post by MattTL on 2009-10-02
Mark,

You're right, I did let Unbuntu resize the partition (rather than using something like Norton) and I think that's whats corrupted the Windows Partition (at least the early part).  Windows fixmbr didn't help - the problem is some corrupted sys fils in the first  few clusters I think.

Anyway - still struggling to read back the EFS files from Unbuntu.  This seems like something anyone with a dual-boot (i.e. dual OS) pc might want to do.  Surely the Unbuntu team are onto it...?

Help please!

---

