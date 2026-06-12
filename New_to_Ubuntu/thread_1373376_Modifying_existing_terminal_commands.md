---
title: "Modifying existing terminal commands"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by Max_Mackie on 2010-01-05
Is it possible to edit (ie change the output of the "clear" to something other than clearing the terminal) commands that are already "built into" the terminal?

Thanks

---

### Post by Methuselah on 2010-01-05
I don't think (I could be wrong) there is any straightforward way to do that apart from changing the shell's code and rebulding.
It would be kind of scary for me to tell someone to execute clear and it formatted their hard drive!

Maybe what you are interested in are 'aliases' where you can define convenient shortcut names for other commands.
[http://freeunix.dyndns.org:8088/site2/howto/Bash.shtml](http://freeunix.dyndns.org:8088/site2/howto/Bash.shtml)

Shell scripts are probably an even better option.

---

### Post by Max_Mackie on 2010-01-05
Yeah I was thinking of just making an alias to get it to do what I want.

---

### Post by bodhi.zazen on 2010-01-05
> **Max_Mackie said:**
> Yeah I was thinking of just making an alias to get it to do what I want.

alias is the way to go

> root@bodhizazen:~# alias clear='echo "lol"'
root@bodhizazen:~# clear
lol
root@bodhizazen:~#Add them to .bashrc 

careful you do not "break" anything (aliases are easy to un-do);)

---

### Post by Cheesemill on 2010-01-05
Possible, yes.
Good idea? Probably not.

You run the risk of breaking any other scripts or applications that use them.

---

