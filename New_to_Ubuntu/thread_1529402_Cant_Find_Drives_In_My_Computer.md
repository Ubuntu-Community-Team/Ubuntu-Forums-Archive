---
title: "Cant Find Drives In My Computer"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by avishek.ganta on 2010-07-12
I have just installed ubuntu 9.04 , while installing I made 4 partitions with mount points / ,/home,/user ,/tmp ... now in my computer i cant find my drives. How do I get Drives? 
PS  : I am a first time Ubuntu user.Please help.

---

### Post by philinux on 2010-07-12
> **avishek.ganta said:**
> I have just installed ubuntu 9.04 , while installing I made 4 partitions with mount points / ,/home,/user ,/tmp ... now in my computer i cant find my drives. How do I get Drives? 
PS  : I am a first time Ubuntu user.Please help.

What shows up in Places>Computer?

How many physical hard drives has this machine got?

---

### Post by avishek.ganta on 2010-07-12
In my computer it shows cd drive and filesystem folders. and only one physical hardrive.

---

### Post by 3rdalbum on 2010-07-12
those   partitions   are   now   inside   the   Filesystem.   You   will   find   them   in   there.

---

### Post by viralmeme on 2010-07-12
> **avishek.ganta said:**
> I have just installed ubuntu 9.04 , while installing I made 4 partitions with mount points / ,/home,/user ,/tmp ... now in my computer i cant find my drives. How do I get Drives? 
PS  : I am a first time Ubuntu user.Please help.
You don't have drives in Linux, everything gets mapped into the root file system. Fire up Bash and type the following and post the results here.

$du -h
$mount

[Linux Command]("http://www.linuxcommand.org/")

---

### Post by diablo75 on 2010-07-12
> **avishek.ganta said:**
> I have just installed ubuntu 9.04 , while installing I made 4 partitions with mount points / ,/home,/user ,/tmp ... now in my computer i cant find my drives. How do I get Drives? 
PS  : I am a first time Ubuntu user.Please help.

Kinda bold of you to go and create that many partitions manually, considering you are a self admitted "first time Ubuntu user."

Here are the basics as I understand it:

In Linux, you have a file system that begins at / (aka, "root", or the tree-root of the directory structure).  In a default install, this / resides on the same partition as every other file/folder, with the exception of swap.  But, as you've found out, it's possible to create separate partitions on your hard drive to house specific folders, such as /var or /home.  A lot of people will install Linux with not 2 but 3 partitions, one for /, one for /home and then swap.  An advantage of doing this is that everything stored in your /home folder is logically separated away from the rest of the system, which allows you to format the system partition if you ever wished to without erasing your personal documents and settings.  Makes reinstalling the OS a real snap.

That being said, regardless of how many partitions you create for purposes like this, they will still be represented in the filesystem as if they didn't have separate partitions.  To the normal user, they just appear to be another folder among other folders.  So, you could have a system with a /home partition, or just a / partition and nothing fancy, but both will have a /home folder.  The difference is that they have different mount points.  A crappy analogy might be to think of "/home" as phone number that stays the same but can point to different devices at the MAC address level, so when you replace your cell phone you can keep the same number and people can still contact you.  The use of the name /home is sort of a fixed standard in Linux, but you can make it point to whatever you want as far as I know.

I don't think there are any disadvantages to splitting your system apart into several partitions like you have, other than loss of hard drive space (because you'll be creating partitions that are likely sized larger than they need to be).  Keeping everything on / helps share this free space out with the rest of the system.  For me, I just stick with / and /home partitions.

---

