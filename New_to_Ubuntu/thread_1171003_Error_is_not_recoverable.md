---
title: "Error is not recoverable"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by shadowlands on 2009-05-26
Can someone help me with this? Thanks in advance.

torchwood@torchwood-laptop:~$ sudo tar -xzvf hellanzb-0.9.tar.gz
[sudo] password for torchwood: 
tar: hellanzb-0.9.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
torchwood@torchwood-la

---

### Post by pastalavista on 2009-05-26
I'm guessing you either spelled something wrong or you're in the wrong directory.. of course I'm probably wrong because you don't supply me very much information. Maybe it's just a bad tarball...

---

### Post by Drate on 2009-05-27
The error indicates that the file doesn't exist, so check your spelling or check that you are in the same directory as the file.

"ls"  or "dir" will give you a directory listing.  "cd" will help you change directories.  "cd .." will change to the previous (parent) directory.

---

### Post by Metallion on 2009-05-27
Another thing i'd suggest is hitting tab after typing the first letters of hellanzb-0.9.tar.gz. It will autocomplete for you and thus make sure that you have the correct filename.

If there's an incomplete file name or nothing happens after pressing tab, it means that there's more than one possibility. Hit tab twice in rapid succession to see all options.

---

### Post by halitech on 2009-05-27
just a question, why are you using sudo to extract the file in your home folder?

---

### Post by shadowlands on 2009-05-28
I saw it on a board I think I was just following the directions.Is there a better way to do this? If so. please tell me. > **halitech said:**
> just a question, why are you using sudo to extract the file in your home folder?

---

### Post by cariboo on 2009-05-28
If the file is on your desktop, why not just double-click and let file-roller extract it for you.

---

### Post by halitech on 2009-05-28
> **shadowlands said:**
> I saw it on a board I think I was just following the directions.Is there a better way to do this? If so. please tell me.

either just use the tar command without sudo or as cariboo907 says, double click it or right click - extract to here. The only time you need sudo is if you are doing something outside your home folder.

---

### Post by shadowlands on 2009-05-28
Thanks, as you can tell I am clueless.  U guys are great!!! Thanks.

---

### Post by shadowlands on 2009-05-28
After I extract it.. a folder appears on my desk top.  Did i complete the task of installing the program correctly?

---

### Post by halitech on 2009-05-28
no, that means you've extracted it, now you need to use the terminal to enter that directory and run the command you were trying to run earlier.

---

### Post by shadowlands on 2009-05-29
Thanks

---

### Post by paul_anders on 2009-05-29
but the million dollar question remains
why does the system generate an error
i tried to recreate a similar situation here and i get no errors

soundquake@sq-dt:~$ sudo tar -xzvf to-sort-out.tar.gz
to sort out/
to sort out/xorg.conf
to sort out/howto.txt
to sort out/the illuminati.txt
to sort out/tunein-station(2).pls
to sort out/trrp -gmail account.png
to sort out/tunein-station.pls
to sort out/phone
to sort out/links.txt
to sort out/as.dog
to sort out/sql for ebyta.txt
to sort out/sql for ebytar
to sort out/Jordan Maxwell - Matrix of Power
to sort out/xorg.conf.backup
to sort out/ORIGxorg.conf.backup
to sort out/Firefox_wallpaper.png
to sort out/nvid.run
soundquake@sq-dt:~$

so in reality the problem that the user posed to the forum 
has not been dealt with. hence the user has a problem still outstanding that will raise its ugly head again in the future

PA

---

### Post by 3rdalbum on 2009-05-29
> **paul_anders said:**
> but the million dollar question remains
why does the system generate an error.
so in reality the problem that the user posed to the forum 
has not been dealt with. hence the user has a problem still outstanding that will raise its ugly head again in the future

PA

The file has a different name to what was typed, or is located in a different directory. That was the answer given earlier in the thread. The easiest answer is to use File Roller to extract the file, which was the method followed.

---

