---
title: "nautilus issue"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by metallicamike on 2009-01-26
I am trying to free up some space and getting rid of unused application folders with nautilus and whenever i move them to trash it works, but does not show up. So when I try to open trash in nautilus, it says the operation is unsupported? I was wondering where these files might be and how I can delete them without having to use any command lines.

Thanks!

---

### Post by metallicamike on 2009-01-26
anyone?

---

### Post by metallicamike on 2009-01-26
bump

---

### Post by TheLions on 2009-01-26
open in nautilus or in terminal /home/username/local/Trash/ and delete files from "files" and "info"

---

### Post by Kellemora on 2009-01-26
Hi Lion

I have three files showing in my trash can!
Opening Trash shows the File as empty!

Also, there is NO folder named LOCAL under /home/user/, However, there is a HIDDEN folder named .local in /home/user/.local/Trash and all folders within that location are EMPTY..........

I've also checked the ROOT trash folders as well and they are EMPTY Also.

So in my case, I think it's just another glitch in the git along!

It would help if the Trash Icon HAD a Properties table with it!  But it don't!

TTUL
Gary

---

### Post by theozzlives on 2009-01-26
I deleted some BIG files as root in Nautilus and it put a .Trash in my /home folder. I didn't find it until I noticed a big part of my disk space gone. You might check there (or type ```
locate .Trash
``` at the command prompt).

---

### Post by metallicamike on 2009-01-26
ok, so how do i 'empty the trash' root folder? i would prefer not to use terminal, but if I have to...

---

### Post by Kellemora on 2009-01-26
Hi Ozz

My ROOT trash folder is LOADED with nearly everything I've deleted since September of 2008.  Even opening Nautilus from the Root Terminal, if you try to delete the files, they disappear for like 7 seconds then reappear with a digit longer filename.
Emptying Trash don't work either, even while in ROOT.......

Seems like I hit this on another machine and we found a workaround for this Bug, but that was when I was first starting and didn't make the proper notes, as I didn't know what things meant yet.

TTUL
Gary

---

### Post by Kellemora on 2009-01-27
Hi Mike

You can do it from Terminal

```
sudo rm -rfv /home/user/.local/share/Trash/*
```
or from Root Terminal in Root
```
rm -rfv /root/.local/share/Trash/*
```
But you won't see the trash can empty until you reboot.

I just remembered how to do it and did it on this machine, so it works just fine.  I ADDED the "v" behind -rf to make it verbose, that way you SEE what's being deleted.  I LIKE to see things doing what they do when they are working!

Seems like they would make emptying trash a little more easier!
After All, it is Just Trash!
Don't think it will mess up the Environment too much, hi hi...........

TTUL
Gary

---

