---
title: "Running application via terminal, then continue usage of terminal"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by delata3 on 2009-12-27
I'm sure this is a very silly question, but whenever I run an application from the terminal (for example, sonata), it opens the application, but then I can't use that terminal anymore because sonata is using it to display what it's doing. It's almost like the application owns the terminal after you run it from there.

Is there a way to run the application and then allow me to keep using the terminal without killing it (ctrl+c or ctrl+z)?

Thanks!

---

### Post by taurus on 2009-12-27
Just send the app into the background.

```
**program** &
```

---

### Post by delata3 on 2009-12-27
Ah! Thank you! Easy enough. :)

---

### Post by falconindy on 2009-12-27
You have the ability to use Ctrl-Z to suspend a program currently holding the 'attention' of the terminal, and then using 'bg' to background the application. Similarly, a backgrounded application can be brought back under your control by using 'fg'. If you have multiple applications running in this manner, you can use the 'jobs' command to identify an application by job number, e.g. 'fg 3'.

---

### Post by delata3 on 2010-01-01
Thanks for the in-depth reply! Appreciate it!

---

