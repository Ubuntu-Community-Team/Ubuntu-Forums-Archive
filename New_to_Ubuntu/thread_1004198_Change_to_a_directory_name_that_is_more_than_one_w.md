---
title: "Change to a directory name that is more than one word?"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by ItecKid on 2008-12-07
Hello,

I am curious, is there a way, using the cd terminal command, to change to a directory which has spaces in it's name?

---

### Post by cartisdm on 2008-12-07
Here's an example of navigating to the folder "untitled folder" listed in the Documents directory:

```
$ cd /home/dan/Documents/untitled\ folder/example
```

---

### Post by xjcannonx on 2008-12-07
I am not 100%, i think you can, but i do know that it will make your life a lot easier if you just use underscores like_this

---

### Post by cartisdm on 2008-12-07
> **xjcannonx said:**
> I am not 100%, i think you can, but i do know that it will make your life a lot easier if you just use underscores like_this

absolutely.  get it the habit of naming files like **xjcannonx** described and you'll be better off in the long run;)

---

### Post by bodhi.zazen on 2008-12-07
Or use tab completion ....

Start typing a directory (or file) and hit the tab key.

You can also use quotes 

"file with spaces"

---

### Post by Kareeser on 2008-12-07
What you need to learn is the "escape" character... which is the backslash "\".

Use it whenever you want to add a forbidden character into something... like a space or a quotation mark (if that were possible in filenames).

```

cd ~/Music/Alvin\ and\ the\ Chipmunks

```

---

### Post by vishzilla on 2008-12-07
Use tab completion as bodhi said. Its lot easier.

---

### Post by bodhi.zazen on 2008-12-07
> **Kareeser said:**
> Use it whenever you want to add a forbidden character into something... like a space or a quotation mark (if that were possible in filenames).


You mean like this ???
> bodhi@jaunty:~/foo$ [COLOR=blue]touch fi\?le[/COLOR]

bodhi@jaunty:~/foo$ ls 
[COLOR=darkred]**fi?le**[/COLOR]
bodhi@jaunty:~/foo$ 

bodhi@jaunty:~/foo$ [COLOR=blue]rm fi?le[/COLOR]                                
rm: remove regular empty file `fi?le'? y
bodhi@jaunty:~/foo$ ls                                      
bodhi@jaunty:~/foo$

---

### Post by Kareeser on 2008-12-07
Nono, that's a question mark :)

---

### Post by Rolcol on 2008-12-07
> **Kareeser said:**
> Use it whenever you want to add a forbidden character into something... like a space or a quotation mark (if that were possible in filenames).> **Kareeser said:**
> Nono, that's a question mark :)

They are possible```
roly@rolyslaptop:~/Desktop/te"sting$ mkdir quo\"tation
roly@rolyslaptop:~/Desktop/te"sting$ mkdir sin\'gle
roly@rolyslaptop:~/Desktop/te"sting$ ls
quo"tation  sin'gle
roly@rolyslaptop:~/Desktop/te"sting$ 

```

Everything except the null character and the forward-slash (/) is allowed

---

### Post by Ubu-freak on 2009-09-09
you can also do it like this

```

foo@bar:~$ cd '/home/foo/Desktop/untitled folder' 

```

---

