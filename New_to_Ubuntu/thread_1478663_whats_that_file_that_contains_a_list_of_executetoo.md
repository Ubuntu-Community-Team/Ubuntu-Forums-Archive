---
title: "whats that file that contains a list of execute/tool/utility/binary directories?"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by Sharft 6 on 2010-05-10
quick question. I know there is a file somewhere that contains a list of directories that are searched every time a command is typed in the terminal.

Where is that file? I want to add a directory.

---

### Post by theneoindian on 2010-05-10
It's an environment variable - $PATH
```
echo $PATH
``` to get the directories .

to add a directory to the search path , 
```
export $PATH=newdirectorypath:"$PATH"
```

in fact you need to add it to startup scripts to get it to work each time you login . try putting it in /etc/rc.local or via Startup Applications

---

### Post by Ocxic on 2010-05-10
echo $PATH

will tell you

---

### Post by Sharft 6 on 2010-05-10
> **theneoindian said:**
> 
```
export $PATH=newdirectorypath:"$PATH"
```


it says
```

export $PATH=/media/data/programs/ventsrv:"$PATH"
bash: export: `/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games=/media/data/programs/ventsrv:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games': **not a valid identifier**

```

is there a way to make a link on desktop open a program in the terminal?

---

### Post by 3rdalbum on 2010-05-10
> **Sharft 6 said:**
> it says
```

export $PATH=/media/data/programs/ventsrv:"$PATH"
bash: export: `/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games=/media/data/programs/ventsrv:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games': **not a valid identifier**

```

is there a way to make a link on desktop open a program in the terminal?

Yes, when you create the launcher, in the popup menu choose "Application in Terminal".

---

### Post by theneoindian on 2010-05-10
> **Sharft 6 said:**
> it says
```

export $PATH=/media/data/programs/ventsrv:"$PATH"
bash: export: `/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games=/media/data/programs/ventsrv:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games': **not a valid identifier**

```

is there a way to make a link on desktop open a program in the terminal?

I'm sorry . I mistyped it . There's no $ in front of PATH , it would be :

```
export PATH=/media/data/programs/ventsrv:"$PATH"
```

---

