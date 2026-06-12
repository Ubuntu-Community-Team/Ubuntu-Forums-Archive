---
title: "more install problems"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by Nod3225 on 2011-02-28
I have been trying to install ubunto alongside windows sp for 3 days now.  The last time I tried it I alocated 40 gig to ubunto.  The install appeard to go well until it rebooted  and now I get the following message.   error: out of disk then the next line says grub rescue>.  I am a total loss as to what to do now.  I don't know much about partitions either.

---

### Post by Nod3225 on 2011-02-28
bump

---

### Post by Rubi1200 on 2011-03-01
Hi,

please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

Once we see the results we can hopefully offer some solutions.

---

### Post by Nod3225 on 2011-03-01
I dicided to reformat the hard drive and re install windows xp and then ubunto.  Is there a glossary somewhere I can refer to?  What is a swap file and what is grub?

---

### Post by Rubi1200 on 2011-03-02
Well, I suppose that is one way of dealing with things, but I am glad you got it sorted out.

For swap:
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

for GRUB:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by slooksterpsv on 2011-03-02
SWAP is like what windows does for Paging. When a program isn't being used or if RAM is filled, it puts whatever should go into RAM into SWAP or moves items from RAM to SWAP so your computer can store and process those instructions.

GRUB is a boot manager; when you boot the computer, it either looks for files to load the OS or it looks for a boot manager where the boot manager tells the computer what to boot into. The awesome thing about boot managers is you can have multiple OSes where with it loading into the OS directly, you don't get the option. Most (if not all) Linux distros use a boot manager either GRUB or LILO.

---

