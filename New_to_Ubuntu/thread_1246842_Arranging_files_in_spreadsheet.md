---
title: "Arranging files in spreadsheet"
date: 2009-08-22
forum: New to Ubuntu
---

### Post by L Campbell on 2009-08-22
I'm on a PC with 8.04 and have a collection of ' .dwg ' files that I want to arrange alphabetically in a spread sheet (unless you have a better suggestion as to how to arrange them).

My problem is that I have accumulated these files over several years, on several different computers and realize that many of them are duplicates.

Does the 'O. O.' spreadsheet program alert me to duplicates, or just stuff everything into the list?

TIA

---

### Post by gldearman on 2009-08-22
I don't know exactly what your final goal is, so this may be off-base.  My solution would be to identify and remove the duplicate files before creating the list.

I use a program called fastdup for tracking down duplicate files.  Sadly, fastdup is not in the Ubuntu repositories, so you will have to install it from source.  You can get the source code [here]("http://sourceforge.net/projects/fastdup/").  Fastdup can identify all of the duplicate .dwg files on your machine, so that you can delete the superfluous ones before creating your sorted list.

There is almost certainly a program in the repositories that does this same thing, and would be easier to install, but I don't know what program that would be.  Maybe someone else will reply with an answer.

Hope this helps.

---

### Post by gldearman on 2009-08-22
Or, you could follow the steps on [this page]("http://blogs.sun.com/oootnt/entry/removing_duplicate_rows_in_calc"), if you just want the names of duplicate files removed from your list, but don't want to delete the files themselves.

---

### Post by L Campbell on 2009-08-23
> **gldearman said:**
> Or, you could follow the steps on [this page]("http://blogs.sun.com/oootnt/entry/removing_duplicate_rows_in_calc"), if you just want the names of duplicate files removed from your list, but don't want to delete the files themselves.

Thanks for your helpful suggestions.

What I ended up doing was putting ALL (696) of the files into the OO word processor and using the 'find replace' to go through the file.

It turned out that there were 10 copies of most of the files.

Kind regards.

---

### Post by gldearman on 2009-08-23
Glad I could help.  Wanted to clarify one misstatement I had made earlier, in case anyone cares.

I use FSlint to find and eliminate duplicate files, not fastdup.  FSlint is in the repositories.  I tried both and thought that I had decided to stick with fastdup, but had actually decided to use FSlint.  I misremembered; sorry.

Also, there was an easier way to do that.  Assuming that duplicate files had duplicate names, and that all of your dwg files were in a single directory tree (for this example, your home directory or subdirectories within it), you could have opened a terminal window and typed the following command:

```
ls -R | grep -i dwg | sort -bdfi | uniq -u > list_of_dwg_files.txt
```

That command would have found all of the *.dwg files hiding anywhere in your home directory, even buried deep in subdirectories, sorted them alphabetically, removed the duplicates, and put the list in a convenient file called "list_of_dwg_files.txt"  All that from typing a one-line command. Easy and powerful; sorry it comes too late for you.

---

### Post by PGScooter on 2009-08-23
Hi gldearman,

I have a few comments:

> **gldearman said:**
> Glad I could help.  Wanted to clarify one misstatement I had made earlier, in case anyone cares.

I use FSlint to find and eliminate duplicate files, not fastdup.  FSlint is in the repositories.  I tried both and thought that I had decided to stick with fastdup, but had actually decided to use FSlint.  I misremembered; sorry.

