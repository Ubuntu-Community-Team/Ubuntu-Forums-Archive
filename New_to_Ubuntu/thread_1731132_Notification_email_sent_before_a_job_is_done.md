---
title: "Notification email sent before a job is done"
date: 2011-04-16
forum: New to Ubuntu
---

### Post by tpemartin on 2011-04-16
Hi, I searched the internet and use the following script to send a notification email when a R program is done. However, I found that it always sends me email immediately even when R is still running. Is there anything wrong in this script? Thanks.

```
#!/bin/sh
clear
R CMD BATCH --vanilla ./Programs/ranktest20110415.R ./Programs/ranktest20110415.log &
ssmtp [email]xxx@me.com[/email] < jobdone.txt
```

---

### Post by lisati on 2011-04-16
When you put the & at the end of the line, the command is "backgrounded", and the script keeps on running without waiting for the program to finish.

---

### Post by SeijiSensei on 2011-04-16
You need two ampersands ("&&") which is a logical connector in bash.  The sequence

```
command1 && command2
```

runs command2 only if command1 completes successfully.

With only one ampersand, the first command is run in the background as lisati notes, then the second command is run regardless of the outcome of the first command.

---

### Post by tpemartin on 2011-04-17
Thank you, lisati and SeijiSensei. It helps alot. :KS

---

