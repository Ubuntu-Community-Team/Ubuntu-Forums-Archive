---
title: "grep not working with CSV files"
date: 2010-12-17
forum: New to Ubuntu
---

### Post by Paddy Landau on 2010-12-17
I want to search many files within a directory for a specific string. "No problem," I thought, "I'll type the following command." (In this example I'll use my name as a search string.)
```
grep -F 'Paddy' *
```But that returned no matches. After some testing, I discovered that grep thinks CSV files are all binary (all the files are *.csv). So, I revised my command as follows.
```
grep -aF 'Paddy' *
```But that still returned no results. It returned results if I use just the one character:
```
grep -aF 'P' *
```But of course I need the whole string, not just the one character. I tried this, too:
```
cat * | grep -aF 'Paddy'
```But again I had no results. I also used:
```
grep -UF 'Paddy' *
```Again, no results.

Of course, I did check a few of the files manually to verify that the string does exist.

Can anyone please help me use grep to find the string I'm looking for in the many files in my directory?

---

### Post by The Cog on 2010-12-17
I wonder if it is a clue that grep thinks the files are binary. Is it possible that the files contain UTF16 text, where each character in the file is made of two bytes? You need a hex editor to see this properly, and then it looks like the characters are alternated with null bytes.

---

### Post by seawolf167 on 2010-12-17
This may help you:

[http://stackoverflow.com/questions/2373885/searching-a-csv-file-using-grep](http://stackoverflow.com/questions/2373885/searching-a-csv-file-using-grep)

---

### Post by ajgreeny on 2010-12-17
grep is working OK on at least some of my csv files.  I have just tried it to make sure, and it did just what it should do and found the data I asked of it.

The files I checked on were csv file backups of addressbooks for thunderbird, and are executable when I look at permissions, though this may well be a different property to being binary as questioned by The Cog.

---

### Post by Paddy Landau on 2010-12-18
Thank you all. The Cog had the answer. I used a hex editor and found that indeed 00 follows each character.

The following code worked for me.
```
grep -a 'P.a.d.d.y' *
```This would make it complicated if we had a mix of files with UTF-16 and (I presume) UTF-8. I looked at the grep manual but found nothing to refer to UTF-16.

---

