---
title: "Is copying with command line faster than with nautilus?"
date: 2011-08-17
forum: New to Ubuntu
---

### Post by jeneverboy on 2011-08-17
Just what the title says.

EDIT: for instance about 10 GB from internal hard drive to external drive via USB 2.0

---

### Post by spiky001 on 2011-08-17
Proberbly not why? is that your only reason for Question

---

### Post by jeneverboy on 2011-08-17
Well, it's taking about 10 minutes now. If somehow with command line it would only take 4 or less, I would consider it doing via command line. Sounds reasonable, right?

---

### Post by spiky001 on 2011-08-17
Have you tried the command line instead with the same file,

---

### Post by Triblaze on 2011-08-17
I think the actual act of the computer copying the files should be the same with either method.

If you're talking about the act of telling the computer what you want copied and to where, it depends. Copying something into a folder above it or near it is quick with nautilus. If you're copying it farther away or deep into the filesystem, it's usually quicker to just define where you want it copied to with the command line.

---

### Post by n213978745 on 2011-08-17
I don't think there has any different, perhaps GUI "copy" will give you more details(such as percentage), compare to CLI without "--verbose" option.

But let say if you have a folder that have 1000 photos in it.  You have backed it up to external hard drive (EHDD) from your computer few weeks ago.

This week you delete 50 photos from that folder, and adding 300 more photos and editing 5 photos.  You want to back it up to EHDD from your computer again.
I would say that in this case CLI will do better job because:
you don't need to find which photos you deleted
you don't need to find which photos you added
you don't need to find which photos you edited

If you tried to delete everything from hard drive and manually copy the whole folder again, it will take very long.  However, if you use CLI, it will be easier because it will help you to:
skip to copy the exact same photos you have on your EHDD
help you to update the photos that you edited
add the photos according to your computer to EHDD
delete the photos according to your computer to EHDD

If this is the case you are talking about, then the command line for it is:
> $ rsync --delete --archive --verbose /path/of/source /path/of/destionation

Hope it will help you, I may be wrong though XD

---

### Post by jeneverboy on 2011-08-17
[http://ubuntuforums.org/showthread.php?t=1694241](http://ubuntuforums.org/showthread.php?t=1694241)

so is it? Maybe it's not a beginners question.\

I have tried it just now with the command line. Got some invalid argument error. I leave it there and hoping somebody just knows the answer.

There must be an advantage in learning and using the command line otherwise most of the people here wouldn't suggest using the command line not that often.

EDIT: ok thanks for above reactions, kinda what I found out by googling the subject. Remains the question of Triblaze whether copying to 'far' directories is faster with command line. Lets say a friend of mine want to get my musicx collection on his EHHD from my EHHD. So no extra options like n213978745 said.

---

### Post by Triblaze on 2011-08-17
> **jeneverboy said:**
> [http://ubuntuforums.org/showthread.php?t=1694241](http://ubuntuforums.org/showthread.php?t=1694241)

so is it? Maybe it's not a beginners question.\

I have tried it just now with the command line. Got some invalid argument error. I leave it there and hoping somebody just knows the answer.

There must be an advantage in learning and using the command line otherwise most of the people here wouldn't suggest using the command line not that often.

EDIT: ok thanks for above reactions, kinda what I found out by googling the subject. Remains the question of Triblaze whether copying to 'far' directories is faster with command line. Lets say a friend of mine want to get my musicx collection on his EHHD from my EHHD. So no extra options like n213978745 said.
What'd you enter into the command line?

@the edit: I think the computer will still do it around the same speed for each, it's just a matter of being able to enter in what you want it to do quicker. Instead of navigating all the way to one set of data and copying it to another place that you have to navigate through the filesystem to get to, you can just enter the locations to be copied and where they will be copied to. Just a quicker way of entering it in. I really don't think the speed of the actual copy process would be affected, but I'm not sure.

---

### Post by CatKiller on 2011-08-17
> **jeneverboy said:**
> There must be an advantage in learning and using the command line otherwise most of the people here wouldn't suggest using the command line not that often.

All these messages are text. Everyone's desktop looks different, and is potentially in a different language. What else are you going to do? Giving a command for someone to copy-and-paste is simple, repeatable, universal and quick.

A lot of people mistakenly believe that everyone that uses Linux uses the command line all the time simply because that's the easiest way to help a complete stranger halfway around the world. That isn't the case. For some tasks, the command line is the best tool for the job. For other tasks, not so much.

---

### Post by eriktheblu on 2011-08-17
The GUI will consume more system resources by displaying the related windows, but the overhead is not great. In Windows it seems to make a bigger difference than in Ubuntu.

Where the CLI shines is when you want to specify certain categories of files. e.g. if you wanted to to copy all image file in your home directory and subdirectories to an external disk. This would be quite tedious with the GUI, but one line in BASH.

---

### Post by The Cog on 2011-08-17
+1 for CatKiller (#9). It is certainly easier to give one command than to write a paragraph on the menu/button/checkbox clicks needed in l/k/x/ubuntu. 

Using rsync from command line may well be quicker than drag/drop from nautilus, even when you're copying from scratch. It seems to me that rsync rattles the disk heads a lot less, which presumably equates to less time seeking and more time reading/writing. I don't know why rsync rattles the heads less though - maybe the way it does its I/O.

---

### Post by pi.boy.travis on 2011-08-17
As far as raw copy speed goes, there might be a slight overhead advantage for the command line, but it all comes down to how fast your disks can read/write and how fast your motherboard can move data around.

---

