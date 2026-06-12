---
title: "How to cd to desktop????"
date: 2011-08-26
forum: New to Ubuntu
---

### Post by pcvchriskmg on 2011-08-26
This has been driving me crazy for ten minutes.

On the cli, I am at chris@chris-studio-1737 (studio-1737 is the name of my computer).

I need to access the desktop via the cd command.

I have tried:

cd /desktop
cd /home/desktop
cd home/chris/desktop
cd /chris/desktop
cd desktop

And some other combinations.

I get the following response:

bash: cd: home/chris/desktop: Not a directory

Can anyone explain to me what is going on, please?

Thanks,
Chris

---

### Post by nothingspecial on 2011-08-26
Capital D

~ is shorthand for your $HOME

so 

```
cd ~/Desktop
```

---

### Post by pcvchriskmg on 2011-08-26
> **nothingspecial said:**
> Capital D

~ is shorthand for your $HOME

so 

```
cd ~/Desktop
```

all directory names are case-sensitive, then?

Chris

---

### Post by whatthefunk on 2011-08-26
Full path would be:
/home/chris/Desktop

---

### Post by whatthefunk on 2011-08-26
> **pcvchriskmg said:**
> all directory names are case-sensitive, then?

Chris

Yes they are.  From your home directory, you can do the following to see all the directories:

```
ls
```

---

### Post by pcvchriskmg on 2011-08-26
OK,thanks guys.

Consider this this thread **CLOSED.**

---

### Post by nothingspecial on 2011-08-26
Everything you type into the shell is case sensetive........



........ unless you are using something like grep and use the ignore case option (but don't worry about that right now).

---

