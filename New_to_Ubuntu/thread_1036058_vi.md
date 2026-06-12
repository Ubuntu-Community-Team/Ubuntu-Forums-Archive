---
title: "vi"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by ozbolt on 2009-01-10
I need to open a file and edit it and that with vi (maybe vim) - need little of instructions please (without X).
I am usng Zenwalk

---

### Post by snova on 2009-01-10
Vi is hardly the easiest of editors to use...

You wouldn't happen to have Nano installed, would you?

Otherwise, press i to go into Insert mode, in which text can be added. Press Esc to go to Command mode (i again to get out) and hjkl to go Left, Down, Up, and Right, respectively.

I don't know much more than that, but it should suffice.

---

### Post by The Cog on 2009-01-10
The commands I can remember for vi are:
x - delete char
r - replace char (with next char typed)
i - enter insert mode
Esc - leave insert mode
a - append (insert mode after the current character)
dd - delete line
yy - yank (copy) current line into copy/paste buffer
p - paste buffered line
:w - write to disk
:q - quit
:q! - quit discarding changes
:w! - write ignoring read-only status
:wq - write and quit

Most command can be preceded by a numberm e.g. 3d deletes 3 chars, 5yy yanks 5 lines.

---

### Post by Slim Odds on 2009-01-10
man vi

---

### Post by andrew.46 on 2009-01-10
Hi,

Easiest way is to download and print one of the many vim 'cheat-sheets' that can be found everywhere on the internet. For example:

[http://www.tuxfiles.org/linuxhelp/vimcheat.html](http://www.tuxfiles.org/linuxhelp/vimcheat.html)

I have one of these laminated by my desk :-).

Andrew

---

### Post by -kg- on 2009-01-10
> **Slim Odds said:**
> man vi

Except that, at least in straight Ubuntu, vi is no longer present.  You will need to issue the command,

```
man vim
```

That is the only "vi"-related terminal editor that is available, at least in Ubuntu 8.04 Hardy Heron.

I can't speak for the other sub-distros.

<edit> Correction:  I just tried it, and "man vi" will still bring up the vim manual.  My bad!

---

### Post by Claus7 on 2009-01-10
Hello, 

vim is a newer version of vi, so an advanced vi.

I would add that opening a file with vi(m) and pressing:

Ctrl+V

you enter in control visual mode and you can select columns with the arrow keys. With y and p you can copy and paste them and with d you can delete them.

Also by typing just v you will have visual mode and that way you can select many lines so as to remove them. 

In order to exit the aforementioned modes press esc.

Vi(m) is a powerful text editor, yet it is a little bit difficult.

Regards!

---

### Post by andrew.46 on 2009-01-10
Hi -kg-,

> **-kg- said:**
> Correction:  I just tried it, and "man vi" will still bring up the vim manual.  My bad!

It is quite a convoluted path as well:

```
andrew@skamandros:~$ ls -l /usr/share/man/man1/vi.1.gz
lrwxrwxrwx 1 root root 25 2008-12-28 21:37 /usr/share/man/man1/vi.1.gz -> /etc/alternatives/vi.1.gz
andrew@skamandros:~$ ls -l /etc/alternatives/vi.1.gz
lrwxrwxrwx 1 root root 28 2008-12-28 21:30 /etc/alternatives/vi.1.gz -> /usr/share/man/man1/vim.1.gz
```

I had not seen /etc/alternatives before ...

Andrew

---

### Post by snova on 2009-01-10
/etc/alternatives holds a bunch of symlinks so that multiple packages can provide the same file.

In this case, there is both the 'vim-tiny' package and then the 'vim-full' package and then possibly another. So they'll each install into /usr/bin with names like vim.tiny or something.

Then dpkg sets up symlinks- /usr/bin/vim points to /etc/alternatives/vim, which changes depending on what you want 'vim' to be.

manpages are linked just like programs.

The program 'update-alterternatives' can be used to list the packages that provide something, and to change the one that is used.

---

