---
title: "Finding Files In Ubuntu?"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by TAspr on 2011-05-29
Why can't I find a particular file?  I did a search for *.jpg files, so I would bring up everything .jpg, and the location that I knew would have files did not come up with anything.  I already tried the "Ctrl F".  Pic is attached.

Any ideas?

---

### Post by ohadcn on 2011-05-29
don't search regular expressions, search for jpg or .jpg (i checked, it's work)

---

### Post by KL_72_TR on 2011-05-29
Use the commands [find] and [locate].

---

### Post by konsolelover on 2011-05-29
y don't u just try
locate    command it works great... :)

---

### Post by TAspr on 2011-05-29
It does work great, but how do find duplicate files?

---

### Post by TAspr on 2011-05-29
> **KL_72_TR said:**
> Use the commands [find] and [locate].


And how do you do this?  I just went to the location of the files and did a search within the directory.  So, how do you do this?

---

### Post by KL_72_TR on 2011-05-29
> **TAspr said:**
> It does work great, but how do find duplicate files?
[http://manpages.ubuntu.com/manpages/karmic/man1/fdupes.1.html](http://manpages.ubuntu.com/manpages/karmic/man1/fdupes.1.html)

---

### Post by KL_72_TR on 2011-05-29
> **TAspr said:**
> And how do you do this?  I just went to the location of the files and did a search within the directory.  So, how do you do this?
Use the [locate] command better. This command has a file database, that must be updated if you want the most of the command.
> sudo updatedb
than simply 
> locate filename

---

### Post by m_duck on 2011-05-29
> **KL_72_TR said:**
> This command has a file database, that must be updated if you want the most of the command.
Depending on how recent the files you want to find are. It is (or at least used to be) the case that updatedb is run as an hourly cron job so the database *should* always be pretty much up to date.

---

### Post by TAspr on 2011-05-29
> **m_duck said:**
> Depending on how recent the files you want to find are. It is (or at least used to be) the case that updatedb is run as an hourly cron job so the database *should* always be pretty much up to date.

So you don't have to do anything for the databse to update then?

---

### Post by m_duck on 2011-05-29
It won't hurt to update it before you run locate, in case you are looking for a newer file. I tend to run it beforehand since if I'm looking for a file it is usually a newer one. IIRC, locate doesn't search in all directories though so I tend to use find instead. You can configure locate to search more directories, but I'm lazy! Find is a little slower though, as it has to look for the files when you run the command.

---

### Post by TAspr on 2011-05-30
> **m_duck said:**
> It won't hurt to update it before you run locate, in case you are looking for a newer file. I tend to run it beforehand since if I'm looking for a file it is usually a newer one. IIRC, locate doesn't search in all directories though so I tend to use find instead. You can configure locate to search more directories, but I'm lazy! Find is a little slower though, as it has to look for the files when you run the command.

How do you exactly use the find command?

---

### Post by jtarin on 2011-05-30
For help on the largest percentages of Linux commands you can use the terminal. Enter "man <commandname>" such as "man find". "man" is the abbreviation for manual as in documentation..

---

### Post by andrew.46 on 2011-05-31
You might be interested to read the following page:

find - Community Ubuntu Documentation
[https://help.ubuntu.com/community/find](https://help.ubuntu.com/community/find)

which I spent some considerable time renovating a while back! It has some real life examples to get you started with a most useful utility.

---

### Post by TAspr on 2011-06-02
> **andrew.46 said:**
> You might be interested to read the following page:

find - Community Ubuntu Documentation
[https://help.ubuntu.com/community/find](https://help.ubuntu.com/community/find)

which I spent some considerable time renovating a while back! It has some real life examples to get you started with a most useful utility.

Thanks Andrew

---

