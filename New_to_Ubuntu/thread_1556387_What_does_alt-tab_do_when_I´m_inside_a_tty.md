---
title: "What does alt-tab do when I´m inside a tty?"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by carlos.hernandez on 2010-08-19
When I´m inside a tty in Ubuntu and I press ALT-TAB it shows me some data in the screen, like a list of directories and commands but I know they are not directories.

I wanna know what that data is.

thx.

---

### Post by martin_legion on 2010-08-23
> **carlos.hernandez said:**
> When I´m inside a tty in Ubuntu and I press ALT-TAB it shows me some data in the screen, like a list of directories and commands but I know they are not directories.

I wanna know what that data is.

thx.

Probably it's the output of the tab key alone. When you start to type a command, if you press tab, it completes the comand. Also, you can complete the names of files and folders with the tab key. For example:

ls he[tab pressed]
completes to:
ls hello.txt

If you press tab alone, without writing any command or filename, the shell will offer you a list of all the possible commands that you can use in that context, and this is probably what you are seeing.

Hope it helps!

---

### Post by komputes on 2012-03-06
I am seeing something different than auto completion. 

Pressing tab will show me "Display all 1,600 possibilities"
Pressing alt-tab will show me the last few commands broken up and laid out cleanly. What is the purpose of this?

[IMG]http://people.ubuntu.com/%7Ekomputes/forum_tty.png[/IMG]

---

### Post by oldos2er on 2012-03-06
Old thread closed. Please start a new thread for your question.

---

