---
title: "Multithread from command line"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by alanwalterthomas on 2009-01-20
I'm curious to know how I might make better use of my 2 CPU cores. I understand that most applications don't make use of multithreading but I've found that when I give my computer a list of tasks at once, only one core is used. For example, I want to decompress a set of bz2 files. If I select them all from the GUI & say extract here, they decompress one by one. However, if I select some & extract, then select the rest & extract while the first bunch is extracting, both cores work at 100%. How could I get several (probably all in the same folder, but I'd be interested in knowing how to make it work in different locations at the same time with a single command) files to extract making full use of 2 or more cores from the command line? I'm aware of "&&" and ";" but don't those just make the second operation follow after executing the first? Also, how could I get a bunch of files with similar names to extract? I found that "tar -xjvf *tar* to extract all files in the directory with a tar in the name didn't work right.

Thanks for the education,

---

### Post by mister_pink on 2009-01-20
To send a process into the background you end the line with a single &

I guess it wouldn't be too hard to write a script that would do this.... In fact this does them all at once, and the computer should automatically distribute them between the cores:
```

for file in `ls -1 | egrep .tar.gz$`; do tar -xzf $file & done;

```

Or obviously change it for .tar.bz2 to:
```

for file in `ls -1 | egrep .tar.bz2$`; do tar -xjf $file & done;

```

---

### Post by mcduck on 2009-01-20
You'd have to run instances of tar, one to extract half of the files and other extract the other half.

For two files it would go like this:
```
tar -xjvf file1.tar.bz2&
tar -xjvf file2.tar.bz2
```
The first tar command would run in the background, allowing you to start second tar before the first has finished. Since you now have 2 separate programs running they can both use their own CPU core.

How to do the same with a directory full of randomly named files is another question.. But I suppose you could simply run as many tar instances at the same time as you have files. You'd get quite a lot of tar instances running at once but at least they'd effectively use every core you have available..
```
for f in *.tar.bz2; do tar -xjvf "$f"&; done
```
I wouldn't suggest doing that with hundreds of files, though.. ;)

---

### Post by sankarv on 2009-01-20
adding to that... you can write a C program with pthreads and use exec/system function inside to invoke the commands and run the compiled binary of the program, that will surely account for multithreading....., you can check if some options are existing inside there for selecting processors....

however as far as i know all processes will on one processor... this is an expected behaviour.....

---

### Post by alanwalterthomas on 2009-01-20
I'm just beginning to learn the basics of bash scripting (forget C for now). Will the code you wrote work for several files that have a name that contains "file", or just a file name "file"?
Also, would someone please explain 

Code:

for f in *.tar.bz2; do tar -xjvf "$f"&; done

as in, what does the "f" in "for f" represent? Is it for "file" like in the script above? And what does "$f"&; done" mean broken up?
Finally, if I download in one folder, then want to extract the contents to another, would I just add something like ~/alan/Games to the end of the command line?
Thanks,

---

### Post by mcduck on 2009-01-20
the "f" or "file" is just a variable. You can use almost any letter or word here as long as it has no special meanings in Linux

```
for f in *.tar.bz2
```
means something along "for each file fitting the rule *something*.tar.bz2", and the name of the file currently being processed is stored in variable called "f" (which is later referenced by "$f".

```
do tar -xjvf "$f"&
```
The next part tells what to do to these files; run "tar -xjvf" for file (name stored in variable $f). I put the $f inside quote marks as this solves the problems if there are spaces in file names. The "&" in the end tells that this command should be run in the background, allowing the script to continue to next step before this command has finished.

```
done
```
This simply tells that this ends the loop. The script returns to start, takes next file, stores it's name in $f and runs the tar command, and so on as long as there are files left.

the same command could be written in a bit more clear way:
```
for f in *.tar.bz2;
  do tar -xjvf "$f"&;
done
```

---

