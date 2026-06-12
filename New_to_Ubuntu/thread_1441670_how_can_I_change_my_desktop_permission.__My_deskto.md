---
title: "how can I change my desktop permission.  My desktop icons disappeared"
date: 2010-03-29
forum: New to Ubuntu
---

### Post by Chuancey on 2010-03-29
Hello All,
I am very new to ubuntu.  Last night I accidentally clicked on what I guess was a "permission icon" (it was located next to the wifi/battery etc icons).  My desktop icons then disappeared.  I did some research and checked my permissions for the desktop. The file permissions all have a dash through them.  When I switch them to a check and try to apply they reset to the dash.  I have gone to the terminal and tried to change the permission.  I typed "chmod ugo+rwx home/(my user name)/desktop" and got "no such file or directory" I realize this may be basic, but I've only been using ubuntu for 2 days.  I think this is may be the problem(?) Please help.  
Thank you!

---

### Post by Chuancey on 2010-03-29
Hello All,
I am very new to ubuntu. Last night I accidentally clicked on what I guess was a "permission icon" (it was located next to the wifi/battery etc icons). My desktop icons then disappeared. I did some research and checked my permissions for the desktop. The file permissions all have a dash through them. When I switch them to a check and try to apply they reset to the dash. I have gone to the terminal and tried to change the permission. I typed "chmod ugo+rwx home/(my user name)/desktop" and got "no such file or directory" I realize this may be basic, but I've only been using ubuntu for 2 days. I think this may be the problem(?) Please help. 
Thank you!

---

### Post by the yawner on 2010-03-29
Try:
```

sudo chmod ugo+rwx /home/*user*/Desktop

```
Note that the beginning slash '/' before home and capitalized D in Desktop. Unlike Windows, Linux is case sensitive; this is probably the reason why you're getting the error.

---

### Post by overdrank on 2010-03-29
Hi and welcome, please do not create multiple threads on the same issue. Threads merged. :)

---

### Post by Chuancey on 2010-03-29
"The Yawner,"
thank you.  I tried that code. I didn't get an error message, but the permission didn't change and my desktop icons are still missing.  Any other ideas?
Thanks.

---

### Post by Chuancey on 2010-03-29
Sorry, I realized after I posted this thread that it did not belong in the desktop forum, it belonged in absolute beginner.  Is there a way to delete very new posts?  Won't happen again.

---

