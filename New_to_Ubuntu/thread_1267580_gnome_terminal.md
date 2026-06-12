---
title: "gnome terminal"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by DukeLuke on 2009-09-15
How can I log ssh and/or telnet sessions when using the gnome terminal? When I am logged into devices I like to log commands, etc.

Thanks

---

### Post by k33bz on 2009-09-15
```
ssh user@xxx.xxx.xxx.xxx
```
That is one way you can with ssh, or you can install putty

---

### Post by DukeLuke on 2009-09-15
Thanks., but I would like to log the session output to a log file such as a text file. In the future, if I need to go back to the session to view commands and configuration edits, I can open the text file and browse. I know kermit and other apps may be able to do this, but was hoping I can do this in gnome terminal.

---

### Post by k33bz on 2009-09-15
> **DukeLuke said:**
> Thanks., but I would like to log the session output to a log file such as a text file. In the future, if I need to go back to the session to view commands and configuration edits, I can open the text file and browse. I know kermit and other apps may be able to do this, but was hoping I can do this in gnome terminal.

o, ok, sorry, I miss understood, that part is a little above my head.

---

### Post by wojox on 2009-09-15
Try this down and dirty:

ssh [email]user@server.com[/email] | tee -ai logfile.log

This will log whatever you type on the server. The problem here is, "tee" will capture every inputs (it will capture even if you press arrow keys, backspace, tab key...... and will log it). So, if you open the log file you will see a lot of unreadable characters.

Using commands like "strings" or "col -b" you can remove unwanted characters to an extend, but not fully. A solution what I found here is to use "cat" to view the log file. (using "tail" also looks fine).

Remember there really isn't a log file for ssh sessions since they are only in your bash history.

---

### Post by DukeLuke on 2009-09-19
Thanks Wojox!

---

