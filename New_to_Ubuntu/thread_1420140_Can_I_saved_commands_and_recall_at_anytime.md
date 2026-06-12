---
title: "Can I saved commands and recall at anytime?"
date: 2010-03-02
forum: New to Ubuntu
---

### Post by TurnOfTide on 2010-03-02
Sort of like a bookmarks thing for commands.... Say I wanted to save something often typed like:

mysql -uroot -pcheesey1 mydb


Also, I don't care if the pwd is saved somewhere that isn't encrypted since the DB in question contains nothing of value.

---

### Post by Tibuda on 2010-03-02
yes, it is called aliases.
open (or create if it does not exists) the ~/.bashrc hidden file using your favorite text editor, and add the following:
```
alias mydb='mysql -uroot -pcheesey1 mydb'
```
then the next time you open a terminal, you just have to type **mydb** to execute that command.

See also: [http://en.wikipedia.org/wiki/Alias_%28command%29](http://en.wikipedia.org/wiki/Alias_%28command%29)

---

