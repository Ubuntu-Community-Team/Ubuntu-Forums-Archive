---
title: "just curious about Linux"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by Ben Page on 2008-12-22
Hey guys!

Im just curious about Linux (started to use it 1 week-ish ago).

I have installed Ubuntu 8.10 via Wubi in Win. When I was installing it there was that Wubi option but it sayed that this way Ill have slightly lower disk preformance. How lower is disk preformance actually comparing to a "real" installation on ext3 filesystem?

My system resource manager is showing 310MB of RAM is in use after startup, all/only default services are activated + compiz maxed out, is this normal RAM usage? When I ran LiveCD openSUSE 11.1 RAM usage was 170 MB, is openSUSE using less resources than Ubuntu? I am aware that this was running from LiveCD and that compiz was off and that nvidia driver was not loaded, so I ran Ubuntu from LiveCD, too, but it still used more ram than openSUSE, 230 MB. Is openSUSE more resource friendly? (not that it matters alot, but im just curious)

---

### Post by Nepherte on 2008-12-22
310MB of RAM is pretty normal and I don't think that OpenSUSE will be any different.

---

### Post by ultimate_aektzis on 2008-12-22
No, OpenSuse is heavier distro than ubuntu.

---

### Post by Zzl1xndd on 2008-12-22
OpenSuSE and Ubuntu would have different packages, Different ways of doing things, and different processes that run on start up. I havn't played with OpenSuse in a while so I couldn't give examples but thats likely the difference.

---

### Post by Paddy Landau on 2008-12-22
When I experimented, I found that running 8.04 under Wubi was faster than running Windows (go figure!).

When I uninstalled Wubi, and installed 8.04 into its own partition, it was even faster. Although I didn't notice much of a difference at first, every time I boot into Windows, I'm reminded of just how slow and frustrating I find Windows.

If you're happy with the limitations of Wubi, or if you're just experimenting, it's OK to stay with Wubi.

If you want to get into Linux seriously, you probably want to install into its own partition. But play around with Wubi first, until you feel comfortable to go for the "real thing".

---

### Post by Ben Page on 2008-12-22
wow! turbo rplies!:lolflag:

I have heard that SUSE is heavier, but resource manager is sayng diffrent. Maybe it would change after "real" install.

So, what is the opinion related to disk preformance? Is it noticable? Because Wubi install is mutch more practical to me, I can use both Win and Lin files on same partition and filesistem, but if there is a big difference, I would install Lin for "real".

---

### Post by Ben Page on 2008-12-22
> **Paddy Landau said:**
> When I experimented, I found that running 8.04 under Wubi was faster than running Windows (go figure!).

When I uninstalled Wubi, and installed 8.04 into its own partition, it was even faster. Although I didn't notice much of a difference at first, every time I boot into Windows, I'm reminded of just how slow and frustrating I find Windows.

If you're happy with the limitations of Wubi, or if you're just experimenting, it's OK to stay with Wubi.

If you want to get into Linux seriously, you probably want to install into its own partition. But play around with Wubi first, until you feel comfortable to go for the "real thing".

Didn't see this reply before I posted...so, what are the limitations of Wubi? I read that its disabled hibernation and disk preformance, I can live with that...:)

---

### Post by mkvnmtr on 2008-12-22
I can't answer about Open Suse but on my Ubuntu I use 2 or 3 browsers, maybe a game, a torrent app and sometimes a couple of other things and never see more than about 350MB usage unless I am using Gimp. Then I go to maybe 750MB. I have 1.25 Gb installed. This seems to me like low ram usage. But I don't know how it compares to other Linix distros.

---

### Post by Paddy Landau on 2008-12-22
> **Ben Page said:**
> Because Wubi install is mutch more practical to me, I can use both Win and Lin files on same partition and filesistem, but if there is a big difference, I would install Lin for "real".
Actually, you can access Windows and Linux partitions from each other without Wubi.

When you install Ubuntu "for real", Ubuntu will automatically enable access to the Windows partition, read-write access.

In Windows, you can install Ext2 for Windows:
[http://www.fs-driver.org/](http://www.fs-driver.org/)
This allows you to choose read-only access (which I do, in case of good ole Windows viruses), or read-write.

But if Wubi is fast enough for you, and you're happy with the limitations, it's fine to stick with it.

---

### Post by Greyed on 2008-12-22
> **Ben Page said:**
> My system resource manager is showing 310MB of RAM is in use after startup, all/only default services are activated + compiz maxed out, is this normal RAM usage?

It depends on what figure of "usage" you're looking at.  Linux uses RAM for buffers/cache and are effectively free since they can be freed up for programs at a moments' notice.  So saying it is "using" 300Mb does not really mean anything.

---

### Post by Paddy Landau on 2008-12-22
> **Ben Page said:**
> ...so, what are the limitations of Wubi? I read that its disabled hibernation and disk preformance, I can live with that...
Apparently, the file system is more prone to error in Wubi. You also run the risk of corruption from Windows viruses.

I found that installing Ubuntu in its own partition was very easy. In fact, I made it more difficult for myself, because being used to Windows, I assumed it would be harder (LOL).

---

### Post by Ben Page on 2008-12-22
Well, im not happy abut the limitations but I can live with them, just wanted to know if im missing something even better...As for the real install of Ubuntu (in fact im using Mint 6) it would take major reorganisation of my hdd and risk of loosing vital data, so im trying to asses the risk-value ratio.

---

### Post by Zzl1xndd on 2008-12-22
Its not really apples to apples, but As Wubi uses a Virtual drive much like Virtual Machines, The drive speed will be fairly reduced but if you aren't affected by it I wouldn't be too concerned about it.

---

### Post by Ben Page on 2008-12-22
> **tweakedenigma said:**
> As Wubi uses a Virtual drive much like Virtual Machines, The drive speed will be **fairly** reduced

That is what im asking, how fairly? I use Excelstor SATA300 7200rpm HDD, so its fast, but can it be even more faster - drasticly faster (in tearms of copying and managing files)?

---

### Post by Liviu-Theodor on 2008-12-22
> **Ben Page said:**
> That is what im asking, how fairly? I use Excelstor SATA300 7200rpm HDD, so its fast, but can it be even more faster - drasticly faster (in tearms of copying and managing files)?

I don't know your model, but from my experience Ubuntu (7.10, 8.04 and 8.10) performs far better than Windows (98, XP, Vista) talking about operation with files. I used the liveCD to backup a whole 200 GB SATA150 drive to a 320 GB IDE100 drive, and the speed was much bigger to copy the content than with installed Windows.

---

