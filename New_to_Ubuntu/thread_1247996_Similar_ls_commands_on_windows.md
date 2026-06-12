---
title: "Similar ls commands on windows ?"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by ubfu on 2009-08-23
As I know ubuntu have a list command directory and files and save it as text 
example:

ls -l -R /media/disk/ > ~/Desktop/C_drive.txt

So is there any similar ls command on window xp ? I remember there's a dos like command on window x typing it at command prompt.

Sorry to ask here , I really can't remember it for windows.
Thank you for reading.

---

### Post by BinaryFeast on 2009-08-23
```
dir
``` is what you are loocking for. I suggest you read the help file in CMD for future reference (type "help" I think).

---

### Post by slakkie on 2009-08-23
[http://gnuwin32.sourceforge.net/](http://gnuwin32.sourceforge.net/)

---

### Post by porchrat on 2009-08-23
dir has quite a few options if I recall correctly, but I don't know if it as useful as 'ls'.

Stuff like "dir /p" is pretty much a slightly lamer version of "ls | more".

Also "dir /w" displays the directory contents in a wide form.

I must admit I have forgotten most of the other options, it has been a while since I used that prompt for anything other than pinging.

---

### Post by oldos2er on 2009-08-23
IIRC, I used to run **dir /n /o /p /v**. But like slakkie suggested, there are *nix tools (e.g. bash) available for DOS/Win.

---

### Post by ubfu on 2009-08-24
```
Displays a list of files and subdirectories in a directory.



DIR [drive:][path][filename] [/A[[:]attributes]] [/B] [/C] [/D] [/L] [/N]

  [/O[[:]sortorder]] [/P] [/Q] [/S] [/T[[:]timefield]] [/W] [/X] [/4]



  [drive:][path][filename]

              Specifies drive, directory, and/or files to list.



  /A          Displays files with specified attributes.

  attributes   D  Directories                R  Read-only files

               H  Hidden files               A  Files ready for archiving

               S  System files               -  Prefix meaning not

  /B          Uses bare format (no heading information or summary).

  /C          Display the thousand separator in file sizes.  This is the

              default.  Use /-C to disable display of separator.

  /D          Same as wide but files are list sorted by column.

  /L          Uses lowercase.

  /N          New long list format where filenames are on the far right.

  /O          List by files in sorted order.

  sortorder    N  By name (alphabetic)       S  By size (smallest first)

               E  By extension (alphabetic)  D  By date/time (oldest first)

               G  Group directories first    -  Prefix to reverse order

  /P          Pauses after each screenful of information.

  /Q          Display the owner of the file.

  /S          Displays files in specified directory and all subdirectories.

  /T          Controls which time field displayed or used for sorting

  timefield   C  Creation

              A  Last Access

              W  Last Written

  /W          Uses wide list format.

  /X          This displays the short names generated for non-8dot3 file

              names.  The format is that of /N with the short name inserted

              before the long name. If no short name is present, blanks are

              displayed in its place.

  /4          Displays four-digit years



Switches may be preset in the DIRCMD environment variable.  Override

preset switches by prefixing any switch with - (hyphen)--for example, /-W.

```

I tried using dir /TC /A- > C_drive_test.txt it works.
But I can't display both results of date timeframe.I wanted it to display Date Cration C , date Modified W, date Access A .All together.
And there's no size like [ls -h, --human-readable] 4kb 1mb.

Anyone can guide me through ? Thank you again :)

---

### Post by porchrat on 2009-08-24
> **ubfu said:**
> I tried using dir /TC /A- > C_drive_test.txt it works.
But I can't display both results of date timeframe.I wanted it to display Date Cration C , date Modified W, date Access A .All together.
And there's no size like [ls -h, --human-readable] 4kb 1mb.

Anyone can guide me through ? Thank you again :)

As was recommended previously, you can get 'ls' working under windows.

If I recall correctly you can add a few binaries to the windows install and just direct the prompt's opening command to them as additional libraries or something. There are guides out there and it relatively simple. Though the method suggested by slakkie looks a lot cleaner, but I wasn't aware that you could do it like that. Basically these sort of things put UNIX terminal commands into the windows prompt quite easily. It was one of the first things I did when I started using bash.

IMO that is the ideal answer. It also won't deactivate any of your current prompt commands.

---

### Post by ubfu on 2009-08-25
> **porchrat said:**
> As was recommended previously, you can get 'ls' working under windows.

If I recall correctly you can add a few binaries to the windows install and just direct the prompt's opening command to them as additional libraries or something. There are guides out there and it relatively simple. Though the method suggested by slakkie looks a lot cleaner, but I wasn't aware that you could do it like that. Basically these sort of things put UNIX terminal commands into the windows prompt quite easily. It was one of the first things I did when I started using bash.

IMO that is the ideal answer. It also won't deactivate any of your current prompt commands.

Besides ,I wanted to ask , how to save it as unicode ? I have some other language character other than language.
How do I do that ?

---

### Post by benj1 on 2009-08-25
are you wanting something thats cross platform ?

in that case something like 

os.listdir()
from python might be better

---

### Post by ubfu on 2009-08-25
> **benj1 said:**
> are you wanting something thats cross platform ?

in that case something like 

os.listdir()
from python might be better

As above , using ubuntu I can't view files sorting with date created which is the biggest draw back on ubuntu.I had a lot of doc files daily updated and modified.Once I wanted to check date created , I had to switch back window xp to view them.It's very troublesome.

That's why I wanted to generate a textfile which print out the date of doc list created.

(I found a away typing cmd /u on command prompt will change it to unicode) Still can't list out date created+modifed+access at a single output

---

### Post by benj1 on 2009-08-25
i dont think linux actually keeps data on file creation times, just modification.
'ls -t'
will give you modification time, but theres no point installing it on windows because a creation date option probably wont be there.

1 idea might be to find an app that can extract the date from the document itself (i assume it would hold it internally), perhaps antiword ?

---

