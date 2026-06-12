---
title: "How to copy files of a particular extension RECURSIVELY?"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by dennyk23 on 2009-08-14
Dear all,

i'm a new Ubuntu user, just recently experimented with making a file server using Samba and everything's going well...
i wish to make periodical backups, but just i do not need to make a full backup, just of files of a certain name and extension, but i need it to be recursive and maintain folder trees...

Example:
/Directory-to-be-backed-up
   /Folder1
      junkfile1
      junkfile2
      backmeup.bak
   /Folder2
      junkfile3
      junkfile4
      backmeup.bak

i want to just copy the backmeup.bak files and maintain the directories, ie. i want a command to copy the files to an empty USB-stick so that the outcome will be:

/media/USB_stick
   /Folder1
      backmeup.bak
   /Folder2
      backmeup.bak

In Windows, i usually just use the command:
xcopy C:\Directory-to-be-backed-up\backmeup.*bak U:\ /s /e
and it will create the folder1 and folder2 directories and copy just the backmeup.bak files (the * is necessary for the xcopy command in order to tell it to look for that criteria recursively)

Can someone please help me out =)
Will be most appreciated.... thanks so much in advance :)

dk

---

### Post by dennyk23 on 2009-08-14
Ugh the spaces didnt show well to illustrate the directory tree structure :( tried using Indent and it made it as one long train instead... what i meant was:

/Directory-to-be-backed-up
-->/Folder1
----->junkfile1
----->junkfile2
----->backmeup.bak
-->/Folder2
----->junkfile3
----->junkfile4
----->backmeup.bak

and i want the outcome to be:
/media/USB_Stick
-->/Folder1
----->backmeup.bak
-->/Folder2
----->backmeup.bak

Thanks =)

---

### Post by Cheesemill on 2009-08-14
```
 
man rsync

```

---

### Post by harry2006 on 2009-08-14
i guess that will include the "junkfiles" as well, which i think is not to be copied, as per the post , right @ dennyk23 ?

---

### Post by unutbu on 2009-08-14
Try this command:```


rsync -avm --include='*.bak' -f 'hide,! */' /Directory-to-be-backed-up/ /media/USB_stick

```
It will recursively copy only files that end in .bak from /Directory-to-be-backed-up/ to /media/USB_stick.

By way of a little explanation:
"-f" tells rsync to filter according to a pattern:
'*/' is a pattern which matches 'any directory'
'! */' matches anything which is not a directory (i.e. a file)
'hide,! */' means hide all files

Filter rules are applied in order, and the first rule that matches is applied.

--include='*.bak' has precedence, so if a file ends in .bak, it is included.
Any other file gets excluded from the list of files to transfer.

---

### Post by dennyk23 on 2009-08-14
Thanks a lot guys :D
Sounds like the kind of command i need to get the job done :D
Will try it once i reach home :)
Thanks again!

---

### Post by matthewbpt on 2009-08-14
you can use the program called rsync to do the backup,a dn use the --exclude or --exclude-from parameter for the exclusions, with the exclude option you specify a particular file, ie --exclude=junkfile1, with the --exclude-from parameter you specify a file containing the name of files you want to exclude. For example:

I create a file in my home folder called exclude and type the lines
```
junkfile1
junkfile2
junkfile3
junkfile4
```

then I can type in the terminal
```
rsync -auv --exclude-from=/home/$USER/exclude /directory/to/be/backed/up/ /media/USB_Stick
```

This will back up the folder but leave out the files in /home/$USER/exclude , you can inclde wildcards in the exclude file, for example to exclude all .txt files you would add a line in the file *.txt

type in 'man rsync' in the terminal to get a full list of the options available to rsync.

Matt

EDIT: as the user above said you can also use the --include parameter

---

### Post by colau on 2009-08-16
> **unutbu said:**
> Try this command:```


rsync -avm --include='*.bak' -f 'hide,! */' /Directory-to-be-backed-up/ /media/USB_stick

```
It will recursively copy only files that end in .bak from /Directory-to-be-backed-up/ to /media/USB_stick.

