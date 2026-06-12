---
title: "? Best FS for VBox vm's to live in"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by mikodo on 2010-10-14
Hello everyone,      I am using Lucid as my OS, and have made 5 Ext4 partitions, to put VBox vm's in. I want to have newer distros like Lucid, Maverick, the soon new releases of Mint and Fedora, along with Windows 7 in them.   When I installed Windows 7 as a guest, VBox told me to use an Ext3 FS for it, as there is a bug attached to Ext4, with Windows vm's.     Question:      For all of the distros mentioned above, would Ext3 be better, than Ext4? I am thinking of compatibility with the distros and certainty Ext3 is stable. Or should I use Ext4 when I can for new distros for it's enhancements?    Hopefully that question made sense.      Thanks.

---

### Post by CharlesA on 2010-10-14
I haven't had any problems with using EXT4.

I recall a mention of something to do with running VMs on EXT4 partitions, but I can't recall what the error message said (and what it mentioned for a solution)

---

### Post by mikodo on 2010-10-14
Thanks Charles, 

All I am aware of is the warning with Windows 7 guests vms, that Ext4 should not be used because of a bug. For accuracy sake, it didn't **say** to use Ext3, but I didn't get a warning with it either.

 Thanks.

---

### Post by CharlesA on 2010-10-14
Is it the same error mentioned [here]("http://forums.opensuse.org/english/get-help-here/applications/445379-getting-error-message-virtualbox-about-ext4.html")?

I had to have "Use host I/O cache" checked under storage to get rid of that error.

---

### Post by mikodo on 2010-10-15
> **CharlesA said:**
> Is it the same error mentioned [here]("http://forums.opensuse.org/english/get-help-here/applications/445379-getting-error-message-virtualbox-about-ext4.html")?

I had to have &quot;Use host I/O cache&quot; checked under storage to get rid of that error.

 Hi Charles,  This exactly the bug I was referring to, now that you have taken the time to investigate it, I recognize it.  I was running Windows 7, in an Ext4 FS partition and had made a snapshot of it once, with out permanently enabling the host's I/O cache settings in the vm. I then installed it a few times in different Ext3 FS's Partitions and found that the OS would no longer install, it just continually installed and reinstalled, without ever completing. I had thought the disk had become corrupted, didn't worry about it, as I had already made up by mind to get another copy of Windows 7 only a 32-bit instead of the 64-bit, I was using last nite. Maybe I had tried to put it back in another Ext4 FS, and didn't notice.  Charles, your efforts of bringing this to my attention, has not gone unnoticed by me! I will correct my actions.  Thank you.

---

