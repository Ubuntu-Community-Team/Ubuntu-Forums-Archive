---
title: "[SOLVED] Count how many times a word occurs in a document"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by owenll on 2008-12-08
Hi - I have a number of pgn files and I need to count how many chess games is in each. As the word "Round" occurs once for each game, if I was able to count how many times it occurs in the file I would learn how many games it includes. Is it posssible to use gedit, the command line or any other way to count how many times a certain word occurs in a document?

---

### Post by Her Ghost on 2008-12-08
```
grep Round filename | wc -l
```

should do it (where filename is your file containing the data)

edit: in the Terminal

---

### Post by geirha on 2008-12-08
or just: ```
grep -c Round *filename*
```

---

### Post by owenll on 2008-12-08
Thank you both very much. I have loads of these pgn files, so just to show you how much work you have saved me here is the result of the first one I did! Your response is very much appreciated.

> grep -c Round spassky1948-1978.pgn
1193


---

### Post by geirha on 2008-12-08
You can use that command on all files in one go. It will list filename:count for each file.
```
grep -c Round *.pgn
```

---

### Post by owenll on 2008-12-08
One more question: if I have a file with 650 games, and the white player is called Gwyn in every game, and I want to change this so that the white player in game 1 is Gwyn 1, the white player in game 2 is Gwyn 2, the white player in game 3 is Gwyn 3 etc, is this possible without doing it manually?

---

### Post by geirha on 2008-12-08
Depends a bit on the format of the file. Could you show a sample file with 3-4 entries?

---

### Post by owenll on 2008-12-08
> **geirha said:**
> Depends a bit on the format of the file. Could you show a sample file with 3-4 entries?

Thanks for your reply.

At present every game has the same title which displays as Gwyn v Du. Is there a command that would replace the first Gwyn with Gwyn 1, the second with Gwyn 2 etc. The format is pgn, I use gedit usually to read. 

Have attached a sample.

---

### Post by geirha on 2008-12-08
Incrementing the number for each hit is the hardest part, and I believe awk is the best tool for the job. I'm not very proficient with awk though, but this seems to do the trick:

```

# Create a new file with the changes:
awk '/Gwyn/{sub("Gwyn","Gwyn "++i, $0)} {print}' gwyn.txt > gwyn.new.txt
# Do the change in-place
awk '/Gwyn/{sub("Gwyn","Gwyn "++i, $0)} {print > FILENAME}' gwyn.txt

```

EDIT: 
This one is probably better as it doesn't search twice for each hit.
```

awk '{sub("Gwyn","Gwyn "i+1, $0) && i++; print}' gwyn.txt

```

---

### Post by endacoz on 2008-12-08
Interesting thread.  So your code is what we are calling shell scripting?  I have done similar text manipulation in windows based editors (ultra edit) using Regular Expressions.  Please explain in more detail how they are different and I guess the power of your "shell scripting"

thanks

---

### Post by geirha on 2008-12-08
> **endacoz said:**
> Interesting thread.  So your code is what we are calling shell scripting?  I have done similar text manipulation in windows based editors (ultra edit) using Regular Expressions.  Please explain in more detail how they are different and I guess the power of your "shell scripting"

thanks

Well, regular expressions are regular expressions. Their syntax differ slightly between implementations, but they generally do the same thing.

I guess you could call the above commands "shell-scripting", but I would just refer to them as one-liners. Awk is a programming language which is well suited for parsing and manipulating text files, and the reason I used it in this case was because I needed to have a number that would increment for each substitution. It could be done with a shell script (bash or sh), but awk does it with alot less code.

I think its best you read a tutorial on awk to see how it differs from other programs you've used for manipulating text files.

---

### Post by owenll on 2008-12-14
> **geirha said:**
> Incrementing the number for each hit is the hardest part, and I believe awk is the best tool for the job. I'm not very proficient with awk though, but this seems to do the trick:

```

# Create a new file with the changes:
awk '/Gwyn/{sub("Gwyn","Gwyn "++i, $0)} {print}' gwyn.txt > gwyn.new.txt
# Do the change in-place
awk '/Gwyn/{sub("Gwyn","Gwyn "++i, $0)} {print > FILENAME}' gwyn.txt

```

EDIT: 
This one is probably better as it doesn't search twice for each hit.
```

awk '{sub("Gwyn","Gwyn "i+1, $0) && i++; print}' gwyn.txt

```

Absolutely brilliant!

Thanks:p

---

