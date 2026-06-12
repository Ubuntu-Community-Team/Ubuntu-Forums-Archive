---
title: "editing .bashrc file"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by docetes on 2009-07-25
how do I add the line
```
export PATH=/var/lib/gems/1.8/bin:$PATH
```
to my .bashrc file

---

### Post by credobyte on 2009-07-25
```
cd $HOME && gedit .bashrc

```

---

### Post by SuperSonic4 on 2009-07-25
```
nano .bashrc
```

---

### Post by docetes on 2009-07-25
cheers guys. Do I just chuck the line in at the end?

---

### Post by SuperSonic4 on 2009-07-25
Yeah, anywhere. Save and Exit the terminal and it should work from then on

---

### Post by docetes on 2009-07-25
thanks for all the help. That worked perfectly

---

### Post by Jago6060 on 2009-07-25
What's .bashrc do?

---

### Post by llamabr on 2009-07-25
> **Jago6060 said:**
> What's .bashrc do?

It runs when the bash shell starts.  So any commands, aliases, paths set, etc, will get run when you log in.

---

### Post by Jago6060 on 2009-07-25
Ah I see.  So just to make sure I'm understanding this correctly...in the .bashrc file, I could add a line that says "backup home directory"(with the proper variables of course), and that would execute on login?

---

### Post by SuperSonic4 on 2009-07-25
Perhaps, but for programs it's better to put it in Autostart

---

### Post by credobyte on 2009-07-25
> **Jago6060 said:**
> Ah I see.  So just to make sure I'm understanding this correctly...in the .bashrc file, I could add a line that says "backup home directory"(with the proper variables of course), and that would execute on login?

.bashrc isn't a "launcher" - it's a configuration file ( eg. you can add aliases, custom environment paths, etc. ).

---

### Post by llamabr on 2009-07-25
it isn't an auto launcher, though it would probably do what you want.  but it would also do it every time you login, or open a terminal.  There's a better app for doing what you want.

open your .bashrc, and have a look.

---

