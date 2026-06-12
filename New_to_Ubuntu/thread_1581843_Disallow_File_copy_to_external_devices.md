---
title: "Disallow File copy to external devices"
date: 2010-09-25
forum: New to Ubuntu
---

### Post by TTR123 on 2010-09-25
Hi,

We have a web development server running on Ubuntu OS (Server). This server has one folder shared (Password protected) on our local network. 

We wish to disallow copying of the files and folders from the server to any other place (to their computer mainly). (They can copy it from the server to server if they wish)

The developers open the files and save on the server for development work.

Can anyone tell me if this will be possible or not?

Thanks
TTR

---

### Post by SeijiSensei on 2010-09-25
Quick answer?  Probably not.  If I can read a file and find a writable location on my local machine, I can copy it there as well.

Harder answer.  Maybe you need to consider something like [CVS]("http://en.wikipedia.org/wiki/Concurrent_Versions_System") or [git]("http://git-scm.com/"), though if they are a bunch of web developers, they're probably tied to Windows and Windows software.  (Unless they're like me who uses a text editor for everything and writes every site from scratch on a Linux box.)

---

### Post by TTR123 on 2010-09-25
Actually, we are using SVN but my main purpose is to stop employees from taking our code. 

I think, if they have read-write access then they can copy. I think I should look for ways to disable USB drives.

---

### Post by SeijiSensei on 2010-09-25
Well, sure, that's a start, but it's not much protection.  How about if I open a file, copy its contents by highlighting it with my cursor, then paste it into my mail client and send it to my off-site mailbox?  What if I just print the code and take the paper with me?

The best solution to USB drives is to fill the outlets with a sealant.  On both Windows and Linux, it's possible to disable the mass-storage functions of USB either through a registry setting or by adding "blacklist usb_storage" in /etc/modprobe.d/blacklist.conf.  

Do their workstations have CD/DVD writers?  Better disable those, too.

The fact of the matter is that you won't be able to protect your code against a sufficiently clever and motivated developer.  You need to figure out how to keep your employees happy so they won't want to be stealing your stuff.  This sort of advice doesn't make managers happy; they want technological solutions that will make them feel warm and fuzzy.  They need to grow up and realize there are no such solutions other than good employee relations.

---

### Post by TTR123 on 2010-09-25
I actually gave a thought the same way, Yes, the smart guy can do whatever he wants. We make sure that the employees are always happy but out of 100 guys, even if one if bad, he will end up shaking up the whole organization. 

And I really don't want to be in a situation where, our hardwork of couple of years on a single project is washed away by a single employee. 

I have been looking these kind of options on Ubuntu, Windows and OSX, but so far, not much luck.

---

