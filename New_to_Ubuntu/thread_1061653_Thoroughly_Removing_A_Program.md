---
title: "Thoroughly Removing A Program"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by JohnWesleyMethodist on 2009-02-06
I don't know how many times I would uninstall a program in Windows, only to do a search in the Registry after uninstalling it, and still find traces of the program! Going through and deleting those traces was necessary to keep Windows running smoothly.
 
 So I ask now about Ubuntu. If I uninstall a program, and then search for files of that program on the drive (search hidden files as well) and delete them all (with gksu nautilus if necessary) and find no traces of the program on the computer, is it thoroughly removed? Or is there a place that traces of the program may yet reside, similar to the Windows Registry?

 Thanks!

---

### Post by Voland on 2009-02-06
Try Cruft Remover or Ubuntu Tweak to delete unused packages. If you use apt in terminal, have a try to use option --purge when you uninstall package.

---

### Post by Sorivenul on 2009-02-06
Manually deleting files like that is, generally, not the proper method to remove a program in Ubuntu.

If you installed "progfoo", for example, the proper way to remove it and its configurations would be:
```
sudo apt-get remove --purge progfoo
```

If you want to make sure you get the files it depended on after you uninstall it:
```
sudo apt-get autoremove --purge
```

---

### Post by glotz on 2009-02-06
Or if you're probably using Synaptic, select completely remove instead of remove. I wonder why it isn't default operation.

---

### Post by Voland on 2009-02-06
> **glotz said:**
> I wonder why it isn't default operation.
Complete uninstall removes configuration files. If you want to reinstall program, you have to reconfigure it instead of using old configuration

---

### Post by kspncr on 2009-02-06
> **Sorivenul said:**
> Manually deleting files like that is, generally, not the proper method to remove a program in Ubuntu.

If you installed "progfoo", for example, the proper way to remove it and its configurations would be:
```
sudo apt-get remove --purge progfoo
```

If you want to make sure you get the files it depended on after you uninstall it:
```
sudo apt-get autoremove --purge
```

This is good advice, but you can also try
```
sudo apt-get clean
```
for fun.

---

### Post by jerome1232 on 2009-02-06
> **glotz said:**
> Or if you're probably using Synaptic, select completely remove instead of remove. I wonder why it isn't default operation.

I actually prefer it that way, config files generally take up what a whooping 25 KiBs

The only time I remove a package with the purge option is if I've butchered the config file past repair and need to start with a fresh config.

---

### Post by glotz on 2009-02-06
> **Voland said:**
> Complete uninstall removes configuration files. If you want to reinstall program, you have to reconfigure it instead of using old configurationI know.

> **jerome1232 said:**
> I actually prefer it that way, config files generally take up what a whooping 25 KiBs

The only time I remove a package with the purge option is if I've butchered the config file past repair and need to start with a fresh config.You and me maybe but I doubt Joe Blogs.

---

### Post by JohnWesleyMethodist on 2009-02-06
> **glotz said:**
> Or if you're probably using Synaptic, select completely remove instead of remove. I wonder why it isn't default operation.

 I have done this. But there are still traces of the program on my drive. If I "Completely Remove" something, then I expect to do a search and not find a trace of it on my computer.

 But if after choosing "Completely Remove," and then searching and deleting any files that remain, is that adequate to remove every trace of the program off the pc?

---

### Post by glotz on 2009-02-06
What kind of traces are you talking about after a complete removal?

---

### Post by DonaldJ on 2009-02-06
I tried those cleaning methods...  I ended up reinstalling Ubuntu, twice...
I'm a little "gun-shy" now, when it comes to Ubuntu cleaners...

I'm guessing that it's better to get a good understanding of the codes, before you start molesting the OS, like you could with windows...  Ubuntu isn't as forgiving as windows... Plus there's not all that crap in Ubuntu like there is in windows...  
Me thinks you need to relax about Ubuntu...  Maybe you are still quite a bit "shell-shocked from just escaping the windows toilet-class wars"...  Relax with Ubuntu.. there ain't any of that insanity in Ubuntu...  Why not just run it like it is for a month or two..?  There ain't anyone chewing on your ankle like there was with windows... No one is trying to drain your wallet and bleed your soul like it was with windows...
Linux is like an integral segment of "the brotherhood of man"...

---

### Post by Sorivenul on 2009-02-06
> **kspncr said:**
> This is good advice, but you can also try
```
sudo apt-get clean
```
for fun.
True, but apt-get clean will only remove the package files from your apt cache. While this has potential to free some space on the machine, it doesn't deal with the actual programs, their dependencies, and configurations. Still, a good idea nonetheless.

---

### Post by JohnWesleyMethodist on 2009-02-06
> **DonaldJ said:**
> I tried those cleaning methods...  I ended up reinstalling Ubuntu, twice...
I'm a little "gun-shy" now, when it comes to Ubuntu cleaners...

I'm guessing that it's better to get a good understanding of the codes, before you start molesting the OS, like you could with windows...  Ubuntu isn't as forgiving as windows... Plus there's not all that crap in Ubuntu like there is in windows...  
Me thinks you need to relax about Ubuntu...  Maybe you are still quite a bit "shell-shocked from just escaping the windows toilet-class wars"...  Relax with Ubuntu.. there ain't any of that insanity in Ubuntu...  Why not just run it like it is for a month or two..?  There ain't anyone chewing on your ankle like there was with windows... No one is trying to drain your wallet and bleed your soul like it was with windows...
Linux is like an integral segment of "the brotherhood of man"...

 You are right. I am probably more concerned then I ought to be. I am just worried it will crash like Windows.

