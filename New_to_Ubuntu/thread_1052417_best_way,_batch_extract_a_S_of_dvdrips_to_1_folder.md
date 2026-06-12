---
title: "best way, batch extract a S of dvdrips to 1 folder? plus other question"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by mishkin on 2009-01-27
What's the best way to batch extract a series of folders (1 episode in each) of .rar 's 

a cli command?
a small script (please supply?)?
a little app?

In windows I used extractit or extractnow I can't remember it had lots of options but basically you droped a folder on it and hit go and it extracted all archives within the folder structure

it had options to extract  it to a location but also inside a folder that contained the folder name that the rars were in

this is useful because sometimes movies and to a lesser extent tv are named not well enough once they are extracted (or have subs with them)
 
Anyway any suggestions welcome just gettnig a bit tired  ef doing it manually I've done about 75 episodes of show "24" so far and about that many more to extract.

thx

---

### Post by Monicker on 2009-01-27
> **mishkin said:**
> What's the best way to batch extract a series of folders (1 episode in each) of .rar 's 

a cli command?
a small script (please supply?)?
a little app?

In windows I used extractit or extractnow I can't remember it had lots of options but basically you droped a folder on it and hit go and it extracted all archives within the folder structure

it had options to extract  it to a location but also inside a folder that contained the folder name that the rars were in

this is useful because sometimes movies and to a lesser extent tv are named not well enough once they are extracted (or have subs with them)
 
Anyway any suggestions welcome just gettnig a bit tired  ef doing it manually I've done about 75 episodes of show "24" so far and about that many more to extract.

thx



This has been covered before, by myself and others.  A search of this and the General Help forum should turn up several results.

*Edit: Found some of my earlier posts which should get you going in the right direction.*

[http://ubuntuforums.org/showthread.php?t=793154&highlight=extract+script](http://ubuntuforums.org/showthread.php?t=793154&highlight=extract+script)

[http://ubuntuforums.org/showthread.php?t=791467&highlight=unzip](http://ubuntuforums.org/showthread.php?t=791467&highlight=unzip)

Also take a look at the find command in conjunction with xargs.

---

### Post by mishkin on 2009-01-27
those links wern't very helpsful.. must be a simple way of doing it

---

### Post by mishkin on 2009-01-27
I think gnome is using "unrar" to unrar stuff... this makes searching for an answer very difficult as the program name is the action itself...

info on the program is 

> 
UNRAR 3.80 beta 2 freeware      Copyright (c) 1993-2008 Alexander Roshal

Usage:     unrar <command> -<switch 1> -<switch N> <archive> <files...>
               <@listfiles...> <path_to_extract\>

<Commands>
  e             Extract files to current directory
  l[t,b]        List archive [technical, bare]
  p             Print file to stdout
  t             Test archive files
  v[t,b]        Verbosely list archive [technical,bare]
  x             Extract files with full path

<Switches>
  -             Stop switches scanning
  ad            Append archive name to destination path
  ap<path>      Set path inside archive
  c-            Disable comments show
  cfg-          Disable read configuration
  cl            Convert names to lower case
  cu            Convert names to upper case
  dh            Open shared files
  ep            Exclude paths from names
  ep3           Expand paths to full including the drive letter
  f             Freshen files
  id[c,d,p,q]   Disable messages
  ierr          Send all messages to stderr
  inul          Disable all messages
  kb            Keep broken extracted files
  n<file>       Include only specified file
  n@            Read file names to include from stdin
  n@<list>      Include files in specified list file
  o[+|-]        Set the overwrite mode
  or            Rename files automatically
  ow            Save or restore file owner and group
  p[password]   Set password
  p-            Do not query password
  r             Recurse subdirectories
  sl<size>      Process files with size less than specified
  sm<size>      Process files with size more than specified
  ta<date>      Process files modified after <date> in YYYYMMDDHHMMSS format
  tb<date>      Process files modified before <date> in YYYYMMDDHHMMSS format
  tn<time>      Process files newer than <time>
  to<time>      Process files older than <time>
  ts<m,c,a>[N]  Save or restore file time (modification, creation, access)
  u             Update files
  v             List all volumes
  ver[n]        File version control
  vp            Pause before each volume
  x<file>       Exclude specified file
  x@            Read file names to exclude from stdin
  x@<list>      Exclude files in specified list file
  y             Assume Yes on all queries


---

### Post by mishkin on 2009-01-27
I found this using google

>  

#!/bin/bash
for i in $(find $(pwd) -name '*.rar')
do
cd $(dirname $i)
unrar e $i
done


I saved it to my desktop as a txt file and chmod +x it, then I pasted a copy in the season 4 dir and navigated to it in terminal then did ./script (this is the filename i saved it as)

and now it appears to be batch extracting (to where I dunno yet)

---

### Post by mishkin on 2009-01-27
it extracted each movie into it's folder that contained the rars

how could i mod the above script to extract them all to a specific location

ie /home/mishkin/Desktop/24/

Obviously I could manually change the extract location in the script and then pop it in the right place before executing it


As for the 10 or so it already extracted I'll move them manually since I can't even figure out how to make the script instead of finding and unraring just finding avi and moving :(

no coding expert here... just did visual basic in high school 5-6 year ago lol!!!

---

### Post by happ0sai on 2009-07-31
check out this site for a simple script which seems to fit your needs completely:

[http://nogui.wordpress.com/2009/07/31/bulk-unrar-script-perfect-for-rapidshare-users/](http://nogui.wordpress.com/2009/07/31/bulk-unrar-script-perfect-for-rapidshare-users/)

it asks you for the file path, accepts a password if there is one, and then unrars ALL files within that directory (nice)  =)

---

