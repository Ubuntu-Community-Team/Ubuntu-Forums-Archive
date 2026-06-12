---
title: "[SOLVED] Keeping Your Computer Clean"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by Raynman37 on 2008-12-23
I was wondering, after looking through the filesystem (which is still a little intimidating right now), when you install and un-install a package from the package manager, does it remove everything that was put on the computer, or is it like Winblows where you'll be finding files and dependencies for years after or at least until you reload the OS?

I guess I'm just looking for any advice on how to keep Ubuntu running smooth and clean and avoiding a bloated hard drive with useless files cluttering things up.  Thanks, and sorry if I missed this in a thread that's already been discussed.

---

### Post by Titan8990 on 2008-12-23
Remove will leave behind config files unless you use purge. Example:


sudo apt-get remove samba


Above will leave config files behind, below will purge config files:


sudo apt-get remove --purge samba

---

### Post by tarps87 on 2008-12-23
It tends to keep the dowloaded packages in a cache. Too clean this out run
```

sudo apt-get autoclean

```
or 
```

sudo aptitude autoclean

```
It's best to only use apt-get or apitiude

also you may need to use
```

sudo apt-get autoremove *packageName*

```
this will usually be suggested when removing a package if it needs to be done

---

### Post by Titan8990 on 2008-12-23
Also,

sudo apt-get autoremove


will remove packages that were installed for dependencies of programs that no longer exist.

---

### Post by tarps87 on 2008-12-23
> **Titan8990 said:**
> sudo apt-get remove --purge samba

I think it is
```

sudo apt-get purge samba

```

---

### Post by zephyrcat on 2008-12-23
For anyone looking for a slightly easier way to do the same thing, going into System > Administration > Synaptic Package Manager and marking a package for "Complete Removal" will do the same thing.

---

### Post by Raynman37 on 2008-12-23
Cool, thanks much for the previous posts!

Is there anything like defragmenting in Ubuntu?  I'm not sure how it keeps system files organized (yet), but if there is a need to defragment, how would you go about that?

Edit:

> **zephyrcat said:**
> For anyone looking for a slightly easier way to do the same thing, going into System > Administration > Synaptic Package Manager and marking a package for "Complete Removal" will do the same thing.

I also saw the "Not Installed (Residual)" section in synaptic.  Should I mark all of those for complete removal as well?

---

### Post by SuperSonic4 on 2008-12-23
You don't need to defrag if you made your system ext3, it is journaled and therefore it puts files into one 'journal' on the drive before going to the next one

---

### Post by Titan8990 on 2008-12-23
> **tarps87 said:**
> I think it is
```

sudo apt-get purge samba

```

sudo apt-get remove --purge samba 

is correct.

Your command might work as well but the one I gave an example of is what I use and know works.

---

### Post by tarps87 on 2008-12-23
The is a way by converting its format and there are also plans to include it in ext4 (the next Linux file system format) but I isn't really necessary to defragment it unless you are running a large scale server or have been using it for several years. Yes ext3 (default format) can get fragmented but a lot less than fat and ntfs.

Some more info on ext3
[http://en.wikipedia.org/wiki/Ext3#Defragmentation](http://en.wikipedia.org/wiki/Ext3#Defragmentation)

Hope this helps

> **Titan8990 said:**
> sudo apt-get remove --purge samba 
is correct.

Your command might work as well but the one I gave an example of is what I use and know works.

Just checked and they both work, too much choice :)

> **Raynman37 said:**
> I also saw the "Not Installed (Residual)" section in synaptic.  Should I mark all of those for complete removal as well?
There should be no harm in removing them, I believe autoclean should automatically do this
```
sudo apt-get autoclean
```

---

### Post by Raynman37 on 2008-12-23
Thanks for all of the helpful info!  Should be running a lean, mean, Ubuntu machine now.

---

### Post by zephyrcat on 2008-12-23
> **Raynman37 said:**
> Edit:



I also saw the "Not Installed (Residual)" section in synaptic.  Should I mark all of those for complete removal as well?

I believe you should be able to without a problem, but just take a quick look to make sure there is nothing there you need.

Keep in mind that if you ever plan on reinstalling an application, you may not want to completely remove it, since you will lose your configuration.

---

### Post by Paddy Landau on 2008-12-23
If you want to be thorough, you could use clean instead of autoclean (which removes even more stuff):
```
sudo apt-get clean
sudo apt-get autoremove
```Edit: You can also clear your backups:
```
 sudo rm /var/backups
```

---

### Post by DJ_Peng on 2008-12-23
I tried 
```
 sudo rm /var/backups
```
but it returned 
> sudo rm /var/backups
Otherwise thanks for the great tips. I've used Ubuntu for a year or two and I didn't know about those.

---

### Post by Titan8990 on 2008-12-23
It returned that command you put in as output?


That command shouldn't return anything.

---

### Post by RookieUbuntuUser58 on 2008-12-23
For me that code returned /var/backups is a directory and cannot be removed.

---

### Post by Titan8990 on 2008-12-23
When deleting directories, you have to use -r:


sudo rm -r /var/backups


rm -r is a very powerful command with a lot of potential of unwanted damage. Be careful when using it with sudo.

---

### Post by Raynman37 on 2008-12-23
Yeah I got:

> ray@Hal:~$ sudo rm /var/backups
rm: cannot remove `/var/backups': Is a directory

Same thing when I switched to root.

Edit: Never mind, Titan posted while I was typing.

---

### Post by Titan8990 on 2008-12-23
See my post that came up right before yours did.

---

### Post by linux_tech on 2008-12-23
There are alot of good clean up tips here
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

I'd also recommend cleaning up firefox-
(Tools/Clear Private Data)

and of course emptying the trash is always a good idea

---

