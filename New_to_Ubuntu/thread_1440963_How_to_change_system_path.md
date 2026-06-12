---
title: "How to change system path"
date: 2010-03-28
forum: New to Ubuntu
---

### Post by Paddy Landau on 2010-03-28
I know how to add extra directories to the system path when I use the terminal. I add them to [FONT=Courier New]$PATH[/FONT] in my [FONT=Courier New].bashrc[/FONT] file.

But that doesn't change the system path, so that (for example) if I add a launcher or if I press Ctrl-F2 to "Run Application", it won't see my new directories in the path.

How do I add to the system path so that launchers and Ctrl-F2 use it?

---

### Post by llamabr on 2010-03-28
you have to reload bash after changing your .bashrc.  from terminal, type:

```
bash
```

or, more easily, log out, and log back in.

---

### Post by Paddy Landau on 2010-03-28
Thanks for the reply, but no, that doesn't work for me.

It seems that .bashrc is run only when starting a terminal. I need to get hold of wherever the path is set at login time.

---

### Post by JKyleOKC on 2010-03-28
Have a look at /etc/environment...

---

### Post by Paddy Landau on 2010-03-28
Thank you, that did the trick.

Curiously, though, the path has an extra [FONT=Courier New]/opt/real/RealPlayer[/FONT] at the end even though [FONT=Courier New]/etc/environment[/FONT] doesn't have that. Any idea how RealPlayer puts that on?

---

### Post by gmargo on 2010-03-28
> **Paddy Landau said:**
> Curiously, though, the path has an extra [FONT=Courier New]/opt/real/RealPlayer[/FONT] at the end even though [FONT=Courier New]/etc/environment[/FONT] doesn't have that. Any idea how RealPlayer puts that on?

Check /etc/profile.d/realplay.sh, which was installed by the RealPlayer package.

---

### Post by Paddy Landau on 2010-03-28
Thank you.

---

### Post by Paddy Landau on 2010-04-09
I've just discovered another method.

Put the command in [FONT=Courier New][COLOR=Sienna][SIZE=3].profile[/SIZE][/COLOR][/FONT] in your home directory.

There is a puzzle, though.

[LIST]
[*]Changes to PATH in [FONT=Courier New][COLOR=Sienna][SIZE=3].profile[/SIZE][/COLOR][/FONT] are remembered, so when I press Ctrl-F2 it uses the changed PATH.
[*]And [FONT=Courier New][COLOR=Sienna][SIZE=3].profile[/SIZE][/COLOR][/FONT] runs [FONT=Courier New][COLOR=Sienna][SIZE=3].bashrc[/SIZE][/COLOR][/FONT].
[*]Yet, changes to PATH in [FONT=Courier New][COLOR=Sienna][SIZE=3].bashrc[/SIZE][/COLOR][/FONT] are forgotten (outside of a terminal session), so Ctrl-F2 doesn't see those changes to PATH.
[/LIST]
I don't understand the logic of that.

Is it because [FONT=Courier New][COLOR=Sienna][SIZE=3].profile[/SIZE][/COLOR][/FONT] runs under the default shell (sh), whereas [FONT=Courier New][COLOR=Sienna][SIZE=3].bashrc[/SIZE][/COLOR][/FONT] runs bash? Does the [FONT=Courier New][COLOR=Sienna][SIZE=3]#!/bin/bash[/SIZE][/COLOR][/FONT] at the top of [FONT=Courier New][COLOR=Sienna][SIZE=3].bashrc[/SIZE][/COLOR][/FONT] somehow negate the changes made when [FONT=Courier New][COLOR=Sienna][SIZE=3].profile[/SIZE][/COLOR][/FONT] runs?

---

