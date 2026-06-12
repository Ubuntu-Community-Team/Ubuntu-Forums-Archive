---
title: "Problem opening .py files from a terminal"
date: 2010-10-31
forum: New to Ubuntu
---

### Post by carlosmavros on 2010-10-31
Hi, I started a small guide about programming in python for non-programmer beginners and it made me do a small test.
I had to write in an text editor (I used gedit) and write : print ''Hello World'' and save it as a .py file. Then the colors of the words changed as expected but, when I go into the terminal (Yakuake or an other one) and I write  

python (and the name of the file) 
it sais:

python: can't open file 'myfirstprogram.py': [Errno 2] No such file or directory

Please tell me if I'm doing something wrong.
Thanks

---

### Post by Vaphell on 2010-10-31
use the autocompletion feature of shell (tab key), it will type the proper file name for you so you can be sure the name is correct. Are you sure you were in the proper directory in your terminal?

---

### Post by Clever_Username on 2010-10-31
I'm no python expert, but I have to ask, are you certain the path to the file and file name are correct?

---

### Post by carlosmavros on 2010-10-31
OK, guys I figured it out! thanks!
The thing was I had saved it in documents and I tried to open it as if had been saved in my home folder :p
I moved it to the home folder and now it's alright!
That was really a beginners question!

---

