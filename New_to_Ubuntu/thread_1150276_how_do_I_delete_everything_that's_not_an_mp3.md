---
title: "how do I delete everything that's not an mp3?"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by querent on 2009-05-05
I got a nice discography collection, but i want to strip out all the jpg's and m3u's and such.  don't know what all's in there , and don't want to look.  I want to run a recursive rm (or something) that'll delete all files (not folders) that don't end in ".mp3" anywhere in the discography's little sub-folder tree.

Is there an easy way?  Many thanks in advance.

---

### Post by Don1500 on 2009-05-05
Goto the folder with the programs you want to delete
Select LIST VIEW on the upper right
sort by type
select the files you don't want and send them to the trash
(or select all the MP3s and move them)

---

### Post by kaibob on 2009-05-05
The following will do what you want: 

```
find /target/directory ! -iname '*.mp3' -type f -exec /bin/rm -f '{}' \;
```

I would be hesitant to use this command because it deletes every file in the target directory and subdirectories that is not an MP3 file. One mistake and your computer doesn't work. If you do decide to use this command, I would recommend that you first run the following command, which echoes the files that will be deleted to the terminal window. Then, if all appears well, you can remove the echo command to actually delete the files. 

```
find /target/directory ! -iname '*.mp3' -type f -exec echo /bin/rm -f '{}' \; 
```

---

### Post by querent on 2009-05-05
Excellent!  Many thanks!  I'll be careful.

---

### Post by kaibob on 2009-05-06
> **querent said:**
> Excellent!  Many thanks!  I'll be careful.
Please note that I changed -name to -iname in the command. This makes the search case insensitive and retains both file.mp3 and file.MP3.

---

### Post by querent on 2009-05-06
Right.  I'm in the man pages now trying to figure out what I'll be doing.

Thanks for the lead.  :)

---

### Post by llamabr on 2009-05-06
for a safer, less technical route, copy everything that's mp3 into another directory, rm everything that's left, and move your mp3's out.

Though, looking briefly, the exec command above will work.

---

### Post by querent on 2009-05-06
And it worked!  Many thanks again.

Took me a while to get that the "!" in there was what was keeping it from deleting only my mp3's.

Problems are where you learn.  Thanks, friend!

---

### Post by andrew.46 on 2009-05-06
Hi kaibob,

> **kaibob said:**
> If you do decide to use this command, I would recommend that you first run the following command, which echoes the files that will be deleted to the terminal window. Then, if all appears well, you can remove the echo command to actually delete the files. 

```
find /target/directory ! -iname '*.mp3' -type f -exec echo /bin/rm -f '{}' \; 
```

Always best to be cautious :-). A variation of the above could be:

```
find /directory ! -iname '*.mp3' -type f -ok rm {} \;
```

Andrew

---

