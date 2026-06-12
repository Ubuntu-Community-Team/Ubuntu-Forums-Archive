---
title: "Xsane crashes on start-up / Simple Scan works."
date: 2011-02-20
forum: New to Ubuntu
---

### Post by mn_voyageur on 2011-02-20
Xsane crashes on start-up.  Re-installing the software did not help.

Simple Scan works fine.

Any ideas?

Thanks,
MarkN

---

### Post by sanderd17 on 2011-02-20
run xsane from the terminal and see what errors it spits out. Paste them here between CODE tags

---

### Post by mn_voyageur on 2011-02-20
```
mark@10:~$ xsane
Xlib:  extension "RANDR" missing on display ":0.0".
The program 'xsane' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 17226 error_code 8 request_code 154 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

Is there something else you would like me to do?

MarkN

---

### Post by sanderd17 on 2011-02-20
google knows about the problem, but not about the sollution, it seems to be abug in xsane or some librarie of xsane. So if you don't really need it, I would use another scan program.

---