It sounds like fastdup had some features that you would like in FSlint. The FSlint maintainer is very nice about accepting comments and suggestions. It would be great if you added some requests: 
[http://code.google.com/p/fslint/issues/list](http://code.google.com/p/fslint/issues/list)

> 
Also, there was an easier way to do that.  Assuming that duplicate files had duplicate names, and that all of your dwg files were in a single directory tree (for this example, your home directory or subdirectories within it), you could have opened a terminal window and typed the following command:

```
ls -R | grep -i dwg | sort -bdfi | uniq -u > list_of_dwg_files.txt
```

That command would have found all of the *.dwg files hiding anywhere in your home directory, even buried deep in subdirectories, sorted them alphabetically, removed the duplicates, and put the list in a convenient file called "list_of_dwg_files.txt"  All that from typing a one-line command. Easy and powerful; sorry it comes too late for you.
Don't mean to be picky, but grep -i dwg does not find only files of the format *.dwg. The i makes it case insensitive and the dwg can occur anywhere in the filename. I'm sure you know that, but I wanted to clarify for anyone who comes across this thread.

I did not know about the uniq command. Thanks!

---

### Post by gldearman on 2009-08-23
> **PGScooter said:**
> Don't mean to be picky, but grep -i dwg does not find only files of the format *.dwg. The i makes it case insensitive and the dwg can occur anywhere in the filename. I'm sure you know that, but I wanted to clarify for anyone who comes across this thread.]

Good point.  For *.dwg files, the way I did it might work, because "dwg" is a pretty unusual string, so it would be unlikely to come up except as that extension.  But, for other extensions, that isn't true; e.g. *.doc files.  So, a better way to do it would be to substitute:

```
grep -i '\.dwg$'
```

and that would truly search by extension.

Thanks for the info about FSlint.  I haven't really used it for long enough to know how much i like it or not.  Thus far, it seems pretty great except for the fact that it is abysmally slow.  But there isn't much that can be done about that -- abysmally slow is sort of the nature of the game when comparing that many files.

---

### Post by L Campbell on 2009-08-23
Thanks to both you and PGScooter for your continued interest.

I spent several hours today manually depleting my 696 files down to 175 and your suggestions look like they would enable me to do a MUCH faster job of this process.

Kind regards.

---

### Post by PGScooter on 2009-08-23
> **L Campbell said:**
> Thanks to both you and PGScooter for your continued interest.

I spent several hours today manually depleting my 696 files down to 175 and your suggestions look like they would enable me to do a MUCH faster job of this process.

Kind regards.

eh, sometimes doing it the manual way makes you feel better just because you know you didn't make a mistake whereas with the computer it's always scary if the command is off and does something you didn't want.

---

### Post by L Campbell on 2009-08-24
> **PGScooter said:**
> eh, sometimes doing it the manual way makes you feel better just because you know you didn't make a mistake whereas with the computer it's always scary if the command is off and does something you didn't want.

OK, I did a 'file search' (including my 4GB thumb drive and 30GB Iomega HDD) and came up with the 696 files again.

I then entered:- 

ls -R | grep -i '\.dwg$' | sort -bdfi | uniq -u > list_of_dwg_files.txt

into Terminal.

Here is what I got:-

qwer@qwer-desktop:~$ ls -R | grep -i '\.dwg$' | sort -bdfi | uniq -u > list_of_dwg_files.txt
qwer@qwer-desktop:~$ 
qwer@qwer-desktop:~$ 


OK, so I'm doing something wrong but what?       :-)

TIA.

---

### Post by gldearman on 2009-08-24
That looks like the expected output -- nothing.  But, a file called "list_of_dwg_files.txt" should have appeared in your home directory. That's where the output has gone.  You can open that file with the text editor just like any other text file (from the desktop, Applications > Accessories > Text Editor). It will contain each unique *.dwg filename on a separate line.

That command *won't* find files on your thumb drive, though.  It also won't find the files on your hard drive, *unless* they are in your home directory (or a subdirectory of home).  Sorry, I didn't know that any of these files were on a thumb drive.

To find those, and make sure the list is complete, make sure that all drives are mounted (i.e., that you can read information from all of them).  Then, run two commands:

```

cd /
```

followed by

```

ls -R | grep -i '\.dwg$' | sort -bdfi | uniq -u > list_of_dwg_files.txt
```

That will search the *entire filesystem*, including mounted drives like USB drives. It will probably take a while.
 
Although, if your goal is to eliminate duplicate files, at this point I would recommend FSlint.  You can download it with Synaptic Package Manager.  It compares files by their md5checksum -- it is impossible (or feasibly impossible) for two files to have the same md5checksum unless their contents are identical.  It will give you a sorted list of duplicate files, and you can just delete all but one instance of each. It will also be able to identify duplicate files even if they have different filenames.

