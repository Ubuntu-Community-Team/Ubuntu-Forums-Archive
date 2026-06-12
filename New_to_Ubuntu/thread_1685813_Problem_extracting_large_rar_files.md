---
title: "Problem extracting large rar files"
date: 2011-02-11
forum: New to Ubuntu
---

### Post by faviouz on 2011-02-11
Hi,

I download a lot of zip and rar files everyday, meaning I have to extract them. Now, the default extractor has been able to extract most files decently (even though it takes longer than it did on Windows), but I'm having some problems with larger files. I have a file I need to extract of about 7GB in 7 parts like so:

```
file_1.part1.rar (1GB)
file_2.part2.rar (1GB)
file_3.part3.rar (1GB)
file_4.part4.rar (1GB)
file_5.part5.rar (1GB)
file_6.part6.rar (1GB)
file_7.part7.rar (983.64 MB)
```

I know how the part1, part2, part3 process works. You have to extract the first one and it will go through the others and extract them too putting it all together. I've been able to extract files like this, just not as big. Most of the files I download are password-protected, and it all works ok except for this 7GB file.

I have all the files in a folder on my desktop. I open up the folder, double-click the part1 and select Extract Here. It asks me for the password, I type it in and it seems to be doing its thing. It says it's extracting part1, then part2, then part3... but then it asks me for the password of part1 (the password is the same for each file if you're wondering). I type it in and it says it's extracting part1, then part2, then part3... and it asks me for the password of part1 again.

I let it extract itself for about an hour and typed in the password when asked, but it just repeats the whole process again. So my question is, **am I doing something wrong or should I install some other program to archive and extract files**? If so, which do you recommend?

Thank you.

---

### Post by cariboo on 2011-02-11
It sounds to me like the password is wrong.

---

### Post by faviouz on 2011-02-13
Hi, thank you for replying!

I don't think the password is wrong. I've tried multiple instances of the password and even copied the password directly from the website. The same thing happens. I checked the website I downloaded this from and nobody seems to be having this issue.

In the meantime I will try to move the files over to Windows and see if they can be extracted there. If you got any other suggestions, please let me know.

---

### Post by Mark Phelps on 2011-02-14
It may be more than coincidence that when you start to extract part 4, your are already writing a file that might be larger than 4GB.  Some filesystems (notably FAT32) can not hold files larger than 4GB.

Check what filesystem you're trying to extract the file to.

Also, a password error is a typical side effect of corrupted archives.  If one of more of the parts fails a CRC check, it may spit out the password stuff instead of telling you the file is corrupt.

---

### Post by faviouz on 2011-02-24
I just transfered the files over to Windows and it could not extract the files either. There is definitely some kind of problem with the files. I'll just delete them for now and get them somewhere else.

Thanks everyone who tried to help me. :)

---

### Post by pqwoerituytrueiwoq on 2011-02-24
I have had issues with Japanese character's in rar files files names
i just used winrar in wine and that worked

---

