---
title: "Help renaming files with too many periods"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by DavidVS on 2009-11-06
Hello again!

I need help with renaming files.  The context is trying to move the Audio Book of "Dr. No" to my MP3 player.

Extracting the files from the CDs yielded 146 files of the format:

**  Ian Fleming - 01.01-James Bond- Dr. No.mp3**

I'd like to use MP3Wrap but it's not working -- I'm guessing the plethora of periods in the filenames is causing the problem, and even if not I'd like simpler file names anyway.

How do I rename the files to instead look like

**  01-01-DrNo.mp3**

There must be an easy way for the terminal to do this, but I know so little Linux.

Thanks!

---

### Post by Old *ix Geek on 2009-11-06
> **DavidVS said:**
> Extracting the files from the CDs yielded 146 files of the format:

**  Ian Fleming - 01.01-James Bond- Dr. No.mp3**Please give a few more examples of the naming sequence.
> There must be an easy way for the terminal to do this, but I know so little Linux.There's ALWAYS a way at the *nix command line. :)

---

### Post by bodhi.zazen on 2009-11-06
for i in `ls`;do
 cat "$i" >> 01-01-DrNo.mp3
 rm -rf "$i"
done

This will make all 1 file.

If you need to keep all 146 files separate it will be more complex and i need to see more examples of how your files are named.

---

### Post by RedRat on 2009-11-06
Thunar the file manager has a neat file renaming feature. Click on all of the files you want to rename then right click and select Rename. There is a box that has a "Search and Replace" feature.  Make sure you also select "Name Only" to the right of the "Search and Replace". In the two boxes below enter what you want to search for, i.e., '.' and then the replacement, e.g., '_' or whatever you want. 

Thunar should be in Synaptic. Works quite well, I had a similar problem with some files.

---

### Post by 73ckn797 on 2009-11-06
> **RedRat said:**
> Thunar the file manager has a neat file renaming feature. Click on all of the files you want to rename then right click and select Rename. There is a box that has a "Search and Replace" feature.  Make sure you also select "Name Only" to the right of the "Search and Replace". Works quite well, I had a similar problem with some files.

This will be the simplest method. You can see what the name will be before making the change. You can designate a numerical sequence.

---

### Post by sisco311 on 2009-11-06
+1 for thunar.

other GUI renamer tools are:
[list]
[*]thunar (file manager)
[*]gprename (gtk)
[*]purrr (gtk)
[*]pyrenamer (gtk)
[*]gwenrename (qt)
[*]krename (qt)
[/list]

or:
```

cd /path/to/dir
for file in *.mp3; do f=${file%\.*}; **echo** mv "$file" "${f//./-}.mp3"; done
```

remove the **echo** command to actually rename the files.

---

### Post by wojox on 2009-11-06
```
rename 's/\.mp3$//' *.mp3
```

---

### Post by Old *ix Geek on 2009-11-06
> **sisco311 said:**
> ```

cd /path/to/dir
for file in *.mp3; do f=${file%\.*}; **echo** mv "$file" "${f//./-}.mp3"; done
```

remove the **echo** command to actually rename the files.That will not rename the files per the OP's needs, i.e., this: **Ian Fleming - 01.01-James Bond- Dr. No.mp3** needs to become this: **01-01-DrNo.mp3**.

Not only that, but it will also change the names of any other files [if they exist] in that directory with dots in their names, and the OP may not want that.

---

### Post by Old *ix Geek on 2009-11-06
> **wojox said:**
> ```
rename 's/\.mp3$//' *.mp3
```

See my reply to sisco311.

---

### Post by sisco311 on 2009-11-06
> **Old *ix Geek said:**
> That will not rename the files per the OP's needs, i.e., this: **Ian Fleming - 01.01-James Bond- Dr. No.mp3** needs to become this: **01-01-DrNo.mp3**.

Not only that, but it will also change the names of any other files [if they exist] in that directory with dots in their names, and the OP may not want that.

point taken. (oh, well any .mp3 file)

