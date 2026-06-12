---
title: "No or slow internet after installing Ubuntu 10.10"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by Len666 on 2010-12-01
I used to run Windows 7 on my HP G62 laptop and had no problems accessing the internet via Wifi USB adapter, the only way I can access the internet. For several reasons I formatted my disk and installed Ubuntu 10.10.

The problem with 10.10 was that my wireless USB adapter did not work or did a very bad job. It took minutes for a simple page to emerge. After 5 minutes there was no traffic at all.

I formatted again and reinstalled Windows 7. I expect to have totally removed any trace of Ubuntu, but: the problem with the internet stayed the same in Windows 7.

What te f..k does Ubuntu do with the wireless connection.
I totally formatted my disk and did a complete fresh reinstall of W7 but I still see some GRUB application stayed in place. 
How do I get my internet connection back?
I have to use another computer to get online.

Please help.

Len.

---

### Post by cariboo on 2010-12-01
It's pretty hard to diagnose an Ubuntu problem, when you don't have it installed any more. I assume you are installing from the the restore partition on your laptop, and don't have an actual Windows 7 install disk. To repair you mbr have a look [here]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/").

To get your wireless to work, you'll probably have to download and install the correct drivers from your laptop's manufacturers web site.

---

### Post by Len666 on 2010-12-02
> **cariboo907 said:**
> It's pretty hard to diagnose an Ubuntu problem, when you don't have it installed any more. I assume you are installing from the the restore partition on your laptop, and don't have an actual Windows 7 install disk. To repair you mbr have a look [here]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/").

To get your wireless to work, you'll probably have to download and install the correct drivers from your laptop's manufacturers web site.

Thank you.
I have a full set of W7 recovery discs, includding all the drivers. I have a working W7 driver for my USB Wireless adapter.
The point is after a full recovery, including total formatting the hardd drive, making new partitions and installing OS, MBR and application software, the wireless is still performing as badly as under Ubuntu.

Ubuntu ****ed someting up and I am stuck with the consequences here.

So, what could possibly be altered by Ubuntu that can't be undone by a W7 recovery?

And even more important: how can it be undone?

Getting pretty desperate.

Thanks for advice, referral to another forum, or whatever.

Len.

---

### Post by paulocoghi on 2010-12-02
If Ubuntu changed something in your USB adapter, I think it will be easier to correct the "possible" problem in Ubuntu, not in Windows.

You either need to install Ubuntu again. Just open it via Live CD.

In fact Windows will hardly offer advanced options to (re)configure your adapter.

---

### Post by Len666 on 2010-12-02
Sorry guys, I sent you on a wild goose chase.
I forgot to adjust the sending power of the alfa adapter (blush)
Everything is ok and I'll put this thread on "solved".
 
One last remark: the way the adapter behaved was very, very much like the way the adapter behaved under Ubuntu (with sending power on 100%). Looks like the Linux driver for the Alfa doesn't react properly to this setting.
 
Well, thanks for your time...
Len.

---

