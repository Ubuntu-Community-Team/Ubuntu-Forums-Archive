---
title: "wireless backup from ubuntu laptop to xp home wired"
date: 2011-03-29
forum: New to Ubuntu
---

### Post by themanfromiac on 2011-03-29
Hi Everyone,

I have a wired xp home and an Ubuntu 10.10 laptop(wireless). Everything is working fine. I samba share from the laptop(T42) to xpHome(BFC), and also share from BFC to T42. All the shares are working fine.

I would like to automatically backup (via lucky backup or similar) T42 (and everything that is in it) to an external hard drive (F drive) on BFC. How do I do this, when I can't see the F drive on BFC from T42?
Thanks for all the help in advance.:smile:

---

### Post by Paddy Landau on 2011-03-30
You said that you can use Samba. I don't remember Windows well, but can't you create a folder on F: and set that folder to public shared?

Once you can see the folder from your laptop, you could use something like [rsync]("apt:rsync") or [rdiff-backup]("apt:rdiff-backup"). However, bear in mind that when you back up from Linux to a Windows machine, you will lose your files' permissions settings. This could be a problem when restoring.

Personally, I would back up either using an off-site on-line program (such as [SpiderOak]("https://spideroak.com/")), or onto an ext4-formatted external drive. (I do both.)

---

### Post by themanfromiac on 2011-03-30
Thanks Paddy,

I was starting to suspect that I was attempting to do something that wasn't quite right.
I will take your advice and backup to correctly formatted external drive.

Thanks and all the very best:smile:

---

