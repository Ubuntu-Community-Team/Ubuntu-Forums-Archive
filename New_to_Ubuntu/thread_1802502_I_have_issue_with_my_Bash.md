---
title: "I have issue with my Bash"
date: 2011-07-12
forum: New to Ubuntu
---

### Post by emeka_micro on 2011-07-12
Hello All,

Yesterday I tweaked my .bashrc because I was trying to get rvm to work. Now , whenever I start my terminal I get this message:

Bash: source: no such file or directory.

My box is 64bit running Ubuntu 11-04.


Regards,
Janus

---

### Post by mcduck on 2011-07-12
Could you post your .bashrc here, so people could have a look to find what's wrong in there?

---

### Post by ~!geek!~ on 2011-07-12
You may check the block of text you added or modified in .bashrc file. There is possibilty that you might have added a command name starting with capital letter or inverted comma missing somewhere or forgot to hit the spacebar where needed. 

I would suggest to delete the portion you added to file and do 
> source ~/.bashrc 
and start a new terminal window.
 If error isn't there, you may carefully check the code you want to add and again run above command and start new terminal.
See if it helps!!!!
Or you may put the text you want to add to file here. (although, I don't suggest that.)

---

### Post by nothingspecial on 2011-07-12
If you ever completely stuff up your .bashrc, there is a default one you can copy to fix things.

```
mv ~/.bashrc ~/.bashrc_stuffed
cp /etc/skel/.bashrc ~/
. ~/.bashrc
```

That will get you back to where you started.

---

### Post by emeka_micro on 2011-07-12
nothingspecial , it worked. Thank you all

---

