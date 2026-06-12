---
title: "Photorec questions"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by Old Jimma on 2011-02-03
Hi Ubuntu Community:

I want to use photorec to recover files from a HD that I accidentally wiped out using rm onto a new 1Tb HD.

(In a previous thread [http://ubuntuforums.org/showthread.php?t=1679997]("http://ubuntuforums.org/showthread.php?t=1679997") I learned how to back up the hard drive that I wiped out! 

 ;)

Here are my questions:

Do I need to format that 1Tb drive before using photorec?

Then, do I need to mount that 1TB drive to use photorec?

Thank you, Ubuntu Community!  :p
Phil Smith
Duluth, GA

---

### Post by fabricator4 on 2011-02-03
> **Phil Smith said:**
> Do I need to format that 1Tb drive before using photorec?

Absolutely.  You'll need to both partition and format the new drive.  Install Gparted: it's possibly one of the easier to use partition programs and can even resize an existing partition.  Make sure that you DON'T work on the partitions of the drive you want to rescue.  The first hard drive will probably be sda, while the second drive (the new one) will probably be sdb and will not have any existing partitions on it (usually).


> Then, do I need to mount that 1TB drive to use photorec?

Probably.  It will either show up as a device under "computer" (in "Places") or you can mount it manually.

Chris

---

### Post by Old Jimma on 2011-02-03
Hi Chris:

thanks for your reply.

Since the 1Tb drive is my 'rescue' drive, I'm going to format it and create a single parition.

Does that sound ok?

Phil Smith
Duluth, GA

---

