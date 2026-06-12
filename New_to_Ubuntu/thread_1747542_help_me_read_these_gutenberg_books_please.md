---
title: "help me read these gutenberg books please"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by fatharraxman on 2011-05-02
Hello
I required a 2010 cd/dvd from Gutenberg project then I copied it in my mini but when I try to browse them with mozilla the file index.HTML does not open the index to see the titles of books or authors instead it says 
```
File not found
      
      
      
      
      
        
        
          Firefox can't find the file at /home/fatharrahman/Documents/Project Gutenberg DVD/indexes/authors_a.html.
        

        
        

  Check the file name for capitalization or other typing errors.
  Check to see if the file was moved, renamed or deleted.
``` what annoys more is that I tried them in Windows it opens there and I tried all possible threads on the subject but in vein 
please help me

---

### Post by Tibuda on 2011-05-02
That's probably because Linux is case sensitive, while Windows is not. The index has links in a case different from the filename, so Linux can't find them.

---

### Post by fatharraxman on 2011-05-02
No way ? at all 
that's so bad

---

### Post by rezaervani on 2011-05-02
> **fatharraxman said:**
> 

[CODE]File not found
      
         
          Firefox can't find the file at /home/fatharrahman/Documents/Project Gutenberg DVD/indexes/authors_a.html.
        


It seems the problem is that you use space for your folder name. Change it into something like this :

home/fatharrahman/Documents/ProjectGutenbergDVD/indexes/authors_a.html (without space)

or

home/fatharrahman/Documents/Project_Gutenberg_DVD/indexes/authors_a.html (with underscore)

Hope it can help

Regards
Reza Ervani
http://tanyarezaervani.wordpress.com

---

### Post by Tibuda on 2011-05-02
> **fatharraxman said:**
> No way ? at all 
that's so bad

If my guess is correct, you would have to rename all html files to match the same case of the links. You can also browse the files using your filemanager instead of the index.html, I think this is easier.

---

### Post by fatharraxman on 2011-05-02
> Firefox can't find the file at /home/fatharrahman/Documents/ProjectGutenbergDVD/indexes/authors_j.html.
        

        
        

  Check the file name for capitalization or other typing errors.
  Check to see if the file was moved, renamed or deleted.
browsing files is not easy because it contain 29500 + books and not named only numbered, the browser is the only way to find title you want

---

### Post by jmore9 on 2011-05-02
You can always install Komposer from the repos .  It is almost a frontpage replacement, It should open everything with html content

---

### Post by Tibuda on 2011-05-02
Can you browse them from the DVD? I ask this because the ISO standard is not case sensitive.

Another way is to use the index.html to browse the authors, and after the error then use your file manager to try to find the file.

---

### Post by fatharraxman on 2011-05-02
> **jmore9 said:**
> You can always install Komposer from the repos .  It is almost a frontpage replacement, It should open everything with html content
from where please be some specific  to me

---

### Post by Tibuda on 2011-05-02
> **fatharraxman said:**
> from where please be some specific  to me

He means using Ubuntu Software Center.

---

### Post by fatharraxman on 2011-05-02
mean this one ?

---

### Post by fatharraxman on 2011-05-02
Same problem with komposer  from reps

---

### Post by Tibuda on 2011-05-02
It is not an issue with the applications, but with the case sensitive file system. Have you tried opening index.htm from the DVD?

---

### Post by fatharraxman on 2011-05-02
> **Tibuda said:**
> It is not an issue with the applications, but with the case sensitive file system. Have you tried opening index.htm from the DVD?
seem so 
my problem is that I don't have dvd in my mini laptop only  in the desktop where windows works the index open there from dvd and frm copied on drive as well but here where I deadly need it no benefit

---

