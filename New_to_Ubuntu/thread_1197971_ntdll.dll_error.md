---
title: "ntdll.dll error"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by leebyn on 2009-06-26
I set up dual boot Xubuntu/XP on my Toshiba Satellite laptop about a month ago, and I've been using Xubuntu quite frequently.   I tried to start XP recently and I got a ntdll.dll error, and I can't boot XP at all.   Is this a dual boot problem? How do I fix this?  I wasn't sure which section to post in, so I apologize if it's in the wrong place. Thanks.

---

### Post by zeroseven0183 on 2009-06-26
Yeah. I think so because this is an Ubuntu forums not Windows. Anyway, try to do a chkdsk (and apply the option to fix errors) on your Windows by booting to Recovery Console.

You can also check some of the solutions, if already posted, in [Windows IT Pro]("http://www.windowsitpro.com")

---

### Post by philcamlin on 2009-06-26
virtual machine?

---

### Post by zeroseven0183 on 2009-06-26
By the way, have you tried booting to Safe Mode?

---

### Post by leebyn on 2009-06-26
I posted here because I thought that this could be a problem with my dual boot setup with the Grub loader. It's one drive with two equal partitions. It worked fine but then I didn't use XP for a while and now the error comes up.  Unfortunately, I'm away from home and I don't have my XP installation CD with me, so I can't try the recovery.  I'm not using a virtual machine and I really don't know how those work.  I tried booting into the safe modes that XP shows (Safe Mode with Prompt/Networking) but I haven't had any success.  Is it possible for me to replace the ntdll.dll file by using the Xubuntu Live CD? and how would I mount the XP partition?

---

### Post by zeroseven0183 on 2009-06-30
Yes, you can try it but you must have a working ntdll.dll file. Boot to Live CD and access /host/Windows/system32 then paste the working file to it.

---

### Post by jrusso2 on 2009-06-30
Its rarely that the file is missing it just can't find it is the issue.

---

### Post by balachandarlinks on 2009-06-30
Hi,
 In windows it hides some important operating system files.But you can find them in nautilus.You may mistakenly deleted the dll file when you delete some other junk files i guess.
 So go to [www.dll.com](www.dll.com) to download the dll and replace it to its location using ubuntu.Then restart your system and go to windows.It ll fix you.

---

### Post by leebyn on 2009-06-30
I got it to work. Turns out the file was corrupted or something.  Thank you all!

---

