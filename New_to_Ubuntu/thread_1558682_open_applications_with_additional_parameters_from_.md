---
title: "open applications with additional parameters from nautilus"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by FreeTheBee on 2010-08-22
Hi, I am trying to find out if I can force nautilus to open gvim with the --remote-silent option. That way files will be opened in an existing gvim session if there is one.

I solved this for now using the nautilus actions configurator, by adding an option in the context menu that does what I want. It would be nice though, if the default action would work like this, so I can simply double click a file and get the preferred behaviour. 

In my .bashrc I aliased gvim to gvim --remote-silent, which does the trick when opening files from the terminal. Is there perhaps a similar trick that can be used with nautilus?

---

### Post by gzarkadas on 2010-08-23
I believe that the following should work. Note that this is a system-wide change; all users will be affected:

[LIST]
[*]Press Alt+F2 and type in the run dialog box the command: ```
gksudo gedit /usr/share/applications/gvim.desktop
```
[*]Change the Exec key-value pair (the entry Exec=...) so that it includes the --remote-silent option in its command line. See [http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s06.html](http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s06.html) for the available options.
[*]Save the file and exit gedit.
[/LIST]
If you want to apply this only to your account, make a custom desktop entry in your (note the dot) _~/.local/share/applications_ directory. For example, copy the system-wide desktop entry from /usr/share/applications, change its ownership and then modify it to your needs. You may need to logout to see the changes; I don't know, cause I haven't actually tried it yet.

---

### Post by _0R10N on 2010-08-23
> **FreeTheBee said:**
> Hi, I am trying to find out if I can force nautilus to open gvim with the --remote-silent option. That way files will be opened in an existing gvim session if there is one.

I solved this for now using the nautilus actions configurator, by adding an option in the context menu that does what I want. It would be nice though, if the default action would work like this, so I can simply double click a file and get the preferred behaviour. 

In my .bashrc I aliased gvim to gvim --remote-silent, which does the trick when opening files from the terminal. Is there perhaps a similar trick that can be used with nautilus?

Right click on the icon of the desired file. Then enter the Properties menu. On the "Open With" option select "use custom command" and then enter
```
gvim to gvim --remote-silent
```
That will do the trick from Nautilus.

---

### Post by FreeTheBee on 2010-08-24
Thanks for the replies. I used the 'open with custom command' option, which works like a charm.

---

