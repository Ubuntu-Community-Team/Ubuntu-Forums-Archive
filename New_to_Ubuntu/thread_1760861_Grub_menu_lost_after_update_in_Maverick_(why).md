---
title: "Grub menu lost after update in Maverick (why?)"
date: 2011-05-17
forum: New to Ubuntu
---

### Post by frogo on 2011-05-17
Hi, 

I'm running a fresh install of Maverick (2.6.34-020634-generic). I ran the update manager for the first time. After that, I lost the grub menu I had on start up before. 

I ran an update-grub since, but it seems to have done nothing. I looked into /boot/grub/grub.cfg and it seems to have entries for both a lucid and a maverick (as I had in the grub menu before). 

I have to say it doesn't trouble me in this instance because it wasn't practical to use the machine under Lucid. I'd just like to understand, however, if there's something I should be aware of in relation to future updates. 

many thanks and apologies if I missed obvious explanations in related places

---

### Post by ratcheer on 2011-05-17
You need to run grub-install first, then update-grub.

Tim

---

### Post by frogo on 2011-05-17
> **ratcheer said:**
> You need to run grub-install first, then update-grub.

Tim

Thanks for the reply, but I never had to do that before, including after updating grub itself. 

I installed Maverick after downloading the packages within an Lucid install. I had a grub menu when rebooting after that. It's only when I ran the update manager (which brought no kernel update) that I lost the grub menu. 

sorry if i am thick...

---

### Post by ratcheer on 2011-05-17
Sorry, I don't know *why* the problem occurred, that is just what I suggest trying in order to get it fixed. I have had grub go kerplooey on several occasions. In the long run, it happened for whatever reason, and it still needs to be fixed.

Tim

---

### Post by frogo on 2011-05-17
> **ratcheer said:**
> Sorry, I don't know *why* the problem occurred, that is just what I suggest trying in order to get it fixed. I have had grub go kerplooey on several occasions. In the long run, it happened for whatever reason, and it still needs to be fixed.

Tim

fair enough.

i'll actually give it a try -- i just fear i'll mess up but better sooner than later and maybe i'll even learn something.

Thanks

---

### Post by ratcheer on 2011-05-17
Here's one more tip. You may need to boot to a Live CD, then chroot to your hard disk installation to run grub-install. There are specific instructions all over the place for doing this, if you don't know how. This is assuming that you cannot currently boot to your Linux installation.

Tim

---

### Post by frogo on 2011-05-17
> **ratcheer said:**
> Here's one more tip. You may need to boot to a Live CD, then chroot to your hard disk installation to run grub-install. There are specific instructions all over the place for doing this, if you don't know how. This is assuming that you cannot currently boot to your Linux installation.

Tim

I can boot into one of my installations (Maverick). So I tried:

sudo grub-install  --recheck /dev/sda
sudo grub-update

it didn't complain and grub-install was surprisingly fast (maybe that's normal).  the grub-update listed also the Lucid kernel. But I'm still not seeing a grub menu at startup and the machine boots directly into Maverick. I even tried holding the SHIFT key during a boot sequence, and I think I saw a flickering 'loading GRUB' or something like that, but no GRUB menu.

i didn't know about chroot, which sounds like I could have used it in the past! but i learnt about mount and blkid..

---

### Post by ratcheer on 2011-05-17
> **frogo said:**
> I can boot into one of my installations (Maverick). So I tried:

sudo grub-install  --recheck /dev/sda
sudo grub-update

it didn't complain and grub-install was surprisingly fast (maybe that's normal).  the grub-update listed also the Lucid kernel. But I'm still not seeing a grub menu at startup and the machine boots directly into Maverick. I even tried holding the SHIFT key during a boot sequence, and I think I saw a flickering 'loading GRUB' or something like that, but no GRUB menu.

i didn't know about chroot, which sounds like I could have used it in the past! but i learnt about mount and blkid..

No, if you have a bootable system, it sounds like you did ok. However, if your other installation is Natty, you are still getting the older Maverick grub by doing it that way.

To manage your grub menu, I suggest this thread:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Once you get into Natty, you should grub-install and update-grub, again.

Good luck,
Tim

---

### Post by drs305 on 2011-05-17
Edited thanks to input form Miljet:

You can tell which one is controlling your boot because it's Ubuntu will be the first entry (as well as having the Grub version displayed at the top).

If you are still having difficulties, please run the boot info script. Instructions on how to run it are on the site, and there is an additional help link on the left side.

Posting the contents of RESULTS.txt will give us a better idea of what's happening. And if you'd briefly summarize your remaining Grub issues...

---

### Post by Miljet on 2011-05-17
I believe the OP stated in his first post that he had Maverick and Lucid installed. Therefore giving instructions involving Natty is just confusing.

---

### Post by drs305 on 2011-05-17
> **Miljet said:**
> I believe the OP stated in his first post that he had Maverick and Lucid installed. Therefore giving instructions involving Natty is just confusing.

You are right. I've been working Maverick/Natty problems all day. Thanks for pointing that out. I'll edit the post.

---

### Post by frogo on 2011-05-18
> **drs305 said:**
> Edited thanks to input form Miljet:

You can tell which one is controlling your boot because it's Ubuntu will be the first entry (as well as having the Grub version displayed at the top).

If you are still having difficulties, please run the boot info script. Instructions on how to run it are on the site, and there is an additional help link on the left side.

Posting the contents of RESULTS.txt will give us a better idea of what's happening. And if you'd briefly summarize your remaining Grub issues...

I'm not sure I follow the above, but it made me look around a bit more (your guide and [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) too). So I have a hunch as to the original 'why?' now.

My current GRUB is 1.98-1ubuntu10. Seems I should expect no grub menu at start up (although I'm not sure why two kernel versions are not different OS). However, I can get the menu if I press SHIFT (at the right time) and it shows both the Lucid and Maverick kernels. 

So I guess that my install of Maverick had an old grub that was updated when I ran the update manager within it and that the new version of grub is one bypassing the menu by default... 

Anyway, that's only an academic question I guess. Maverick--which is what the machine boots into by default--works and I can get the grub menu at the press of a key...

many thanks to all (I'll close the thread)

---

