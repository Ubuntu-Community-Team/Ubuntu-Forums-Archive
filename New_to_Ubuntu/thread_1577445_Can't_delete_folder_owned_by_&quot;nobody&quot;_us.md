---
title: "Can't delete folder owned by &quot;nobody&quot; user even as administrator"
date: 2010-09-18
forum: New to Ubuntu
---

### Post by AvicusUK on 2010-09-18
I was trying to delete folders from my home folder that I had copied from a data cd and now even as administrator rights it still tells me i do not have permission to change or delete these folders. I tried deleting them using sudo rm but as I try to delete them it has an issue as some folders have the "(" symbol so i'm totally stuck

Please help, I'm desperate

Many thanks in advance

Miguel

:confused:

---

### Post by Chris1274 on 2010-09-18
```
gksu nautilus
```

Then you can delete it in the GUI way.

---

### Post by MooPi on 2010-09-18
If your deleting a folder add -r to indicate recursive.

---

### Post by bodhi.zazen on 2010-09-18
> **AvicusUK said:**
> I was trying to delete folders from my home folder that I had copied from a data cd and now even as administrator rights it still tells me i do not have permission to change or delete these folders. I tried deleting them using sudo rm but as I try to delete them it has an issue as some folders have the "(" symbol so i'm totally stuck

Please help, I'm desperate

Many thanks in advance

Miguel

:confused:

If a file has odd symbols in the name, either escape them with a \ or use tab completion.

---

### Post by srs5694 on 2010-09-18
MooPi and bodhi.zazen have given good suggestions for the specific problems they solve; however, it's not clear to me what's causing the permissions issue you describe. If you continue to have problems, I suggest you post an ls command that shows the files or subdirectories in question (as in "ls -dF foo*" if all the files and directories begin with "foo"), as well as the exact command you're using to delete those files and the exact error message you're receiving.

Also, IMHO Chris1274's suggestion of using "gksu nautilus" is dangerous. It's too easy to forget that you're running a file manager as root; in most cases there are more subtle and less dangerous solutions to the problems that can be overcome by running a file manager as root; and even aside from potentially disastrous mistakes, running a file manager as root can end up creating additional problems down the road. These problems can all be minimized by running the program for one small task and then terminating it, but IMHO there's no reason to reach for the sledgehammer of a file manager running as root when the ball pein hammer of some other solution will do just as well. You'll learn more when you find a more elegant solution, too.

---

### Post by Chris1274 on 2010-09-19
> **srs5694 said:**
> Also, IMHO Chris1274's suggestion of using "gksu nautilus" is dangerous. It's too easy to forget that you're running a file manager as root.

I don't think it's all that easy. The root file manager appears completely different from the one for the normal user. At least it does so in Mint, where it has an ugly red background which practically screams "BE CAREFUL!" (I forget what it looks like in Ubuntu.) So long as you do what you need to do quickly and close it right away, there shouldn't be any great risk. Besides, one stupid sudo command can do just as much damage.

When it comes to elegance, I'm not sure how typing out some arcane terminal command is more elegant than simply dragging the folder into the trash bin.

---

### Post by Old *ix Geek on 2010-09-19
> **Chris1274 said:**
> When it comes to elegance, I'm not sure how typing out some arcane terminal command is more elegant than simply dragging the folder into the trash bin.You know, that's a hard thing to explain. I FEEL that way, but can't really explain why. Tradition, perhaps?

---

### Post by lobralleo on 2010-09-19
What if you try and change the ownership using chown and chmod?

```

sudo chown yourusername foldername

sudo chmod a+rw foldername

```

This way, you will get ownership and writing privileges over the files. If you want to apply it recursively to a folder, add -R:

```

sudo chown -R yourusername foldername

sudo chmod -R a+rw foldername

```

Hope this helps!

---

### Post by bodhi.zazen on 2010-09-19
> **lobralleo said:**
> What if you try and change the ownership using chown and chmod?

```

sudo chown yourusername foldername

sudo chmod a+rw foldername

```This way, you will get ownership and writing privileges over the files. If you want to apply it recursively to a folder, add -R:

```

sudo chown -R yourusername foldername

sudo chmod -R a+rw foldername

```Hope this helps!

chown and chmod do not work on fat or ntfs, you need to set ownership and permissions when you mount.

If the permissions are off on the flash drive, most likely there is a problem with the file system. The tools to fix fat and ntfs are better on windows then linux.

---

### Post by scorchgeek on 2010-09-19
> **bodhi.zazen said:**
> chown and chmod do not work on fat or ntfs, you need to set ownership and permissions when you mount.

If the permissions are off on the flash drive, most likely there is a problem with the file system. The tools to fix fat and ntfs are better on windows then linux.

