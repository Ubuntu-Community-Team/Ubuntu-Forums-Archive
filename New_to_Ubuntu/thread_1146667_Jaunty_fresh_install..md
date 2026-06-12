---
title: "Jaunty fresh install."
date: 2009-05-02
forum: New to Ubuntu
---

### Post by mykyi on 2009-05-02
I'm installing jaunty and have a few partition ?'s.  Should I use Ext4 for my root and home partitions? Also, is /home a logical or primary partitions?  I've read that ext4 is faster, but is it stable?

Right now I have 20 GB / Primary Ext4
                 4GB Swap Logical (Have 2gb Ram)
                 96 GB /Home Logical ext4.

Any suggestions?

Thanks, 

mykyi

---

### Post by nandemonai on 2009-05-02
> **mykyi said:**
> I'm installing jaunty and have a few partition ?'s.  Should I use Ext4 for my root and home partitions? Also, is /home a logical or primary partitions?  I've read that ext4 is faster, but is it stable?

Right now I have 20 GB / Primary Ext4
                 4GB Swap Logical (Have 2gb Ram)
                 96 GB /Home Logical ext4.

Any suggestions?

Thanks, 

mykyi

That looks fine though you really only need equal swap to your RAM in order to hibernate. As far as ext4 goes yes, I hear it's faster but because it's so new and there are still bugs in it I'm not using it myself yet. If you keep regular backups and wont flip out if it corrupts something then go for it, if not then you may want to rethink using it just yet. Depends how important your data is really.

---

### Post by Melk79 on 2009-05-02
I went with ext4 and haven't ran into any problems.  But, the release notes of Jaunty and some other articles have discussed the potential for data loss.  I had moved all my data to an external HDD and then copied back without trouble.  You'd want root primary, as it's the bootable partition, and the others can be logical.  Your approach would work, although from what I've read you don't need that much for root unless you prefer it that way.  10-12GB is supposed to be plenty, so I've read.

---

### Post by Didius Falco on 2009-05-02
> **mykyi said:**
> I'm installing jaunty and have a few partition ?'s.  Should I use Ext4 for my root and home partitions? Also, is /home a logical or primary partitions?  I've read that ext4 is faster, but is it stable?

Right now I have 20 GB / Primary Ext4
                 4GB Swap Logical (Have 2gb Ram)
                 96 GB /Home Logical ext4.

Any suggestions?

Thanks, 

mykyi

1. It depends on you. EXT4 isn't officially recommended, and earlier implementations of it had some problems, but most people using it now say they aren't having any problems with it. I've read that EXT4 was updated right before the build freeze.

If it was a "mission-critical" machine, I'd stick with EXT3. If it's a personal use desktop, I'd go with the EXT4.

keep your back-ups up to date and no worries even it it does have a problem.

One thing to note: Ubuntu 8.10 and down cannot read EXT4 partitions, at least not at this time. So if you are using more than one version of Ubuntu, or more than one flavor of linux, there is that to consider. 

2. I would go with the logical, if only to save the limited Primary partitions for something down the line that requires it. Since Ubuntu will happily live in a logical partition, I'd use that.

I'd Suggest making a 3rd partition, strictly for your own data. I'd shave 70 Gigs of that Home partition and make a separate Data partition, set it up to auto-mount and save all your own stuff in there.

That way if, down the road, you want to do a fresh install of Karmic Koala, all your personal data will be out of the way. Strictly optional, but it was suggested to me by a forum Guru, and it's working out well for me.

3. See #1

---

### Post by mykyi on 2009-05-02
Thanks for the suggestions. I'm gonna stick with ext4 and just backup. Here goes....! Woo hooo!!:guitar:

---

