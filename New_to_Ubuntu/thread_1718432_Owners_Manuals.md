---
title: "Owners Manuals"
date: 2011-03-31
forum: New to Ubuntu
---

### Post by DGINSD on 2011-03-31
I'm looking for instructions for, as of right now, 2 programs, the first is descriptions of what all the Terminal commands do exactly. I pressed TAB TAB and got a full list of commands but thats not much good if I don't know what all of them actually do?

The other program I'd like detailed instructions for is Compiz, this program's got a ton of settings and a lot I have no clue what they do because the descriptions are so very vague, is there a owners manual with in depth descriptions of each setting?

---

### Post by Grenage on 2011-03-31
> **DGINSD said:**
> I'm looking for instructions for, as of right now, 2 programs, the first is descriptions of what all the Terminal commands do exactly. I pressed TAB TAB and got a full list of commands but thats not much good if I don't know what all of them actually do?

The other program I'd like detailed instructions for is Compiz, this program's got a ton of settings and a lot I have no clue what they do because the descriptions are so very vague, is there a owners manual with in depth descriptions of each setting?

Generally you can use the *man* command to view such things, for example:

```
man compiz
```

---

### Post by Niedzwiedz on 2011-03-31
> **DGINSD said:**
>  ...what all the Terminal commands do exactly.
 ......I'd like detailed instructions for is Compiz?

Terminal Commands;
[http://oreilly.com/linux/command-directory/](http://oreilly.com/linux/command-directory/)
This kinda old, but may still help;
[http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)

Compiz;
[http://wiki.compiz.org/](http://wiki.compiz.org/)

---

### Post by DGINSD on 2011-03-31
> **Grenage said:**
> Generally you can use the *man* command to view such things, for example:

```
man compiz
```

Excellent, thank you sir. Does that work for the terminal as well or whats it called "BASH Shell"?

---

### Post by Grenage on 2011-03-31
> **DGINSD said:**
> Excellent, thank you sir. Does that work for the terminal as well or whats it called "BASH Shell"?

Yup, that should work in your shell. :)

Out of curiosity, is there a reason you're not using the GUI options?  Under Preferences, it would be listed as CompizConfig Settings Manager; I can't recall if it's installed by default.

---

### Post by DGINSD on 2011-03-31
> **Grenage said:**
> Yup, that should work in your shell. :)

Out of curiosity, is there a reason you're not using the GUI options?  Under Preferences, it would be listed as CompizConfig Settings Manager; I can't recall if it's installed by default.

Oh I guess I didn't compose my question clearly and maybe got what was intended as 2 subjects mixed together.  

For Compiz I do use the GUI my specific questions regaurding Compiz is basically I'd like find detailed descriptions of individual Compiz settings and functions. 
 
My question regaurding Teminal is where can I get descriptions of the functions of individual terminal commands. For example if you press tab twice in Terminal a list of available commands are generatetd, I'd like descriptions of what each of these commands do.

---

### Post by Cheesehead on 2011-03-31
man terminalcommand

For example, 'man date'
or , 'man ls'
or 'man sort'

Though you might do better simply looking through a search engine for a bash tuorial. A plethora are available on the web, and they are much easier to understand than hundreds of man pages.

---

