---
title: "Queuing Processes one by one..."
date: 2011-05-19
forum: New to Ubuntu
---

### Post by geepradeep on 2011-05-19
Hi,

I have been using ubuntu for about an year now... I wanted to know if there are any commands in the terminal window to queue processes...

Let us say I have a process by the name "Process1" with pid <1000>... I want to start another process by the name "Process2" as soon as the "Process1" is over or terminated. And, "Process3" must start after "Process2" is successfully done or terminated.

Is there any commands to queue processes in such a way???

PLZ HELP ME... This would be of a real big use to me...

Thanks in advance...

-Pradeep.

---

### Post by mcduck on 2011-05-19
You can use "&&" between commands to execute them one after another (although the next command will only execute if the first one finishes successfully.).

*command1 && command2 && command3*

for example:
```
sudo apt-get update && sudo apt-get upgrade
```

edit: In case you need to queue commands this way regardless of if the first command executes successfully or not, then use a semicolon:
*command1; command2; command3*

---

### Post by jre6 on 2011-05-19
process1 && process2 && process3

---

### Post by geepradeep on 2011-05-19
Thank you guys... Thank you so much... Wonderful learning experience for me... :D:D:D:D:D

---

