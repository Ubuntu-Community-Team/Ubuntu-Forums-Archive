---
title: "Can't start GNOME-Shell to try it..."
date: 2010-01-21
forum: New to Ubuntu
---

### Post by Psumi on 2010-01-21
It gives me a whole mess of errors:

```
Failed to start shell
Traceback (most recent call last):
  File "/usr/bin/gnome-shell", line 265, in <module>
    shell = start_shell()
  File "/usr/bin/gnome-shell", line 138, in start_shell
    (server_glx_extensions, client_glx_extensions, glx_extensions) = _get_glx_extensions()
  File "/usr/bin/gnome-shell", line 67, in _get_glx_extensions
    glxinfo = subprocess.Popen(["glxinfo"], stdout=subprocess.PIPE)
  File "/usr/lib/python2.6/subprocess.py", line 621, in __init__
    errread, errwrite)
  File "/usr/lib/python2.6/subprocess.py", line 1126, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory
ian@ubuntu:~$ Cannot register the panel shell: there is already one running.
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
```

I can't kill metacity nor gnome-panel, they auto-revive themselves when I use killall.

---

### Post by phidia on 2010-01-21
Hi, You might want to try googling your error output-each line as a unique search.

There appears to be a bug report [here]("http://www.mail-archive.com/universe-bugs@lists.ubuntu.com/msg148294.html") that could be related?

---

### Post by J V on 2010-01-21
gnome shell, a project thats 9 months away from proposed release, in the absolute beginners forum?

---

### Post by Psumi on 2010-01-22
> **J V said:**
> gnome shell, a project thats 9 months away from proposed release, in the absolute beginners forum?

Then why is it included with karmic at all? Or Lucid for that matter?

---

### Post by MichaelRX8 on 2010-01-22
I'm having the same trouble.

---

### Post by no2498 on 2010-01-23
you can not run 2 at a time
terminal and shell

---

### Post by wojox on 2010-01-23
[Gnome Shell]("http://wojox.homelinux.net/?p=40") in 9.10

---

### Post by austin512 on 2010-01-24
are you using the "--replace" option?

```
gnome-shell --replace
```

---

### Post by Psumi on 2010-01-24
Yes, I was using the replace option. Anyway, I'm not using gnome anymore, so......... don't even bother.

---

