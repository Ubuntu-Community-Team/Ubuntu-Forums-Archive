---
title: "What is the easiest way to purge data through the terminal?"
date: 2011-03-08
forum: New to Ubuntu
---

### Post by 007casper on 2011-03-08
I want to clean up one of my hard drives that has tremendous amount of dublicate photos, text files, documents etc scatterred around in different folders.

How can I purge the dublicate data and keep the largest file size and with the latest date? (there are text files that has the same name, however, some of them has more content)

thank you.

---

### Post by yeats on 2011-03-08
I would use fdupes:

```
sudo apt-get install fdupes
```

It's a straightforward command-line based program. To search a directory recursively:

```
fdupes -r /home/username/Pictures
```

for example.  It will prompt you each time it finds a duplicate file.

---

### Post by 007casper on 2011-03-10
I scaned the whole hard drive with fdupes command.  The hard drive is around 890gb.  

It grouped all the dublicates.  There are so many that it is hard to delete these files manually. And the terminal doesnt go up after a certain point.

What is the command to purge the dublicates and keep only one file.  I would like to keep the largest file size and also make sure it is the most recent date. 

Thank you.

---

### Post by 007casper on 2011-03-10
it took around 36 hours to scan 890gb hard drive through fdupes.  I dont know how to purge the data through the terminal.  

I was trying to find a manual, or a "how-to" guide and I came across FSlint.  It guess it is like fdupes.  I did couple test using FSlint, and it seems it only can detect exact duplicate.  It doesnt sort it as the most recent, and the largest size.

I am assuming most likely fdupes works the same way. 

Since I scan the whole hard drive with fdupes, I would like to finish this task with fdupes.  How can I delete the duplicates through the terminal. 

Thank you.

---

### Post by doas777 on 2011-03-10
well, what is the output of fdupes -h or fdupes --help?

---

### Post by 007casper on 2011-03-10
I found this link over here regarding fdupes
[http://www.ubuntugeek.com/how-to-find-duplicate-copies-of-files-using-fdupes-in-ubuntu.html](http://www.ubuntugeek.com/how-to-find-duplicate-copies-of-files-using-fdupes-in-ubuntu.html)

the two examples in that link doesnt make sense to me.
1) fdupes -r ./stuff > dupes.txt
2) fdupes -r /home/user > /home/user/duplicate.txt

fdupes -h gives me the following
> 
 -r --recurse     	for every directory given follow subdirectories
                  	encountered within
 -R --recurse:    	for each directory given after this option follow
                  	subdirectories encountered within
 -s --symlinks    	follow symlinks
 -H --hardlinks   	normally, when two or more files point to the same
                  	disk area they are treated as non-duplicates; this
                  	option will change this behavior
 -n --noempty     	exclude zero-length files from consideration
 -A --nohidden    	exclude hidden files from consideration
 -f --omitfirst   	omit the first file in each set of matches
 -1 --sameline    	list each set of matches on a single line
 -S --size        	show size of duplicate files
 -m --summarize   	summarize dupe information
 -q --quiet       	hide progress indicator
 -d --delete      	prompt user for files to preserve and delete all
                  	others; important: under particular circumstances,
                  	data may be lost when using this option together
                  	with -s or --symlinks, or when specifying a
                  	particular directory more than once; refer to the
                  	fdupes documentation for additional information
 -N --noprompt    	together with --delete, preserve the first file in
                  	each set of duplicates and delete the rest without
                  	without prompting the user
 -v --version     	display fdupes version
 -h --help        	display this help message



so after scanning the whole hard drive and looking at the help, and the example above.  I am thinking something like

> 
fdupes -d -N /media/harddrive/

would that be correct?

it would be nice if it ouput a log of the duplicate files, and deleted files.

Thank you.

---

### Post by 007casper on 2011-03-10
I did a test with a dummy folder
> 
fdupes -r /media/harddrive/dummyfolder
/media/harddrive/dummyfolder/a/test
/media/harddrive/dummyfolder/b/test

> 
fdupes -d -N /media/harddrive/dummyfolder 

it didnt work

then tried 
> 
fdupes -d /media/harddrive/dummyfolder

that didnt work either

---

### Post by doas777 on 2011-03-10
that sucks. as I read the help, that is the command sequence I would have thought would do it, though you may need -R to recurse into the sub directories a and b. 

what happens if you add -R  ?

---

### Post by 007casper on 2011-03-11
> fdupes -R -d -N /media/harddrive/dummyfolder
                                        
   [+] /media/harddrive/dummyfolder/a/test
   [-] /media/harddrive/dummyfolder/b/test

it gives you an option to delete one or the other.  Since I have a lot of them, I wanted to try without -N, and it worked.

> fdupes -R -d /media/harddrive/dummyfolder

it worked.  It deleted "test" in /media/harddrive/dummyfolder/b/

However, it left the b folder empty and didnt delete the folder.

I am wondering two things.  

1. How do you create if then statements?  Lets say there are four different duplicate folders as follows

/media/harddrive/dummyfolder/a/test
/media/harddrive/dummyfolder/b/test
/media/harddrive/dummyfolder/sort-it-d/non/test
/media/harddrive/dummyfolder/d/sort-non/test

