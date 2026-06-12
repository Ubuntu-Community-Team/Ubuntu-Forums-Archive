---
title: "Gnome shell in Karmic. --replace problem?"
date: 2010-03-05
forum: New to Ubuntu
---

### Post by zosolm on 2010-03-05
I'm in Karmic and can't get the new gnome shell to work..
running

```
sudo gnome-shell --replace
```gives

```
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Failed to start shell
Traceback (most recent call last):
  File "/usr/bin/gnome-shell", line 265, in <module>
    shell = start_shell()
  File "/usr/bin/gnome-shell", line 138, in start_shell
    (server_glx_extensions, client_glx_extensions, glx_extensions) = _get_glx_extensions()
  File "/usr/bin/gnome-shell", line 75, in _get_glx_extensions
    server_glx_extensions = set(re.split("\s*,\s*", glxinfo_map['server glx extensions'].strip()))
KeyError: 'server glx extensions'
X@X-desktop:~$ Cannot register the panel shell: there is already one running.
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.

```:S
Help!
I thought

```
--replace
```was supposed to stop the current window manager?
and what does the rest of it mean? It looks like i've not installed everything i need, but i have no idea what a GLX extension is or even if i need to get one..
Thanks.

---

### Post by lewisdeane on 2010-03-08
Run without sudo, ie: gnome-shell --replace
If you had enable a root account (*Don't* unless you know how!) you would have gnome-shell running there perhaps!?
I'm trying to find out how to revert to gnome 2 by a simple command without rebooting - anyone know how?

---

### Post by MooPi on 2010-03-08
I use gnome-shell on a test machine and if I need to switch back to the paneled version I use this command ```
sudo chmod +x /usr/bin/gnome-shell
``` Previously I had changed the executable status of gnome-panel. I remove gnome-shell from startup applications and log out. I suppose all of these steps could be accomplished with a simple script and a logout and in.

---

