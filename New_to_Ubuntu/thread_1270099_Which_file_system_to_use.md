---
title: "Which file system to use?"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by Speedwagon on 2009-09-19
I just got a 1TB drive, and plan to move everything over to it shortly.  I will be dual booting with Vista.

So, what would be the best way to go about handling partitions and file systems?  Advantages/disadvantages of different setups?

---

### Post by scragar on 2009-09-19
For / I recommend EXT4, and for home, well, that's tricky, I'm tempted to say EXT4 as well, because given the huge size if your computer crashes EXT4 is really quick to check for errors and recover, but windows can't read EXT4 at all. :(

---

### Post by gnudoc on 2009-09-19
If you keep ext4 for your main partitions (reasons above), you could still have a smaller partition that vista can read, for the purpose of transferring stuff between the two. I would have this one in fat32 or ntfs for maximum compatibility with vista.

It's ages since I dualbooted, but the windows drivers for ext3 are still apparently buggy and crash more than I would accept for a filesystem.

---

### Post by NoaHall on 2009-09-19
I would use ext4, but if you use windows, have another partition with ntfs, not fat32.

---

### Post by scragar on 2009-09-19
> **gnudoc said:**
> It's ages since I dualbooted, but the windows drivers for ext3 are still apparently buggy and crash more than I would accept for a filesystem.
EXT3 read only support is really stable, so that's an option.

---

### Post by Speedwagon on 2009-09-19
Ok, so Ubuntu has free and clear access to any partition & file system it wants, but Vista has limited access to linux file systems then, correct?

The main reason I'm still holding on to Winblows, is because I haven't found anything I like enough to replace my J River Studios Media Center yet.  I've tried Amarok, but it just doesn't seem to cut it.

If I could get a linux version of [this](http://www.mediajukebox.com), I'd got EXT4+Ubuntu and never look back.  But my music collection on my drive is enormous, the big reason for going up to the terabyte drive.

---

### Post by NoaHall on 2009-09-19
Try Songbird. I have over 10000 songs, and it runs lightweightly.

---

### Post by sunchiqua on 2009-09-19
I would go for NTFS - mounting ext4 on Vista can be a painful process ( if possible at all ).

---

### Post by talsemgeest on 2009-09-19
I would say EXT4 for your Ubuntu partitions, but store your files on the Vista partition. That way you have a good FS, but can access your files perfectly from both OSs.

---

### Post by Speedwagon on 2009-09-19
> **NoaHall said:**
> Try Songbird. I have over 10000 songs, and it runs lightweightly.

Looks promising, I will have to give that a try.  Though I see it can't rip CDs just yet, kind of a bummer.

Can a windows program, running under WINE or Win4Lin, access the EXT4 system?

---

### Post by scragar on 2009-09-19
> **sunchiqua said:**
> I would go for NTFS - mounting ext4 on Vista can be a painful process ( if possible at all ).

ext4 support for windows doesn't currently exist outside of a "There's a 25% change it will corrupt the file system and a 74% chance windows will crash, but look, some of the time it works" sort of thing, I don't think anyone has actually taken the task of writing drivers for it at the moment actually.

---

### Post by NoaHall on 2009-09-19
Yep, because it's a layer.

---

### Post by k3lt01 on 2009-09-19
> **Speedwagon said:**
> Can a windows program, running under WINE or Win4Lin, access the EXT4 system?They can certainly read it and most that I know of can write to it, but I do not know if every WINE enabled program can write to ext4.

As for your first question I'd say ext4 for Linux and ntfs for Vista but only use Vista for the minimum of things.

---

### Post by Speedwagon on 2009-09-19
> **NoaHall said:**
> Yep, because it's a layer.

So things like Win4Lin(researching more in the background right now) is alot like the Wincenter we use at work on our *nix machines then, correct?  Where it loads up what appears to be Windows, and you go about your business in there.

---

### Post by NoaHall on 2009-09-19
Yeah, they let you write onto the linux filesystem, because it's like they are a Linux "app". If you see what I mean.

---

### Post by scragar on 2009-09-19
For a better explanation I'll simply say that windows applications for the most part don't have a clue about the file system, they just make calls to windows opperations. When they're running in wine they do the same thing, and wine does the same thing actually, wine let's the linux kernel handle the file system, and since linux knows how to use EXT4 or 3 or RFS or any other file system really, wine can use it, and subsequently applications can use it. Am I making sense?

---

### Post by Speedwagon on 2009-09-19
> **NoaHall said:**
> Yeah, they let you write onto the linux filesystem, because it's like they are a Linux "app". If you see what I mean.

Yes, I get it now.  I've only used WINE at home, with limited success on things.  But I understand Wincenter(for the most part) at work.  Just didn't realize that other programs, like Win4Lin, were the equivalent of Wincenter.

---

### Post by Speedwagon on 2009-09-19
> **scragar said:**
> For a better explanation I'll simply say that windows applications for the most part don't have a clue about the file system, they just make calls to windows opperations. When they're running in wine they do the same thing, and wine does the same thing actually, wine let's the linux kernel handle the file system, and since linux knows how to use EXT4 or 3 or RFS or any other file system really, wine can use it, and subsequently applications can use it. Am I making sense?

Completely.

---