Just be careful to double-check the output that FSlint gives you before you delete anything.

---

### Post by L Campbell on 2009-08-25
> **gldearman said:**
> That looks like the expected output -- nothing.  But, a file called "list_of_dwg_files.txt" should have appeared in your home directory. That's where the output has gone.  You can open that file with the text editor just like any other text file (from the desktop, Applications > Accessories > Text Editor). It will contain each unique *.dwg filename on a separate line.

That command *won't* find files on your thumb drive, though.  It also won't find the files on your hard drive, *unless* they are in your home directory (or a subdirectory of home).  Sorry, I didn't know that any of these files were on a thumb drive.

To find those, and make sure the list is complete, make sure that all drives are mounted (i.e., that you can read information from all of them).  Then, run two commands:

```

cd /
```

followed by

```

ls -R | grep -i '\.dwg$' | sort -bdfi | uniq -u > list_of_dwg_files.txt
```

That will search the *entire filesystem*, including mounted drives like USB drives. It will probably take a while.
 
Although, if your goal is to eliminate duplicate files, at this point I would recommend FSlint.  You can download it with Synaptic Package Manager.  It compares files by their md5checksum -- it is impossible (or feasibly impossible) for two files to have the same md5checksum unless their contents are identical.  It will give you a sorted list of duplicate files, and you can just delete all but one instance of each. It will also be able to identify duplicate files even if they have different filenames.

Just be careful to double-check the output that FSlint gives you before you delete anything.

Thanks again for the help.

I did reply earlier but I must have done something wrong, as my message is not here.

Anyway, I now have FSlint installed but do not see any 'help' files associated with it.  Is it supposed to be intuitive?

Kind regards.

---

### Post by gldearman on 2009-08-25
Oh, right.  I forgot that FSlint has no appreciable documentation.

Assuming you are using the FSlint GUI (there are command line options as well), it is *supposed* to be intuitive ... I mean, that's the point of GUIs.  But, without documentation, it can be kinda hard to figure out.

The top part of the FSlint window has two tabs.  When you run it, it should open to the "Search Path" tab.  There's a box on this tab that lists the directories to be searched.  Your home directory should be in the box already.  You can add other directories with the <+ Add> button.  Add your USB drive and whatever other drives, partitions, or directories you think might contain dwg files.

Next to that box is a check box that reads "recurse?"  It should be checked by default.  If checked, then FSlint will check all subdirectories (and subdirectories of subdirectories, etc.) in the search path as well as the directories listed.  So, you probably want it checked.

Switch the top part of the window to the "Advanced Search Parameters" tab.  This tab has two fields.  The first one lists directories to skip when searching -- by default, these are system directories, and you'll probably be OK leaving them skipped.

The second field is titled "Extra find parameters."  FSlint uses the find command to do its searching, so you can use this box to pass any parameters to the find command.  You should probably enter this into that box:

```
-iname "*.dwg"
```

That tells FSlint to look only for files that have the .dwg extension (no matter how the extension is capitalized).

The bottom part of the FSlint window has a big, white field with a list of options to the left.  The default option should be "Duplicates," which is what we want.  The big field is where your search results will appear.

Below that is the <Find> button.  Click that to start your search.  Then go make some popcorn or something, 'cause this will take a while.

When FSlint is done, it will report all the duplicate files it finds.  Each set of duplicates will be grouped together, and FSlint will tell you how many there are of each (e.g., 5 copies of the first file, 10 copies of the second).  I believe it automatically sorts the files from largest to smallest.

Look at each file FSlint reports.  If you are sure that everything listed in that list is a duplicate, you can delete them (just select the file you want to delete, and push the <Delete> button).  There is a merge option as well, and I've never used it.

Be very careful when deleting, of course.  Make sure that you know what it is you are deleting.

---

### Post by L Campbell on 2009-08-26
> **gldearman said:**
> Oh, right.  I forgot that FSlint has no appreciable documentation.

