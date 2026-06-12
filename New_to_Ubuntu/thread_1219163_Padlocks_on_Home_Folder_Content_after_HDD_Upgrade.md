---
title: "Padlocks on Home Folder Content after HDD Upgrade?"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by mapes12 on 2009-07-21
Hi

I got a bigger HDD for my laptop so I copied my entire /home folder and burnt it to a CD. Next I removed my HDD and inserted my new bigger one. I did a fresh install of 8.04 (which is what was on my old HDD) separating /home onto a different partition to "/" (i.e. the same partition configuration as my old HDD), loaded in all the updates then copied from the CD the content of /home into my filesystem. I did this with root privilges with the command ```
gksudo nautilus
``` and copied and paste across. The copy went OK but there are some problems:

1. All the files in /home have padlocks next to them
2. The wallpaper pic that normally is my desktop background isn't being displayed. The display defaults to the Hardy Heron image.

EDIT: Forgot to mention that when I burnt /home to the CD-R I wasn't using root priviliges. I guess this is the problem but don't know how to fix it?

Any suggestions would be appreciated.

Thank you.

Mark

---

### Post by kidux on 2009-07-21
Use gksudo nautilus again to get root privleges, then right click the folder, then click on properties. Under the Permission tab, change the owner to yourself, then read-write permissions to yourself. That should fix the problem.

---

### Post by saj0577 on 2009-07-21
> **mapes12 said:**
> Hi

I got a bigger HDD for my laptop so I copied my entire /home folder and burnt it to a CD. Next I removed my HDD and inserted my new bigger one. I did a fresh install of 8.04 (which is what was on my old HDD) separating /home onto a different partition to "/" (i.e. the same partition configuration as my old HDD), loaded in all the updates then copied from the CD the content of /home into my filesystem. I did this with root privilges with the command ```
gksudo nautilus
``` and copied and paste across. The copy went OK but there are some problems:

1. All the files in /home have padlocks next to them
2. The wallpaper pic that normally is my desktop background isn't being displayed. The display defaults to the Hardy Heron image.

EDIT: Forgot to mention that when I burnt /home to the CD-R I wasn't using root priviliges. I guess this is the problem but don't know how to fix it?

Any suggestions would be appreciated.

Thank you.

Mark


Just been fiddling around and this is what I came up with.

Hope it helps i have tested it and it seems to work (only difference is i was no doing it with home folder so the directory on the end might not be fool proof)

```
sudo chown -hR <USERNAME> 

```

```
sudo chown -hR <USERNAME /home/<USERNAME>
```


Saj

---

### Post by mapes12 on 2009-07-21
Saj

Tried that and this is the output > mark@laptop:~$ sudo chown -hR <mark> /home/<mark>
bash: syntax error near unexpected token `newline'
mark@laptop:~$ sudo chown -hR /home/mark
chown: missing operand after `/home/mark'
Try `chown --help' for more information.
mark@laptop:~$ 

kidux

Tried that and this is the output:

---

### Post by saj0577 on 2009-07-21
Sorry dont use the <> when typing username. 

Saj


i typed them to try show that username was a blank for you to fill in my bad :)

---

### Post by saj0577 on 2009-07-21
```
sudo chown -hR mark 

```

```
sudo chown -hR mark /home/mark
```

---

### Post by saj0577 on 2009-07-21
> **mapes12 said:**
> Saj

Tried that and this is the output 

kidux

Tried that and this is the output:



Fro that screenshot from top downwards the drop down menus should say

mark
create and delete files
---

mark
create and delete files
---

access files
---




and then click apply ot enclosed files and folders and that should work doing it the GUI way.


Saj

---

### Post by mapes12 on 2009-07-21
Hi Saj

Just had another go and got this > mark@laptop:~$ sudo chown -hR mark
chown: missing operand after `mark'
Try `chown --help' for more information.
mark@laptop:~$ sudo chown -hR mark /home/mark
chown: cannot access `/home/mark/.gvfs': Permission denied
mark@laptop:~$ 

