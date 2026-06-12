---
title: "beginner conky question"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by mick_86 on 2011-03-07
just wonder if someone can explain some conky commands to me?

```
${voffset -850}
```

```
${alignr}    or   $alignr
```

need a quick explanation of what these do is thats ok.

---

### Post by mick_86 on 2011-03-07
also if anyone could let me know how to get 2 conkys running at the same time. i already have mine in place but i'm trying to create a new one and would like to know how i can see it to make sure its working ok.

---

### Post by Verbeck on 2011-03-07
voffset is used to offset the text vertically by the number of pixels given. negative value moves it up and positive values moves it down[FONT=monospace]

[/FONT]alignr will justify the text to the right of the available area

to run a second conky, run[FONT=monospace]
[/FONT]conky -c /path/to/second/conkyrc

edit: if the -c option and the path is not given, the .conkyrc in your home folder or /etc/conky/conky.conf will be used

---

### Post by mick_86 on 2011-03-07
> **Verbeck said:**
> voffset is used to offset the text vertically by the number of pixels given. negative value moves it up and positive values moves it down[FONT=monospace]

[/FONT]alignr will justify the text to the right of the available area

to run a second conky, run[FONT=monospace]
[/FONT]conky -c /path/to/second/conkyrc

with alignr what do you mean by justify?

---

### Post by Verbeck on 2011-03-07
> **mick_86 said:**
> with alignr what do you mean by justify?
[RIGHT] like this 
[/RIGHT]

---

### Post by mick_86 on 2011-03-07
> **Verbeck said:**
> [RIGHT] like this 
[/RIGHT]

would this work with an image? instead of writing the exact pixels?

---

### Post by Verbeck on 2011-03-07
> **mick_86 said:**
> would this work with an image? instead of writing the exact pixels?
its supposed to be used with text so i don't think it'll work.. no harm in trying though

---

### Post by mick_86 on 2011-03-07
> **Verbeck said:**
> its supposed to be used with text so i don't think it'll work.. no harm in trying though

ok will give it a try. thanks for your help.

---

### Post by tyleruk on 2011-03-07
You can open two conkys by having two config files, e.g. conkyrc1 & conkyrc2 then entering the following into the terminal:
> 
conky -c conkyrc1 -a left
conky -c conkyrc2 -a right

Also you can find infomation on conky and images here:
[http://wiki.conky.be/index.php?title=Conky_and_Images_%28Imlib2%29]("http://wiki.conky.be/index.php?title=Conky_and_Images_%28Imlib2%29")

---

### Post by RememberWhenItRained on 2011-04-15
beginner question here too: i want to use one of the configs from another user in the "Post your .conkyrc files with screenshot" (since i don't yet know enough to configure it on my own)

is .conkyrc the same as conky.config or do i have to create the .conkyrc file? if so where do i create it?

---

