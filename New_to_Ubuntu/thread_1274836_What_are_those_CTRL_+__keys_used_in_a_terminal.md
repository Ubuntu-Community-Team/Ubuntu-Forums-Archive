---
title: "What are those CTRL + ? keys used in a terminal?"
date: 2009-09-25
forum: New to Ubuntu
---

### Post by rob86 on 2009-09-25
Could someone explain the CTRL-Z/CTRL-C type things when using a terminal. How many are there and what exactly do they do? I thought they were for killing a process, and I've been using them to exit out of things, but the I saw they make the process sleep not kill them, so I think I need a little lesson on that :D

---

### Post by mcduck on 2009-09-25
Ctrl-C exits, Ctrl-Z moves the process to background.

Read more here: [http://linux.about.com/od/linux101/l/blnewbie5_1.htm]("http://linux.about.com/od/linux101/l/blnewbie5_1.htm")

---

### Post by scorp123 on 2009-09-25
> **rob86 said:**
> Could someone explain the CTRL-Z/CTRL-C type things when using a terminal. How many are there and what exactly do they do? I thought they were for killing a process, and I've been using them to exit out of things, but the I saw they make the process sleep not kill them, so I think I need a little lesson on that :D

**Ctrl+C:** Abort a process.
**Ctrl+Z:** Send process to background. You can get a list of running background processes via the **"jobs"** command and you can get them back with the **"fg"** command.

```
> jobs
[1]-  Stopped                 vim
[2]+  Stopped                 htop
```

So to get above session of "htop" back I'd type:
```
fg 2
```

Then last but not least:

**Ctrl+D:** Terminate a connection or file. E.g. you can hit Ctrl+D in an open shell, it will terminate as if you had typed "exit". Same with SSH connections. Ctrl+D and they end. Some commands ("at" comes to mind) expect a list of commands that you're supposed to enter line by line. When you're done with your list you're supposed to send the "End of file" signal .... Yes, that would be Ctrl+D.

---

