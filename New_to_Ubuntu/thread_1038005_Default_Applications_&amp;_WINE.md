---
title: "Default Applications &amp; WINE"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by ReD-SpideR on 2009-01-12
Hello all, I'm new here and to linux, but am enjoying it greatly.

I recently put Ubuntu on my laptop. everything seems ok.

I put WINE on my laptop to run some windows programs.

was working fine, then i decided to add a few applications via "add/remove"

once i was all updated my wine doesn't open my windows stuff anymore.

it opens, and closes right away.


im assuming this had to do with my recent action of adding applications.

my only guess to fix this would be to find out if i can somehow set a default settings to the applications list?

is there a way to re-apply just the applications that were installed from the fresh install?

thanks for your time!

:)

---

### Post by HunterK on 2009-01-12
Normally when something opens and then disappears suddenly there is some sort of error (that you can't see) when the program crashes. If you run the same thing via command line (it will still crash) but it should also write out what the error is in the terminal.

Open a terminal and try running the same program that you were trying to run before:

```
# wine '/home/USER/.wine/drive_c/Program Files/Appdir/program.exe'
```

Hopefully it will crash out, but with more detail this time. :p

---

### Post by ReD-SpideR on 2009-01-21
Hey typing wine at the beginning didn't do anything, i just typed out the whole path and it worked...

this is what was said in the terminal screen... is it fixable?


```
red-spider@red-spider-laptop:~$ wine '/home/red-spider/.wine/dosdevices/c:/Program Files/Diablo II/Diablo II.exe'
red-spider@red-spider-laptop:~$ 
red-spider@red-spider-laptop:~$ 
red-spider@red-spider-laptop:~$ 
red-spider@red-spider-laptop:~$ 
red-spider@red-spider-laptop:~$ 
red-spider@red-spider-laptop:~$ '/home/red-spider/.wine/dosdevices/c:/Program Files/Diablo II/Diablo II.exe'
fixme:advapi:SetSecurityInfo stub
red-spider@red-spider-laptop:~$ X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  25625
  Current serial number in output stream:  25625

```

please help :-)

---

