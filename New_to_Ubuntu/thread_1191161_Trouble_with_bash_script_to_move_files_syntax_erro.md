---
title: "Trouble with bash script to move files: syntax error near unexpected token"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by davidmigl on 2009-06-18
I have a bunch of .html files in a folder that I want to move into a subfolder. So I wrote a simple script but it isn't working.

I test it out first:
```
davidmigl@davidmigl:~$ for FILE in *.html;do echo "${FILE}" "Notes_Enzymes/${FILE}";done
Notes_Enzymes.html Notes_Enzymes/Notes_Enzymes.html
Notes_Enzymes_ind.html Notes_Enzymes/Notes_Enzymes_ind.html
Notes_Enzymess.html Notes_Enzymes/Notes_Enzymess.html
davidmigl@davidmigl:~$ 

```

That looks good, let's go ahead and move everything:
```
davidmigl@davidmigl:~$ for FILE in *.html;do mv "${FILE}" "Notes_Enzymes/${FILE}";done
mv: cannot move `Notes_Enzymes.html' to `Notes_Enzymes/Notes_Enzymes.html': Permission denied
mv: cannot move `Notes_Enzymes_ind.html' to `Notes_Enzymes/Notes_Enzymes_ind.html': Permission denied
mv: cannot move `Notes_Enzymess.html' to `Notes_Enzymes/Notes_Enzymess.html': Permission denied

```

Oh, I must need to be root.
```
davidmigl@davidmigl:~$ sudo for FILE in *.html;do echo "${FILE}" "Notes_Enzymes/${FILE}";done
bash: syntax error near unexpected token `do'

```

Well adding "sudo" into the mix gives me this really weird error with a totally unhelpful error message.

Why does this error pop up and what can I do to remedy it?

---

### Post by Mornedhel on 2009-06-18
1. Probably the whole thing looks like sudo for FILE in *.html; in a subshell started for sudo, then do echo "${FILE}" "Notes_Enzymes/${FILE}";done in your normal toplevel bash shell.

2. Have you mkdir'd the Notes_Enzymes folder ? mv won't create it for you.

3. What's wrong with mv *.html Notes_Enzymes/ ?

---

### Post by Locutus_of_Borg on 2009-06-18
place sudo before the mv command

not before the entire script

---

### Post by KIAaze on 2009-06-18
This seems to work:
```
sudo sh -c 'for FILE in *.html;do mv "${FILE}" "Notes_Enzymes/${FILE}";done'
```

I can't believe I didn't even think of "mv *.html Notes_Enzymes/" when answering this. :lolflag:
That's a lot easier.

Otherwise, in general, I write commands with for loops into a script (text file with .sh extension, made executable).
This is much more readable and avoids problems like the one you had with sudo in front of the command.

ex:
```
#!/bin/bash
for FILE in *.html;
do
 mv "${FILE}" "Notes_Enzymes/${FILE}";
done

```

edit:> 
place sudo before the mv command

not before the entire script
Ah, yes, better than my solution indeed. :)

---

### Post by ghostdog74 on 2009-06-18
```

find . -type f -name "*.html" -exec mv "{}" /destination/"{}" +;

```

---

### Post by davidmigl on 2009-06-19
Duh. Putting the sudo before mv and not just the whole thing makes sense. I was just so used to putting sudo at the beginning of the line every time until now.

As to why mv *.html wouldn't work... ummm... it would! That was an oversight. I was just learning about bash scripts and looping and using a loop was the first thing that came to my mind.

Thanks!!

---