Does this help > mark@laptop:~$ ls -l /home
total 20
drwxr-xr-x  2 root root 16384 2009-07-21 13:52 lost+found
drwxr-xr-x 35 mark mark  4096 2009-07-21 19:07 mark
mark@laptop:~$ ls -l /home/mark
total 52
drwxr-xr-x 2 mark mark 4096 2009-07-21 19:07 Desktop
drwxr-xr-x 3 mark mark 4096 2009-07-21 17:09 Documents
dr-xr-xr-x 3 mark root 4096 2009-07-21 16:54 Examples
-r--r--r-- 1 mark root  166 2008-06-05 20:51 Holiday Destinations
-r--r--r-- 1 mark root  155 2008-06-05 20:48 Holiday Destinations~
drwxr-xr-x 2 mark mark 4096 2009-07-21 14:35 Music
dr-xr-xr-x 2 mark root 4096 2009-07-12 17:05 PDF
dr-xr-xr-x 2 mark root 4096 2009-07-19 10:13 Photos
drwxr-xr-x 3 mark mark 4096 2009-07-21 17:09 Pictures
drwxr-xr-x 2 mark mark 4096 2009-07-21 14:35 Public
dr-xr-xr-x 3 mark root 4096 2008-12-10 10:03 pulse-backup
drwxr-xr-x 2 mark mark 4096 2009-07-21 14:35 Templates
drwxr-xr-x 2 mark mark 4096 2009-07-21 14:35 Videos
mark@laptop:~$

---

### Post by mapes12 on 2009-07-21
> Fro that screenshot from top downwards the drop down menus should say

mark
create and delete files
---

mark
create and delete files
---

access files
---Thanks Saj

But which directory. /home or /home/mark?

---

### Post by saj0577 on 2009-07-21
I will look into that now,just going to boot up an old machine and simulate the problem.

Change it through the GUI if possible this time and when i figure it out I will figure out the CL way of doing it.

Read upto see how to do it in GUI.

Hope it helps
Saj

---

### Post by saj0577 on 2009-07-21
> **mapes12 said:**
> Thanks Saj

But which directory. /home or /home/mark?


/home/mark




Saj

---

### Post by rbc on 2009-07-21
Saj, I may be showing my ignorance but shouldn't it be
sudo chown -hR mark:mark /home/mark

---

### Post by saj0577 on 2009-07-21
> **rbc said:**
> Saj, I may be showing my ignorance but shouldn't it be
sudo chown -hR mark:mark /home/mark



I only just researched it to try help mapes12 out. So if you say so from experience I believe you,like I said I researched and learnt it to try and help out.


Saj

---

### Post by mapes12 on 2009-07-21
Hi Guys

I think it's a problem with a hidden file. Here's the output to the last post

> mark@laptop:~$ sudo chown -hR mark:mark /home/mark
chown: cannot access `/home/mark/.gvfs': Permission denied
mark@laptop:~$ 

---

### Post by saj0577 on 2009-07-21
Tried the GUI way aswell?

Saj

---

### Post by mapes12 on 2009-07-21
> **saj0577 said:**
> Tried the GUI way aswell?

SajYep. No joy.

---

### Post by mapes12 on 2009-07-21
Googled this .gvfs directory. It's a gnome thing. I think when I copied /home that .gvfs got corrupted somehow. But haven't a clue how to fix it?

Other posts are reporting problems with rsync and this .gvfs issue.

---

### Post by saj0577 on 2009-07-21
```
gksudo nautilus
```

navigate to /home

right click mark>select properties

Click permissions tab.

Make it look like the attachment (with mark replacing Stephen)

CLick apply settings to encloed files.


Saj

---

### Post by mapes12 on 2009-07-21
Hi Saj

I have replicated the Permissions via> gksudo nautilusGUI but I still have the same problem. I've restarted the system after each change but still no joy. I think the problem is this .gvfs directory:

---

### Post by saj0577 on 2009-07-21
Try CTRL+ALT+BACKSPACE (it will log you out,then log back in and that way if anything is caught up it will all refresh.)

Saj

---

### Post by rbc on 2009-07-21
> Googled this .gvfs directory. It's a gnome thing. I think when I copied /home that .gvfs got corrupted somehow. But haven't a clue how to fix it?

I don't think it got corrupted. I think what has happened is that doing a simple copy/paste of your home directory has messed up permissions, since not everything, even within your home, has the same permissions. Sorry, maybe I'm stating the obvious. Type this in terminal:
ls -al | grep .gvfs
and post back

---

### Post by mapes12 on 2009-07-21
Hi rbc

Here's the output > mark@laptop:~$ ls -al | grep .gvfs
dr-x------  2 mark mark    0 2009-07-21 20:25 .gvfs
mark@laptop:~$ 

---

### Post by rbc on 2009-07-21
Well darn. I was hoping that would help. The permissions actually look correct, or at least it matches my .gvfs directory. I am afraid you issue exceeds my abilities. Anyone else want to jump in?

---

### Post by juanoleso on 2009-07-21
Are you still having the issue with the padlocks?  If so try:

```

