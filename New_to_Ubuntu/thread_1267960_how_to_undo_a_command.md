---
title: "how to undo a command"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by gkraju on 2009-09-16
hi i am having ubuntu 9.04
today i made a mistake while copying a shell-script file to /usr/local/bin/ i left the "/" next to bin so my bin folder is replaced by the file 

instead of > sudo cp gk.sh /usr/local/bin/

i gave it as  > sudo cp gk.sh /usr/local/bin

is there any i can recover from it ?

---

### Post by kellemes on 2009-09-16
sudo cp /usr/local/bin /usr/local/bin/gk

---

### Post by gkraju on 2009-09-16
> **kellemes said:**
> sudo cp /usr/local/bin /usr/local/bin/gk

i dont understand the code
i  said my /usr/local/bin folder is replaced by the file gk.sh so 
how do this command works ?please explain

---

### Post by CoolHand on 2009-09-16
> **gkraju said:**
> i dont understand the code
i  said my /usr/local/bin folder is replaced by the file gk.sh so 
how do this command works ?please explain

First, the behavior you describe is not how it should function.  If the directory existed, and it should by default, it would not have been replaced by that file with that command.  The file simply would have gone into the directory with or without the /.  The command is smart enough to know that.  I double checked and performed a test on my own sys to verify.

Now assuming that somehow you did wipe it out, just recreate the bin directory under /usr/local and put your file back in it.  Set the permissions and owner to match the other directories in /usr/local.  There are no files in /usr/local/bin by default so you will only have lost something if you installed something there yourself.

---

### Post by wojox on 2009-09-16
Good news and Bad news.

Bad news is you clobbered it and there is no undo. From now on use cp -i to double check.

Good news is there shouldn't have been anything critical in there. Unless you had stored other files you personally put in there. Your best bet is to delete the file and create a new bin directory.

---

