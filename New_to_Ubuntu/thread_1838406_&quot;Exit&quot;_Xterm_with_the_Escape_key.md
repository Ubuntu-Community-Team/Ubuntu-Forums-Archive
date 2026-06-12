---
title: "&quot;Exit&quot; Xterm with the Escape key?"
date: 2011-09-03
forum: New to Ubuntu
---

### Post by honeybear on 2011-09-03
Hi,

I would like to quit/exit xterm with simply pressing onto "Escape" key. 

How to configure xterm so that it detects pressing Escape, and to run the exit command.

Thanks

---

### Post by Paddy Landau on 2011-09-04
In the terminal, Esc has a specific meaning.

It may be better to stick with the default exit command, which is Ctrl-D.

---

### Post by honeybear on 2011-09-06
> **Paddy Landau said:**
> In the terminal, Esc has a specific meaning.

It may be better to stick with the default exit command, which is Ctrl-D.

Thank you, but I would like to have it simple: Escape 
(for many reasons)

anyone?

---

### Post by Paddy Landau on 2011-09-06
Well, Esc is only one key simpler than Ctrl-D.

As I say, Esc has a specific meaning within the terminal (not just gnome-terminal, but all terminals beginning before even Linux -- back when Unix was text-only; Steve Jobs hadn't had his bright idea yet; graphics were drawings on paper; and 'terminal' meant a literal terminal, i.e. a text-only monitor).

Both Esc and Ctrl-D are embedded into the meaning of Unix's and Linux's text input and output. If you were to change Esc to mean *exit*, then I think half the commands you run (e.g. *man*, *grep*) would exit, as part of their output includes Esc!

If there is a way to tell Bash to swap their meanings, I've yet to see it.

Having said all that, there is a way to reprogram the Esc key on the keyboard to mean Ctrl-D, but then that would affect every program, not just gnome-terminal.

---

### Post by honeybear on 2011-09-07
I confirm well the thread. "Exit" Xterm with the Escape key. which would be similar indeed to ctrl+d or killall -e xterm for a single xterm

---

