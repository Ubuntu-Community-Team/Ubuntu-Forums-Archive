---
title: "[SOLVED] need help writing script to auto-unrar and rename"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by jmd9qs on 2008-12-23
hi,

i downloaded a lot of files that are .rar'ed... they are sorted alphabetically in directories (A, B, C, etc...). since there are so many files i've gotten tired of unraring each subdirectory and then changing the filename from 'example rar' to 'example' (and i accidentally typed mv A* *)... i don't know what happened to all those files but i can't find them. is there anyone willing to help me figure out how to write a script for this? i am a total noob when it comes to bash scripting, and any help would be appreciated. 

also, what happened to my stuff when i typed:
```

mv A* *
```

????

---

### Post by cmnorton on 2008-12-23
You might have more luck putting this post in [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39), but as to the mv command you posted.

I believe most *nix implementations do not expand wildcards on the target as you might expect. Enter ls -l \** to see if you have any files starting with the wildcard character.

Edit:
-----------------------------

Can you make a small directory list subset showing this environment's configuration. I am having difficulty imagining it.

---

### Post by jamesrl on 2008-12-23
It all depends on how your setup was arranged.  Bash takes
mv A* * and interprets it as if you typed:

Pretend you had five files/directory in your current directory when you typed the command, called: Aa Ab Ac B C.  Bash expands the wildcards * to be

mv A* * to be equivalent to:

mv Aa Ab Ac Aa Ab Ac B C

(all the files that begin with A*, and then all the files in the directory).
The mv command shouldn't do anything, unless the last name (C in my case) refers to a directory, and then everything gets moved into that.

EDIT: Well, unless there were just two files present and neither of them began with A, and then the first file would overwrite the second.  As in if the files were just B C, then mv A* * becomes mv B C (as A* matches nothing, and * matches B C), so B overwrites C.  Also if you had any files in directory C with the same name as the files you moved, they probably got overwritten as well.

---

### Post by jamesrl on 2008-12-23
What you may have been trying to do, is say change all files
A.rar B.rar C.rar into files A B C.
You can accomplish that quickly with the rename command (type man rename).

E.g.,
```
rename -n 's/\.rar$//' *.rar  ## Removes .rar end of all file names with .rar
```
and if you want to do it the other way:
```
rename -n 's/$/.rar/' * ## Adds .rar to end of all file/dir names
```
would do the trick mentioned above.  (Try first with the -n, to test what it would do, and then repeat command without the -n and it will actually rename everything.)

EDIT: The $ represents the end of the filename.  s is just telling what kind of replacement to do (see man sed).  So basically what it does is searches the file name for the stuff between the first slashes (e.g. in first example: \.rar where the . is backslashed as . means one character wildcard), and replaces it with what is betweeen second set of slashes (nothing in the first case).  [Instead of s/orig-str/replaced-str/  you can also do y/A-Z/a-z/  which would say replace all uppercase letters with lowercase letters or y/ABC/123/ which would replace all capital A B C with 123.

---

### Post by Sarmacid on 2008-12-23
You'll need to adjust the unrar command, I'm not familiar with it. Just put this in the folder of the files you need to unrar```
#! /bin/sh

for file in `ls` ; do
        if [ ./$file != $0 ] ; then
                [COLOR="Red"]unrar $file[/COLOR]
        fi
done

```

---

### Post by jmd9qs on 2008-12-23
thank you all for your help....


jamesrl: the problem is that the filename isnt set up like that. the subdirectories for 'A' are, say, 'example rar' and contain 'example.rar'. what i want to do is unrar 'example.rar' in its current location, delete the now unneeded .rar file, and then rename 'example rar' to 'example', with no whitespace at all. i don't know how to set up a wildcard situation where there is whitespace in front of the name in question..

---

### Post by jamesrl on 2008-12-24
I'm not particularly familiar with rar (just use gzip/gunzip (LZ77) for everything).  
You should be able to run the script sarmacid gave (provided the command unrar example.rar will uncompress example.rar), and then afterwards do the rename I gave above.  If the files are named "example1 rar", "example2 rar", etc. and you want to rename them to "example1" "example2" the following command should do the trick.

```

computer:~/tmp$ touch example1\ rar example2\ rar
computer:~/tmp$ ls
example1 rar example2 rar
computer:~/tmp$ rename -n 's/\ rar$//' *
example1 rar renamed as example1
example2 rar renamed as example2

```

[Take off the -n argument when you want it to actually rename rather than perform no action.]  The space character is typed in, by prefacing with a backslash to escape it.  The touch command is used to create (0 byte) files with the proper names.  Removing the rar file should also be quite straightforward 'rm *.rar' once you have ensured everything has been properly unrar'd.

---

