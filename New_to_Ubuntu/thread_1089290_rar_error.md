---
title: "rar error"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by patchido on 2009-03-06
i am traying to unzip a file taht is 4 files large no password .rar and i get this error



```
Write error in the file /home/patricio/Desktop/TW.2008-Pathfinder.part1/Twilight[2008]DvDrip-aXXo/Twilight[2008]DvDrip-aXXo.avi [R]etry, [A]bort 
```

any idea? i dont think the file is currupted

---

### Post by Roanoke on 2009-03-07
What command did you use?

---

### Post by patchido on 2009-03-07
no command, just extract here GUI

---

### Post by Roanoke on 2009-03-07
Do it through a terminal.
ALT+F2
Type in 'terminal'
Type 'cd <insert directory here>'
Type
```

unrar -e <insert filename here>

```
And tell me what it says after you hit enter.

---

### Post by patchido on 2009-03-07
gives me all this

```
patricio@patricio-laptop:~/Desktop$ unrar -e TW.2008-Pathfinder.part1

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
patricio@patricio-laptop:~/Desktop$ 

```

---

### Post by patchido on 2009-03-07
gives me all this

```
patricio@patricio-laptop:~/Desktop$ unrar -e TW.2008-Pathfinder.part1

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
patricio@patricio-laptop:~/Desktop$ 

```

---

### Post by patchido on 2009-03-07
double post srry


wow it was triple srry bad connection

---

### Post by 2hot6ft2 on 2009-03-07
That just doesn't look right. I haven't seen aXXo use rar files like that and sure enough that looks to me like it's just an avi file you're trying to unrar.

Is the size "Twilight[2008]DvDrip-aXXo.avi	701.4 MB"?
Does this look familiar? [http://isohunt.com/torrent_details/69193113/Twilight%5B2008%5DDvDrip-aXXo?tab=summary](http://isohunt.com/torrent_details/69193113/Twilight%5B2008%5DDvDrip-aXXo?tab=summary)
aXXo makes some good rips although if you look here [http://isohunt.com/torrents/?ihq=Twilight[2008]DvDrip-aXXo](http://isohunt.com/torrents/?ihq=Twilight[2008]DvDrip-aXXo) you'll notice 2 that are kinda off looking.

Personally I think it's really an avi. Right click on it and select properties and change the extension to .avi if it's not already and try opening it. You can always change it back if I'm wrong.

Assuming of course that you have the codecs installed to play avi files.

Might be a good idea to remove the []'s from around 2008 too.

---

### Post by Roanoke on 2009-03-07
Ooooh, sorry. Add './' to the end of the command I told you to execute and hit enter again.

---

### Post by polkadotteapot on 2009-07-28
Any further advice, I get the same error off one off my .rar files and can't get it to unrar or play on anything?

---