Assuming you are using the FSlint GUI (there are command line options as well), it is *supposed* to be intuitive ... I mean, that's the point of GUIs.  But, without documentation, it can be kinda hard to figure out.

The top part of the FSlint window has two tabs.  When you run it, it should open to the "Search Path" tab.  There's a box on this tab that lists the directories to be searched.  Your home directory should be in the box already.  You can add other directories with the <+ Add> button.  Add your USB drive and whatever other drives, partitions, or directories you think might contain dwg files.

Next to that box is a check box that reads "recurse?"  It should be checked by default.  If checked, then FSlint will check all subdirectories (and subdirectories of subdirectories, etc.) in the search path as well as the directories listed.  So, you probably want it checked.

Switch the top part of the window to the "Advanced Search Parameters" tab.  This tab has two fields.  The first one lists directories to skip when searching -- by default, these are system directories, and you'll probably be OK leaving them skipped.

The second field is titled "Extra find parameters."  FSlint uses the find command to do its searching, so you can use this box to pass any parameters to the find command.  You should probably enter this into that box:

```
-iname "*.dwg"
```

That tells FSlint to look only for files that have the .dwg extension (no matter how the extension is capitalized).

The bottom part of the FSlint window has a big, white field with a list of options to the left.  The default option should be "Duplicates," which is what we want.  The big field is where your search results will appear.

Below that is the <Find> button.  Click that to start your search.  Then go make some popcorn or something, 'cause this will take a while.

When FSlint is done, it will report all the duplicate files it finds.  Each set of duplicates will be grouped together, and FSlint will tell you how many there are of each (e.g., 5 copies of the first file, 10 copies of the second).  I believe it automatically sorts the files from largest to smallest.

Look at each file FSlint reports.  If you are sure that everything listed in that list is a duplicate, you can delete them (just select the file you want to delete, and push the <Delete> button).  There is a merge option as well, and I've never used it.

Be very careful when deleting, of course.  Make sure that you know what it is you are deleting.

Thanks, I appreciate it and hope to give it a 'try out' today.

Kind regards.

---

### Post by L Campbell on 2009-08-27
> **gldearman said:**
> Oh, right.  I forgot that FSlint has no appreciable documentation.

Assuming you are using the FSlint GUI (there are command line options as well), it is *supposed* to be intuitive ... I mean, that's the point of GUIs.  But, without documentation, it can be kinda hard to figure out.

The top part of the FSlint window has two tabs.  When you run it, it should open to the "Search Path" tab.  There's a box on this tab that lists the directories to be searched.  Your home directory should be in the box already.  You can add other directories with the <+ Add> button.  Add your USB drive and whatever other drives, partitions, or directories you think might contain dwg files.

Next to that box is a check box that reads "recurse?"  It should be checked by default.  If checked, then FSlint will check all subdirectories (and subdirectories of subdirectories, etc.) in the search path as well as the directories listed.  So, you probably want it checked.

Switch the top part of the window to the "Advanced Search Parameters" tab.  This tab has two fields.  The first one lists directories to skip when searching -- by default, these are system directories, and you'll probably be OK leaving them skipped.

The second field is titled "Extra find parameters."  FSlint uses the find command to do its searching, so you can use this box to pass any parameters to the find command.  You should probably enter this into that box:

```
-iname "*.dwg"
```

That tells FSlint to look only for files that have the .dwg extension (no matter how the extension is capitalized).

The bottom part of the FSlint window has a big, white field with a list of options to the left.  The default option should be "Duplicates," which is what we want.  The big field is where your search results will appear.

Below that is the <Find> button.  Click that to start your search.  Then go make some popcorn or something, 'cause this will take a while.

When FSlint is done, it will report all the duplicate files it finds.  Each set of duplicates will be grouped together, and FSlint will tell you how many there are of each (e.g., 5 copies of the first file, 10 copies of the second).  I believe it automatically sorts the files from largest to smallest.

