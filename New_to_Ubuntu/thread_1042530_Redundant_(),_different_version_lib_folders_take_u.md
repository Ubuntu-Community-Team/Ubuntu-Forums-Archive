---
title: "Redundant (?), different version /lib folders take up HD space"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by marcelin0 on 2009-01-17
First of all, apologies if I don't ask in the proper way. **Read only the sentences in bold if you're in a hurry**.

I have a PC laptop (an "old" Dell Latitude C400) with no internal HD (it screwed up). My solution to that was:

- Use a Live CD to install Linux in an external, USB connected HD (not a flash drive, though).
- As my poor ol' PC can't boot from an external HD, **every time I boot I have to:**

**   # boot from the Live CD**
   # I change the **boot options to boot from the external HD**, i.e. I choose any of the first three options, then press F6 to change them to:
      **root=/dev/sda3 initrd=/casper/intrd.gz quiet splash ro --**
     I probably should say that /dev/sda3 is my external hard drive.
     [as a side note, does adding "ro" at the end change anything?]

I had heard that this could cause some inconveniences because the loaded kernel was always the one from the LiveCD, and there's no way to get away from it.

**Now the "problem":**
I have allocated 3.75 GB for the Linux OS, and now it is already almost full. To reduce used space to the minimum, I decided to check what was taking up so much space, and found out among other things that **/lib was taking up a lot of space**. When checking further, I realised that there were **three folders with almost the same tree structure, corresponding to different versions of what seems to be the same thing** (see image. The tree structures are highlighted in three different colours).

My question is:
[LIST]
[*]Can I delete at least one of these without risk?
[*]Is there a way to do this safely with ubuntu's tools?
[/LIST]

Thank you very much

[IMG]http://farm4.static.flickr.com/3438/3204126645_6fd930b277_o.png[/IMG]

---

### Post by Bachstelze on 2009-01-17
The "thing" you have different versions of is the Linux kernel, which is the core of your system. It is indeed not necessary to keep them all, and you can uninstall the [font="monospace"]linux-image[/font] packages corresponding to the kernel versions you wish to uninstall in your favourite package manager to free up space (but be sure to keep at least one!).

---

### Post by northern lights on 2009-01-17
3/5th of your filesystem is unused, though.

A kernel image is less than 40MB - the 1/8000th part of the space you have.

I'd keep two or three.

---

### Post by marcelin0 on 2009-01-17
First of all, thanks for your quick responses, I really appreciate that.

You'd be right if I hadn't partitioned my external hard drive. Unfortunately, most of those hundreds of gigabytes are for my personal files, and are partitioned under /media/something (or /dev/sda3, don't know which). The OS itself has to fit within the remaining 3.75 GB.

I guess I'll delete at least one of the kernels, although as you've suggested that probably won't make much of a difference.

Cheers!

---

### Post by cariboo on 2009-01-17
Just don't delete the unused kernel use System-->Administration-->Synaptic Package Manager to completely remove them. If you just delete them you may run into a problem with the apt database.

When you have synaptic running, click the search button and search for linux-image. You can remove 2.6.24-16 and 2.6.24-21.

Jim

---

### Post by marcelin0 on 2009-01-21
Thanks Jim, you couldn't have made it any clearer!
I guess if 3 people say the same thing, I don't risk so much =)

Thank you every one!

---

### Post by marcelin0 on 2009-05-10
It was completely wrong!
Ubuntu didn't start at all and I had to reinstall everything AND lost some data. I probably needed to start up with the latest version of the ubuntu CD, but since I didn't have access to a burner, I can't even say for sure whether it'd have worked.
Thanks guys, now I know not to trust ubuntuforums.
Please, next time make sure your know what you're talking about.

---

### Post by northern lights on 2009-05-11
> **marcelin0 said:**
> It was completely wrong!
[...]
Thanks guys, now I know not to trust ubuntuforums.
Please, next time make sure your know what you're talking about.
None of the info given by anybody was faulty at all.

> **marcelin0 said:**
> Ubuntu didn't start at all and I had to reinstall everything AND lost some data.
I believe you that that's what happened. It just didn't due to bad instructions. Face it - you screwed something up in the process. That's okay, human errors happen under any OS. Just please don't blame it on the community.

---

