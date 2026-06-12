---
title: "&quot;Defrag&quot; needed?"
date: 2011-02-08
forum: New to Ubuntu
---

### Post by jcouillard on 2011-02-08
Hi everyone...very new to Linux...

 

I havea  few questions I hope you guys can help me out with...

 

1. Do I need to "defrag" in Linux?

2. Besides S.m.a.r.t. is there any other built in HDD diagnostics tool(s) in Ubuntu 10.10?

3. I want to become good with CLI in Linux so I would like to know some basic things I need to know to get started with using CLI more?

4. Is there a built in backup software in Ubuntu 10.10?

5. I was not connected to the Internet when I installed. I cannot play avi files, mp3's, I am assuming once I get back to shore (I am a Navy IT) I should be able to automatically get all these plugins for these very basic codecs? Thanks

---

### Post by vanadium on 2011-02-08
I will answer the question which is the topic of this thread:

Short answer: no, practically no defrag is needed when using an ext4 file system.

Longer answer: linux file systems are designed such that file fragmentation will be minimal, and of no importance practically. The only situation where fragmentation will significantly start to occur, is when the file system is quite full. It is advised to stay below 70% of disk usage in order to avoid any significant fragmentation from happening.

I presume that there are some defrag tools available by now, but the classical way to defrag a volume is to reformat it then copy all files back.

Practical answer: you should not really bother: it is not an issue, normally.

---

### Post by eriktheblu on 2011-02-08
3. Start with learning the file system structure, then basic file manipulation commands. 

The file system is quite different from Windows in that it is based on the actual operating system and the physical configuration of drives is less relevant. Physical drives and partitions can be allocated to any part of the file system rather than limited to drive letters.

Use cd to change directories/subdirectories, ls to list files in a directory, rm to remove files, mkdir to create directories. Typical syntax for commands is [command][options][source][destination]. You can typically read the manual on most commands by typing man [command].

Several guides exist; Google search BASH to find them.

4. rsync is a command line tool present in most Linux systems (Included in Ubuntu)

5. Not automatic, but fairly simple. These formats are proprietary so Ubuntu will not distribute them. Once you have internet, search the software center for "restricted extras" (or in the command line: sudo apt-get install ubuntu-restricted-extras)

You can read more about it [here.]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by petox on 2011-02-08
5. I suggest you use for multimedia playback a player that already has codecs installed in it...like vlc
[http://www.videolan.org/](http://www.videolan.org/)

---

### Post by ikt on 2011-02-08
> **jcouillard said:**
> 2. Besides S.m.a.r.t. is there any other built in HDD diagnostics tool(s) in Ubuntu 10.10?

smart is the main one you'll need,

[http://en.wikipedia.org/wiki/S.M.A.R.T](http://en.wikipedia.org/wiki/S.M.A.R.T).

If your drive is going to die soon, smart should know about it and tell you.

---

### Post by jcouillard on 2011-02-09
Thanks a lot guys!! Your posts have really helped me out already. As far as a player I use VLC in Windows too so I will probably use that in Ubuntu also. I will look into using this rsync tool to try it out. I do need to learn the file system, so I appreciate the link for it. The only thing I am still surprised by is the fact that you just wait for S.M.A.R.T. to say it's going bad. How do I do all I can to prevent it from going bad is what I am trying to ask? Thanks

---

### Post by jcouillard on 2011-02-09
Thanks a lot guys!! Your posts have really helped me out already. As far as a player I use VLC in Windows too so I will probably use that in Ubuntu also. I will look into using this rsync tool to try it out. I do need to learn the file system, so I appreciate the link for it. The only thing I am still surprised by is the fact that you just wait for S.M.A.R.T. to say it's going bad. How do I do all I can to prevent it from going bad is what I am trying to ask? Thanks

---

### Post by mike555 on 2011-02-09
You can check your "smart" in your disk utility app. ,  Lucky backup is a good simple backup.

---

### Post by migs73 on 2011-02-09
> **mike555 said:**
> You can check your "smart" in your disk utility app. ,  Lucky backup is a good simple backup.


System> Administration> Disk Utility

The smart data is on the main screen.

Mike

---

### Post by Dutch70 on 2011-02-09
> **jcouillard said:**
> Hi everyone...very new to Linux...

3. I want to become good with CLI in Linux so I would like to know some basic things I need to know to get started with using CLI more?


[http://www.linuxcommand.org/index.php]("http://www.linuxcommand.org/index.php")

---

### Post by Paqman on 2011-02-09
> **jcouillard said:**
> The only thing I am still surprised by is the fact that you just wait for S.M.A.R.T. to say it's going bad. How do I do all I can to prevent it from going bad is what I am trying to ask? Thanks

The drives themselves handle that automatically. For example, if a drive detects that a write has failed due to a bad block, that block is automatically marked as bad, and a one from a pool of spares is brought into use to replace it. As another example, if you're using an SSD it will automatically keep track of how many writes each block has done, and allocate writes in a way that ensure the wear is evenly spread across the drive.

These are just examples, but they show that there's a lot going on behind the scenes on a hard drive. As far as you're concerned you don't need to worry about any of it until the integrated drive electronic alert you to something that the drive thinks is an issue. If you're interested then taking a look at the SMART data once in a while will tell you how the drive is doing. 

You can't actually prevent a drive from going bad, they do have a finite life span. About the only thing you can do to imrpove reliability is make sure they're not subjected to excessive heat, cold, humidity, dust, shock or vibration. If you're at sea you might want to think about an SSD instead of a magnetic drive.

---

### Post by jcouillard on 2011-02-10
> **Paqman said:**
> The drives themselves handle that automatically. For example, if a drive detects that a write has failed due to a bad block, that block is automatically marked as bad, and a one from a pool of spares is brought into use to replace it. As another example, if you're using an SSD it will automatically keep track of how many writes each block has done, and allocate writes in a way that ensure the wear is evenly spread across the drive.

These are just examples, but they show that there's a lot going on behind the scenes on a hard drive. As far as you're concerned you don't need to worry about any of it until the integrated drive electronic alert you to something that the drive thinks is an issue. If you're interested then taking a look at the SMART data once in a while will tell you how the drive is doing. 

You can't actually prevent a drive from going bad, they do have a finite life span. About the only thing you can do to imrpove reliability is make sure they're not subjected to excessive heat, cold, humidity, dust, shock or vibration. If you're at sea you might want to think about an SSD instead of a magnetic drive.
Thanks for the information...I am just so used to Windows I can't help but feel I need to do more...lol

---

### Post by Paqman on 2011-02-10
> **jcouillard said:**
> Thanks for the information...I am just so used to Windows I can't help but feel I need to do more...lol

For sure, the lower maintenance requirements of Linux were one of the things that (pleasantly) surprised me when I switched too.

Some stuff that you can do to keep your system trim:
[LIST=1]
[*]Clean out old kernels you don't need
[*]Run "sudo apt-get autoremove && sudo apt-get autoclean" occasionally to get rid of junk in your APT cache
[*]Backups!
[*]Er, that's about it...
[/LIST]

---

### Post by jcouillard on 2011-02-10
> **Paqman said:**
> For sure, the lower maintenance requirements of Linux were one of the things that (pleasantly) surprised me when I switched too.

Some stuff that you can do to keep your system trim:
[LIST=1]
[*]Clean out old kernels you don't need
[*]Run "sudo apt-get autoremove && sudo apt-get autoclean" occasionally to get rid of junk in your APT cache
[*]Backups!
[*]Er, that's about it...
[/LIST]

Thanks for the info man

---

