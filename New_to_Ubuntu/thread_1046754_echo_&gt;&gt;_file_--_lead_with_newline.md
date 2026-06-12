---
title: "echo &gt;&gt; file -- lead with newline"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by jimmy the saint on 2009-01-21
I have a file in which I drop random little notes from time to time using 
```
echo "note" >> file
```

I cannot figure out how to lead with a new line so that the notes are separated by a blank line.  It is very hard to discern where one not begins and another ends without a blank line.  I have tried the -e option, but the \n shows up in the text rather than creating a new line.

Is there any way to do this?  thanks JTS

Edit: fixed the \n... oops.  It was a typo here, not in what I was actually doing.

---

### Post by Titan8990 on 2009-01-21
You want this:

echo -e "/n note" >> file.txt


Also see:

man echo

---

### Post by mrbiggbrain on 2009-01-21
if you use it quite often it might be better to make a small command for yourself called notes... that takes command line arguments and outputs them to a file via c++.

```

#notes this is a simple note that im leaving for myself

```

the code really isnt that hard, its a for loop and a few file operations, you could even add switches like

```

notes -clear
notes -new

```

---

### Post by Joeb454 on 2009-01-21
> **Titan8990 said:**
> You want this:

echo -e "/n note" >> file.txt


Also see:

man echo

Wouldn't that be ```
echo -e "\n note" >> file.txt
``` Any time I've come across newline escape characters it's been a backslash.

I could be wrong :)

---

### Post by jimmy the saint on 2009-01-24
Hey thanks guys.  I figured it out finally.  I guess in my trial and error I never got the \n character inside the quotes while using the -e option.  I am learning python as we speak so maybe I will try to make a little python script for this.  Practical solutions are the best way to learn! Thanks again.  Gold medals for all (but youll have to just imagine them for the time being!)

---

