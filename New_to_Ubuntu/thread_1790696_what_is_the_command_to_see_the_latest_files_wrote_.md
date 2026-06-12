---
title: "what is the command to see the latest files wrote to disk?"
date: 2011-06-25
forum: New to Ubuntu
---

### Post by s1baker on 2011-06-25
Is there a command or script that will tell you the files that were wrote to the file system, hidden or unhidden, within the last user supplied time frame?
 Other words, if one wanted to see all and any files wrote in the last 24 hours, or last 3 days etc., is there a terminal command or script that would do that ?

thanks

---

### Post by s1baker on 2011-06-25
and also, any files that have been modified, like with a new date for the file.

---

### Post by Impute on 2011-06-25
For all files in your home directory modified in the last hour:
find ~ -type f -mmin -60

You can also use the same command to find all files or directories modified more than a year ago:
find / -mtime +365

If you're just looking at one directory then you can sort by modification time using:
ls -lt

---

### Post by s1baker on 2011-06-25
How would you check the system directories that are hidden and unhidden, where you need to use sudo?

---

### Post by Impute on 2011-06-26
For just hidden files, which have a "." at the start of the name of the file, or any of the directories:

```
find ~ -xdev -type f -mmin -10 | grep -F '/.'
```

For just unhidden files:

```
find ~ -xdev -type f -mmin -10 | grep -F -v '/.'
```

Most of the time you shouldn't need sudo, since you can usually read most of the system file, but if you really want to search everything:

```
sudo find / -xdev -type f -mmin -10 | grep -F '/.'
```




To explain that a bit more...

Just to be safe I added the "-xdev" option which tells "find" to skip other filesystems so it won't go off searching some network share by mistake (e.g. through the /mnt or ~/.gvfs directory).

There are several ways to find just hidden files, but I think the easiest one is to take to output from "find" and feed it into "grep". The "|" character is called a pipe if you want to search for other examples of using it.

Grep (which stands for "get regular expression and print") is very powerful because it can specify almost any pattern of characters to search for, but to do this a lot of characters have special meanings so it can also be confusing to use at times. I used the "-F" option to tell it to ignore all the special characters and just search for a substring. In this case "/."

The "-v" option tells grep to print only lines that don't match the pattern.

---

### Post by s1baker on 2011-06-27
wow, I just did a 'man find' in the terminal, and there is 37 pages there of instructions on how to use this one command. Everything in there but the launch codes for launching an ICBM on an Ohio class nuclear sub.

---

