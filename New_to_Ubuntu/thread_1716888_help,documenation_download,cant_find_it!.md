---
title: "help,documenation download,cant find it!"
date: 2011-03-29
forum: New to Ubuntu
---

### Post by rapidvictory13 on 2011-03-29
Hey there just started with ubuntu and I recently downloaded some documentation about programming and e books from the software center but I can't find where they are!!!! I'm running lucid lynx and have download the document viewer okular! So please help me step by step I wanna read these documents! Thanks in advanced

---

### Post by Dutch70 on 2011-03-29
Try opening a terminal and type in "locate" without the quotes, followed by the name of your document or program.

Did you check the downloads folder? 

To see where you are downloading to in Firefox, go to preferences > General tab & see where it says it's downloading files to.

---

### Post by rapidvictory13 on 2011-03-29
Its not a download manually from the internet I used the software center so its not under downloads and I tried but the terminal started showing info I don't understand but nothing popped up. Can you help me out by downloading the "ruby book" from the software center? And then tell me how you were able to see it and where ubuntu sent it ? Please and thanks!

---

### Post by oldos2er on 2011-03-29
Check /usr/share/doc

**dpkg -L rubybook** will show you where it installed.

---