@OP mp3wrap works well (at least for me) with spaces, periods and/or special characters in the filename.

please post the error message you get from mp3wrap.

---

### Post by ghostdog74 on 2009-11-09
> **bodhi.zazen said:**
> for i in `ls`;do
 cat "$i" >> 01-01-DrNo.mp3
 rm -rf "$i"
done

This will make all 1 file.

If you need to keep all 146 files separate it will be more complex and i need to see more examples of how your files are named.
no need to use ls with back ticks. its prone to spaces in file names error
```

for i in *

```
anyway, to make into 1 file, there's even no need for a loop
```

cat * > onefile.mp3

```

---

### Post by ghostdog74 on 2009-11-09
> **DavidVS said:**
> Hello again!
Extracting the files from the CDs yielded 146 files of the format:

**  Ian Fleming - 01.01-James Bond- Dr. No.mp3**
...

How do I rename the files to instead look like

**  01-01-DrNo.mp3**



Assuming your files are always named this way, and you have Python 2.4+, you can use the script in my sig( called File Renamer)
usage:
```

$ ls -1
Ian Fleming - 01.01-James Bond- Dr. No.mp3
$ filerenamer.py -p "(.*?)\s*-\s*(.*?)\s*-\s*(.*?)-\s*(.*?)" -e "\2-\4" -l "*.mp3"
==>>>>  [ /home/Ian Fleming - 01.01-James Bond- Dr. No.mp3 ]==>[ /home/01.01-Dr. No.mp3 ]


```

remove the -l option to commit changes

---

### Post by DavidVS on 2009-11-23
Thunar was a great help.

MP3Wrap did not give any error messages.  I'm not sure the file name issue was a problem from MP3Wrap.  But the wrapped file didn't play right, so something went wrong.

---

### Post by DavidVS on 2009-12-02
Well, the renaming works great with Thunar.

But I still have problems using mp3wrap.  Almost half the time the resulting file is broken: it plays, but both my computer and mp3 player see it as only a few minutes long and pause/resume has problems.

No errors seem to be displayed by mp3wrap.  With the one example I checked, the time length from the first file became the incorrect time length of the wrapped file.

How do I fix this?

---

### Post by DavidVS on 2009-12-02
Ah, found the answer here and here:
 [http://lyncd.com/2009/02/how-to-merge-mp3-files/](http://lyncd.com/2009/02/how-to-merge-mp3-files/)
 [http://ubuntuforums.org/showpost.php?p=7787254&postcount=18](http://ubuntuforums.org/showpost.php?p=7787254&postcount=18)

Apparently, a know "feature" of mp3wrap is that it plays havoc with ID3 tags!

---

### Post by DavidVS on 2009-12-02
Hm.  The fixes I linked to in the previous post turn out to be incomplete.

Now the time for the wrapped file changes constantly as the file is played!

How do I fix this?

---

### Post by TunaCanTommy on 2010-01-03
I too work with audio books quite a lot. I solved the problem of multiple files getting merged by using a nice little ripper called "abcde" using the -1 option. Visit Andrew's Corner of the Web (search Google) to read up on how to use this great little tool. Wonderful for ripping audio-book CD's.

If I happen to get an audiobook with lots of small files in one folder, the first thing I do is open an ID3 tag tool and REMOVE all the tags, both ID3 v1 and ID3 v2. It's easy to add them later with the same tool.  After you've removed the tags then use:

```
cat *.mp3 > newfile.mp3
```

 . . . make sure you're in the directory where the files you want to join live when you execute the "cat" command. Or include all the directory detail in the command. You'll get a new .mp3 file in the directory with the new name you've chosen.

To join the small files into one big one - I usually have as many files as there are/were disks in the original set. When you join them using the "cat" command you can rename the file to any thing you want.  I usually use the name of the book and a "padded" disk number - ie; Dr.No.01.mp3 . . . Dr.No.12.mp3. This scheme works great in most MP3 players.

After you get all the files and names squared away you can use a ID3 tagger program to tag your files. I use "Audio Tag Tool".

---

