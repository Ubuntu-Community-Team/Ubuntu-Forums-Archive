---
title: "It's gone and I'm almost in panic mode!"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by familyweare on 2009-02-01
OMG its gone.... I was upgrading to 8.10 and I tried backing out when it said something like it wasn't compatible with the graphics card and it frooze. I couldn't get it to do anything so I restarted and it went to what looked like DOS stuff (in other words command line stuff that I don't know). It would scroll and say stuff like ok, ok , then failed on several of the lines... then went to a line where my only response was to hit enter where it went back to that list.

I had 8.04 and was upgrading. I have a Dell Inspiron 8600.

Before I did the upgrade I wanted to back up the system and tried using the "home" backup and it would not work, it would get to the end and say it was not successful. 

So can I recover? How do I do that? How will you contact me? When and where will I get suggestions?

At this point I had an old 7.?? Ubuntu disk but not one for the 8.04 version I was using. After getting 7.?? I was always updating till I was able to upgrade to 8.04 which went without a hitch. That is why I tried the upgrade to 8.10.

Right now I'm downloading version 8.04 to burn to disk (I'm using a windows system to do that, will that be a problem?).

Ok I'm a user but not a geek, so what do I do next?

Thanks

Family guy

---

### Post by jimmy the saint on 2009-02-01
If you have a **good backup** of your data, just do a fresh install.  There are likely other ways to go about doing it, and I hate jumping to the "fresh install" solution, but if you have a good backup, and are looking for a simple solution, a fresh install may work better for you.  If you have trouble installing from the live cd, look into the alternate cd, which doesn't require a full desktop.  Once it is installed, you can worry about the video drivers and we can help with that!

---

### Post by familyweare on 2009-02-04
Thanks for the thought. While I was pondering, I read some in the pocket guide, and did a youtube video to get some ideas. 

So here is what I did. I put ubuntu live 8.04 on a usb stick. I had to do it three times in order to get a good copy. Finally it booted up. Yeah!

To do that I went to this website and downloaded a small utility called Unetbootin at [http://sourceforge.net/projects/unetbootin/](http://sourceforge.net/projects/unetbootin/)

This utility offers several distributions and besides ubuntu.

Of course I was on another working computer. It happened to be a windows machine. This utility goes out over the internet and grabs the package you have selected and loads it on the stick. 

It is recommended that the stick be 1gb. However if you load "Linux Puppy" or "Damn Small Linux" you can do it on a 256 stick. However, I did not use either so I do not know what those versions are like. 

So I booted up using ubunut live 8.04 on a stick. And walla I was able to navigate to the info I wanted to recover thinking I would move the files to another stick and recover the info I wanted before doing a "clean' install.

But I encountered my next problem. The files I wanted to move or copy would not allow me to do so because I didn't have permission to do so since I wasn't the owner. So, I've tried going to properties and changing permission but could not figure out how to change permission for the hard drive I need info from. Not all files on the hard drive stopped me from putting a copy on another stick so I could recover them, only some of them, and I don't know why.

How do I change permissions on the hard drive I'm trying to access from the ubuntu live usb stick?

---

### Post by cariboo on 2009-02-04
You don't need to change any permissions, when you are at the desktop press Alt-F2 and type:

```
gksu nautilus
```

this will start nautilus (the file manager) in root mode. You can then copy files that you don't have permissions for to anywhere you want. When nautilus starts in root mode , it starts in /root, so you will have to navigate to your home directory, by selecting File System in the left panel.

Jim

---

### Post by familyweare on 2009-02-04
Thanks sounds like that will work! 

I will do that to retreive those files. But I have a question. Does it sound the right approach? 

Would it be possible to regroup and restore what I had/have? 

That way I keep my bookmarks, addons, etc.... without loosing them to a new 8.10 install.

Seems to me since I am able to access files for back up purposes, that there would be someway to restore the 8.04 version I was using before the 8.10 upgrade problem happened.

Thanks

---

### Post by familyweare on 2009-02-04
Thanks for the instructions. It didn't work but I think it is because I have a partition. 

9.2GB media - not used 
48.8GB media - with 45.26GB used

Here is what I tried: alt-F2 then gksu nautilus. 

The first time I did not check the box "run in terminal" and nothing happened and I still couldn't move files.

The second time I checked the box "run in terminal" and "yeah" the files I wanted did not have that box over them indicating locked like they usually did but still would not move because of permissions.

I'm not sure why it did not work. 

Do you think it is because of the partitions? And what should I try next?

---

### Post by NHArticleTen on 2009-02-04
Perhaps you could live-run Ubuntu 8.04 from your CD and then just navigate to the directories and files that you want to copy to a secure location.  I use Puppy Linux for my rescues as it is only 100MB total and can live-run just in RAM even with no virtual memory/swap.

So please keep us informed of your progress!

Thanks!

---

### Post by familyweare on 2009-02-04
Thanks NHArticle10 for the suggestion. I've been able to get to those files but they won't let me copy them to a secure location. In the meantime Puppy Linux might be a good idea to just keep on a usb stick to keep handy for rescues like this.

I wish it were as easy as knowing what fiat money was... go porcupines!

Thanks

---

### Post by familyweare on 2009-02-06
While using change of permission commands, I found that code: "sudo chamod xxx" did not work for every file. 

So when changing privileges I wasn't able to get them all to grant me permission to move them over to the flash drive for recovery. 

Having partial success I recovered what I could and reinstalled 8.04. After copying my last file over to my usb stick and moving the files off to another computer, when I put my usb stick into the freshly re-installed ubuntu 8.04 it then said.... "Cannot mount volume". So the computer is up and running ... but the usb stick isn't. At least my problems are getting smaller.

So I'm moving to the next level of the forum and finish researching why the privilege command wasn't entirely successful and why the usb stick is unmountable. 

Thanks for everyones help!

In the meantime should I mark this thread solved?

Thanks

---

