---
title: "can't erase files from trash; tried recomendations on forum"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by jadu on 2009-01-25
hi,
I copied old word files from a floppy to a cd, then from a cd to a laptop. I realized I couldn't erase or change them. I managed to move them to the trash, but then I can't get them out of the trash. Some of them I want to delete, but others I want to keep and change. I guess this means I want to change the status from read-only?

I tried different things I saw on the forums. I tried

gksudo nautilus

and it gave me that window, but when I go to trash it says "the folder contents could not be displayed". I tried copying of the files from the trash to the desktop, but it didn't show up on the desktop after I did nautilus.

I tried
sudo chmod u+w /home/[user]/.local/share/Trash
but it says "cannot access..."

Any advice please? I'm very unskilled at computers in general, I don't really know how to use the terminal stuff, so I'm probably missing something obvious. thanks

---

### Post by Cresho on 2009-01-25
```
sudo rm -rf ~/.local/share/Trash/*
```

do that in terminal.  I will advise you this is a powerfull command.  "rm" means remove, "-rf" means recursive and force.  "~" tilda means your home and the rest of the line is the specific location.  rm is dangerous especially if you do it in "/"

---

### Post by Cresho on 2009-01-25
for permissions.  you need to do 2 things.

When ever you have files or folders which you want permission for, here are two vital commands.  Nautilus can't do recursive properly yet or maybee im missing something but I'm too use to the terminal.```
sudo chown -R johndoe:johndoe /home/johndoe/afileorfolder
```

and

```
sudo chmod -R 755 /home/johndoe/afileorfolder
```

remember to replace johndoe with your home user name exactly. ;)

---

### Post by metallicamike on 2009-01-25
or you could do ```
sudo rm -r
``` and drag the file you want to delete into the terminal window. but make sure that you get rid of the quotes aroung the directory first. it works flawlessly.

---

### Post by metallicamike on 2009-01-25
as for permissions listen to Cresho.

---

### Post by jadu on 2009-01-26
Thanks to both of you for your help. I still need a little more though...

I think I might be writing the file name and path wrong, I've never done this before. I tried to change the status of a folder in my trash folder called "documents" like this:

sudo chown -R mark:mark /home/mark/trash/documents

but it said "chown: cannot access `/home/mark/trash/documents': No such file or directory"
 
I got the same response with:
 sudo chmod -R 755 /home/mark/trash/documents

