---
title: "how to select 'ok' when configuring sun-java5 jre?"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by JDuc on 2008-12-26
I feel like this is an extremely simple question, but for some reason, I simply cannot figure out how to do it.  I am very green when it comes to Linux, but I'm really wanting to learn.

For some strange reason, I cannot figure out how to select 'ok' in the Terminal for Configuring sun-java5 jre.

Currently, I'm reading through the Ubuntu wiki page to try and get a basic understanding: [http://ubuntuguide.org/wiki/Ubuntu:Hardy](http://ubuntuguide.org/wiki/Ubuntu:Hardy)

I've attached a screen shot (figured out how to do that in Ubuntu!) of the terminal window to help explain where I'm stuck.

Anyone?  I tried searching for an answer, but I just couldn't find anything.

Thanks in advance!

---

### Post by taurus on 2008-12-26
Press the Tab key to highlight the <OK> and Return key to accept it.

---

### Post by JDuc on 2008-12-26
many thanks, that was super simple.  Is that the same in windows command line interface as well or is that something that's unique to Linux, like the ability to 'shift + insert' in the terminal window.

---

### Post by 2hot6ft2 on 2008-12-26
> **JDuc said:**
> many thanks, that was super simple.  Is that the same in windows command line interface as well or is that something that's unique to Linux, like the ability to 'shift + insert' in the terminal window.
Same in windows and DOS

---

### Post by jamesstansell on 2008-12-26
> **JDuc said:**
> many thanks, that was super simple.  Is that the same in windows command line interface as well or is that something that's unique to Linux, like the ability to 'shift + insert' in the terminal window.

It's from a text windowing library, called curses, which predates ms/windows by a decade or more.  It's possible to use on ms/windows, but you won't see it very often (generally just from unix programs that have been ported.)

BTW, ubuntu uses the ncurses implementation; you can find more from the libncurses5 and related packages.

---

