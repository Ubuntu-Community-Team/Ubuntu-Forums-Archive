---
title: "phpmyadmin problem"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by hemoali on 2011-01-31
HI , I have a problem with phpmyadmin
when I enter to 
localhost/phpmyadmin 
[IMG]http://store3.up-00.com/Feb11/mLv68018.png
Then when I enter the password and click (GO)
this picture appears 
[IMG]http://www.y4yy.net/images/72127051711355688093.png
OK now what I can do to solve this problem and please quickly because I want to use phpmyadmin now before tomorrow  
*** you should now before I reinstall the Ubuntu 10.10 I tried to open that but 
no benefit and one time that opened I don't how but I also didn't Any thing only when I tried the last time that worked 
now you now all of the problem 
please who can help me ??????????????

---

### Post by overdrank on 2011-01-31
Hi and welcome, please use thumbnails when posting images. :)

Moved to Absolute Beginner Talk.

---

### Post by cavh on 2011-01-31
Easiest way is to reinstall MySQL and phpMyAdmin using this command from a terminal:

```
sudo tasksel
```

and select the 'LAMP Server' option using your arrow key to move between choices and the space bar to select an entry, then your tab key to choose 'OK'. LAMP stands for Linux, Apache, MySQL and phpMyAdmin.

***DO NOT DESELECT any other entry which is currently ticked***

Make sure you keep a note of the MySQL and phpMyAdmin passwords you use create using the LAMP install. The install is very quick, no more than 5 minutes I would say.

---

### Post by hemoali on 2011-02-01
[CENTER]no it doesn't work
that what appears

" sudo: tasksel: command not found "
[/CENTER]

---

### Post by cavh on 2011-02-01
There shouldn't be a colon between *sudo *and taskel, did you type the command (or give the error message) correctly?

---

### Post by hemoali on 2011-02-01
I am sorry th error is
taskal :command not found
but now I found the solution
And I will but it by images as my first helping topic to this great site and Thanks very much


my regards

---

### Post by indytim on 2011-02-01
You will need to install tasksel.  I believe it is no longer installed by default.  Install via the package manager or 
```

sudo apt-get install tasksel

```

After it is installed:

```

sudo tasksel

```

Then select ONLY the LAMP Server by clicking the space bar to select.  DO NOT DE-SELECT ANYTHING THAT IS ALREADY SELECTED (unless you know specifically what your are doing or you have a yearning desire to break your system).

IndyTim / DataMan

---

### Post by hemoali on 2011-02-01
ok 
thanks with this exposition
I cannot Explain more than this
so Thanks

---

