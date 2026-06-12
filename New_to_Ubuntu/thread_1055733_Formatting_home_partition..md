---
title: "Formatting /home partition."
date: 2009-01-31
forum: New to Ubuntu
---

### Post by Superdarion on 2009-01-31
Hello there. I have a bit of a problem here and I was wondering if anyone could help me.

I have 3 partitions in my HD. One is for Windows, another one for linux (/) and the last one for /home. I want to be able to see the /home partition from Windows and I got this driver with a name I can't remember.

Now, the problem is that the Inode must be set to 128 for the driver to work and for that I must re-format the /home partition. That's problematic for obvious reasons (me being logged-in, basically), so I wanted to know if there's an easy way to do this.

I was thinking something in the lines of enabling the root account (or maybe failsafe mode) and from there just run the mkfs.ext3 utility to format, but I'm not really sure if the root account has any files in the /home folders or not.

Any ideas?

---

### Post by Eisenwinter on 2009-01-31
To touch any partitions, you need to use a LiveCD, so they're not mounted.

Also bear in mind, if you want your Linux /home partition to be viewable in Windows, it needs to be in a format Windows supports, like NTFS or FAT32 or something.

---

### Post by zabien1970 on 2009-01-31
Not quite sure how to help but was wondering if you could use the live cd to split your /home folder in half then use the cp command to make a copy of your /home folder so you have a backup, less worries if you screw something up then

---

### Post by HotShotDJ on 2009-01-31
> **Eisenwinter said:**
> Also bear in mind, if you want your Linux /home partition to be viewable in Windows, it needs to be in a format Windows supports, like NTFS or FAT32 or something.Thats not completely true.  If the drive is formatted ext2 or ext3, one can use the [Ext2 Installable File System For Windows]("http://www.fs-driver.org/") driver to give Windows read/write access to it.

---

### Post by Superdarion on 2009-01-31
Aah, the liveCD, of course!

About back-up, I JUST formatted, so my /home is about 100mb and I just copied into a thumb drive. And as I said in the original post, I already have an ext3 driver for windows, the only problem is that it doesn't support Inodes>128 and that's why I need to reformat.

Thanks a lot for answering.

---

