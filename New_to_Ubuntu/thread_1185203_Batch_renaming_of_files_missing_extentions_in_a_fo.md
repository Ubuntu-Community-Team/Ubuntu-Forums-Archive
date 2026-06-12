---
title: "Batch renaming of files missing extentions in a folder with different filetypes"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by tinge on 2009-06-12
Here's the problem:
I have a folder with many (several thousand) images or mixed type (jpg, png, gif, etc.), many of the jpg's don't have a file extension.  I'd like to run a batch conversion to add ".jpg" to the end of the extension-less files.

Ie: I'd liek to convert this:

001.jpg
02eert
htt7.png
7uu78.gif
trreet

to this:

001.jpg
02eert.jpg
htt7.png
7uu78.gif
trreet.jpg

I've been trying to sort this out using mv or pyRenamer, as they seem to be the solutions to most people with similar problems, but I haven't had any luck.  I just don't have enough experience with reg-expressions to get it right.  Does anyone have any suggestions?  Any help would be greatly appreciated.

---

### Post by lloyd_b on 2009-06-12
Here's a very simple shell script to do the job.  Note: it will rename ANY file without an extension to .jpg.  With some further trickery, it's possible to tweak it so that it determines the file type, and selects the appropriate extension...
```
#!/bin/bash

# Select all files in current directory, and process one at a time
for FILE in *; do
    # Strip of any extension, and save to FILE2
    FILE2=${FILE%\.*}
  
    # If it's the same afterward, then there was no extension - rename it
    if [ "$FILE" = "$FILE2" ]; then
        mv "$FILE" "$FILE.jpg"
    fi
done
```

Hope this helps.

Lloyd B.

---

### Post by tinge on 2009-06-12
Thanks a million Lloyd, That worked great!

looks like learning a little bash will go a long way in automation and batch processing, and may become my new best friend... :- )

---

### Post by ghostdog74 on 2009-06-15
> **lloyd_b said:**
> 
```

....
    # Strip of any extension, and save to FILE2
    FILE2=${FILE%\.*}

done
```

what if file name is like this eg "htsd.fglj" which actually is not jpg? its better to check the file name actually does not contain ".jpg" at the back.
```

 ${file%.jpg}

```

---

### Post by lloyd_b on 2009-06-15
> **ghostdog74 said:**
> what if file name is like this eg "htsd.fglj" which actually is not jpg? its better to check the file name actually does not contain ".jpg" at the back.
```

 ${file%.jpg}

```

If you read the original post, you'll see that he's got a mix of JPGs, PNGs, GIFs, etc, all in the same directory.  That solution would wind up sticking a ".jpg" on the end of them...

Lloyd B.

---

### Post by Gen2ly on 2009-06-15
does the find command have the ability to check mime type?

---

### Post by lloyd_b on 2009-06-15
> **Dirk.R.Gently said:**
> does the find command have the ability to check mime type?

Nope.  Not too surprising - the find command does not look at the *contents* of files in any way, just the metadata...

If it were necessary to actually determine the file type (not an issue with the OP's requirements), I'd just modify the script so that instead of using the extension (or lack thereof), it would pass each file through the "file" command, getting the mime-type that way, and then use that to determine if the file has an appropriate extension, changing it if necessary.

At any rate, as far as I can tell this issue is *solved* as far as the OP is concerned.  So I don't see any reason to spend any time on it...

Lloyd B.

---

### Post by acreech on 2010-06-22
Thanks Lloyd this was a great program. I altered it a little to add a help section to help you know how to right the command to execute it. 

the only issue if I have 2 files file "1" and file "1.jpg". When it renames "1" it will overwrite "1.jpg"

How do I add a command that checks for this problem and then adds a unique identifier, such as a 1_1.jpg? Then I would have files 1_1.jpg and 1.jpg

```
#!/bin/bash
program () {
     filetype="$1"
# Select all files in current directory, and process one at a time
for FILE in *; do
    # Strip of any extension, and save to FILE2
    FILE2=${FILE%\.*}
  
    # If it's the same afterward, then there was no extension - rename it
    if [ "$FILE" = "$FILE2" ]; then
        mv "$FILE" "$FILE.jpg"
    fi
done
exit 0
}

case $1 in
    --help)   echo;echo;echo "Usage: noext.sh filetype i.e. noext.sh JPG changes all files with no extension to a .JPG";echo;echo;echo
    ;;
    -h)   echo;echo;echo "Usage: noext.sh filetype i.e. noext.sh JPG changes all files with no extension to a .JPG";echo;echo;echo
    ;;
    *) program $1
    ;;
esac    
```


thanks
acreech

---

### Post by acreech on 2010-06-23
bump

---

### Post by kaibob on 2010-06-23
> **acreech said:**
> the only issue if I have 2 files file "1" and file "1.jpg". When it renames "1" it will overwrite "1.jpg"

I think you only have to check if the file exists, as in the following:

```
for file in * ; do
  file1="${file%.*}"
  if [ "$file" = "$file1" ] ; then
    if [ -f "${file}.jpg" ] ; then
      file1="${file}_1"
    fi
    mv "$file" "${file1}.jpg"
  fi
done
```

A test run:

> $ ls -1
1
1.jpg
file 2
file 2.jpg
file.png

$ testscript

$ ls -1
1_1.jpg
1.jpg
file 2_1.jpg
file 2.jpg
file.png


BTW, for the above to work, all files in the target directory without extensions have to be JPEG's. This was stated to be the case in the original post. Otherwise, as previously mentioned, you would have to check the file type of all files without extensions. This could be done with the file utility or similar. Also, the mv command has a backup option which could be used as an alternative.

---

### Post by sweetleaf on 2011-02-27
> **kaibob said:**
> I think you only have to check if the file exists, as in the following:

```
for file in * ; do
  file1="${file%.*}"
  if [ "$file" = "$file1" ] ; then
    [COLOR="Red"]if [ -f "${file}.jpg" ] ; then
      file1="${file}_1"
    fi[/COLOR]
    mv "$file" "${file1}.jpg"
  fi
done
```

If both asdf and asdf.jpg exist, the code above would will prevent asdf.jpg from being overwritten. However, if asdf_1.jpg ALSO already exists, it WILL be overwritten. So it's safer to use a while loop:

```

#!/bin/bash
program () {
    FILETYPE="$1"
# Select all files in current directory, and process one at a time
for FILE in *; do
    # Strip of any extension, and save to FILE1
    FILE1=${FILE%\.*}
  
    # If it's the same afterward, then there was no extension - rename it
    if [ "$FILE1" = "$FILE" ]; then
	[COLOR="Red"]while [ -f "${FILE1}.${FILETYPE}" ] ; do
	    FILE1="${FILE1}_1"
	done[/COLOR]
        mv "$FILE" "$FILE1.$FILETYPE"
    fi
done
exit 0
}

case $1 in
    --help)   echo;echo;echo "Usage: noext.sh filetype i.e. noext.sh JPG changes all files with no extension to a .JPG";echo;echo;echo
    ;;
    -h)   echo;echo;echo "Usage: noext.sh filetype i.e. noext.sh JPG changes all files with no extension to a .JPG";echo;echo;echo
    ;;
    *) program $1
    ;;
esac
```

---

