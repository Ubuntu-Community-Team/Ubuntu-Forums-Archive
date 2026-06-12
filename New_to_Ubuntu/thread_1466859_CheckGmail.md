---
title: "CheckGmail"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by grobar87 on 2010-04-30
How to make CheckGmail program,when new mail arrive and when i click on icon in tray to open messege in inbox folder?
Now command for execute when i click on icon in system tray is:
firefox %u
and open gmail site but not in inbox.:confused:

---

### Post by danthegoodman on 2010-04-30
So, when using CheckGmail, you want the browser to open to your inbox instead of the login screen?

To my knowledge this is the way CheckGmail works with the %u. I find it frustrating at times too, so I just replaced the command with
firefox [http://mail.google.com](http://mail.google.com)
and it sends me to the inbox like I want. The downside to this hack is that clicking the 'Compose Mail' button will still send you to the inbox.

---

### Post by grobar87 on 2010-04-30
thanks..works! :)
I have one more question.How to run CheckGmail automatic on startup?

---

### Post by P4man on 2010-04-30
system > preferences > startup applications > add

enter

```
checkgmail 
```

as command (and give it a name)

Also, checkgmail in the repository is slightly out of date. Quit the application, open a terminal and type

```
checkgmail -update
```
Make sure you answer the question with Y (uppercase) and not y (lowercase !)

It will fetch the latest version (also fixes the background issue)

---

### Post by grobar87 on 2010-04-30
thanks again for help :)

---

