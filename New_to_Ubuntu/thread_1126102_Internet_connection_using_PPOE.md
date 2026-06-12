---
title: "Internet connection using PPOE"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by iamleaf on 2009-04-15
Hello everyone, I've posted a previous thread asking for help on how to install the modem. 

As I have found out, you guys told me that it was plug and play.

I've finally formatted my disks and installed windows and ubuntu using different partitions.

How can I connect to the internet? I've tried typing in the appropriate commands in the terminal (sudo pppoeconf) following the help documentation, but the terminal messages say that it can't access, even though it has recognize the three ethernet ports. So I can't modify anything.

I have modified the network, using a ppoe connection. I typed in a DNS server and everything....

please help?

And why doesn't my third partition where I've installed ubuntu show up in windows? I need that extra space.

---

### Post by zvacet on 2009-04-15
Did you tied to configure your network with network manager tool?If you use username and password then in network manager select DSL click on add button and type your info.

You can not see Ubuntu partition from Windows.You need driver for that.Try [this]("http://sourceforge.net/projects/ext2fsd") one.

---

### Post by iamleaf on 2009-04-16
Thanks for the help mate.

I tried googling the problem. Found a forum that already had the same problem solved.

YAY!

Now I'm using internet from ubuntu

---

### Post by ubuntu27 on 2009-04-16
> **iamleaf said:**
> Thanks for the help mate.

I tried googling the problem. Found a forum that already had the same problem solved.

YAY!

Now I'm using internet from ubuntu

Can you provide the URL of the Forum where it helped you to solve your problem?

---

### Post by iamleaf on 2009-04-16
Its the Ubuntu Forum only.

[http://ubuntuforums.org/showthread.php?t=78337](http://ubuntuforums.org/showthread.php?t=78337)

---

