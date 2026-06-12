---
title: "Filename search within *.zip files"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by lkraemer on 2009-01-29
I am looking for a good way to search a multitude of zip files
on a hard drive for a specific file name.

Example:  I want to find CN-6655-5.dwg within all my *.zip files
stored on a server.  Also, I would like to be able to use CN-6655*.*
to find all versions of that drawing.

Any suggestions on software or a script to do that with Linux?

In the old days of DOS there was Supersonic Search Tool (SST.EXE)
but it has to be run from a Windows environment.

Thanks.

lkraemer

---

### Post by kaibob on 2009-01-29
I don't know about servers, but you can search ZIP files on a local hard drive with the zipinfo utility. For example, the following command will list all files in archive.zip that contain a particular string in their file name:

```
zipinfo archive.zip *string*
```

A simple command line or shell script can search multiple ZIP files. Have a look at the zipinfo man page to see all of the file-listing and search options available with zipinfo.

---

### Post by fubbleskag on 2009-01-29
[google says:](http://www.linuxforums.org/forum/linux-programming-scripting/121215-find-file-directory-tree-also-jar-zip-archives.html)
```

find . -name '*.zip' | while read file
do
  echo "[*] Listing coincidences into ${file}:"
  echo "==================="
  unzip -l "$file" | grep <whatever>
done

```

---

### Post by lkraemer on 2009-02-04
Thanks kaibob & fubbleskag,
I tried both and found a few problems using each.  I did get a script
to work, but I can't use Wildcards.  But that won't be a problem since
I know what the file name is, and I can just make a few extra searches
with the dfferent -? revisions.

Here is my script.

```

#!/bin/bash
# Proper header for a Bash script.
# sst <pattern> <path>
#	Search for pattern within zip files while recursively searching 
#	down a directory tree starting from the passed directory path.
#
# example: ./sst.sh teledisk.exe /home/larry/Downloads
#  Wildcards are not valid.....
#
# You may need to add the following test!
# Run as root, of course.
# Insert code here to print error message and exit if not root.
clear
echo
echo "sst <pattern> <path>"
echo "Search for pattern within all zip files while recursively searching"
echo "down a directory tree starting from the passed directory path."
echo
pattern=${1:?'usage: sst pattern path'}
path=${2:?'usage: sst pattern path'}
echo
echo "Script is searching for a pattern in all *.zip files in passed path....."
echo $path

#Variables are better than hard-coded values.
LOG_DIR=$path
cd $LOG_DIR

echo "Searching for ......" $pattern
echo

find . -name '*.zip' | while read file
do
  if unzip -l "$file" | grep -i $pattern
  then echo "[*] Listing coincidences into ${file}";
  echo "======================================================";
  fi
done

echo
echo "exiting the script."
echo

exit # The right and proper method of "exiting" from a script.

```

lkraemer

---

### Post by restofactor on 2011-03-28
> **lkraemer said:**
> Thanks kaibob & fubbleskag,
I tried both and found a few problems using each.  I did get a script
to work, but I can't use Wildcards.  But that won't be a problem since
I know what the file name is, and I can just make a few extra searches
with the dfferent -? revisions.

Here is my script.

```

#!/bin/bash
# Proper header for a Bash script.
# sst <pattern> <path>
#    Search for pattern within zip files while recursively searching 
#    down a directory tree starting from the passed directory path.
#
# example: ./sst.sh teledisk.exe /home/larry/Downloads
#  Wildcards are not valid.....
#
# You may need to add the following test!
# Run as root, of course.
# Insert code here to print error message and exit if not root.
clear
echo
echo "sst <pattern> <path>"
echo "Search for pattern within all zip files while recursively searching"
echo "down a directory tree starting from the passed directory path."
echo
pattern=${1:?'usage: sst pattern path'}
path=${2:?'usage: sst pattern path'}
echo
echo "Script is searching for a pattern in all *.zip files in passed path....."
echo $path

#Variables are better than hard-coded values.
LOG_DIR=$path
cd $LOG_DIR

echo "Searching for ......" $pattern
echo

find . -name '*.zip' | while read file
do
  if unzip -l "$file" | grep -i $pattern
  then echo "
[*] Listing coincidences into ${file}";
  echo "======================================================";
  fi
done

echo
echo "exiting the script."
echo

exit # The right and proper method of "exiting" from a script.

```lkraemer

Hi Lkraemer, 

I want to know whether I could post your script to another board as an example. I kind of want to do the same. See below;

[http://www.unix.com/shell-programming-scripting/156870-searching-string-pdf-files-inside-rar-zip-archives.html](http://www.unix.com/shell-programming-scripting/156870-searching-string-pdf-files-inside-rar-zip-archives.html)

---

### Post by lkraemer on 2011-03-28
restofactor,
Yes, you may post it to help/assist others, and THANKS for Asking.

THANKS Again.

Larry

---

### Post by lloyd_b on 2011-03-28
> **lkraemer said:**
> Thanks kaibob & fubbleskag,
I tried both and found a few problems using each.  I did get a script
to work, but I can't use Wildcards.  But that won't be a problem since
I know what the file name is, and I can just make a few extra searches
with the dfferent -? revisions.
The reason your wildcards aren't working is that 'grep' doesn't use standard shell wildcards (*.*), but regexes instead.

For the case of all files starting with CN-6655, use "CN-6655.*" for your search pattern instead.  Regexes are actually *way* more powerful than the shell wildcards, but it takes some time to learn how to use them.  If the "everything starting with ..." case is all you're worried about, then just sticking ".*" on the end of the search string is all you need to know.

Note: when entering this command, be sure to put the search regex in quotation marks - having the '*' outside of quotation marks will give you *very* weird results do to the shell trying to handle it, rather than passing it along to the script.

Lloyd B.

---

### Post by lkraemer on 2011-03-28
Lloyd,
Thanks for the tip on regular expressions.


```

#!/bin/bash
# Proper header for a Bash script.
# sst <pattern> <path>
#	Search for pattern within zip files while recursively searching 
#	down a directory tree starting from the passed directory path.
#
# examples: ./sst teledisk.exe /home/larry/Downloads
#  Wildcards are valid.....
# ./sst "CN-6655*" /home/larry
# ./sst "CN-66*" /home/larry
#
# You may need to add the following test!
# Run as root, of course.
# Insert code here to print error message and exit if not root.
clear
echo
echo "sst <pattern> <path>"
echo "Search for pattern within all zip files while recursively searching"
echo "down a directory tree starting from the passed directory path."
echo
pattern=${1:?'usage: sst pattern path'}
path=${2:?'usage: sst pattern path'}
echo
echo "Script is searching for a pattern or "pattern*" in all *.zip files in passed path....."
echo $path

#Variables are better than hard-coded values.
LOG_DIR=$path
cd $LOG_DIR

echo "Searching for ......" $pattern
echo

find . -name '*.zip' | while read file
do
  if unzip -l "$file" | grep -i $pattern
  then echo "[*] Listing coincidences into ${file}";
  echo "======================================================";
  fi
done

echo
echo "exiting the script."
echo

exit # The right and proper method of "exiting" from a script.

```

lkraemer

---

### Post by newbuntuxx on 2011-03-28
Wouldn't this do the job:

```
find / -iname "*\.zip" -exec zipinfo {} \; | grep -i "CN-6655-5*"
```

find /: start search at root
-i: case insensitive
name: file name
"*\.zip": file name, * refers to 0 or greater characters, \ escapes the . 
-exec: execute the following command on the found files
zipinfo: command to be executed
{}: place holder for all found files 

You can then grep for which expression/file name you want.

---

### Post by lloyd_b on 2011-03-28
Here's a tweaked version.  Whenever you use a variable that may contain shell special characters such as * (or a variable that may contain spaces), that variable should be enclosed in quotation marks.  

```
# examples: ./sst teledisk.exe /home/larry/Downloads
#  Wildcards are valid.....
# ./sst "CN-6655*" /home/larry
# ./sst "CN-66*" /home/larry
#
# You may need to add the following test!
# Run as root, of course.
# Insert code here to print error message and exit if not root.
clear
echo
echo "sst <pattern> <path>"
echo "Search for pattern within all zip files while recursively searching"
echo "down a directory tree starting from the passed directory path."
echo
pattern="${1:?'usage: sst pattern path'}"
path="${2:?'usage: sst pattern path'}"
echo
echo "Script is searching for a pattern or "pattern*" in all *.zip files in passed path -> $path"

#Variables are better than hard-coded values.
LOG_DIR="$path"
cd "$LOG_DIR"

echo "Searching for pattern \"$pattern\"" 
echo

find . -name '*.zip' | while read file
do
  if unzip -l "$file" | grep -i "$pattern"
  then echo "[*] Listing coincidences into ${file}";
  echo "======================================================";
  fi
done

echo
echo "exiting the script."
echo

exit # The right and proper method of "exiting" from a script.
```

Lloyd B.

---

### Post by newbuntuxx on 2011-03-28
Or you can use unzip -l:
```
find / -iname "*\.zip" -exec unzip -l {} \; | egrep -i "CN-6655-5\.dwg"
```

That will search root and sub dirs for all zip files, it will then search all of those zip files for a file named CN-6655-5.dwg

If you want to find versions of a specific file then use this:

```
find / -iname "*\.zip" -exec unzip -l {} \; | egrep -i "CN-6655-[0-9]\.dwg"
```

This will search root and sub dirs for all zipped files and then search those zipped files for all files that start with CN-6655- and end with .dwg and in between CN-6655- and .dwg, there is one number between 0 and 9.

If your version numbers span more than one digit, then you can do this

```
find / -iname "*\.zip" -exec unzip -l {} \; | egrep -i "CN-6655-[0-9]{1,2}\.dwg"
```

Where {1,2} means 1 or 2 times the previous character [0-9]. So, it will find these type of files:
CN-6655-5.dwg 
And
CN-6655-15.dwg

---

