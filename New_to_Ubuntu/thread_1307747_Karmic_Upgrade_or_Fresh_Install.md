---
title: "Karmic: Upgrade or Fresh Install?"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by ovroniil on 2009-10-31
I am in little bit confused. I am using Jaunty. Now I want to switch to Karmic. For switching, which process will be better for me? Should I use the Update Manager for upgrading or should I perform a fresh install? Which option has more pros and less cons?

[By the way while installing Jaunty, I had mounted my '/' in one partition and '/home' in another partition. Both of them are using EXT3.] 

Any suggestion?

---

### Post by phillw on 2009-10-31
> **ovroniil said:**
> I am in little bit confused. I am using Jaunty. Now I want to switch to Karmic. For switching, which process will be better for me? Should I use the Update Manager for upgrading or should I perform a fresh install? Which option has more pros and less cons?

[By the way while installing Jaunty, I had mounted my '/' in one partition and '/home' in another partition. Both of them are using EXT3.] 

Any suggestion?

well, before you anything, read my blog.

A fresh install will allow the system full usage of ext4, an upgrade leaves you on ext3.

Me ? as you will read, i upgraded.

Phill.

---

### Post by RC1139 on 2009-10-31
In my opinion, doing a fresh install is the safer and quicker option.  I like starting fresh every now and then.

---

### Post by drseuk on 2009-10-31
Hi,

As I've posted elsewhere in the forums here, I concur with RC1139 - a fresh install (obviously after having backed up your data elsewhere to be restored later) is a much safer bet.

---

### Post by donato roque on 2009-10-31
Since you have your /home in a separate partition you can opt to stay with ext3 and leave it untouched.
I believer in installing the os itself.  After downloading the iso, burn it in your cd.  Use the cd to install the new os in the / partition.  Here's a [link if you want to review the steps]("https://help.ubuntu.com/9.04/installation-guide/i386/index.html").

Mount your /home.  You can actually mount it during the installation.  Letting the installer do the work is a good idea.

---

### Post by invenit on 2009-10-31
> Should I use the Update Manager for upgrading or should I perform a fresh install?

I triple boot WinXP, Ubuntu & CrunchBang on a Dell Dimension 3000, so I ended up doing both. I upgraded jaunty to karmic during the beta period, then performed a new install on the 29th (mostly curious about grub2).

My experience: either way is great! The devs really did some good work. I liked jaunty all right, but since my machine suffered from the Intel graphics bug so my upgrade was not smooth. OTOH, Intel graphics works great in karmic.

Anyway, works for me. :KS

---

### Post by ovroniil on 2009-10-31
Just a recheck[I]**.**[B]

"If I upgrade using the update manager, the ext3 will be used."
"If I run a fresh install, the ext4 will/may be used." [/B][/I]

So there is no big difference between these two process. I mean both processes are same, Right?

---

### Post by invenit on 2009-10-31
> So there is no big difference between these two process. I mean both processes are same, Right? 

Kinda, sorta. IMO ext4 & grub2 weigh the scales in favor of a new install, but that is mostly because I want to familiarize myself with the newest technology.:popcorn:

---

### Post by ovroniil on 2009-10-31
hmmm.... but for the last couple of days, I've seen that in this forum people are facing lots of problem after upgrading to Karmic compare to a fresh installation. So (as a noob) I think although there is no difference in theory but the practical scenario is different. There may be some difference between an UPGRADE and a FRESH INSTALL.

---

### Post by sdpiowa on 2009-10-31
When you perform a fresh install, Karmic creates its own configuration files.  When you upgrade, it will attempt to use a lot of the old ones.  The fresh install can be more reliable, but the upgrade should work just fine.

I did encounter a major problem with a distribution upgrade once (it corrupted the OS), but overall it works well.

---

### Post by sdim on 2009-10-31
Fresh installation is the best,I think,as you will benefit from the ext4 file system,and Grub 2.Otherwise,upgrading is ideal if you don't want to back up your files and re-install the OS.

---

### Post by Norm24 on 2009-10-31
I upgraded without any issues whatsoever.As far as Grub2 and Ext4 goes I have no need for those as Grub Legacy and ext3 work fine for me.

---

### Post by Zoot7 on 2009-10-31
Another vote for a fresh install; I gave up on Upgrades after Hardy to Interpid broke everything.
These days my solution is to have /home on a separate partition, saves a lot of hassle. :)

---

