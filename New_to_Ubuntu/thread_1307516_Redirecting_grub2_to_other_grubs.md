---
title: "Redirecting grub2 to other grubs"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by jrrader on 2009-10-31
I have several operating systems on my computer at any given time.  Ubuntu and Win7 are on sda, the others (currently crunchbang and fedora) are on sdb.  The way I got them working (to avoid having the kernels too far back for bios to find them) was by redirecting ubuntu's grub to the menu.lst of the OS on the second drive.  Worked great.  Looked like this:

```

title         Fedora 11
configfile    (hd1,1)/grub/grub.conf  

title        Crunchbang 9.04
root        (hd1,0)/grub/grub.conf
chainloader    +1

```

After a clean install of 9.10, Grub2 is trying to load the kernels for Fedora and Crunchbang, which gives an error (load kernel before booting).  How can I redirect Grub2 to load the grubs of Fedora and crunchbang like I did before?

(I'm not knocking grub2 or anything.  I think it's great that it updates with the kernels of other operating systems - it just doesn't work with my partitioning scheme.)

---

### Post by kansasnoob on 2009-10-31
I had a similar situation and, because I'm a distro-hopping, multi-booting, anal retentive, control freak, I decided to revert to legacy grub. I made some notes here:

[http://ubuntuforums.org/showpost.php?p=8071880&postcount=18](http://ubuntuforums.org/showpost.php?p=8071880&postcount=18)

I actually go back to grub 2 from time to time when I'm bored and feel like playing around, and I believe for most folks with a single OS, or even a simple dual-boot, grub 2 is fine, but for now I like what I'm used to.

---

### Post by NCLI on 2009-10-31
You may also want to PM [ranch hand]("http://ubuntuforums.org/member.php?u=647614"), he wrote an excellent guide to GRUB2 in the now-closed Karmic Koala Testing and Discussion forum.

---

### Post by jrrader on 2009-10-31
Thanks.  Not sure if I really want to go back to legacy.  When I have some time I'll read up on everything grub2 related and try to get it working.  Found [this post]("http://ubuntuforums.org/showthread.php?p=8191211#post8191211") from ranch hand which seems to have enough links educate me on the subject.  None of it is really urgent as 99 percent of what I do on my computer is in ubuntu, but it will be nice to be able to play around with other distros again.

---

### Post by jrrader on 2009-11-25
I'm bumping this because I still haven't managed to solve it (as my school work hasn't permitted me the time I need to fully understand grub2 yet).  This is what I have so far in /etc/grub.d/40_custom
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
echo "Adding crunchbang" >&2 
cat << EOF
menuentry "#!crunchbang linux" {
        configfile (hd1,0)/grub/grub.conf
	chainloader +1
}
EOF
echo "Adding Fedora 11" >&2
cat << EOF
menuentry "Fedora 11" {
        configfile (hd1,1)/grub/grub.conf  
	chainloader +1
}
EOF
```

Displays in the grub menu, but still doesn't load.

---

