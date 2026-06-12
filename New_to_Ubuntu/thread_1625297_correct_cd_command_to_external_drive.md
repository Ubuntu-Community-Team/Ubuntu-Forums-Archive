---
title: "correct cd command to external drive"
date: 2010-11-18
forum: New to Ubuntu
---

### Post by Telos3K on 2010-11-18
An admittedly basic question:

I've attached a Toshiba external drive, and want to change directory into it so that I can back up my ubuntu install onto it. It shows up on my Places list, and in media, as TOSHIBA EXT.
When in the terminal I type:

cd /media/TOSHIBA EXT

however, I get 

bash: cd: /media/TOSHIBA: No such file or directory

which somehow doesn't surprise me, but I can't figure out the correct command.

Thanks.

---

### Post by amauk on 2010-11-18
The drive name has a space in it,
spaces are treated as delimiters in the shell

you need to either escape the space, or quote the command

```
cd /media/TOSHIBA\ EXT
```or```
cd "/media/TOSHIBA EXT"
```

*edit*
Btw, Bash's tab completion will automatically escape stuff like this, and negate the need to type in the whole path
Just type in
cd /media/T
then press the Tab key

---