Look at each file FSlint reports.  If you are sure that everything listed in that list is a duplicate, you can delete them (just select the file you want to delete, and push the <Delete> button).  There is a merge option as well, and I've never used it.

Be very careful when deleting, of course.  Make sure that you know what it is you are deleting.

I am appreciating what you have posted here more each time I read it.

At this point I still haven't 'made my move' because I just REALLY don't want to lose any of my .dwg files by making a dumb error, so I did some thinking and came up with an idea that I could put .dwg files from my XP 'puter onto a thumb drive and then have FSlint examine the thumb drive with my Ubuntu 'puter.

When I tried this I couldn't get FSlint to 'find' my thumb drive when I used the ' + ADD ' button.  Hopefully the attached screenshot will show this.

I realise that there is something that I am missing, not something wrong with the FSlint program.

Kind regards.

---

### Post by PGScooter on 2009-08-27
thumbdrive should be in the folder /media/thumbdrivename/ so click on the "." to go up a few directories and then go to media and find it. If you still can't find it, make sure your thumbdrive is plugged in and mounted and post the output of the command "mount". Or just open it up from your desktop and look at the location bar.

---

### Post by gldearman on 2009-08-27
Yep, what he said.  If your USB drive doesn't have a volume name, Ubuntu will assign it a generic one.  The first drive mounted, aside from the root filesytem, is usually /media/disk.  Then the next is /media/disk1, etc.  It doesn't matter whether these are internal or external drives, Ubuntu can name them the same way.

"../" will take you up a level.  So, if you start in your home directory (/home/qwer), hitting "../" once will take you to /home.  Hitting it again will take you to /.  From there, you can look for /media.

---

### Post by L Campbell on 2009-08-28
> **gldearman said:**
> Yep, what he said.  If your USB drive doesn't have a volume name, Ubuntu will assign it a generic one.  The first drive mounted, aside from the root filesytem, is usually /media/disk.  Then the next is /media/disk1, etc.  It doesn't matter whether these are internal or external drives, Ubuntu can name them the same way.

"../" will take you up a level.  So, if you start in your home directory (/home/qwer), hitting "../" once will take you to /home.  Hitting it again will take you to /.  From there, you can look for /media.

Many thanks again to you good people.  I feel like I took a leap forward today.    :-)

Now, if I understand things correctly, the files that I found today (see screenshot) should be the duplicates and, therefore, superfluous?

Kind regards.

---

### Post by PGScooter on 2009-08-28
hi again L Campbell,

If I were you, I would NOT delete all of those duplicates! You scanned your entire filesystem (every file you have, well.. every file you have permission to access). I can tell because of the "/" in the "path". A lot of those dups may be necessary. Restrict your search to your external hard drive, which once again should be under the media folder if you are lookin in the / tree. Does that make sense?

---

### Post by L Campbell on 2009-08-28
> **PGScooter said:**
> hi again L Campbell,

If I were you, I would NOT delete all of those duplicates! You scanned your entire filesystem (every file you have, well.. every file you have permission to access). I can tell because of the "/" in the "path". A lot of those dups may be necessary. Restrict your search to your external hard drive, which once again should be under the media folder if you are lookin in the / tree. Does that make sense?

OK, I'm still confused but feel like I'm making a little progress.