Um--where did the flash drive come from? He said they were in his home folder. So I think those commands should work. Preceding the ( with a backslash, as bodhi.zazen said, should then make the rm command work normally. Just remember to recheck what you typed before you hit enter.

---

### Post by Irony on 2010-09-19
User ID not set to 1000?

---

### Post by bodhi.zazen on 2010-09-19
> **scorchgeek said:**
> Um--where did the flash drive come from? He said they were in his home folder. So I think those commands should work. Preceding the ( with a backslash, as bodhi.zazen said, should then make the rm command work normally. Just remember to recheck what you typed before you hit enter.

oops, my mistake, wrong thread :redface:

In that case, we should look at ownersip and permissions of the file.

```
ls -l ~
```

Post the file name with ownership and permissions (you can copy-paste from the terminal).

---

### Post by srs5694 on 2010-09-19
> **Chris1274 said:**
> I don't think it's all that easy. The root file manager appears completely different from the one for the normal user. At least it does so in Mint, where it has an ugly red background which practically screams "BE CAREFUL!" (I forget what it looks like in Ubuntu.) So long as you do what you need to do quickly and close it right away, there shouldn't be any great risk. Besides, one stupid sudo command can do just as much damage.

It's the same principle as running a root shell -- that is, activating the root account and logging into a text-mode console as root. Ubuntu deliberately makes this difficult, instead favoring sudo, which necessarily limits the potential damage to a single command. (Unless of course you use it to launch a utility like nautilus or another shell!) So long as something is running as root and accepting an arbitrary number of future commands, it's a risk. Ugly red backgrounds and other cues can reduce that risk, but not eliminate it.

Using sudo to run a command is also a risk, but it's not clear that sudo is actually necessary in AvicusUK's case. For instance, if the root cause is lack of write permissions (which is very plausible), then something like this will work:

```

chmod -R a+w problem-files

```

Where problem-files is the file or files that are causing problems. So long as they were copied as an ordinary user, that user owns them and should be able to do this without using root access. This illustrates one of my other points about using Nautilus as root: If you were to copy files, rather than delete them, as root, then they'd be owned by root, which could necessitate a *second* use of root access to modify them or (if they're directory trees) to delete them. Thus, turning to root to overcome problems like this can turn into a sort of addiction, multiplying the risks involved. I realize that the specific issue under discussion is one of deleting files, but *as a general rule,* using root can have unintented future consequences.

> When it comes to elegance, I'm not sure how typing out some arcane terminal command is more elegant than simply dragging the folder into the trash bin.

It's more elegant because it's a solution that directly addresses the root cause of the problem and nothing more. My analogy about the hammers is appropriate; using root access, if it's not necessary, is a sledgehammer, where something much more subtle is quite adequate. Precisely *what* smaller hammer is necessary isn't yet 100% clear yet, but in the process of learning what tool to use, AvicusUK and others are likely to learn more than they would be pulling out the sledgehammer and pounding away.

Also, don't get hung up on the command-line aspect of it. I suggested posting the output of "ls -dF" because AvicusUK had already mentioned using a text-mode command and because *I* know how to interpret the output. There are GUI alternatives to many text-mode commands, and these can be used as well. They often vary from one environment to another though (GNOME, KDE, XFce, etc.), and they take longer to describe. It could take a few paragraphs to describe how to get the information that "ls -dF" provides in every common GUI file manager, and the user would then have to save a screen shot and post it here.

[quote=bodhi.zazen]chown and chmod do not work on fat or ntfs, you need to set ownership and permissions when you mount.[/quote]

Although this claim was made in an erroneous belief that the files were on a USB flash drive, I think it should be noted that chmod *will* work on FAT or NTFS to add or remove write permission:

```

$ sudo blkid /dev/sdc1
/dev/sdc1: UUID="0E14-DC50" TYPE="vfat" 
$ sudo mount -o uid=500 /dev/sdc1 /mnt/usb
$ ls -l /mnt/usb
total 1336
-r-xr-xr-x 1 rodsmith root 1365486 Sep 19 12:57 f0201.tif
$ chmod a+w /mnt/usb/f0201.tif 
$ ls -l /mnt/usb
total 1336
-rwxr-xr-x 1 rodsmith root 1365486 Sep 19 12:57 f0201.tif

```

Note the permissions on the two ls commands; the chmod command *did* add write permissions to the file, albeit only for the owner. (The FAT mount option's umask eliminates write permissions for the group and world, at least by default for this system.)

---

### Post by The Cog on 2010-09-19
If you copied directories from a CD, they will have copied as read-only because a CD is read-only. My guess is that you need to change the permissions on the parent folder - the folder that contains the stuff you are trying to delete. But of course any sub-folders will also be read-only so you need to make them writeable too. Try:
> chmod -R +w foldername
ir if you edit the folder permissions in nautilus, use the option to also apply the same permissions to sub-folders.

---

### Post by niteshifter on 2010-09-19
> **Chris1274 said:**
> I don't think it's all that easy. The root file manager appears completely different from the one for the normal user. At least it does so in Mint, where it has an ugly red background which practically screams "BE CAREFUL!" (I forget what it looks like in Ubuntu.) So long as you do what you need to do quickly and close it right away, there shouldn't be any great risk. Besides, one stupid sudo command can do just as much damage.

When it comes to elegance, I'm not sure how typing out some arcane terminal command is more elegant than simply dragging the folder into the trash bin.

gksu nautilus on stock Ubuntu looks very nearly identical to user-perm nautilus. 

It's not an issue of "elegance": no matter how its done, via nautilus (either root or user) or by command line the same syscalls wind up being performed: unlink / remove / open-read-write, etc. The difference is in the amount of complexity encountered on the way to those syscalls. A desktop environment (GNOME, KDE) interjects more code, virtual file system "hooks" and other stuff. If the DE is functioning properly: No problem, gksu nautilus to your heart's content.

If. A lot rests on those two letters. The DE can appear OK but be badly glitched. Why take the chance of making the system worse off?
 
Another point to make is the mouse. A flaky mouse (hardware or software) with gksu nautilus can mean a bombed file system. Related, but more along the lines of "human factors": At least by typing, in theory there's some thinking happening about doing something. With the mouse, maybe not so much thinking, maybe more impulsive in doing something.

This is why getting familiar with the shell (command-line), at least to the point of knowing how to use su / sudo, ls, rm, rmdir, and mv is recommended. Us old-timers / purists will go so far as to skip the DE altogether on a goofy system and reach for a virtual console or kill the DE. Mainly because we learned to do this the hard way :)

---

### Post by Chris1274 on 2010-09-19
> **niteshifter said:**
> This is why getting familiar with the shell (command-line), at least to the point of knowing how to use su / sudo, ls, rm, rmdir, and mv is recommended. Us old-timers / purists will go so far as to skip the DE altogether on a goofy system and reach for a virtual console or kill the DE. Mainly because we learned to do this the hard way :)
 
