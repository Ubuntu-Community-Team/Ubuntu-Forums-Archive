---
title: "Question with cat / vim"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by Drenriza on 2010-02-19
What is the driffence between using the cat / vim command to display a files content?

Thanks on advance.

EDIT
Don't they show exactly the same?

---

### Post by ad_267 on 2010-02-19
No, they're quite different.

Vim is a very powerful text editor. 

Cat just outputs the whole of the contents to the screen. Cat means "concatenate" by the way, so cat will actually output a whole lot of files joined together if you give it more than one file name. You can also join files together and output to another file using something like "cat a b > c". 

I only use cat for very small files. For anything that could be longer than my screen I use less so that I can easily scroll through the file.

---

### Post by llamabr on 2010-02-19
> **ad_267 said:**
> 

I only use cat for very small files. For anything that could be longer than my screen I use less so that I can easily scroll through the file.

less is good, but more is better.

---

### Post by Drenriza on 2010-02-19
A okey.

I just saw it that, when viewing a single tekst file i used (as a test) both the cat and vim command to view the same file. And i got the same result (in 2 driffent ways).

But when viewing multiple files in cat cant you do it like
cat /etc/gshadow /etc/group |less    ?? and then still be able to go up and down in the file tekst.

---

### Post by ad_267 on 2010-02-20
Cat should just output the contents of the file to your terminal and then go back to the prompt. So it's pretty useless for viewing large files.

Vim should start the vim editor. So if you press the "i" key you should go into insert mode and be able to start inserting text. You can also move up and down with PageUp and PageDown (or Ctrl+F and Ctrl+B, or j and k).

And I'm pretty sure less is better than more :). More can only go forward in a file, less can go forwards and back. So less gives you more than more.

---

