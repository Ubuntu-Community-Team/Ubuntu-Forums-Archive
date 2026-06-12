---
title: "Search for a word in multiple files at once"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by MockY on 2009-01-15
I have a directory where multiple folders reside along with hundreds of files. I would like to look for a phrase or a word in all those files at once to find the file that contain that word or phrase. How do I go about to do this?

grep -r "word" is supposed to work, but appears to be painfully slow and does not return any results.

---

### Post by HotShotDJ on 2009-01-15
I'm not sure if I'm understanding your question properly or not... but for searching files, I use tracker (Found in Applications --> Accessories).  If it is not installed, you can add it to your system using Applications --> Add/Remove...

---

### Post by Titan8990 on 2009-01-15
It usually does take a long time grep entire directories. If it comes across a file that can not be grepped, such as a binary executable, then it will typically lock up.

Look at the -d option for omitting files that may be executable. Never tried myself.


> I'm not sure if I'm understanding your question properly or not... but for searching files, I use tracker (Found in Applications --> Accessories). If it is not installed, you can add it to your system using Applications --> Add/Remove...


That GUI program is by no means as good as grep. Doesn't even accept regex!

---

### Post by lswest on 2009-01-15
do this:
```
cd /path/to/parent/folder/
grep -r -w "searchterm" *
``` it'll return the list of files that contain the searchterm and the line where the searchterm occurs.

The parent folder should be the folder containing the other directories you want to have searched (e.g. if the folders are in Music, that's where you should go).

*EDIT* I tested this in my scripts folder...full of executables, worked fine.

---

### Post by jonobr on 2009-01-15
Hello

You must have a whole lot of files.

If they are all in the one directory you could simply

grep string *
Finds all occurrences of some_string in all files in the current directory that you are in

grep -c string *
does the same but shows how many occurrences in each file rather than listing each one.

you can find in a directory by doing grep string /this/directory

you need to watch the string your finding also, and watch for special characters that may have meaning.

You can also redirect all results

cat *.txt | grep string > mystrinfile.txt

The -r switch you are using simply searches recursively.
Im thinking the reason why it may be slow is its looking in a lot of places it doesnt need to look.
So if you can specify exactly where you want to search, or copy those files you want to search to a certain directory.,that may be quicker.

Thanks

---

### Post by MockY on 2009-01-15
> **lswest said:**
> do this:
```
cd /path/to/parent/folder/
grep -r -w "searchterm" *
``` it'll return the list of files that contain the searchterm and the line where the searchterm occurs.

This worked perfectly. Returned a specific string in the blink of an eye.

Thank you so much.

jonobr - thank you for the information. It will come in handy in the future.

---

### Post by lswest on 2009-01-15
Glad I could help, I was surprised by the speed of the return myself (I played around with the grep command after reading your post to figure out the correct arguments and flags).

---