By way of a little explanation:
"-f" tells rsync to filter according to a pattern:
'*/' is a pattern which matches 'any directory'
'! */' matches anything which is not a directory (i.e. a file)
'hide,! */' means hide all files

Filter rules are applied in order, and the first rule that matches is applied.

--include='*.bak' has precedence, so if a file ends in .bak, it is included.
Any other file gets excluded from the list of files to transfer.

Isn't it also possible with cp command?

---

### Post by scorp123 on 2009-08-16
> **colau said:**
> Isn't it also possible with cp command? "rsync" does a better job when bulk-copying stuff, e.g. it goes after the big files first, then fills the gaps between big files with the small files, it makes sure that your cache is maxed out and used well and yet it makes sure that your system remains responsive ...

"cp" does nothing of that. It's plain stupid in that regard. It will grab whatever file it encounters first and then copy it wherever you told it to. That's all it does. OK if you just copy a bunch of files ... but for copying files from one directory tree into another directory tree I'd definitely recommend "rsync". The result you get is worth the little extra-effort to learn rsync's syntax (which isn't too hard anyway).

---

### Post by colau on 2009-08-16
> **scorp123 said:**
> "rsync" does a better job when bulk-copying stuff, e.g. it goes after the big files first, then fills the gaps between big files with the small files, it makes sure that your cache is maxed out and used well and yet it makes sure that your system remains responsive ...

"cp" does nothing of that. It's plain stupid in that regard. It will grab whatever file it encounters first and then copy it wherever you told it to. That's all it does. OK if you just copy a bunch of files ... but for copying files from one directory tree into another directory tree I'd definitely recommend "rsync". The result you get is worth the little extra-effort to learn rsync's syntax (which isn't too hard anyway).
Thank you.

---

### Post by unutbu on 2009-08-16
colau, in addition to what scorp123 said, I recommended rsync simply because cp by itself can not accomplish the job.

If you do
```

cd /Directory-to-be-backed-up/ 
cp -R *.bak /media/USB_stick
```

Then the shell expands *.bak before it reaches the cp command. So cp is fed all the top level files and dirs that end in .bak, but it will not copy, say,

/Directory-to-be-backed-up/Folder1/backmeup.bak

since backmeup.bak occurs 2 levels down, and Folder1 does not end in ".bak". Try it, you'll see.

---

### Post by colau on 2009-08-16
> **unutbu said:**
> colau, in addition to what scorp123 said, I recommended rsync simply because cp by itself can not accomplish the job.

If you do
```

cd /Directory-to-be-backed-up/ 
cp -R *.bak /media/USB_stick
```

Then the shell expands *.bak before it reaches the cp command. So cp is fed all the top level files and dirs that end in .bak, but it will not copy, say,

/Directory-to-be-backed-up/Folder1/backmeup.bak

since backmeup.bak occurs 2 levels down, and Folder1 does not end in ".bak". Try it, you'll see.
I tried this.
In folder P,
ls -l
```

total 0
hi                n (4th copy).bak  n (6th copy).bak  n (8th copy).bak      n.bak         not
n (3rd copy).bak  n (5th copy).bak  n (7th copy).bak  n (another copy).bak  n (copy).bak

```
```

cd p
cp -R *.bak /home/<user>/cpl

```
ls -l /home/<user>/cpl
```

total 0
n (3rd copy).bak  n (5th copy).bak  n (7th copy).bak  n (another copy).bak  n (copy).bak
n (4th copy).bak  n (6th copy).bak  n (8th copy).bak  n.bak

```

---

### Post by kevdog on 2009-08-16
Perhaps someone could help me with the syntax but couldn't this be done with the find command and then pipe the resultant into cp?

---

### Post by unutbu on 2009-08-16
colau, the problem only exhibits itself when cp has to copy *.bak files out of a subdirectory of p.

---

### Post by scorp123 on 2009-08-17
> **kevdog said:**
> Perhaps someone could help me with the syntax but couldn't this be done with the find command and then pipe the resultant into cp? Sure, but depending on the size of the directory tree you're using "find" against the performance will suck badly.

---

### Post by unutbu on 2009-08-17
I don't think you can accomplish this task with just "find" and "cp" either. You'd have to figure out how to execute "mkdir" commands to reproduce the directory structure. By the time you figure that out, you'd probably just say, "oh, the heck with this, let's use rsync..." :)

---

### Post by dennyk23 on 2009-08-17
> **unutbu said:**
> Try this command:```


rsync -avm --include='*.bak' -f 'hide,! */' /Directory-to-be-backed-up/ /media/USB_stick

```
It will recursively copy only files that end in .bak from /Directory-to-be-backed-up/ to /media/USB_stick.

By way of a little explanation:
"-f" tells rsync to filter according to a pattern:
'*/' is a pattern which matches 'any directory'
'! */' matches anything which is not a directory (i.e. a file)
'hide,! */' means hide all files

Filter rules are applied in order, and the first rule that matches is applied.

--include='*.bak' has precedence, so if a file ends in .bak, it is included.
Any other file gets excluded from the list of files to transfer.

Hi Unutbu,
Thank you, it worked just like how i wanted it to =)
But just out of curiosity, can you explain more about this part:

"-f" tells rsync to filter according to a pattern:
'*/' is a pattern which matches 'any directory'
'! */' matches anything which is not a directory (i.e. a file)
'hide,! */' means hide all files

By 'hide,! */' did you mean it will also copy hidden files?
And i actually tried changing 'hide,! */' to '*/' or *! */' and it does not work... it says:

'!' rule has trailing characters: ! */
rsync error: syntax or usage error (code 1) at exclude.c(895) [client=3.0.5]

Just to be clear, your rsync -avm --include='*.bak' -f 'hide,! */' /Directory-to-be-backed-up/ /media/USB_stick
line works like a charm, i'm just trying to understand more of this important rsync function and am hoping you can teach me more =)

Thanks lotsa!!
-dk

---

### Post by unutbu on 2009-08-17
Hi dennyk23, I'm glad the command worked for you.

The command that I posted comes straight from the man page of rsync (line 1990).
If you open a terminal and type
```

man rsync
/hide            # search for the word "hide"
/                # search again

```
You will see the command. Search for the section entitled "Filter rules" for the straight scoop on everything I say below. 

I should warn you there are definite limits to my understanding of rsync, and I'm probably hanging on by my fingertips here :)

The rsync command uses two filters:
```

--include='*.bak'

```
and 
```

-f 'hide,! */'
```

(--include is a short-cut for a particular kind of -f filter.)

A filter is comprised of a pattern and an action.

In the case of --include='*.bak' the pattern is *.bak, and if a filename matches, then the action is to include the filename among those rsync copies.

In the case of -f 'hide,! */' the pattern is '! */'  and the action is to 'hide', which means if the pattern is matched, the file (or directory) is hidden from transfer.

You see, rsync generates a list of files and directories in a breadth-first manner. The filters are applied to each file or directory before rsync recurses down into subdirectories.

Filter rules are applied in order, and the first pattern that matches gets its action applied. 

Any file that ends in ".bak" matches (or you might say passes) the "--include" filter, so it gets backed up.

All files and directories that do not end in "*.bak" are sent along to the "-f" filter.
As explained previously, the '! */' pattern matches all files but not directories.

When a file is encountered, the pattern matches, and the filter hides the file from rsync -- it doesn't get copied.
When a directory is encountered, the pattern does not match, so it just passes through the filter. Things that pass through all the filters without being matched are copied by rsync. rsync then recurses down into those directories and applies the filter rules to all the files and directories it finds.

Hope this helps.

---

### Post by unutbu on 2009-08-27
Good news! I'm wrong. find+cp can recursively copy:

This
```

find /Directory-to-be-backed-up/ -type f -iname "*.bak" -exec cp --parents {} /media/USB_stick ";"
```

is equivalent to
```

rsync -avm --include='*.bak' -f 'hide,! */' /Directory-to-be-backed-up/ /media/USB_stick
```

Thanks to bashologist: [http://ubuntuforums.org/showpost.php?p=2449253&postcount=3](http://ubuntuforums.org/showpost.php?p=2449253&postcount=3)

---

