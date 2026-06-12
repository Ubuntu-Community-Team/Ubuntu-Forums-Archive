---
title: "help with commands"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by bigron248 on 2009-05-25
I would like to know if there is an application that will show the commands in the terminal window like if i were to open firefox i would want to know what command was sent to make that happen  does this make sense?:popcorn:

---

### Post by Saint_ on 2009-05-25
Uh, sort of. You want an application that'll monitor the commands sent back and forth between applications and the operating system? ( For example, for firefox you can simply type "firefox http://google.com" without the quotes, to open google in firefox. )

---

### Post by doas777 on 2009-05-25
if you check your system logs (auth.log) you should see most of the commands you issue.

good luck.

---

### Post by kaibob on 2009-05-25
> **bigron248 said:**
> I would like to know if there is an application that will show the commands in the terminal window...

I don't think I understand either, but the following command will "report a snapshot of the current processes." It's pretty easy to figure out what started what:

```
ps -u username -o cmd
```

For example, I just ran this command and one of the items shown was:

```
/usr/lib/firefox-3.0.10/firefox
```

If you need more, perhaps you could provide a little more detail on what you're looking for.

---

### Post by jaceh14 on 2009-05-25
i think i understand. you want a little pop-up like in the corner, or center, or wherever, it doesn't matter where, but you want the pop-up to show what the command would be to be able to run that program from the terminal rather than having to use the GUI. i would also like this for i am still new to linux and ubuntu, and would like to learn how to use just the terminal.

jace

---

