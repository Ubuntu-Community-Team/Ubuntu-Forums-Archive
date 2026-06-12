---
title: "redo ubunutu"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by hollowtd on 2009-03-05
I have xp and ubuntu ibex on my dell d600 with 1 gig ram and 20 gig hd. If I just want to start over with everything and hope some functions work better and such, can I just reinstall Ubuntu? I mean, I want to get rid of windows and the original ubuntu on my system. Is this a way to do it? Will Ubuntu run smoother? It runs Ok but just sometimes flubs up. Cheers

---

### Post by bobmatino17 on 2009-03-05
you can use gparted to delete the NTFS partition and resisize your linux one, unless you want to just reinstall, then you just delete all partitions and start fresh.

---

### Post by cptrohn on 2009-03-05
I used DBAN to completely wipe the HD on my computer and re-installed Ubuntu from the ISO disk when I was ready to completly ditch windoze....

---

### Post by hollowtd on 2009-03-06
Is there a way to do this without the internet? I mean, I can get the ISO images and such, but during install, I won't be able to connect to the inet. It's a long story, but bascially I have wireless only and no cables and my dell won't connect to the wireless unless it has some drivers installed. What is Dban?

---

### Post by Vonnick on 2009-03-06
Gparted is included on the Ubuntu LiveCD. Just boot up the LiveCD, open the terminal and type

```

sudo gparted
```

Delete all of the partitions and install Ubuntu.

---

### Post by Dougie187 on 2009-03-06
Note however, this shouldn't have any effect on the speed of your ubuntu system. There is an off chance that maybe cleaning off some packages will make some other packages work, and different things like that, but in general don't expect drastic changes from reinstalling, unless you upgraded to get to ibex.

You shouldn't need anything special to wipe your hard drive. You can just use the live cd that you would download to install with. Then when you get to the partition editor there is a guided selection for using the entire hard drive, and you would simply select that option.

The live cd uses gparted to repartition, so you don't need to use it separately.

---

### Post by hollowtd on 2009-03-06
Thanks for that Dougie! I might give that a try. I was just thinking that if I cleared of Windows from the HD and redid Ubunut (ibex) then maybe things would work better. 1. Ubuntu won't load with just my battery. It sort of freezes. 2. When I brighter or darken the screen, I then lose all 3d cube ability. 3. the sound button doesn't make it louder. How do I get rid of some packages by the way? Thanks for the nice explanation, as I'm new.

---

### Post by Dougie187 on 2009-03-07
For all of those problems, you most likely want to make a seperate thread for each, to attract the most attention to each of the problems individually. You might try to post them each in the appropriate sub-forums to get the most experts on each subject, as most of the experts don't explore Absolute Beginners that much.

As for removing packages, you probably want to use Synaptic Package Manager, here is a little guide on using it.

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

---

