---
title: "Page command not working"
date: 2011-03-13
forum: New to Ubuntu
---

### Post by 5149.5 on 2011-03-13
I've been away from the CLI too long. I am trying to reacquaint myself with linux after not using it for a while.  Today I was poking around in the directories using the terminal. I attempted to pipe an LS command to page and got a message that I needed to install a package for the page command. HUH? 

Well I got the install of the package done. OK. I then attempted to use the command again and got this error: Unable to locate configuration or load plugin "peg" (ERROR for slave interp1 : "/usr/share/tcltk/tcllib1.12/page/plugins/config_peg.tcl": not in access_path). OK, a little digging around and I found my path statement in etc/environment and added a path to usr/share. 

I then retried the command, got the same error, decided I had done enough hacking, and decided to ask the experts for help. :confused:

---

### Post by mcduck on 2011-03-14
"page" command? What are you trying to do? The only "page" command I can even find is a parser generator for tcllib, not somehting you'd usually want to pipe "ls" output to...

edit: perhaps the command you were looking for was "more" or "less" instead of "page"? :)

---

### Post by 5149.5 on 2011-03-14
> **mcduck said:**
> "page" command? What are you trying to do? The only "page" command I can even find is a parser generator for tcllib, not somehting you'd usually want to pipe "ls" output to...

edit: perhaps the command you were looking for was "more" or "less" instead of "page"? :)

Thanks. That's what I was trying to remember. Getting old sucks.:lolflag:

---

