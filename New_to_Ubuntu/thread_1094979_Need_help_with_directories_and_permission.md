---
title: "Need help with directories and permission"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by mvalviar on 2009-03-13
I want to change the permission of all the files in a directory to 644 and leave permission of all the directory contained therein to 744 (so I can still cd to them). What commands should I use. Thank you.

Tried to google this question but I can't find any relevant answer.

---

### Post by SunnyRabbiera on 2009-03-13
Sudo should help.

---

### Post by mvalviar on 2009-03-13
If I run "sudo chmod -R 644 directory" all files and folders under "directory"  will be 644. If directory doesn't have execute permission I can't cd to it. If I run "sudo chmod -R 744 directory" all files and folders under "directory" will be 744. Meaning everytime I double click on files gnome will tell me that the file is an executable and will ask me if I want to run or display its contents which is annoying.

---

### Post by BDNiner on 2009-03-13
What errors do you get when trying to CD to a directory with permissions set to 644? I guess i don't understand what your problem is.

---

### Post by mcla0203 on 2009-03-13
Why not make a simple script..?

This is a csh script.  If you dont' have CSH, i.e. if the command "which csh" doesn't return anything, then install CSH by typing "sudo apt-get install csh"


Something like this will probably work.  If you have issues and need more permission, then put sudo infront of the chmod.
```

#!/bin/csh
set input = your_input_directory
foreach var ( `find $input` )
  if( -d "$var" ) then ##If it is a directory
   chmod 744 $var      ##change permissions to 744
  else
   chmod 644 $var      ##If it is not a directory, change permissions to 644
  endif
end
```

---

### Post by mvalviar on 2009-03-13
Permission denied. If your using the terminal cding to a directory without execute permission returns permission denied. With nautilus it simply shows an empty folder even if it has contents.

---

### Post by mcla0203 on 2009-03-13
> **mvalviar said:**
> Permission denied. If your using the terminal cding to a directory without execute permission returns permission denied. With nautilus it simply shows an empty folder even if it has contents.

Then you need to do it depth first starting at the leaf nodes.  I mean any folder without sub folders should be chmoded after all of the files in that folder have been chmoded.  Does this make sense?  That way you don't need to cd into a directory with 644 permissions.

---

### Post by mcla0203 on 2009-03-13
i.e. don't do it like this:
```
% chmod 644 test1
% chmod 644 test1/test1
chmod: cannot access `test1/test1': Permission denied
```

do it like this:
```
% chmod 644 test1/test1
% chmod 644 test1
```

---

### Post by mvalviar on 2009-03-13
Is there an automated way of doing it? It will take sometime if I have a large directory. Like a chmod -R that will skip folders?

---

### Post by KayakJim on 2009-03-13
The following should do the trick for you.
```

find . -type f -exec chmod 0644 {} \;

```

The above command finds all files starting from your current directory and applies the "chmod 0644" command to them. The "-type f" option specifies only files so directories are skipped.

---

### Post by mcla0203 on 2009-03-13
> **mvalviar said:**
>  Like a chmod -R that will skip folders?

You could just switch the directories chmod command to something irrelevant that won't change the permissions of the directories.  i.e. :

```

#!/bin/csh
set input = your_input_directory
foreach var ( `find $input` )
  if( -d "$var" ) then ##If it is a directory
   **echo "blah"         ##don't change directory permissions**
  else
   chmod 644 $var      ##If it is not a directory, change permissions to 644
  endif
end

```

For dealing with the chmod on the directories... I'm not really sure of a quick and dirty solution.  It seems like it might require more thought, but I'm sure it could be done somehow.

---

### Post by mvalviar on 2009-03-13
> **KayakJim said:**
> The following should do the trick for you.
```

find . -type f -exec chmod 0644 {} \;

```

The above command finds all files starting from your current directory and applies the "chmod 0644" command to them. The "-type f" option specifies only files so directories are skipped.

Eureka! Thanks. That's exactly what I was looking for. I didn't now how to use find but I the back of my mind I thought this is possible with one line in the terminal. Thanks y'all!

(How come I can't mark this as solved under thread tools?)

---

### Post by carml on 2009-03-13
The "mark as solved" tool is momentarily unavaible,someone in the  forum suggested to rename the thead title so there's the word "Solved".:)

---

### Post by Eldera on 2009-03-13
One can also tag the thread "solved" as per post:
[post]4527051[/post]
Have a good day, Eldera

---

