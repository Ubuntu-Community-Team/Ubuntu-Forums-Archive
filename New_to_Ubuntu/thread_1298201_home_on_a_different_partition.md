---
title: "/home on a different partition"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by Desert Sailor on 2009-10-22
When I upgrade from 9.04 to 9.10, I desire to establish /home on it's own partition.  (so future new installs won't require a save and reload of /home). 

My plan is to copy my existing /home with all pictures and music to a USB external drive, wipe my existing install, then start fresh with a virgin install of Ubuntu 9.10.  I will create a special partition for /home as part of my new install and converstion to the ext4 file system.  Once installed, I'll copy back the documents, pictures, music from my external file.  

Does that sound like a viable plan, or am I missing something here.  Perhaps there is an easier and/or faster way, but I can't think of it...any ideas?

---

### Post by falconindy on 2009-10-22
If you're planning on doing a clean install with 9.10, then this is the right way to go. However, doing this implies that you're partitioning your drives manually. Make sure you understand the implications of this and what the entire process entails.

---

### Post by Mike_IronFist on 2009-10-22
> **Desert Sailor said:**
> When I upgrade from 9.04 to 9.10, I desire to establish /home on it's own partition.  (so future new installs won't require a save and reload of /home). 

My plan is to copy my existing /home with all pictures and music to a USB external drive, wipe my existing install, then start fresh with a virgin install of Ubuntu 9.10.  I will create a special partition for /home as part of my new install and converstion to the ext4 file system.  Once installed, I'll copy back the documents, pictures, music from my external file.  

Does that sound like a viable plan, or am I missing something here.  Perhaps there is an easier and/or faster way, but I can't think of it...any ideas?

Yes that's the way to go.

After that, any further upgrades are very simple. When in the partition editor for the Ubuntu installer, you can mark your /home partition to be mounted as a /home partition but do NOT format it. All you have to do is click "Use as (Whatever filesystem it already has)" and then set its mount point to /home like you did the first time you made it, only making sure that it's not marked for formatting.

Then mark your / (root) partition to be mounted at / (root), and DO format it.

---

### Post by Zoot7 on 2009-10-22
Another recommendation for a separate home partition. All you've to do is install the new version of ubuntu, then install your applications, reactivate the partition with home on it, and you've all your documents and settings back. Here's a good guide:
[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

