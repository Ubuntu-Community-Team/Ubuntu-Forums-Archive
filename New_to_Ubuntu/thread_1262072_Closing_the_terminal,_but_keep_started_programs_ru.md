---
title: "Closing the terminal, but keep started programs running?"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by rob86 on 2009-09-09
I often start things in the terminal, such as apache/ xampp server. I notice that when you close the terminal it kills whatever  was started from within that terminal. For example, web server goes down. This seems rather annoying, is there a way to start programs in the terminal but "unattach" them from it, so you can close the terminal window?

---

### Post by The Judderman on 2009-09-09
Yes there is, although I always forget to do it... If you type ALT+F2, then type the command in the box, you start the program separately from a terminal!

Hope that helps!

The Judderman

---

### Post by j.bell730 on 2009-09-09
[Guake]("apt:guake") works well for that too. I use Guake exclusively now because it's probably the best terminal emulator you can find IMO.

---

### Post by nothingspecial on 2009-09-09
If you want to run an something that`s going to take some time, say a torrent or a big download, launch it in screen.

After it`s started press Ctrl+A then D. This will detach the session and you can close the terminal.

When you want to see how it`s doing, open a terminal and type ```
screen -r
```
Your session will reappear, but it will have continued.

If you use ssh you can reattach your session from another computer from 1000 miles away. If you want.

There`s loads more it can do, it`s probably my favourite app........

.....this week anyway.

---

### Post by philinux on 2009-09-09
Use the screen command.

screen anycommandyoulike

When you close the terminal the app stays open

see man screen

---

### Post by credobyte on 2009-09-09
```
<command> &

```

---

### Post by ddrichardson on 2009-09-09
> **credobyte said:**
> ```
<command> &

```

The ampersand forks a command, it mightn't keep children alive. You want [nohup]("http://en.wikipedia.org/wiki/Nohup") - which tells the system to ignore the hangup command.
```
nohup command
```
Works on any POSIX system.

---

### Post by rob86 on 2009-09-21
Certainly are a lot of options to do one little thing ;)

---

### Post by nothingspecial on 2009-09-21
> **rob86 said:**
> Certainly are a lot of options to do one little thing ;)

That`s linux \\:D/

---

