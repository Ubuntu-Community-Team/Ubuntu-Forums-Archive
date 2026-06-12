---
title: "Should I..."
date: 2009-10-22
forum: New to Ubuntu
---

### Post by herbertportillo on 2009-10-22
I run Ubuntu 9.04 Jaunty 64-bit on my computer. I completely got rid of my Windows Vista. When I installed it on my hard drive a few months ago I ran the default settings, so my hard drive changed from NTFS to ext3. Yesterday, I changed my computer to ext4 following the instructions on the Ubuntu Official Documentations website. So far, I don't feel much of a difference, but I suppose that's because everything was written when my hard drive was ext3.

So my question is when Karmic comes out next week (excited!), should I do a clean install, or should I just do an in-place installation? I know that if I do a clean fresh installation, everything would be completely re-written. I have an extra internal hard drive so that I can move all my important things over, so that isn't a big deal. I suppose my question is since I have ext4, would I see better performance with a clean install than an in-place install?

Any and all input is appreciated. Thanks.

---

### Post by jbrown96 on 2009-10-22
Clean install. You can upgrade ext3-->ext4 but it's not a real upgrade. The largest speed benefit from using ext4 is from extents, but that cannot be upgraded. You are mainly getting the increased address space, but you will never have enough storage, so there's no benefit. 

I always recommend clean installs; I can't think of a situation where it would be undesirable. You should have /home on its own partition, then upgrading is soooo easy. All your settings and files will be preserved. And a clean install will only take 20 minutes.

---

### Post by yeats on 2009-10-22
> **jbrown96 said:**
> Clean install. You can upgrade ext3-->ext4 but it's not a real upgrade. The largest speed benefit from using ext4 is from extents, but that cannot be upgraded. You are mainly getting the increased address space, but you will never have enough storage, so there's no benefit. 

I always recommend clean installs; I can't think of a situation where it would be undesirable. You should have /home on its own partition, then upgrading is soooo easy. All your settings and files will be preserved. And a clean install will only take 20 minutes.

+1 - it's the best way to go :-)

---

### Post by Psyphre on 2009-10-22
> **jbrown96 said:**
> Clean install. You can upgrade ext3-->ext4 but it's not a real upgrade. The largest speed benefit from using ext4 is from extents, but that cannot be upgraded. You are mainly getting the increased address space, but you will never have enough storage, so there's no benefit. 

I always recommend clean installs; I can't think of a situation where it would be undesirable. You should have /home on its own partition, then upgrading is soooo easy. All your settings and files will be preserved. And a clean install will only take 20 minutes.

But even if someone had a separate home directory (like me when I installed jaunty), wouldn't it still be ext3 after installing Karmic? So a clean install wouldnt help unless you wiped it totally clean and reinstalled your home directory aswell.

---

### Post by herbertportillo on 2009-10-23
I think I'll do a clean install. I suppose it didn't do much to upgrade the hard drive to ext4 7 days before Karmic comes out, haha.

Well, thanks for your help everybody. I hope that next week all your upgrading goes smoothly and without any road bumps, that is assuming you choose to upgrade to Karmic.

Oh yeah, and screw Windows 7.

---

### Post by SunnyRabbiera on 2009-10-23
Just remember to BACK UP your data.
But honestly there is no real good reason to "upgrade" to EXT4, it offers no real security or features over EXT3 other then speed.
But I use EXT3 myself on Karmic RC1 and it is speedy.

---

### Post by undecim on 2009-10-23
> **jbrown96 said:**
> I always recommend clean installs; I can't think of a situation where it would be undesirable. You should have /home on its own partition, then upgrading is soooo easy. All your settings and files will be preserved. And a clean install will only take 20 minutes.

+1

the only thing with that though is system wide settings aren't saved, but that's usually only one or two settings, if any, that most people will need to change.

[quote=Psyphre]But even if someone had a separate home directory (like me when I installed jaunty), wouldn't it still be ext3 after installing Karmic? So a clean install wouldnt help unless you wiped it totally clean and reinstalled your home directory aswell[/quote]

True, you wouldn't have that speed bonus, but with the home directory, it really isn't that big of a difference in performance, unless you are running batch scripts on files in your home directory. The main speed boost comes with reading files from /usr/ and read/writing files in /tmp/

Personally, I keep my home directory as reiserfs (slightly faster than ext3, but no need for routine disk checks!)

I'm also considering switching to xfs, since my home dir is ecryptfs encrypted, and xfs supposedly uses less CPU (leaving more cpu cycles for ecryptfs to [de/en]crypt my files)

---

### Post by jbrown96 on 2009-10-23
> **SunnyRabbiera said:**
> Just remember to BACK UP your data.
But honestly there is no real good reason to "upgrade" to EXT4, it offers no real security or features over EXT3 other then speed.
But I use EXT3 myself on Karmic RC1 and it is speedy.

That's not entirely true. Ext4 has significantly better write caching, which lowers wear (somewhat) and power use (more so). Every little bit counts on my laptop. I agree that for most operations disk usage is not a huge factor, but things like boot times are really impacted. In 9.04, I did some benchmarking with various file systems. Ext4 was something like 20 seconds faster to boot (~58 seconds if I remember correctly). There has also been some tweaking in the kernel, so ext4 is working even better in 9.10.

---

### Post by SunnyRabbiera on 2009-10-23
> **jbrown96 said:**
> That's not entirely true. Ext4 has significantly better write caching, which lowers wear (somewhat) and power use (more so). Every little bit counts on my laptop. I agree that for most operations disk usage is not a huge factor, but things like boot times are really impacted. In 9.04, I did some benchmarking with various file systems. Ext4 was something like 20 seconds faster to boot (~58 seconds if I remember correctly). There has also been some tweaking in the kernel, so ext4 is working even better in 9.10.

Still I say why not use EXT3 when it works for you.
Personally I am waiting till Ubuntu 10.04 to see if EXT4 will work for me.

---

