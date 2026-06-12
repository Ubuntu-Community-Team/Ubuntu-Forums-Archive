---
title: "No SD Card Recognition"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by corowakid on 2009-05-02
Hi all,

I've installed 9.04 Remix, and everything is going well on my Aspire One netbook. EXCEPT, I can't get the OS to recognise the 16Gb HC SD card I'm using. Its in the card slot that Aspire uses to add the memory to the overall memory of the system (worked well with Puppy, and of course with Fedora). But it just won't show at all in Ubuntu.

Can anyone help in getting the card to mount, or even show up somewhere in the Ubuntu system menus? I'd appreciate any advice. Thanks

---

### Post by fahadsadah on 2009-05-02
Please type ```
sudo fdisk -l
``` into a Terminal, and post the output here.
You may be asked for a password. If so, give it. Thanks.

---

### Post by corowakid on 2009-05-02
> **fahadsadah said:**
> Please type ```
sudo fdisk -l
``` into a Terminal, and post the output here.
You may be asked for a password. If so, give it. Thanks.

Thanks for your response. Here's the output:

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         933     7494291   83  Linux
/dev/sda2             934         981      385560    5  Extended
/dev/sda5             934         981      385528+  82  Linux swap / Solaris
barrie@barrie-laptop:~$

I had a look at some of the menu items, but couldn't see any way to mount the SD card. I switched locations (2), made no difference. Seems the only mount options I can see is the CD-rom. Looked for hardware drivers, but no success.

As you can see, I'ver still got a way to go with Linux (hence me using Linpus as it came with the Aspire). I'd prefer to use Ubuntu. but not having the option for extended storage will limit me (plus the fact that I should really learn how things work).

Hope this is enough for you to point me in the right direction.

---

### Post by corowakid on 2009-05-05
Anyone care to make any comments regarding the SD card not appearing as a storage item in my Aspire One?

Any help appreciated.

---

### Post by V-600 on 2009-05-10
I had the same problem.

The guide at the following site solved my problem.

[http://filthypants.blogspot.com/2009/03/ubuntu-904-jaunty-jackalope-on-acer.html](http://filthypants.blogspot.com/2009/03/ubuntu-904-jaunty-jackalope-on-acer.html)

---

