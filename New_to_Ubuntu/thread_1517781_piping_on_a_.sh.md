---
title: "piping on a .sh"
date: 2010-06-25
forum: New to Ubuntu
---

### Post by dancelikeaindian on 2010-06-25
i was wondering if there is a way to pipe something to a executable .sh file and say an argument was in the text.txt

```
$./example | test.txt
```

and you get a result

---

### Post by Bachstelze on 2010-06-25
No, but maybe like this:

```
./example `cat text.txt`
```

Depends what exactly you want to do.

---

### Post by mhgsys on 2010-06-25
hm,only way I know is to 
```
./something > file
```

allowing you to read output of ./something in a (text)file

but  I'm not sure I understood your question correctly.

when you wanted to know how to use a txt file to influence the .sh (./) I'm no help...

---

### Post by dancelikeaindian on 2010-06-25
thanks, it worked. i'm just using bash to manipulate this program my way.

---

### Post by Zeike on 2010-06-25
have a look at 'man xargs'

---

