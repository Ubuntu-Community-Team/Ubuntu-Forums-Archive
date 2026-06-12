---
title: "Acer Aspire One"
date: 2011-04-02
forum: New to Ubuntu
---

### Post by duetome on 2011-04-02
[SIZE=3]Hello,
Just a warning to all of you that use an Acer Aspire One.
If you load Ubuntu 10.10 net-book in side the Windows operating system..
Like I did... watch out for this problem.

I  had Ubuntu working fine for over two months with  both operating systems getting along fine. I loaded a Blue tooth Manager and tried the blue tooth  and it worked fine. I removed one of the blue tooth programs and then lost my Wireless Internet settings and my Internet would only work when I plugged in the land RJ-45.
So when I rebooted I seen in the boot order that I now had:
 Boot to Windows Vista
Major mistake there, As I am wondering why I see Vista. When I have Windows XP Home an Ubuntu 10.10 net-book.
This Vista I started up  is actually   the Acer Recovery console.
Even after I click on do nothing and just exit without saving I lost the boot up for Ubuntu and could only get XP to boot.
Nuts I will never do that again!!!!
Learn from my stupid mistake stay away from the Vista in the boot order. 
[/SIZE]

---

### Post by fabricator4 on 2011-04-03
> **duetome said:**
> This Vista I started up  is actually   the Acer Recovery console.
Even after I click on do nothing and just exit without saving I lost the boot up for Ubuntu and could only get XP to boot.


Yes, it knows nothing about other operating systems and will re-install its MBR over grub.

You can recover it however.  Instructions are [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

Chris

---

