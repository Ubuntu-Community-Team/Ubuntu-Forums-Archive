---
title: "editing GRUB (menu.lst)"
date: 2010-06-15
forum: New to Ubuntu
---

### Post by punkbohemian on 2010-06-15
Right now, I have over a half dozen different entries on my grub menu. I found the file menu.lst in /boot/grub, which I presume is the file that manages that menu. I was thinking of commenting out (with "#", right?) some/all of the older entries just to clean up the menu. Would this a) clean up the menu, and b) not mess anything up? Thanks.

---

### Post by warfacegod on 2010-06-15
At a guess. I'd say you have several older kernels still installed. Either remove them with Synaptic or let Ubuntu Tweak do it for you. [http://ubuntu-tweak.com/]("http://ubuntu-tweak.com/")

---

### Post by anaconda on 2010-06-15
If you have the new GRUB2, which is in ubuntu 10.04 and 9.10. then you should not edit the /boot/grub -file. instead you can edit the grub config files, and then update grub...

---

### Post by punkbohemian on 2010-06-15
I was thinking as much, but I had read somewhere that Linux removes old GRUB entries as they are no longer needed.

What I was thinking was that I could just remove the entries from the menu by commenting, and if there are any problems with my current kernel in the future, I could just tack them back on since I know the path and file.

Oh, and I should mention that I'm still using Hardy.

---

### Post by QLee on 2010-06-15
[QUOTE=punkbohemian]I was thinking as much, but I had read somewhere that Linux removes old GRUB entries as they are no longer needed.[/Quote]

I don't know where you read that but either it was incorrect or you misunderstood. GRUB could be configured to only keep a set number of kernel versions in the menu but it did not do so by default, only through configuration.

[QUOTE=punkbohemian]What I was thinking was that I could just remove the entries from the menu by commenting, and if there are any problems with my current kernel in the future, I could just tack them back on since I know the path and file.[/QUOTE]

That would work if done correctly.

[QUOTE=punkbohemian]Oh, and I should mention that I'm still using Hardy.[/QUOTE]

Yes, you should mention that, it likely means that you are still using legacy GRUB and the differences are significant between it and GRUB-PC (GRUB2)

---

### Post by warfacegod on 2010-06-15
> I was thinking as much, but I had read somewhere that Linux removes old GRUB entries as they are no longer needed.


I *believe* this only applies to GRUB2 and it only works if you remove kernels.

---

### Post by QLee on 2010-06-15
> **warfacegod said:**
> I *believe* this only applies to GRUB2 and it only works if you remove kernels.

Either GRUB would only discover kernel versions that were available, thus any that were removed weren't there to be discovered.

---

### Post by NCLI on 2010-06-15
> **warfacegod said:**
> I *believe* this only applies to GRUB2 and it only works if you remove kernels.

As Ubuntu does automatically from 9.10 and onwards, which the OP really should consider upgrading to in the near future :P

---

### Post by QLee on 2010-06-15
[QUOTE=NCLI]As Ubuntu does automatically from 9.10 and onwards, which the OP really should consider upgrading to in the near future :P[/QUOTE]

Strictly speaking, it isn't Ubuntu which does this, it is the bootloader and the bootloader update which does this. In other words, GRUB.

As people had the choice of legacy GRUB and GRUB2 (GRUB_PC) with 9.10, not all had GRUB2.

However, if the OP is using an LTS for stability and security, then upgrading to the newest LTS is definitely something to consider.

---

### Post by JKyleOKC on 2010-06-15
> **punkbohemian said:**
> I was thinking as much, but I had read somewhere that Linux removes old GRUB entries as they are no longer needed.

What I was thinking was that I could just remove the entries from the menu by commenting, and if there are any problems with my current kernel in the future, I could just tack them back on since I know the path and file.

Oh, and I should mention that I'm still using Hardy.In menu.lst, find "howmany=" which will probably show "howmany=all" since that's the default. Change it to "howmany=2" and save the change, then run "sudo update-grub" from a terminal window. The grub menu will now show you four entries; two normal and two recovery, for the most recent and next most recent kernels. All the others will be gone.

I always set this to "2" to give me a rollback option in case the newest kernel fails to work after an update (kernel updates automatically run update-grub to add the new version to the menu) but keep the menu size to a minimum...

---

### Post by warfacegod on 2010-06-15
Another option is to use Startup Manager. It's available in Synaptic.

If you go the 10.04 route like some have suggested, then hold off a bit until the updated version is released sometime in the end of June. It *should* have fewer bugs.

---

### Post by -kg- on 2010-06-15
> **QLee said:**
> ...if the OP is using an LTS for stability and security, then upgrading to the newest LTS is definitely something to consider.