I also tried this, just guessing:
sudo chown -R mark:mark /home/mark/.local/share/Trash/*

but it didn't do anything.

I tried, just to check, this:
 sudo rm -r

but it said: 
rm: missing operand
Try `rm --help' for more information.

And when I did "rm --help" it was way too technical for me.

But anyways, I'd rather not delete them if I can help it, some of them I want to keep and change. 

Could you give me some other idea please? thanks

---

### Post by drs305 on 2009-01-26
First some friendly but important advice: stop running commands until you are sure of the format. Some of the commands you are running can really mess up a system to the point of having to reinstall. So take your time and we will be glad to help you resolve this.

Is the trash you are trying to work with in /home/mark/.local/share/Trash/files ? That would be the standard place for trash. If you deleted them as root, they would be in /root/.local/share/Trash/files .Remember that everything in linux is case sensitive: cat is not the same as Cat, **d**ocuments is not the same as **D**ocuments. Are you trying to find missing items or do you see them in nautilus and just can't figure out the path to get there?

---

### Post by jadu on 2009-01-26
thanks for the advice-- I definitely don't know what I'm doing! So I could easily mess something up. Also thanks for the reminder about capital letters.

I tried
sudo chown -R mark:mark /root/.local/share/Trash/Documents

and also I tried the same with
/home/mark/.local/share/Trash/Documents

But in both cases, it said "no such file or directory"

I don't know where my trash is. I just see the little icon at the bottom panel. When I click on it and get file browser, it just says location: trash:///

When I go to nautilus (actually I don't really understand what nautilus is either, I just read to use it to fix this problem), I click on the trash but it says "The folder contents could not be displayed. Sorry, couldn't display all the contents of "trash": Operation not supported." 

How can I find out where my trash is kept? thanks

---

### Post by Cresho on 2009-01-27
ohh I.C.!

First off nautilus cannot do root stuff when run in user mode unless you sudo nautilus in terminal but you can easily damage stuff if you are not carefull on what you are clicking.  What you are trying to do is change the permission of your trash so you can view its content because of some "godlike" activity that changed it.  so you do this.....................

```
sudo chown -R mark:mark ~/.local/share/Trash/
```
and
```
sudo chmod -R 755 ~/.local/share/Trash/
```

Now you can view your trash!  but when ever you install stuff under sudo or "a.k.a. super user"  or drop files that are super user controlled, you don't have permission to delete the files.  This is why you ask as a super user kindly to delete stuff.

If you have doubt of your user permission of your filesystem, open nautilus a.k.a."filemanager" and right click on a folder->properties->permission.  It should say owner:mark folder Group:mark   etc etc etc.  "apply Permissions to enclosed files" only does the files but not the other folders or sub folders and files.  This is why those commands I gaved you are powerfull and I think they are safe.  755 in the chmod is secure to my understanding.

One last thing......  * or aka star means everything.  Everything in there gets changed folders and files and etc.  when you did the perms for ~/.local/share/Trash/*, you were telling it to do stuff in there as root but you did not tell it to fix perms for trash.....so try removing the /*  if not, try removing the /Trash/* from the command line and execute to change perms in the whole share directory.

---

### Post by Vaedrah on 2009-01-27
I have had the same problem when windows files are transferred to Ubuntu, deleted and then get stuck forever in a "trash loop". The syntax sequence I found (eventually) that seems to work (in all obstinate cases so far) is

Open terminal;
sudo rm -rfv/root/.local/share/Trash/*

press alt F2

Enter in terminal;
gksu nautilus

Press ctrl h

(shows hidden files)

find in Places/Computer .... etc where the Trash file is located
Mine was
/root/.local/share/Trash/

Now press shift-delete

This may seem excessive - I don't fully understand the procedure. Stubborn cases needed the full measure to "nuke the files", less problematic ones bowed out half way through.

I also had the same issue with stubborn files on a partition. Then I had to replace the syntax string (path?) with

/media/ACER/.Trash-1000/

I have minimal comprehension of Linux systems so I prefer exact syntax strings that accomplish a given task and perhaps comprehension evolves subsequently. Maybe the syntax strings I eventually found will be equally effective?

---

### Post by drs305 on 2009-01-27
> **jadu said:**
> But in both cases, it said "no such file or directory"

I don't know where my trash is. I just see the little icon at the bottom panel. When I click on it and get file browser, it just says location: trash:///

How can I find out where my trash is kept? thanks

I wrote a tutorial about finding and deleting Trash. It might provide some insight into the problems you are having:
[http://ubuntuforums.org/showthread.php?t=898573]("http://ubuntuforums.org/showthread.php?t=898573")

Here is a command you can use to find the location of the Trash folders you are looking for.

To find the location of all the Trash folders on your system:
```
sudo find / -type d -name *Trash* 
```

When you get results, highlight an entry, then CTRL-SHIFT-C to copy it to memory. On a new line in the terminal type *gksudo nautilus * (with a space after *nautilus*)  and hit the middle mouse button or CTRL-SHIFT-C, to produce a result such as:
```

gksudo nautilus /root/.local/share/Trash

```
You will see two folders - *info* and *files*. The deleted items are in the *files* folder. If you use "gksudo nautilus" to browse these files you should be able to delete or move them wherever you wish. Remember that you are running nautilus as 'root' so be careful what you delete.

---

### Post by jadu on 2009-01-27
Wonderful thanks! Cresho's most recent suggestion to me worked. Very grateful!

---

