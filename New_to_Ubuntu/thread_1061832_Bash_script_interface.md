---
title: "Bash script interface"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by Xoanan on 2009-02-06
Hi All

I think there is something I am missing in this script I got from th BASH programming guide.  All I get when I run it is "bad option" no matter what I type.

```
#!/bin/bash
OPTIONS="Hello Quit"
select opt in $OPTIONS; do
    if [" $opt" = "Quit" ]; then
     echo done
     exit
    elif [ "$opt" = "Hello" ]; then
     echo Hello World
    else
     clear
     echo bad option
    fi
done

```

Any ideas?:popcorn:

---

### Post by Dies on 2009-02-06
```
#!/bin/bash
OPTIONS="Hello Quit"
select opt in $OPTIONS; do
    if [ "$opt" = "Quit" ]; then
     echo Done
     exit
    elif [ "$opt" = "Hello" ]; then
     echo Hello World
    else
     echo bad option
    fi
done
```

---

### Post by Xoanan on 2009-02-06
Hmm, just capitalizing "Done"?  Well, that's not too surprising.  I will let you know.

---

### Post by amauk on 2009-02-06
no,
the important change is this

Original
```
if [COLOR="Red"][" [/COLOR]$opt" = "Quit" ]; then
```

New
```
if [COLOR="Red"][ "[/COLOR]$opt" = "Quit" ]; then
```

You had the space in the wong place, causing a syntax error

---

### Post by Xoanan on 2009-02-06
Ah hah!  That's it;  
thanx!

---

### Post by Xoanan on 2009-02-07
Changed it; no luck; still nothing but bad option.
```
#!/bin/bash
OPTIONS="Hello Quit"
select opt in $OPTIONS; do
    if [ "$opt" = "Quit" ]; then
     echo done
     exit
    elif [ "$opt" = "Hello" ]; then
     echo Hello World
    else
     clear
     echo bad option
    fi
done

```

Any ideas:popcorn:

---

### Post by sleepyjon on 2009-02-07
Works fine for me.

Do you type hello or quit? Or do you hit 1 or 2? Hello or quit will not work, 1 or 2 will.

---

### Post by lswest on 2009-02-07
Also, are you sure you want the "clear" in there?  That way if it DOES work but displays "bad option" afterwards for whatever reason you won't see the earlier output.

---

### Post by Xoanan on 2009-02-07
Duh!!  Thanx!! :D

---

