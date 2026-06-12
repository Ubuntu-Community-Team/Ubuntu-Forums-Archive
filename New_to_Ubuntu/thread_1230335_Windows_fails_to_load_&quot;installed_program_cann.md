---
title: "Windows fails to load: &quot;installed program cannot start&quot;"
date: 2009-08-03
forum: New to Ubuntu
---

### Post by Paddy Landau on 2009-08-03
I know that this should be on the Windows forums, but I feel more confident asking this question here.

Here's what happened:

[LIST]
[*]In Windows Vista, I turned off pagefiles and System Restore. I did a full clean-up, disk check and defragment.
[*]I shrunk the Windows Vista partition using the Windows Vista partition editor as much as it would allow me, which wasn't much. I still had 30Gb free space afterwards.
[*]I booted off the Live CD (Jaunty 9.04).
[*]I shrunk the Vista partition further, to 10Gb larger than the minimum that gparted would allow me. That still leaves 17Gb free.
[/LIST]
Now, Windows won't start. It goes through the initial "loading files" bit, and then shows a "System Recovery Options" error: "The installed program cannot start. Click OK to turn off the computer." The only option is to press OK, which turns the computer off.

I can still access my Windows partition from Ubuntu without any problem.

Fortunately, not only do I have a full backup, but also I don't need my Windows any more. Therefore, my question is:

**Is there an *easy* way to get my Windows working again?**

If not, then don't worry, I'll just delete the Windows partition. No big loss.

---

### Post by LowSky on 2009-08-03
sounds like you need your Vista CD to do a repair.

---

### Post by Paddy Landau on 2009-08-03
> **LowSky said:**
> sounds like you need your Vista CD to do a repair.
Yeah, it's one of those CD's that come with the hardware. It will erase my entire disk.

I'd rather lose Windows than do that!

---

### Post by Mark Phelps on 2009-08-03
> **Paddy Landau said:**
> .. I shrunk the Vista partition further, to 10Gb larger than the minimum that gparted would allow me... 
You did this DESPITE post after post on this forum telling folks NOT to use GParted to shrink their Vista OS or ... it could be rendered unbootable!

You just might be able to repair the damage you did ... by going to the NeoSmart forums, downloading and burning their Vista Recovery CD, booting in that CD, and running Startup Repair several times.

This is a Vista "repair" CD; not one of the CDs that came with your machine that will overwrite and restore your complete hard drive.  This one will only repair the boot and startup files; it won't touch the rest of your data or files.

---

### Post by jacklinux on 2009-08-03
> **Paddy Landau said:**
> I know that this should be on the Windows forums, but I feel more confident asking this question here.

Here's what happened:

[LIST]
[*]In Windows Vista, I turned off pagefiles and System Restore. I did a full clean-up, disk check and defragment.
[*]I shrunk the Windows Vista partition using the Windows Vista partition editor as much as it would allow me, which wasn't much. I still had 30Gb free space afterwards.
[*]I booted off the Live CD (Jaunty 9.04).
[*]I shrunk the Vista partition further, to 10Gb larger than the minimum that gparted would allow me. That still leaves 17Gb free.
[/LIST]
Now, Windows won't start. It goes through the initial "loading files" bit, and then shows a "System Recovery Options" error: "The installed program cannot start. Click OK to turn off the computer." The only option is to press OK, which turns the computer off.

I can still access my Windows partition from Ubuntu without any problem.

Fortunately, not only do I have a full backup, but also I don't need my Windows any more. Therefore, my question is:

**Is there an *easy* way to get my Windows working again?**

If not, then don't worry, I'll just delete the Windows partition. No big loss.
i guess thats the problem with GParted. Oh well we all learn from our mistakes.

---

### Post by Paddy Landau on 2009-08-03
> **Mark Phelps said:**
> You did this DESPITE post after post on this forum telling folks NOT to use GParted to shrink their Vista OS or ... it could be rendered unbootable!
LOL! Oh well. I have shrunk it before using gparted without problem, so I guess it's luck of the draw.

I've given up on Windows, and deleted its partition, increasing my Ubuntu partition to take up the lost space.

Actually, I feel quite relieved... No more Windows on my machine!

---

### Post by Paddy Landau on 2009-08-03
> **jacklinux said:**
> i guess thats the problem with GParted. Oh well we all learn from our mistakes.
I just found out that if you install ntfsprogs, then gparted can use it with NTFS partitions (e.g. formatting a partition as NTFS).

I don't know whether it will help with shrinking NTFS partitions, though...

---

### Post by LewRockwell on 2009-08-03
Re: Failure To Use Vista To Reduce Partition Size And Subsequent Vista Failure

> **Mark Phelps said:**
> You did this DESPITE post after post on this forum telling folks NOT to use GParted to shrink their Vista OS or ... it could be rendered unbootable!

You just might be able to repair the damage you did ... by going to the NeoSmart forums, downloading and burning their Vista Recovery CD, booting in that CD, and running Startup Repair several times.

This is a Vista "repair" CD; not one of the CDs that came with your machine that will overwrite and restore your complete hard drive.  This one will only repair the boot and startup files; it won't touch the rest of your data or files.

For future visitors to this thread...and perhaps with the same problems...

I second Mark Phelps on THIS!

.

---

### Post by jacklinux on 2009-08-03
> **LewRockwell said:**
> Re: Failure To Use Vista To Reduce Partition Size And Subsequent Vista Failure



For future visitors to this thread...and perhaps with the same problems...

I second Mark Phelps on THIS!

.
They should make that a sticky on here. Its something people are going to keep doing.

---

### Post by LewRockwell on 2009-08-03
> **jacklinux said:**
> They should make that a sticky on here. Its something people are going to keep doing.

what...do you actually think anyone reads the manual before blowing things up?

lol

.

---

### Post by jacklinux on 2009-08-03
> **LewRockwell said:**
> what...do you actually think anyone reads the manual before blowing things up?

lol

.
Nope, but let it be a lesson to everyone. Read before you dive in.

---

### Post by lisati on 2009-08-03
> **Mark Phelps said:**
> You did this DESPITE post after post on this forum telling folks NOT to use GParted to shrink their Vista OS or ... it could be rendered unbootable!


Been there, done that! When it happened to me I think I got lucky and was able to fix Vista fairly easily without destroying the Ubuntu partition and didn't make the connection at the time between the particular problem I had with Vista and using gparted.

---

### Post by Paddy Landau on 2009-08-03
> **LewRockwell said:**
> what...do you actually think anyone reads the manual before blowing things up?
Well, I think many people do, but they take the risk because Vista's partition editor has such problems with shrinking NTFS partitions. That was the situation with me.

What we really need is for Microsoft to improve its partition editor. That won't happen soon I guess, so an improved NTFS support for gparted would be great.

Anyway, that's not my problem now! :D

---

