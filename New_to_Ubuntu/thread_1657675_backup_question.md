---
title: "backup question"
date: 2011-01-01
forum: New to Ubuntu
---

### Post by simolokid4 on 2011-01-01
Hi ubuntuforums,

Recently I've followed this:
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)
guide and succesfully ended up with a 37gb archive.

So far so good.

I was wondering if this good be more efficient. Seeing all programs and music and stuff is also in that .tgz which isnt very efficient, they wont change much. Just the program settings now and then.

I've also come across a webpage which I currently am unable to find again, which let u save all installed programs as package names in a simple textfile. Allowing u to simply reinstall all that with 1 command in the terminal.

Now I was wondering:

Could I have 1 backup for 2 pcs, if I kept the installed-software textfile updated, and simply backupped my home dir? I think it would come very close to a complete backup, or am i missing something here? (Both 64 bit ubuntu machines, and since processors differ, i could simply grab my 10.10 live cd if the install messes up? )

Could I get confirmation on this? This would save me a loooooooooot of hd space. (Got like 5x 40gb of .tgz's already stacked up over the last 5 weeks.)

---

### Post by solar george on 2011-01-01
You might want to look into deja-dup or BackInTime (in the repos) which would be good for backing up your home dir.

In theory you are correct, unless you've edited any files outside your $HOME in which case you will need to either back them up as well or reconfigure the programs when you re-install them. Personally if I have to reinstall I tend to only install packages as and when I need them since that avoids re-installing loads of stuff that I don't use any more.
However that being said, the command you were thinking of was probably 
```

dpkg --get-selections > package.list

```
to backup and to restore
```

sudo dpkg --set-selections < package.list

```
Where package.list is the path to the file which contains the package list. n.b the first command will overwrite the file package.list every time it's run.

---

### Post by simolokid4 on 2011-01-04
>  	 		**Re: backup question**
 		You might want to look into deja-dup or BackInTime (in the repos) which would be good for backing up your home dir.

In theory you are correct, unless you've edited any files outside your  $HOME in which case you will need to either back them up as well or  reconfigure the programs when you re-install them. Personally if I have  to reinstall I tend to only install packages as and when I need them  since that avoids re-installing loads of stuff that I don't use any  more.
However that being said, the command you were thinking of was probably 
 	Code:
 	dpkg --get-selections > package.list 
to backup and to restore
 	Code:
 	sudo dpkg --set-selections < package.list 
Where package.list is the path to the file which contains the  package list. n.b the first command will overwrite the file package.list  every time it's run. 	

Well, since I'm used to reinstalling windows, aka, taking 4 houres of my day reinstalling and reconfiguring everything, the ubuntu waof doing this takes.. 30 minutes tops. And I just have to hit ~3-4 commands. So it's better from most of the ways you look at it.

I think I will just backup my /home and simply run the selection packages list thingy every now and then, and back that up aswell. Ubutnu is reinstalled and configured in less then a houre so.

Well, thanks a lot ;)

Saves me about 200 gig's of diskspace =P

Thanks you for your response <3

Kind regards,

Simolokid

---

