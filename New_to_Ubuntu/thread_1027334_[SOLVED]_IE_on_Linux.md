---
title: "[SOLVED] IE on Linux"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by rubenchet on 2009-01-01
Hi Noob here 
I have just installed Ubuntu 8.10 on my compaq lappy, intentions were to dual boot, however i had a crash during install from live disk which upon rebooting again with live disk had wiped winXP lol (good ridance really!)

I am loving Linux but i need to connect to my virtual works server, unfortunately this only supports IE 5 +
I have heard a little about wine etc but want to know if i can use Internet Explorer some how?

Is it ok to run anything Microsoft on my 100 % Linux lappy or am i just letting the devil in the backdoor again?

HAPPY NEW YEAR!!!

---

### Post by Dedoimedo on 2009-01-01
Hello,

Here you go:

Internet Explorer in Linux - Tutorial 
[http://www.dedoimedo.com/computers/ie_linux.html](http://www.dedoimedo.com/computers/ie_linux.html)

Dedoimedo

---

### Post by wmoore on 2009-01-01
Couple of options:

One is [URL="http://www.tatanka.com.br/ies4linux/page/Main_Page"]IE4Linux.
[/URL]
The other is you can try to fool the server into thinking it is talking to IE by installing the [User Agent Switcher]("https://addons.mozilla.org/en-US/firefox/addon/59") into Firefox - doesn't always work but easier to configure than IE4Linux in my experience.

---

### Post by wmoore on 2009-01-01
> **wmoore said:**
> ... easier to configure than IE4Linux in my experience.Actually scratch that. I hadn't tried IEs4Linux for a long while and had problems with it last time. But I've just gone and installed it now and can access my work PSA system and also do my online Microsoft training (what can I tell you, I need to do it for work).

It was supposed to install Flash 9 with IE but it didn't work for me for some reason, but I downloaded the installer and ran it with```
 WINEPREFIX=~/.ies4linux/ie6 wine install_flash_player_9_ax.exe 
```and we're in business :D

---

### Post by rubenchet on 2009-01-02
Thanks guys, thats great, really appreciate your help.
I have only been using linux for a week but already i'm feeling more at home than with windows, 
Excellent community here.

Cheers

---

### Post by creek23 on 2009-01-02
mark this, **[SOLVED]**.

---

### Post by rubenchet on 2009-01-03
help lol

I have just followed the instructions, all went great until i got this error:

/home/simon/ies4linux-2.99.0.1/ies4linux-2.99.0.1/ies4linux-2.99.0.1/ui/pygtk/ies4linux-gtk.py:399: GtkWarning: Invalid text buffer iterator: either the iterator is uninitialized, or the characters/pixbufs/widgets in the buffer have been modified since the iterator was created.
You must use marks, character numbers, or line numbers to preserve a position across buffer modifications.
You can apply tags and insert marks without invalidating your iterators,
but any mutation that affects 'indexable' buffer contents (contents that can be referred to by character offset)
will invalidate all outstanding iterators
  gtk.main()
ui/pygtk/python-gtk.sh: line 6: 24745 Segmentation fault      python "$IES4LINUX"/ui/pygtk/ies4linux-gtk.py
simon@Rubenlinux:~/ies4linux-2.99.0.1/ies4linux-2.99.0.1/ies4linux-2.99.0.1$ 

any ideas please?

---