and I wanted to write a command that indicates a specific duplicate folder to be deleted if it exist.  Lets say if the file is in any folder that has variation of the word "sort" then definitely delete those first, and then delete any other, and keep only one file.  What would be the command?


2. In addition, after you deleted the files, is it also possible to delete the empty folder?  How would you do that?
Because in the above dummy test, it deleted the "test" file but kept the b folder.

Thank you.

---

### Post by 007casper on 2011-03-11
trying to make sure certain duplicate folder gets deleted first, and then delete the emptied folders. I was also wondering if it is possible to write a command to skip hidden files.

I figure the command line needs if then statements. How would you create if then statements?  

Maybe it needs to be a shell script.  

Lets say there are four different duplicate folders as follows

/media/harddrive/dummyfolder/a/test
/media/harddrive/dummyfolder/b/test
/media/harddrive/dummyfolder/sort-it-d/non/test
/media/harddrive/dummyfolder/d/sort-non/test

fdupes -R -d if folder "sort" then "any" -purge "emptied" folder -skip "hidden" files /media/harddrive/dummyfolder

looking for something that would delete any folder that has the word "sort"
/media/harddrive/dummyfolder/sort-it-d/non/test
/media/harddrive/dummyfolder/d/sort-non/test

then lets say a random remaining folder
/media/harddrive/dummyfolder/b/test

then gets rid of the b folder

if there are hidden files, it skips those duplicates

and keep the last one that is not deleted
/media/harddrive/dummyfolder/a/test

What would be the proper command?
any ideas... thank you

---

### Post by yeats on 2011-03-11
> looking for something that would delete any folder that has the word "sort"

General information about finding and removing files:

[http://www.cyberciti.biz/faq/linux-unix-how-to-find-and-remove-files/](http://www.cyberciti.biz/faq/linux-unix-how-to-find-and-remove-files/)

You are definitely entering the realm of shell scripting, and I would recommend you do some Google searches for bash tutorials.  A particularly good one is the Advanced Bash Scripting guide:

[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

which is also in the repos if you want a local copy:

```
sudo apt-get install abs-guide
```

Hope that's helpful.

---

### Post by 007casper on 2011-03-13
I am not a coder.  I looked at various shell scripts, and try to come up with one by editing others.
I am not even sure how to go about it.

Even though, I would love to build a tool myself,  I dont necessarily want re-invent the wheel.  

FSlint might do the job.  It also deletes empty folders/directories.
However, I cant select a folder name "sort" delete those first. I would like to delete any folder
that has the name sort in any case format.  i.e. "Sort-it", "SORT", "sorted", "sort-2011" etc

FSlint has a select button.  The wildcard option doesnt seem to select a specific folder.
My luck it selects others, and seems to leave folders with the name sort.

[http://en.flossmanuals.net/FSlint/Duplicates](http://en.flossmanuals.net/FSlint/Duplicates)

 search in multiple directories but not their subdirectories
     findup -r /usr/bin /bin /usr/sbin /sbin
 search for duplicates in $PATH
     findup `/usr/share/fslint/fslint/supprt/getffp`

???

I really appreciate it

---

### Post by 007casper on 2011-03-13
I got something like this.  Can anyone improve on this?  Thank you.
```

#!/bin/bash
####################################
# delete backup files
# Find duplicates, select certain folders first, 
# fdupes -R -d if folder "sort" then "any" -purge "emptied" folder -skip "hidden" files
# 
####################################

# size of the window:
WIDTH="400"
HEIGHT="400"

# set this to FALSE if you don't want to auto-select the files
CHECK="TRUE"

# text displayed :)
TEXT="Select files..."

# find duplicates recursive, -A excludes hidden files
fdupes -r -A /media/harddrive/

#any folder that has variation of the word "sort" delete those first
findup -d '/media/harddrive/sort*'
#find /sort -exec rm -f {} \;
#find / -name sort -exec rm -f {} \;

#delete duplicates (replace harddrive to yours), -A excludes hidden files
fdupes -R -A -d /media/harddrive/

#Print to log
mkdir duplicate-log /home/user/
dest="/home/user/duplicate-log"
date
echo

# Print end status message.
echo
echo "duplicates deleted"
date

exit 0
```

---

### Post by RayArdia on 2011-10-01
> **yeats said:**
> I would use fdupes:

```
sudo apt-get install fdupes
```

It's a straightforward command-line based program. To search a directory recursively:

```
fdupes -r /home/username/Pictures
```

for example.  It will prompt you each time it finds a duplicate file.

Having failed to make any sense of fslint, krusader and kleansweep I decide to give this a try.
My photos are in /home/ray/Photos with folders for each year, subfolders for months and sub-sub folders for days.
I know that there are lots of duplicates, for example in /home/ray/Photos/2010/01/10.
When I try to navigate to this sub-sub folder I get:-

ray@ray-laptop:~$ fdupes -r /home/ray/Photos/2010/01/10
ray@ray-laptop:~$ 
ie no output at all, what am I doing wrong:(:confused:

---