That would certainly be my recommendation.  Hardy will be unsupported in less than a year, unless you're using the Server version.

At any rate, yes, in GRUB Legacy, the only way to remove older kernels from the GRUB menu is by editing the menu.lst file.  There is no "update-grub" command to do this for you.  Removing the older kernels is merely a matter of housekeeping, gaining you room in your root partition.

When you download a kernel update, the GRUB menu is automatically updated to include the new kernel in either GRUB Legacy or GRUB2.  With GRUB2, you can remove the kernel and run "update-grub" in the terminal, and the reference to the removed kernel is removed from the menu.

With Legacy GRUB, the only way you can remove the reference is to edit the /grub/menu.lst file.  You can comment it out, or you can remove the line completely from the file.  If you remove the old kernel(s), it is probably best to just delete the entry referring to it (them).  It (they) are no longer on your system, so having a reference to it (them), even commented out, is redundant.  If you elect to leave them in place, then comment the lines out so that, if you decide you need to access them for one reason or another (though I can't imagine a reason), you can just edit the menu.lst again to gain access.

BTW, it's recommended to leave at least one older kernel resident in case you find you have problems with the new one somewhere down the line.

---

### Post by QLee on 2010-06-15
[QUOTE=-kg-]
At any rate, yes, in GRUB Legacy, the only way to remove older kernels from the GRUB menu is by editing the menu.lst file.  There is no "update-grub" command to do this for you.  [/Quote]

This is incorrect, legacy GRUB also had an update function, that's how a kernel upgrade triggered a new GRUB menu when the new kernel was installed.

[QUOTE=-kg-]When you download a kernel update, the GRUB menu is automatically updated to include the new kernel in either GRUB Legacy or GRUB2.  With GRUB2, you can remove the kernel and run "update-grub" in the terminal, and the reference to the removed kernel is removed from the menu.[/QUOTE]

As you also could with legacy GRUB,updating  GRUB can only discover kernel versions available.

[QUOTE=-kg-]With Legacy GRUB, the only way you can remove the reference is to edit the /grub/menu.lst file.  You can comment it out, or you can remove the line completely from the file. [/QUOTE]

This is incorrect, not the only way. As previously mentioned, GRUB could be configured to use a set number of kernels, as poster JKyleOKC has detailed.

---

### Post by JKyleOKC on 2010-06-15
> **-kg- said:**
> At any rate, yes, in GRUB Legacy, the only way to remove older kernels from the GRUB menu is by editing the menu.lst file.  There is no "update-grub" command to do this for you.  Removing the older kernels is merely a matter of housekeeping, gaining you room in your root partition.

When you download a kernel update, the GRUB menu is automatically updated to include the new kernel in either GRUB Legacy or GRUB2.  With GRUB2, you can remove the kernel and run "update-grub" in the terminal, and the reference to the removed kernel is removed from the menu.

With Legacy GRUB, the only way you can remove the reference is to edit the /grub/menu.lst file.  You can comment it out, or you can remove the line completely from the file.  If you remove the old kernel(s), it is probably best to just delete the entry referring to it (them).  It (they) are no longer on your system, so having a reference to it (them), even commented out, is redundant.  If you elect to leave them in place, then comment the lines out so that, if you decide you need to access them for one reason or another (though I can't imagine a reason), you can just edit the menu.lst again to gain access.Sorry, not quite true. The update-grub command is there in legacy grub as well as in grub 2, and you can manually delete kernel packages via Synaptic or apt-get or aptitude, then run "sudo update-grub" and they'll vanish from the menu.

It may be that the update-grub runs automatically as part of the post-install actions when using the package manager to delete obsolete kernel packages. It's been a while since I cleaned house and I don't remember whether I had to do the update manually or not. In any event, running it twice won't hurt anything.

Incidentally, what area is "KG5"? Seems to me that "KG" was the Canal Zone or Guam -- and Illinois was "9" -- when I held K5JKX (1957-67)!

---

### Post by -kg- on 2010-06-16
Then I stand corrected.

It mystifies me, though, that I had never heard of running that command until GRUB2 came out.  All that time, when I had to make alterations to the GRUB menu, I always edited menu.lst because I thought that was the only way...that and the installable GRUB configuration software, which I also used.

---

### Post by warfacegod on 2010-06-16
I'll confirm that, update-grub worked in GRUB Legacy. From what I understand, it's going to be changed to grub-mkconfig or some such thing. Personally I don't see the point. I'm just going to add it to my list of Stupid, Pointless Changes That Do Nothing But **** Me Off.

---