What I did was to copy my folder 'Clutch' from my folder 'Cad Krap' (which was on my thumb drive) to my Desktop, as it just has 17 .dwg files in it.  My thinking was that I could just explore that one folder but (if I'm beginning to 'catch on' a little bit) the program explored a whole string of other places before getting to 'Clutch'.

In case the screenshot is not clear to read, under 'Paths to exclude' it shows ' /Home/qwer/Desktop/Cad Krap/clutch ' and the program found 255 files, rather than the 17 I was hoping for.

Thanks for hanging in there with me on this, I appreciate it.

---

### Post by gldearman on 2009-08-28
In your first screenshot, you are showing lists of duplicates.  For example, you have 8 identical files called "Lewis clutch.dwg," *seven* of which are superfluous.  If you delete all 8, you won't have a copy left.  Similarly, you have 7 identical files called "True size clutch rev A.dwg." *Six* of those are superfluous.

You could use this search, just like you did in the first screenshot.  PWGScooter is right, you did search all of your system files.  But, aside from making the search take longer, this shouldn't cause you much danger as long as you observe three caveats:

[LIST=1]
[*]If you put the line ```
-iname "*.dwg"
``` in the "Extra find parameters" field, then all you found are *.dwg files.  Hopefully, none of your system files are *.dwg.
[*]I can see by all the "Permission denied" errors at the bottom of the screenshot that you did not run this search with root powers.  So, hopefully, you wouldn't have permission to delete any system files, anyway.
[*]Since the first 2 points are not guaranteed: ***only delete files that you recognize***.  If you don't look at a file and say, "I remember that.  It's a CAD file from such-and-such project," then just leave it be and don't delete it.
[/LIST]

But, a better way ...

In your second screenshot, you accidentally put the folder "/home/qwer/Desktop/CAD KRAP/clutch" in "Paths to exclude."  So, that folder was not searched!  The box to put it in was on the "Search Path" tab.

If you have moved everything from your USB drive to your Desktop, then you don't need to search beyond your home directory (/home/kwer), since your Desktop is a subdirectory of your home directory.  Since FSlint defaults to your home directory, you shouldn't have to change the search path at all!  Just remember to fill in the "Extra find parameters" and you are good to go.

---

### Post by L Campbell on 2009-08-28
> **gldearman said:**
> In your first screenshot, you are showing lists of duplicates.  For example, you have 8 identical files called "Lewis clutch.dwg," *seven* of which are superfluous.  If you delete all 8, you won't have a copy left.  Similarly, you have 7 identical files called "True size clutch rev A.dwg." *Six* of those are superfluous.

You could use this search, just like you did in the first screenshot.  PWGScooter is right, you did search all of your system files.  But, aside from making the search take longer, this shouldn't cause you much danger as long as you observe three caveats:

[LIST=1]
[*]If you put the line ```
-iname "*.dwg"
``` in the "Extra find parameters" field, then all you found are *.dwg files.  Hopefully, none of your system files are *.dwg.
[*]I can see by all the "Permission denied" errors at the bottom of the screenshot that you did not run this search with root powers.  So, hopefully, you wouldn't have permission to delete any system files, anyway.
[*]Since the first 2 points are not guaranteed: ***only delete files that you recognize***.  If you don't look at a file and say, "I remember that.  It's a CAD file from such-and-such project," then just leave it be and don't delete it.
[/LIST]

But, a better way ...

In your second screenshot, you accidentally put the folder "/home/qwer/Desktop/CAD KRAP/clutch" in "Paths to exclude."  So, that folder was not searched!  The box to put it in was on the "Search Path" tab.

If you have moved everything from your USB drive to your Desktop, then you don't need to search beyond your home directory (/home/kwer), since your Desktop is a subdirectory of your home directory.  Since FSlint defaults to your home directory, you shouldn't have to change the search path at all!  Just remember to fill in the "Extra find parameters" and you are good to go.

I want you to know that I appreciate the time and patience that you put into these replies.

This time I tried to compile a log/instruction sheet of what I did, as it might make it easier for you to see what (or, hopefully, if) I made some obvious errors:-  

 1  ) The first thing I did was to put  -iname &#8220;*.dwg&#8221; into the 'extra find parameters'.

 2  )  I clicked 'Search path' and got  /home/qwer  in the upper left box.

 3  ) Now I click ADD, get the 'Select Path' window and double click on DESKTOP.

 4  )  This brings up   ./    ../    CAD KRAP/    and      sunday clutch dwg

 5  )  I double click on   CAD KRAP/   then double click on    Clutch/

 6  )  Clutch/  is the folder I wanted to explore as it only has 17 .dwg files in it.

 7  )  I then click OK and see that I now have     /home/qwer/Desktop/CAD Krap/Clutch
        at the top of the 'Select Path' window.

 8  )  Also,    /home/qwer 
                     /home/qwer/Desktop/CAD Krap
                     /home/qwer/Desktop/CAD Krap/Clutch
        Appear in the top left 'search Path box.

 9  )  Convinced that I am now on the correct path, I now click  Duplicates, then Find.

 10 )  Again I get 270 files, not the 17 that I had hoped for.

 11 )  Looking at the files I see that they are in 122 groups, separated by lines of 'bytes wasted'.

 12 )  I click on the first lines of 'bytes wasted, attempting to 'select' it, then click 'delete' but the line
         doesn't disappear.  A little miffed, I now select the first .dwg file and click 'delete'.  I get the 
        pop- up,  'Are you sure you want to delete this?', I click YES and it's GONE.

