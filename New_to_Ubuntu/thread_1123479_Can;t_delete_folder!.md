---
title: "Can;t delete folder!"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by kamitsukai on 2009-04-12
I mounted a bin file in a folder on my desktop by using acetoneISO and have subsequently deleted the bin file but the folder I mounted it to on the desktop still has the files in it and refuses to delete!
[LIST]
[*]I've tried right clicking on the file but the permissions tab is all greyed out

[*]I've tried deleting the file in root nautilus

[*]I've also tried the dreaded rm delete command thing but it still didn't work

[*]and I've tried to unmount the folder with acetoneISO but it tells me the folder isn't mounted!
[/LIST]

Please Help!:mad:

---

### Post by llamabr on 2009-04-12
> **kamitsukai said:**
> 
[*]I've also tried the dreaded rm delete command thing but it still didn't work

The command line is not so dreaded.

in terminal navigate to where the directory is, and give us the output of 

```
ls -l
```

to use the command line to rm a dir, you need to use the -r flag for recursive, so

```
rm -r dirname
```

---

### Post by kamitsukai on 2009-04-12
**_Trying to delete with "rm -r"_**
```
carl@carl-desktop:~$ sudo rm -r /home/carl/Desktop/untitled*
rm: cannot remove `/home/carl/Desktop/untitled folder': Permission denied

```
[B][U]
and output of "ls -l"
[/U][/B]
```
carl@carl-desktop:~/Desktop/untitled folder$ ls -l
total 43366
-r--r--r-- 1 root root        42 2008-06-03 22:29 [File Name]
-r--r--r-- 1 root root     22486 2008-04-29 19:56 [File Name]
-r--r--r-- 1 root root 177603018 2008-06-06 17:58 [File Name]
dr-xr-xr-x 1 root root      2048 2008-07-10 14:43 [File Name]

```

---

### Post by drowner on 2009-04-12
Is this on that USB drive you were posting about earlier?

---

### Post by kamitsukai on 2009-04-12
nope something completley different etirley =]:lolflag:

---

### Post by drs305 on 2009-04-12
I know you said you tried root nautilus, but did you do this:
```

gksudo nautilus /home/carl/Desktop/

```
and then use SHIFT-DELETE to delete the applicable folder?

Caution: You cannot recover files/folders deleted with SHIFT-DELETE, and you are running as root and can delete anything, including system files.

---

### Post by kamitsukai on 2009-04-12
Sorry I should of mentioned that the folder doesent even show up in root nautilus...

also it appears that there's now a second untitled folder on my desktop one appears to be the original folder and the other is a mounted volume?

---

### Post by drs305 on 2009-04-12
Look in your /media folder. It's not really in ~/Desktop. Before you delete anything make sure of the contents. You might also run "sudo umount -a" to see if the folder goes away. If it does, you need to figure out what is mounting "untitled".

---

### Post by kamitsukai on 2009-04-12
> **drs305 said:**
> Look in your /media folder. It's not really in ~/Desktop.

it's not in my media folder

---

### Post by kamitsukai on 2009-04-12
HA! I managed to delete it but I have no Idea how... I just kept clicking retry as it was annoying the hell out of me and then the screen went blank and the folder was gone =0


Thanks for helping :)

---

### Post by drs305 on 2009-04-12
*Edit:* Too late. Glad you got it deleted. Disregard the following:

Does this command reveal it's location:
```

sudo find / -iname *untitled

```

---

