---
title: "A Compendium of Issues--Dual booting Vista and Ubuntu"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by spazznie on 2009-08-28
My HP HDX 16 is 3 days old and has more problems than my 4-year old Dell. 

I tried to dual boot jaunty and vista. Long story short, the computer came with vista and I installed ubuntu on it. Then vista failed somehow and I was left only with ubuntu...from the terminal, i repartitioned everything and reinstalled vista, but then I couldn't access ubuntu. I loaded the boot CD and loaded GRUB from hd(0,4)--and now ubuntu works but vista is gone.

Right now, the only vista that exists on my system is the loader version, or the recovery partition on my drive. When I try to run it, it begins the recovery process, then fails. 

Also, is it normal to have 5 ubuntu selections on the GRUB screen? one is a memory tester, then I have two each of generic kernels and recovery versions. 

I guess I want to find a way to restore vista completely by wiping out ubuntu and THEN reinstalling ubuntu all over again...any suggestions?

---

### Post by mapes12 on 2009-08-28
Hi

I'm no expert in Grub and MBR issues but I have heard that this may be helpful: [http://www.supergrubdisk.org/index.php](http://www.supergrubdisk.org/index.php)

---

### Post by beastrace91 on 2009-08-28
What partition on your hard drive does vista exist on?... (If you are not sure load up GParted to see your partition layout)

Once you know this it is as simple as adding Vista entry back to your /boot/grub/menu.lst Something along the lines of: ```
title Winblows Vista
    rootnoverify (hdx,y) #Replace x and y with your hard drive info
    chainloader +1
```

~Jeff

---

### Post by oldfred on 2009-08-28
SuperGrub will help you resolve boot issues after a windows install that overwrites teh grub in MBR.

It is normal to have all the updated versions of ubuntu - std & recover as each kernel is updated. You want to have at least 2 just incase the new one has issues.

You can set the number of kernels to show in your menu.lst under the howmany like this:
## e.g. howmany=all
##      howmany=7
howmany=2

Since you have various partitions you will need to download & run this script to define your system and post the results.txt that it generates. 
Boot Info Script 0.32 courtesy of forum member meierfra
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

We will want to add a Vista boot stanza at the end of your menu.lst that will be like this if you do not have one and where [COLOR=DarkRed]x,y[/COLOR] will be the drive & partition of your windows:

title Microsoft Windows Vista
rootnoverify (hd[COLOR=DarkRed]x,y[/COLOR])
savedefault
chainloader +1

---

### Post by spazznie on 2009-08-29
Thanks for the responses, guys!

I'm a newbie at this, so I lost patience (especially since new errors began popping up, including a 5-minute wait at the GRUB screen for a failed build) and just installed ubuntu over everything. Not until after I had wiped out the Vista boot partition did I realize that one of the two "loader" Vista partitions that showed up in the LiveCD partitioner could possibly have been the actual Vista. Still, wouldn't it have shown up as just plain Vista, as I've seen it before when I first installed ubuntu?:confused: I also called HP support and they informed me that the boot partition shouldn't work with another operating system installed. Not sure if I should trust their word, but it's a moot point now.

I did read your replies and learn from them, even though I might not have taken ALL the advice offered ^_^.

---