---

### Post by JohnWesleyMethodist on 2009-02-06
> **glotz said:**
> What kind of traces are you talking about after a complete removal?

 It'll have to wait until I remove something again. Then I will come back and post it.

---

### Post by bwang on 2009-02-06
There's no need to worry about a crash. The stuff left is most likely configuration files (I don't think --purge removes the config files in your home folder).

---

### Post by lloydandj on 2009-03-07
I ran "sudo apt-get autoremove --purge" and clean, yet when I reinstalled, it was still hosed.  I just had the timeline, no effects or preview window.  Evidently, it kept the config files, anyway.  By the way, I*m talking about kdenlive.  The kdenlive program was gone from the app menu, and reappeared after a reinstall.  Thanks

---

### Post by jerome1232 on 2009-03-07
Try just removing the personal config files, there should be a .kdenlive or somesuch directory in your home folder, delete that folder while kdenlive is closed then open kdenlive, it should recreate the folder with a fresh config.

(I thought --purge removed configs  /shrug)

---

### Post by rhcm123 on 2009-03-07
run the whereis command to find all the directories with the title kdenlive
i.e.:
```
whereis kdenlive
```

you should get an output of directories, e.g. /etc/kdenlive /usr/share/kdenlive

and if your worried about problems with the registry - don't. Linux dosen't have a registry. :)

---

### Post by lloydandj on 2009-03-07
Thank you

---

### Post by rhcm123 on 2009-03-07
> **lloydandj said:**
> Thank you

Would you mind telling us what you did so that others can benefit? (Wow i sound like an advertisement :lolflag: ) Also, i'm kinda curious

---

### Post by mkvnmtr on 2009-03-07
One thing to remember. Sometimes files carry the name of a probram but are required bu another program. They won't be deleted and should not be. There are a lot of lib files like this. Really not part of the program just something that is depended on by varios programs.

---

### Post by lloydandj on 2009-03-08
Sorry to say, I got nowhere, but thanks for the help--that*s what I meant.  Whereis showed no kdenlive, just "kdenlive:."
I searched through the home folder as best I could with hidden files shown with no success.
I believe a new install of Ubuntu is next if I want to use kdenlive.  No big thing in Linux.  I spent a good deal more time searching forums, etc., with no success, either.

---

### Post by rhcm123 on 2009-03-09
> **lloydandj said:**
> Sorry to say, I got nowhere, but thanks for the help--that*s what I meant.  Whereis showed no kdenlive, just "kdenlive:."
I searched through the home folder as best I could with hidden files shown with no success.
I believe a new install of Ubuntu is next if I want to use kdenlive.  No big thing in Linux.  I spent a good deal more time searching forums, etc., with no success, either.

Then no directories named kdenlive exists. Why, is this a big problem?

---

### Post by lloydandj on 2009-03-09
No computer guru here.  I*m not sure that means there*s no config files anywhere or no directories.  I think I*ll reinstall the OS.  Ten minutes of my time is about all it will take.

---

### Post by rhcm123 on 2009-03-09
> **lloydandj said:**
> No computer guru here.  I*m not sure that means there*s no config files anywhere or no directories.  I think I*ll reinstall the OS.  Ten minutes of my time is about all it will take.

If you feel like losing all your files, then go ahead, but it looks fairly sure that it's removed. Is somthing not working?

---

### Post by lloydandj on 2009-03-12
Kdenlive.I ran "sudo apt-get autoremove --purge" and clean, yet when I reinstalled, it was still hosed. I just had the timeline, no effects or preview window. I can*t figure out how to get them back. Evidently, it kept the config files, anyway. By the way, I*m talking about kdenlive. The kdenlive program was gone from the app menu after I uninstalled via synaptic, (remove, mark for complete removal), and reappeared after a 
reinstall. I did the "purge and whereis" commands following the advice from the earlier part of the thread, but found no files doing that.  So, kdenlive is unusable for me this way.  Thanks

---

### Post by rhcm123 on 2009-03-21
> **lloydandj said:**
> reappeared after a reinstall.

well, of course it did! thats what reinstall does.
I must honestly say that you are starting to sound a bit nonsensical. I cannot honestly see what you wished to accomplish.

---

### Post by sgosnell on 2009-03-21
I have no idea what kdenlive does, nor any interest in it, but it seems that when he reinstalls it, he doesn't see everything he expects to see.  Perhaps reading the documentation for it would help him out.

---

### Post by rhcm123 on 2009-03-21
> **sgosnell said:**
> I have no idea what kdenlive does, nor any interest in it, but it seems that when he reinstalls it, he doesn't see everything he expects to see.  Perhaps reading the documentation for it would help him out.

but isn't he asking about competley removing it?

---

### Post by sgosnell on 2009-03-22
I don't think so.  My impression is that he tried to completely remove and reinstall it because it wasn't doing what he thought it should, and the complete removal would make it work, because of messed-up configuration files.  I'm not sure the problem is what he thinks it is, though.

---

### Post by rhcm123 on 2009-03-22
> **sgosnell said:**
> I don't think so.  My impression is that he tried to completely remove and reinstall it because it wasn't doing what he thought it should, and the complete removal would make it work, because of messed-up configuration files.  I'm not sure the problem is what he thinks it is, though.

agreed

---

