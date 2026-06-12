---
title: "rm commnad help"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by Diametric on 2009-12-15
I've created a few text files in my home directory that I exited out of and the both vi and emacs have created a "backup" copy identified as #myfile.txt# - how do I remove these?  I've tried the ```

```rm -r #myfile.txt# both with and without the # symbol and I get a message of "missing operand".  I thought the -r was recurrsive; it forced the delete.  What am I missing?

-Diametric

---

### Post by j7%&lt;RmUg on 2009-12-15
Ok, well for starters backup files in ubuntu are like this:

myfile.txt~

Im pretty sure you dont need the -r flag, just try it like this:

rm #myfile.txt#

post back here if that doesnt work.

---

### Post by Diametric on 2009-12-15
Thanks for your quick reply.  From my home directory where the files can be found, I typed as you suggested and this was the reply:

```

```me@me:~$ rm #tinyT#
rm: missing operand
Try `rm --help' for more information.

---

### Post by tubasoldier on 2009-12-15
-f is the force option
-r is the recursive option for recursively deleting files out of directories.

Also if you created the file using sudo you will need to use sudo to remove it.

---

### Post by Defrector on 2009-12-15
Perhaps this will work:
```
rm "#myfile.txt#"
```

---

### Post by j7%&lt;RmUg on 2009-12-15
Hmmm, ok well type these commands in the same order that i put them here one at a time:

ls
rm myfile.txt(use whatever the name of your file is)

If this doesnt work, just open your file manager and delete them by hand.

---

### Post by Diametric on 2009-12-15
Interesting.  When I attempt to force it: rm -f #tinyT# I am returned to my prompt.  Then, when I type "ls" the file is still there.  So, it looked like it accepted the command but ls shows it didn't remove it.

---

### Post by Diametric on 2009-12-15
Something has to be happening with the # symbol and its effect on said file.  I have added .txt to the rm and rm -f commands and still nothing.  The file are not directories, just text files I created practicing with emacs and vi.  One file is #myemacsfile.txt# and the other is #tinyT#

Could it be that the files are empty? Even if that's the case I would think -f would work, but it doesn't

---

### Post by Some Penguin on 2009-12-15
\#

# is interpreted as "rest of line is to be ignored as a comment".

---

### Post by ankspo71 on 2009-12-15
```
rm *#myemacsfile.txt#*
```
Be careful if using asterisks (*) though, because it will delete files the containing the same filename contents.

---

### Post by revanb on 2009-12-15
Are you sure that filename is correct.

What is the output of

```
ls -al
```

---

### Post by revanb on 2009-12-15
Ok, I've checked it myself, this will work

```
rm \#myfile.txt# 
```

Very interesting!

---

### Post by Diametric on 2009-12-15
Yup, that worked.  Can you or anyone else please explain the properties of the terminal that caused a simple text file to exist, but somehow not be subject to a rm -f command..why does it appear that # somehow "locked" the file...I would like to understand the why.

Thanks,
-Diametric

---

### Post by audiomick on 2009-12-15
> **Some Penguin said:**
> \#

# is interpreted as "rest of line is to be ignored as a comment".

the name of the file has a # in it.

The effect of this is that rm sees "ingore the rest of this"  instead of the file name it is supposed to be removing. The \ before it must mean something like "I really mean this as it is written"

Look at
```
man rm
```

it should be in there somewhere, I think.

---

### Post by Some Penguin on 2009-12-15
# is actually interpreted by the shell, not by rm.   Much like ~, or \.

That is, the shell (Bourne shell, C shell both do this, as do probably most other shells -- pretty long-standing convention) will modify the command line you give it before passing it to 'rm' or whatever other command.

\ is the 'escape' character, the next character is to be taken literally.
~ gets interpreted as your home directory, at least where it begins an argument (~/foo, say)
# is the comment-to-end-of-line bit 

and so forth.  Likewise for variable substitution.  


One other useful it is that single quotes ('foo') gets interpreted as "do not interpret anything in the middle", e.g. 
 
  echo '#foo'

yields  #foo, not a blank line.

---

### Post by audiomick on 2009-12-15
Thanks for the correction! :D

---

### Post by Diametric on 2009-12-15
Thanks for the replies...that cleared it up.

---