$sudo chown -fh -R mark:mark /home/mark

```

once you own the files, you can then modify the permissions on your files either through nautilus or through terminal:

```

$sudo chmod -fh -R u+rw /home/mark

```

edit: -f ignores that .gvfs folder

---

### Post by mapes12 on 2009-07-21
> **juanoleso said:**
> Are you still having the issue with the padlocks?  If so try:

```

$sudo chown -fh -R mark:mark /home/mark

```

once you own the files, you can then modify the permissions on your files either through nautilus or through terminal:

```

$sudo chmod -fh -R u+rw /home/mark

```

First CL went OK but second hit the buffers 

> mark@laptop:~$ sudo chmod -fh -R u+rw /home/mark
[sudo] password for mark: 
chmod: invalid option -- h
Try `chmod --help' for more information.
mark@laptop:~$ 

---

### Post by juanoleso on 2009-07-21
sorry, looking at the wrong man page:

```

$sudo chmod -f -R u+rw /home/mark

```

---

### Post by mapes12 on 2009-07-21
Hi and thanks,

It's the .gvfs issue again:

> mark@laptop:~$ sudo chmod -f -R u+rw /home/mark
chmod: cannot access `/home/mark/.gvfs': Permission denied
mark@laptop:~$ 

---

### Post by rbc on 2009-07-21
I have been agonizing over this and offer this solution, albeit a drastic one, which is unfortunate, since you actually did things right by creating the /home partition during install. And it is going to involve somehow connecting one of the hard drives via USB or Firewire. I am also assuming that the old hard drive has not been wiped/erased/thrown in the trash.So hopefully, someone will come along with a panacea.
Use dd, Clonezilla, or PartImage to clone the old Ubuntu install to the larger hard drive, then follow this to move the /home directory to its own partition:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
I have used this tutorial, and were it not for human error (mine) it would have worked flawlessly the first time. Hope this helps if someone else doesn't come to the rescue

---

### Post by mapes12 on 2009-07-22
> I have been agonizing over this.........Me too!

After issuing various commands in terminal and even uninstalling the gvfs server (I read a post somewhere that said it might work, but it didn't) my entire system started to fall over. Therefore, I decided to do a fresh install of 8.04 onto the 3 partitions I had previously setup (one each for "/" /home and swap). Then instead of copying across /home from the CD-R I had burned from the old HDD inc all the hidden files I just copied across my main stuff such as Pictures, Music and Documents. I had to reset their permissions via each Folder>Properties>Permissions>Apply permissions to enclosed files. That got rid of the padlocks. Then I downloaded all the updates (again............386 of them!). Restarted and then manually reset the appearance and background wallpaper to what I had before. Installed my favourite FF ad-ons (Xmarks and LastPass) and pleased to report that everything appears to work OK. Just a shame that a simple copy and paste of my entire old /home coudn't have reset my personal settings but I'm there now and with 3 times more space on the bigger HDD.

A big thank you to all who have posted with suggested solutions. I really appreciate your time.

Mark :D

---

