---
title: "bash alias"
date: 2010-10-05
forum: New to Ubuntu
---

### Post by Hippytaff on 2010-10-05
What am I doing wrong?

put this in .bashrc

```

#update alias
alias up='sudo apt-get update && sudp apt get upgrade'

```

don't work :mad:

---

### Post by lfacchinelli on 2010-10-05
You have an error on your second command.
instead of "sudo" you put "sudp" and "apt get" instead "apt-get"

---

### Post by riseringseeker on 2010-10-05
> **Hippytaff said:**
> What am I doing wrong?

put this in .bashrc

```

#update alias
alias up='sudo apt-get update && sudp apt get upgrade'

```

don't work :mad:

Well, if that is a copy/paste, you need to change sudp to sudo after the dual ampersands as well as putting a dash (minus sign) between the second iteration of "apt get".  Otherwise, I see no problem with it.  I have several myself, like:

alias vi='vim'
alias cd..='cd ..'
alias rm='rm -i'
alias md='mkdir'
alias la='ls -a'
alias ll='ls -l'
alias ln='ls -ln'
alias !='sudo'
alias add='sudo apt-get install'
alias update='sudo apt-get update'

I don't know of any reason you cannot chain commands like you are trying to do, but it may be a problem.

---

### Post by Hippytaff on 2010-10-05
changed the typo...still no luck

---

### Post by luvshines on 2010-10-05
Hope you reloaded the session after changing the alias.

What does it say when you try the alias ?

---

### Post by Hippytaff on 2010-10-05
This doesnt work either grrr

```

#update alias
alias upd='sudo apt-get update'
alias upg='sudo apt-get upgrade'

```

---

### Post by sisco311 on 2010-10-05
Did you start a new shell or source the file after editing it?

```
. ~/.bashrc
```

---

### Post by Hippytaff on 2010-10-05
> **luvshines said:**
> Hope you reloaded the session after changing the alias.

What does it say when you try the alias ?

always reload....cheers :-)

---

