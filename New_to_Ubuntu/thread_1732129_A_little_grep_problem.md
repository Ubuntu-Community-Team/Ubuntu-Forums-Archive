---
title: "A little grep problem"
date: 2011-04-17
forum: New to Ubuntu
---

### Post by CaptainMark on 2011-04-17
Im making a script containing a few rsync commands and im trying to manipulate the out put to show all files that would be deleted but not hidden files, ive used ```
echo "Processing files to delete:"
rsync -avn --delete $source/ $destination/ |grep deleting |grep -Fv /.
```so far ive used rsync in verbosive mode to display all output, pipe the results through "grep deleting" to display only lines referring to deletion operations and ive piped the results further through "grep -Fv /." to remove lines that refer to hidden files and folders, the propblem is hidden files that are in the home directory still show because they dont contain '/.' 
Here is the output i have right now:```
deleting .local/share/gvfs-metadata/home-b661d6e3.log
deleting Documents/scripts/new file

```i need to add another pipe to grep to remove lines starting in "deleting ." so the only remaining output in this example is the line referring to the file "Documents/scripts/new file"
i tried this ```
rsync -avn --delete $source/ $destination/ |grep deleting |grep -Fv /. | grep -v "^deleting ."
```but that removes both of these lines and prints no results, i dont know what to do as i dont understand many regular expressions yet, 

Thanks for any help
Mark

---

### Post by sweetleaf on 2011-04-17
In regex, "." matches any single character. To match a literal period, you need to escape it. Try grep -v "^deleting \."

---

### Post by Vaphell on 2011-04-17
you could do it in single grep
```
grep -Ev '^deleting (.*/)?[.]'
```
.*/ is optional because of ?, so the expression finds both [COLOR="Blue"]something/.[/COLOR]name and [COLOR="Blue"].[/COLOR]name

---

### Post by CaptainMark on 2011-04-18
Thank you, great tips ill definitely remember those, i thought I had the ^ in the wrong place

---

