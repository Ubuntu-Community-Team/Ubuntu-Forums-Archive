---
title: "Samba: Need Help Networking from BASH"
date: 2007-08-04
forum: Networking &amp; Wireless
---

### Post by onering on 2007-08-04
I'm new to Samba.  I have Samba working and I can access my WIndowsXP box using the Ubuntu file browser.  

How can I access the WindowsXP from the BASH shell?  I tries these things but none worked.  Thanks!!

```

$ cd smb://winbox/shareddocs
$ cd  //winbox/shareddocs
$ cd \\winbox\shareddocs

```

---

### Post by nichipet on 2007-08-04
I'm not at home so I can't test anything out, but you need to find the mount point of XP. It may be in /dev or /mnt.

---

### Post by onering on 2007-08-04
> I'm not at home so I can't test anything out, but you need to find the mount point of XP. It may be in /dev or /mnt.
Thanks.  Its definitely not on /mnt.  There is a lot of stuff in /dev. What would I be looking for?

---

### Post by janga on 2007-08-04
The Integrated server mounting program in ubuntu only works with nautilus. It makes only softmounts. If you want to access from shell, you have two options:
1. install mc. The Midnight Commander works in text mode and has smb softmount support.
2. do a hardmount with smbfs. This has been explainded here often. Search the forum and/or the wiki for "smbfs".

---

### Post by nichipet on 2007-08-04
Also take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=249942](http://ubuntuforums.org/showthread.php?t=249942)

---

### Post by onering on 2007-08-04
OK, I understand now about the "soft mount".  My goal was to write a BASH script to backup some directories to the WIndowsXP machine using rsync.  

Maybe there is a better way to do it instead?  Maybe there is a backup program that can see these soft mounted samba folders?

Thanks.

---

### Post by janga on 2007-08-04
well you could write a script, that works like..

#!/bin/sh
mount -t smbfs -o username=xxxx,password=xxxx //xpmachine/share /mnt/temp
rsync -blabla #i dont know the syntax, never used rsync
umount /mnt/temp
[I][I]
and execute it as root.
Something like this. Btw, Rsync is has a network protocol, it should work without smb. But i dont know if there is a Rsync server program for windows.
[/I][/I]

---

### Post by janga on 2007-08-04
Just found rsync for windows:
[http://www.itefix.no/phpws/index.php?module=pagemaster&PAGE_user_op=view_page&PAGE_id=6&MMN_position=150:150](http://www.itefix.no/phpws/index.php?module=pagemaster&PAGE_user_op=view_page&PAGE_id=6&MMN_position=150:150)

So you can forget about the samba stuff.

---

### Post by onering on 2007-08-04
> Just found rsync for windows:
[http://www.itefix.no/phpws/index.php...sition=150:150](http://www.itefix.no/phpws/index.php...sition=150:150)

So you can forget about the samba stuff.

Oh, this looks like a good approach.  I'll give it a try and let you know how it works.  Thanks for the idea!!

---

### Post by onering on 2007-08-04
I was able to mount the WinXP shared folder as a hard nount!!  But there are a few unexpected quirks.  For instance, from the BASH Shell it does not play very nice with files on the WinXP machine that have spaces in the name.  You need to put them in quotes

As was mentioned by janga, you have to create a hard mount point for the WinXP shared folder like this.  Additionally you need to know the admin Password on the WinXP machine.  You will be prompted for two passwords.  The first is the Linux SUDO and the second is the WinXP admin.

1) mkdir /mnt/winxpshare   (or where ever you want it)
2) sudo smbmount //xpmachine/SharedDocs /mnt/winxxpshare

So, I'm essentially back to my original dilemma.  I want to incrementally back up files from my Ubuntu Linux box to my WinXP box.  I want a smart backup that adds new files, overrides files that are older, etc...

I thought I would build it in BAS using rsync, but not sure I want to do that now.  Anyone have any other suggestions for this?

Thanks. :confused::confused:

---

### Post by nichipet on 2007-08-04
Actually, when I read that you want it to add new files, override older files, from what I am aware of, that sounds like rsync would do what you want. I have some bash code that can rename spaces in a filename into underscores, it's a permanent change, but I can get it for you if you want it. That will take care of the spaces problem.

---

### Post by onering on 2007-08-04
> I have some bash code that can rename spaces in a filename into underscores, it's a permanent change, but I can get it for you if you want it.
Sure, thanks.

---

### Post by nichipet on 2007-08-04
The following code will change spaces to underscores for every file (visible only, I believe) in the same directory as the script. It can be adapted if your needs vary.

```
for i in *
  do
    mv "$i" `echo $i | tr ' ' '_'`
  done

```

Once you have everything set up the way you want it and only need the bash script written to automate the process, I can help you with that. We can build it from scratch.

---

### Post by kevdog on 2007-08-04
You might want to take a look at the Unison file sychronization package.  It runs on linux, windows(via cygwin), and it does everything you want.  It also has a GUI interface available if thats important for you.   I use this in conjuction with cron.

---

### Post by onering on 2007-08-05
> You might want to take a look at the Unison file sychronization package. It runs on linux, windows(via cygwin), and it does everything you want. It also has a GUI interface available if thats important for you. I use this in conjuction with cron.

So I fully understand before doing it.  
1) The WinXP box needs to be running cygwin and Unison.
2) The Ubuntu box needs to be running Unson.
3) Then I can then run a cron job on the Ubuntu box that will run Unison and perform some file transfers (backups).

This sounds promising.  Thanks for your response.

---

