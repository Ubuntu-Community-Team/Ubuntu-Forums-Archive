---
title: "How to correctly fork processes...?"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by TurnOfTide on 2010-03-12
For some reason, I can't get processes to fork correctly. This often works:

gedit file.txt &  <--- I will see a new window open and the terminal will return to bash prompt.


However,

conky &   <--- never returns to bash. Why is that?

---

### Post by tom4everitt on 2010-03-12
Processes started from a terminal can either run as foreground or as background. If a process runs in background you can use the terminal to start other processes.

Appending an '&' to a command is supposed to start the process in the background. You can achieve the same thing by:

1. pressing ctrl+z  (stop the process)
2. bg %<the number of the job> (you find the job number with the 'jobs' command).

You can try if that works better.

Another way to get the prompt back is to use the 'screen' or 'nohup' command. How does:

nohup conky &

work?

Also note that some processes requires to be run as foreground processes. A common mistake is to append an '&' to a command launched with sudo, with the result that you never get to type the password! In that case you might want to use the 'fg' (foreground) command, in the same way as 'bg' was used above.

---

### Post by undecim on 2010-03-12
conky & will fork. I think you are just seeing output from conky covering up the bash prompt

Hit enter in the terminal, and you should have your prompt

---

### Post by undecim on 2010-03-12
EDIT: Oops. Somehow managed to double-post that.

---

