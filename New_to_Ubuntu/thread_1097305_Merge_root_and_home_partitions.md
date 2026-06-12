---
title: "Merge root and home partitions"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by Volt9000 on 2009-03-15
Alright, well when I installed Linux I manually set up my partitions according to this one guide I was reading. The guide said to use about 2-3GB for the root partition. Well I did that and of course my root partition is full, preventing me from performing any updates.

What I'd like to do is merge my root and home partitions. Is this possible to do without losing any data?

Attached is a screenshot showing what I have now. What I'd like to do is merge the first two partitions, sdb1 and sdb2. I suppose then the swap partition would become sdb2, and the unused portion would be sdb3.

Can I do this without completely reinstalling Linux? I realize I would have to boot from a LiveCD.

---

### Post by theozzlives on 2009-03-15
It's not possible but you can shrink your /home  and make your root 10-20 GB  with partition editor off the live CD. Believe me you want a seperate /home.

---

### Post by SuperSonic4 on 2009-03-15
> **theozzlives said:**
> It's not possible but you can shrink your /home  and make your root 10-20 GB  with partition editor off the live CD. Believe me you want a seperate /home.

I agree a separate /home is a lifesaver when it comes to upgrading/changing distros.

---

### Post by Volt9000 on 2009-03-15
> **theozzlives said:**
> It's not possible but you can shrink your /home  and make your root 10-20 GB  with partition editor off the live CD. Believe me you want a seperate /home.

Oh? Why is that?
I just checked the installation on my laptop (which I let the installer handle the partitioning itself) and it just has two: the swap and everything else.

Is there a reason I want to keep my root partition separate from my home partition? And how big would I want my home partition?
What's installed in home, anyways? Is it just local settings, scripts, and personal documents and whatnot? Are all programs installed to the root partition?

[Edit]
Ok I just saw SuperSonic4's post.
How big should my /home be?

---

### Post by SuperSonic4 on 2009-03-15
/home has what you mentioned and program settings (like ~/.mozilla has all your firefox data). Programs are installed to the root partition although some files are sent to home (ie settings files)

Keeping root separate from home will enable you to keep all your documents, settings, scripts etc without reinstalling/pasting from a backup in case of a reinstall/distro change/upgrade.

My /home is about 96GiB but then I have no issues with space. On the laptop I gave / 20GiB, /var 6GiB, swap 1GiB and /home the rest (about 30GiB). What I'm trying to say is that give root about 20GiB, swap 2xRAM or 1GiB and home the rest. My /var is formatted to reiserFS for it is meant to be faster at the small files usually found in /var

---

### Post by Volt9000 on 2009-03-15
> **SuperSonic4 said:**
> /home has what you mentioned and program settings (like ~/.mozilla has all your firefox data). Programs are installed to the root partition although some files are sent to home (ie settings files)

Keeping root separate from home will enable you to keep all your documents, settings, scripts etc without reinstalling/pasting from a backup in case of a reinstall/distro change/upgrade.

My /home is about 96GiB but then I have no issues with space. On the laptop I gave / 20GiB, /var 6GiB, swap 1GiB and /home the rest (about 30GiB). What I'm trying to say is that give root about 20GiB, swap 2xRAM or 1GiB and home the rest. My /var is formatted to reiserFS for it is meant to be faster at the small files usually found in /var

Oh you have a separate partition for /var?
What's stored in /var anyways?

---

### Post by Volt9000 on 2009-03-15
Ok so after I resize my partitions, I presume I'll have to fix the fstab file, since my mount points will be different (based on the UUID, I think?)

Would I have to do this manually, or can I just run grub-install or something similar? And would I have to specify any special parameters if running from a LiveCD?

---

### Post by Volt9000 on 2009-03-16
*bump*

For any other noobs who are interested...

After moving around my partitions I had to manually edit a few files.
First I typed:

sudo blkid

And got a of partitions corresponding to UUIDs.
Then I edited the following files:

/etc/fstab
/boot/grub/menu.lst
/etc/initramfs-tools/conf.d/resume

I modified these the UUIDs in these files to match up with the output of blkid. Note that depending on how the partitions get moved around you may not have to change everything.

Once I had those all saved I restarted and bam, no worries.

---

### Post by ydraliskos on 2009-03-16
New user here.

Is it possible to do the opposite of what the OP is trying to do?

I didn't have a separate /home from / at first, because I was planning to use a dual boot system + a separate partition accessible by both OSes for file storage, but now the other OS is dead and I realize the shared partition would be much more useful as mounted to /home.

So, is it possible to decouple / and /home and transfer /home to a different partition post-installation?

---

### Post by sandyd on 2009-03-16
its 100% possible

just create another partition by resising your ubuntu partition

copy home onto it

edit the fstab to mount the new partition

thats just the idea though....

maybe someone could say how its done???

---

