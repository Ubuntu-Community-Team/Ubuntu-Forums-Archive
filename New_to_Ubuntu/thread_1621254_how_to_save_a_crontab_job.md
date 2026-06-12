---
title: "how to save a crontab job"
date: 2010-11-14
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-11-14
okay how do you save a job after you have entered it in crontab
first enter crontab -e in terminal
then of course my job
but what do i enter to save it control key then what key
still just learning
usually i use the program scheduled tasks but want to be able just to use crontab directly/ again tks

---

### Post by MrWES on 2010-11-14
I assume you're in vi the deafult editor for crontab:

Then hit "ESC" once. Then :wq 

That should bring you back to the command line.

If you would like to change the default editor from vi to say, nano:

sudo update-alternatives &#8211;config editor


Bill

---

### Post by mike2357 on 2010-11-14
Afterwards, you can verify that your changes were saved successfully by running this command, which will produce a listing of what's saved:
```
crontab -l
```

---

