---
title: "HELP grub error"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by jezebel on 2009-11-10
Help please!

My Ubuntu was running great, dual boot with Win7; 
In Win 7 I deleted a partition (not ubuntu or grub!); I rebooted. It looked fine. Grub loaded, I chose win7; it started to boot. Then my pc crashed, and rebooted, and I get the error message:

grub error
reason: uknown filesystem
grub rescue


Please any help?

(I'm on an Acer aspire one net book)

---

### Post by mikechant on 2009-11-10
One possibility is that deleting the partition caused other partitions to be renumbered (if I remember right this can happen when you delete a logical partition in the extended partition).
Can you boot from the live CD and then run gparted and post a screen shot, and indicate where the deleted partition was?

If this is the problem it should be quite easy to fix, but are you running 9.10 with grub2 or running the old version of grub (default for 9.04 and below)?

Did you use gparted to delete the partition? What sort of partition was it?

---

### Post by yanceypd on 2009-11-10
From terminal in Ubuntu or live cd try: sudo update-grub.

---

### Post by ranch hand on 2009-11-10
What grub are you using?

If you do not know, run;
```

grub-install -v

```
If you can boot to your ubuntu at all.

Just letting us know what Ubuntu you have may well answer the grub version question.

This makes a BIG difference in how to deal with your problem.

---

### Post by jezebel on 2009-11-11
Hi and thanks for the replies.

I did try sudo update-grub which said it couldn't be found.

Lots of code (way over my head), and I'd already made a mess of partitions etc, so I reinstalled Ubuntu  (luckily just lost a few little docs and things); I used the manual partition option, and deleted the leftover corrupt unbuntu, as well as the other partition I wanted to use for an extra windows storage.

That worked great; grub is now safely and happily running (for now??), and Win7 etc.. are all okay, AND I've got a nice clean set of partitions!

---

