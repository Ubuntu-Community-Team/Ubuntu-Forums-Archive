---
title: "Error Message After Changing PATH Variable"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by plinydogg on 2009-09-06
Hello,

I wanted to change my PATH variable every time I opened a new terminal session so that I could execute some Python scripts from wherever I was. After searching these forums, I learned that to do this I needed to:

(1) open /home/[username]/.bashrc
(2) Add this:

[HTML]PATH=$PATH:$HOME/<Desired Directory>
export $PATH[/HTML]

I did this and it worked (i.e., I can execute python scripts from any directory in the terminal), but oddly, whenever I open a new terminal I get the following error (even though everything works):

[HTML]bash: export: `/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/ben/Development/Python/Scripts': not a valid identifier[/HTML]

Does anyone know what's going on here? 

Thanks!

---

### Post by blazemore on 2009-09-06
Could you remove the export path line from that file, considering it's throwing up an error message and everything else works?

---

### Post by scragar on 2009-09-06
```
export PATH
```
No $

---

### Post by blazemore on 2009-09-06
> **scragar said:**
> ```
export PATH
```
No $

haha yes I just realised that. It's exporting the VALUE of Path, rather than the variable itsself!

---

### Post by blazemore on 2009-09-06
So basically change it to
```
PATH=$PATH:$HOME/<Desired Directory>
export PATH
```

---

### Post by plinydogg on 2009-09-06
You guys are awesome! Thanks, that fixed it!

---

### Post by andrew.46 on 2009-09-06
Hi blazemore,

> **blazemore said:**
> So basically change it to
```
PATH=$PATH:$HOME/<Desired Directory>
export PATH
```

It really is neither here nor there but you *could* shorten the syntx by one line:

```
export PATH=$PATH:$HOME/<Desired Directory>
```

The classic place to add to the path for your own scripts and the like would be $HOME/bin but of course you can add any path or combination of paths.


Andrew

---

### Post by plinydogg on 2009-09-06
Thanks, that's good to know about $HOME/bin...

---

### Post by andrew.46 on 2009-09-06
Hi plinydogg,

> **plinydogg said:**
> Thanks, that's good to know about $HOME/bin...

Well it is not a particularly special location but it is *conventionally* used to house your own scripts. Thus you have /usr/bin for system binaries, applications and scripts, /usr/local/bin for local-machine binaries, applications and scripts and finally $HOME/bin for personal scripts and applications. It is a neat hierarchy that you can completely ignore if you want, it is *your* system after all :-). 

Andrew

---

### Post by scragar on 2009-09-06
> **andrew.46 said:**
> Hi plinydogg,



Well it is not a particularly special location but it is *conventionally* used to house your own scripts. Thus you have /usr/bin for system binaries, applications and scripts, /usr/local/bin for local-machine binaries, applications and scripts and finally $HOME/bin for personal scripts and applications. It is a neat hierarchy that you can completely ignore if you want, it is *your* system after all :-). 

Andrew

/me blushes because he has system binaries in ~/bin (or rather symlinks to them) and his own executables in /usr/bin...

---