I heartily agree, and it's precisely because I like the more "hands-on" approach of command-line interfacing that I switched to Linux. But unless I'm much mistaken, the OP wasn't looking for a lesson in shell commands but for a solution to a problem, and the simplest such solution seems to me (still) the one I suggested.
 
Nonetheless, to each his own :)

---

### Post by srs5694 on 2010-09-19
> **niteshifter said:**
> This is why getting familiar with the shell (command-line), at least to the point of knowing how to use su / sudo, ls, rm, rmdir, and mv is recommended. Us old-timers / purists will go so far as to skip the DE altogether on a goofy system and reach for a virtual console or kill the DE. Mainly because we learned to do this the hard way :)

One rule I heard, and which I heartily endorse, is this: Whenever using a root shell (or sudo or any other means of running programs with superuser privileges), you should type your command and, *before you hit the Enter key,* remove your hands from the keyboard, look over what you've typed, and think about it. Following this rule has saved me more than once when performing risky actions. Tools like disk partitioners, filesystem creation tools, file copying tools, file deletion tools, and so on can all do a lot of damage when used carelessly. I suppose one of the reasons that Chris1274's (and many others', in other threads) advice to use Nautilus as root sits poorly with me is that there's no clear equivalent to this rule when using a file manager as root. More often than not, removing your hand from the mouse completes the operation; and the command may not be as obvious (icons being dragged may be dimmer or clumped up, depending on the file manager).

One other issue: If I'm not mistaken, "deleting" files in Nautilus actually just moves them to a trash directory. Although this reduces some of the risks of operating as root, it's got other problems. Specifically, I'm not sure where files are moved when you run Nautilus as root from an ordinary user login and then delete files -- to the ordinary user's trash directory or to root's. If the former, the original problem will just be encountered again when the user tries to "empty the trash." If the latter, the files will clutter a trash directory in the /root directory, possibly consuming disk space for a very long time. If files are straight-out deleted, of course, these problems won't occur, but then you've also eliminated that one benefit to the riskiness of the operation.

[quote=Chris1274]But unless I'm much mistaken, the OP wasn't looking for a lesson in  shell commands but for a solution to a problem, and the simplest such  solution seems to me (still) the one I suggested.[/quote]

Unless I'm mistaken, the OP hasn't posted back, so it's hard to say what he has or hasn't found helpful.

I agree that your solution of using a sudo'ed Nautilus is a simple one, at least from a user perspective. My contention is that a simple solution isn't necessarily the best one. In this case, it's riskier than some alternatives, and nothing will be learned by using that solution, even if it works. OTOH, analyzing the problem to find the root cause and then using a solution that's tailored to overcome the root cause is likely to be safer and will provide an opportunity to learn.

---

