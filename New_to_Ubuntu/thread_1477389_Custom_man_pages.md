---
title: "Custom man pages"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by 2123 on 2010-05-08
I have a lot of field notes about plants  that can be organized into sections and subheadings. For example, its like how the contents are organized for  the wikipedia entry [http://en.wikipedia.org/wiki/Nerium_oleander](http://en.wikipedia.org/wiki/Nerium_oleander). Would like to know if its possible to create custom man pages using this kind of organization (as in wikipedia) so when I type "man 1 nerium_oleander",  it will show the text in that section. I find this modification quite useful when working with gvim for my studies.

How can I something like this without interfering with the system man pages?

Also do man pages allow URLs and Colored text?

---

### Post by r-senior on 2010-05-08
You can create your own manual pages, although obviously the real purpose of a manual page is to document a program or file on the system, rather than something external.

You write them in a fairly obscure markup language called roff, compress them with gzip and stuff them in places like /usr/local/man/man1. You can look at an example by typing:

$ zcat /usr/share/man/man1/ls.1.gz | more

I guess there are tools for producing this stuff but I've not had reason to write one for a long time. Manual pages don't deal with URLs, although a terminal, e.g. Gnome terminal may highlight URLs and make them clickable.

I honestly think you'd be better with HTML and CSS. More commonly used, better tool support and easier to publish if you need to. Perhaps look at some of the WIKI tools too. You don't need to go as far as MediaWiki (as used by Wikipedia) - there are smaller lightweight WIKIs around. In fact TomBoy Notes is not far off.

---

### Post by 2123 on 2010-05-08
Thanks for the reply r-senior. 
I managed to make it work somewhat. Forgive my noobyness, but does it make a difference if I use a root directory "/usr/share/man/man1" or something like "~/Documents/man/man1" ?


The reason I still like the "manpages" is that if I can add my notes into it, I can access them from vim or terminal when I am typing text. Something that might not be possible in wiki or tomboy notes (correct me if I am wrong). I especially love commands like "man -f mkdir" and being able to type "/<string>" from the gvim interface to quickly locate what I am looking for.

Tomboy notes is a good GUI notes tool. But is there a way to look up in Tomboy notes an entry or a word from the terminal so I dont have to take my hands off the keyboard? Would anyone know any wiki tools that could search using commands from the terminal?

---

### Post by r-senior on 2010-05-08
It feels "right" to me *not* to use system manual page folders like /usr/share/man or even /usr/local/man.

Have a look at these:

$ man mandb
$ man manpath

Also /etc/manpath.config?

You might also want to have a look at GNU "info". Try "man info" for starters or "info cpio" as an example. Also search the web for "[texinfo](http://www.linuxjournal.com/article/2840)". This is text-based (although with an emacs rather than vi bias) and supports hyperlinking.

I suppose if you want hyperlinking within a terminal, the old Lynx browser might also be worth a look. But that would be back to HTML/Wiki.

Not trying to put you off roff/man, just thinking about the hyperlinking issue. ;)

---

### Post by 2123 on 2010-05-08
thank you.
texinfo sounds very good

---

