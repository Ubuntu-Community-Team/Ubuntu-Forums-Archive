---
title: "Terminal ?"
date: 2011-04-22
forum: New to Ubuntu
---

### Post by LadyA on 2011-04-22
I was trying to fix you tube fullscreen, which freezes and I put this fix in terminal, which I found on the Ubuntu forums.
sudo mkdir /etc/adobe
sudo su
sudo echo \"OverrideGPUValidation = 1/" >> /etc/adobe/mms.cfg
I don't know too much about terminal. I hit enter after each one. Nothing came up after each time, so I tried to close terminal, but it said there was still a process running and if I closed the terminal it would kill it, so I'm stuck in terminal not knowing what to do.

---

### Post by Joe of loath on 2011-04-22
Running sudo su counts as a process. You can either close the window, or type exit and hit enter to end the root login, then type exit again to close the terminal.

---

### Post by Paddy Landau on 2011-04-22
You didn't need the 'sudo su' line. That was redundant. It started a new process.

Just enter 'exit' or press Ctrl-D to exit the process, then you can close the terminal.

---

### Post by LadyA on 2011-04-22
Thankyou so much for the replies on how to close the terminal and the commands fixed my problem with youtube.

---

