---
title: "Ubuntu Install"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by Musick Man on 2008-12-31
Hi,

I have a computer, which currently has Windows XP SP2 on it. I also have 3 hard drives in it, 

1. The Windows XP Hard Drive in it
2. A Backup/application and game Hard Drive
-and-
3. A Unused Hard Drive. 

I was wondering if I could install Ubuntu 8.10 on the Un-Used Hard Drive, without risking the lost of all my Windows XP Stuff, and if I do install Ubuntu, if i would be able to access my other 2 Drives (or at least my backup one) for games and other files. 

Thanks for the feedback :D 

Musick Man

p.s. I would like to access XP also, after all of it is done also. (So it would be a duel boot XP/Ubuntu)

Edit: Also, how would I go about installing Ubuntu on the Unused Hard Drive, without messing up XP or the other HD.

---

### Post by donkyhotay on 2008-12-31
Yes, you can put ubuntu on your unused drive and not affect any of your windows files. Just be careful when partitioning which drive you choose to repartition (and if your at all uncertain STOP). Yes you can also access your windows drives/files from ubuntu however be aware that games won't run correctly straight from the windows install. You would need to install them again with wine so that the registry values are correct.

---

### Post by Musick Man on 2008-12-31
ok Thanks. 

Knowing that, to make sure that I partition the right disk drive, can I just unplug the other 2, Install Ubuntu, and then plug the 2 back in? 

If I do this, would Windows XP show up under the Other OS cagatory, in the Boot Loader? And if not, is there a way to make it show up in the list?

Thanks again,

Musick

---

### Post by kansasnoob on 2008-12-31
What you're asking is difficult:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

I personally prefer having all operating systems on one drive. What you're asking can be accomplished but it's difficult!

Hardly a newb thing to do!

---

### Post by crjackson on 2008-12-31
> **Musick Man said:**
> ok Thanks. 

Knowing that, to make sure that I partition the right disk drive, can I just unplug the other 2, Install Ubuntu, and then plug the 2 back in? 

If I do this, would Windows XP show up under the Other OS cagatory, in the Boot Loader? And if not, is there a way to make it show up in the list?

Thanks again,

Musick


Actually that should work, I've done it many times and it's only failed to work on one machine, one time.

Grub may or may not pick up the windows drive on it's own, but it would only be able to do that after pluging the other drives back in and booting once or twice so that the drive is assigned a uuid. It may also depend on the drive type. It works perfect on my SATA drives, not sure about eide though.

---

### Post by crjackson on 2008-12-31
> **kansasnoob said:**
> What you're asking is difficult:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

I personally prefer having all operating systems on one drive. What you're asking can be accomplished but it's difficult!

Hardly a newb thing to do!

It's not really that hard. I did that the very first time I installed Ubuntu 7.04 - but as I said, I was using all SATA drives so I can't speak for eide. They do act differently I think.

---

### Post by Musick Man on 2008-12-31
> **crjackson said:**
> Actually that should work, I've done it many times and it's only failed to work on one machine, one time.

Grub may or may not pick up the windows drive on it's own, but it would only be able to do that after pluging the other drives back in and booting once or twice so that the drive is assigned a uuid. It may also depend on the drive type. It works perfect on my SATA drives, not sure about eide though.

Ok, thanks for the Tip. I got IDE drives in my computer.

Just a thought on this first, if for some reason the Boot Loader doesent pick up Windows XP as a OS, is there a way to get back onto the XP Machine? Would it be as simple as removing the drive with Ubuntu?

Sorry I have so many questions, this is the first time that I have tied something like this.

Thanks,

Musick

---

### Post by crjackson on 2009-01-01
> **Musick Man said:**
> Ok, thanks for the Tip. I got IDE drives in my computer.

Just a thought on this first, if for some reason the Boot Loader doesent pick up Windows XP as a OS, is there a way to get back onto the XP Machine? Would it be as simple as removing the drive with Ubuntu?

Sorry I have so many questions, this is the first time that I have tied something like this.

Thanks,

Musick

Yes you can make it available. If you unplug the drive during the install then plug it back in afterwards that drive won't be affected at all. It would be as simple as just making that drive your 1st boot device. Just back up all your stuff and you'll be fine. Probably the worst that would happen would be that after pluging in the other drives, grub won't boot the Ubuntu partition. That can be adjusted too by just reinstalling grub with all the drives pluged in.

---

### Post by stalkier on 2009-01-01
> **crjackson said:**
> yes you can make it available. If you unplug the drive during the install then plug it back in afterwards that drive won't be affected at all. It would be as simple as just making that drive your 1st boot device. Just back up all your stuff and you'll be fine. Probably the worst that would happen would be that after pluging in the other drives, grub won't boot the ubuntu partition. That can be adjusted too by just reinstalling grub with all the drives pluged in.

+1

---

