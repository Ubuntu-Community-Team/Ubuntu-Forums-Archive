---
title: "Create file of my directory tree?"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by deleyd on 2009-02-07
I'm looking at the help for **ls** but not quite sure. I want to make a text file of my directory tree to show someone (including hidden files). I got as far as **ls -aR**. Gives me a long listing. Not sure how to get that into a file.

Also, is there a way to just show my directory structure without listing all the files in each directory? And get that into a text file?

---

### Post by yeats on 2009-02-07
Try ```
ls -aR > files.list
```

the -R flag searches all directories recursively and the > puts the output into a newly created file.

---

### Post by Partyboi2 on 2009-02-07
You could do something like
```
ls -aR  >file.txt
``` You can change "file" to what ever you want to call the text file.

---

### Post by niteshifter on 2009-02-07
Hi,

Yes, easy is ;) The utility find is your friend. Open a terminal and
```
find ~ -type d > mydirs.txt
```

Don't want the /home/<user_name> part? Do
```
find . -type d > mydirs.txt
```

---

### Post by deleyd on 2009-02-07
OK is there a way to list just the directory structure without any of the files? (Maybe some other program besides **ls**?)

---

### Post by madverb on 2009-02-07
```
man du
```

---

### Post by niteshifter on 2009-02-08
> **deleyd said:**
> OK is there a way to list just the directory structure without any of the files? (Maybe some other program besides **ls**?)

Err ... yeah. That would be the find command I posted.

---

### Post by southbound395 on 2009-07-23
hello all I am very new here and to ubuntu, just wanted to say thanks to niteshifter for answering deleyd's question, 
as that was the question I was going to ask but now I have the answer!
(I learned a long time ago that a little research almost always goes a long way)  :)

again thank you niteshifter for that answer - it was just what I was looking for :D

---

### Post by darincb77 on 2010-05-28
There is a directory tree terminal program too - 

```
sudo apt-get install tree
```

To show all files:
```

tree -a your/favorite/directory > OutputFile.txt
```

To show just directory level:

```
tree -d your/favorite/directory > OutputFile.txt
```

---