Questions

A  )  Should I be able to zero in on individual folders?,Or is that just a waste of time?

B  )  Is there any benefit to being able to remove the lines of 'bytes wasted?'


Kind Regards.

---

### Post by gldearman on 2009-08-30
> **L Campbell said:**
> 
 8  )  Also,    /home/qwer 
                     /home/qwer/Desktop/CAD Krap
                     /home/qwer/Desktop/CAD Krap/Clutch
        Appear in the top left 'search Path box.

This is a redundant search.  If you have the "Recurse?" box checked (and it is checked by default), then your search will automatically include subdirectories and sub-subdirectories, to infinite depth.  So, by including "/home/qwer," you are also *automatically* including "/home/qwer/Desktop/CAD Krap" *and* "/home/qwer/Desktop/CAD Krap/Clutch."  Then, you include "/home/qwer/Desktop/CAD Krap," which was unnecessary, since that path was already automatically included.  That also automatically includes "/home/qwer/Desktop/CAD Krap/Clutch" *again*.  Then, you include "/home/qwer/Desktop/CAD Krap/Clutch" which is doubly unnecessary, since that was already automatically included *twice*.

Now, this shouldn't make a difference, since the program is probably smart enough to ignore redundancy.  And, at worst, this is making the search take longer, not returning false duplicates.  But, just so you know, the search you have in is identical to just searching "/home/qwer" by itself.

> **L Campbell said:**
> 
 10 )  Again I get 270 files, not the 17 that I had hoped for.

 11 )  Looking at the files I see that they are in 122 groups, separated by lines of 'bytes wasted'.


I'm not clear why you thought you would only want to return 17 files.  That should be the total number of *unique* dwg files you have.  But, you went into this knowing in advance that each file was duplicated more than once.  So, you must return way more than 17 results if you are searching for duplicates.

From the results FSlint is giving you, it looks like you have *122* unique files, not 17 as you expected.  I can't tell you why that is.  The total number of files, including redundant duplicates, is 270.

> **L Campbell said:**
> 
 12 )  I click on the first lines of 'bytes wasted, attempting to 'select' it, then click 'delete' but the line
         doesn't disappear.


This line is just a header.  It tells you how many copies you have of the largest unique file (the second "bytes wasted" line tells you how many copies you have of the second largest unique file, etc.).  The "bytes wasted"  line is the total file size of all but one of these duplicates.  So, if you have 8 copies of the first file, the bytes wasted total should be 7 times the file size.

> **L Campbell said:**
> 
  A little miffed, I now select the first .dwg file and click 'delete'.  I get the 
        pop- up,  'Are you sure you want to delete this?', I click YES and it's GONE.


That's exactly what it is supposed to do.  Just remember, these deletions are *permanent*.  *Don't delete* any file unless you **know exactly what it is**, and *don't delete* all of the copies of a file.

> **L Campbell said:**
> 
A )  Should I be able to zero in on individual folders?,Or is that just a waste of time?


This would be a waste of time, wouldn't it?  What are the odds that you have duplicate files in the same folder?  Besides, eliminating duplicate files within a folder leaves any duplicates of that file in other folders.


> **L Campbell said:**
> 
B  )  Is there any benefit to being able to remove the lines of 'bytes wasted?'


No.  Those are just headers in your report.  They don't represent a file that can be deleted.  Even if you could delete the line from the report, it would only serve to make the report more confusing.

---

