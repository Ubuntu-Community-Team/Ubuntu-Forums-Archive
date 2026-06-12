---
title: "What editor is used to produce the &quot;man&quot; pages?"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by Land Rover Series 3 on 2009-11-25
My apologies if this sounds like a really dumb question, but I'm trying to write my own basic notes on Linux, and am impressed at how nicely formatted the "man" pages are when viewed in the desktop terminal (a good example is "man intro"). They have boldface, underline, italic and so on, but stick with a nice, clean monospace font. As far as I can tell, it uses Unicode, but I'm not certain on that. Anyway, I'd like to be able to write my own notes using a similar approach. I know the program is "gnome-terminal", but what programme is actually used to produce the text and then display the shell and man pages contents?

gedit is quick to use, and good for formatting to a printer page size - also does a good job of text-wrapping, but it can't do boldface, underline or italic etc.

Most other text editors that I've looked at don't do font embellishments either. And I just want to write text - I've no inclination at the moment to go down the emacs/vi route no matter how brilliant they are at everything under the sun.

OpenOffice does everything of course, but can be a bit slow and tedious to use when all you want is monospace, bold, underline and italic.

TextEdit just seems a bit weird to me, and I can't get on with it.

Would appreciate any information...

---

### Post by Shpongle on 2009-11-25
well you can make open office faster by allocating more memory , go to tools memory and put the ram up to like 60 or 120 and itll fly along!!! , as for gedit there might be a plugin , thats my favorite editor. it can do loads

---

### Post by chillicampari on 2009-11-25
[http://computerprogramming.suite101.com/article.cfm/creating_linux_man_pages](http://computerprogramming.suite101.com/article.cfm/creating_linux_man_pages)

---

### Post by 3rdalbum on 2009-11-25
Man pages use their own sort of markup (in other words, they are not Rich Text or HTML).

You can create man pages in Gmanedit.

---

### Post by falconindy on 2009-11-25
> **3rdalbum said:**
> Man pages use their own sort of markup (in other words, they are not Rich Text or HTML).

You can create man pages in Gmanedit.
Man pages use a markup language that pre-dates HTML called roff. The GNU implementation is, of course, called groff. Raw files are fed through nroff or troff (I forget which) to produce the formatting you see.

Semi-related: If you think man pages are pretty, you should see them in color. Try this: Install the package 'most', and then open up /etc/manpath.config with your favorite text editor (and sudo). Find your way down to around line 78 where you see a commented out line:
```
#DEFINE    pager    pager -s
```
Uncomment it and change it to:
```
DEFINE     pager    most -s
```
Man pages will now be in color! OOOoooOOOoooohhhh...

---

### Post by diesch on 2009-11-25
Use
```
 man -Hfirefox 
```
to see the man page in Firefox.

---

### Post by falconindy on 2009-11-26
> **diesch said:**
> Use
```
 man -Hfirefox 
```
to see the man page in Firefox.
Neat. Sadly, this only works about 80% of the time with chromium. The other 20%, it picks the wrong directory name out of /tmp. Wild.

I've got an alias setup to convert man pages to PDFs:
```
man2pdf() {
    if [[ -z $1 ]]; then
    	echo "USAGE: man2pdf [manpage]"
    else
    	if [[ `find /usr/share/man -name $1\* | wc -l` -gt 0 ]]; then
		out=/tmp/$1.pdf
		if [[ ! -e $out ]]; then
			man -t $1 | ps2pdf - > $out
		fi
		if [[ -e $out ]]; then
			/usr/bin/evince $out
		fi
	else
		echo "ERROR: manpage \"$1\" not found."
	fi
    fi
}
```

---

### Post by Land Rover Series 3 on 2009-11-26
> **DillByrne said:**
> well you can make open office faster by allocating more memory , go to tools memory and put the ram up to like 60 or 120 and itll fly along!!! , as for gedit there might be a plugin , thats my favorite editor. it can do loads
I'll try your tip for Oo Writer anyway (can't do it any harm to work a bit quicker, and my system monitor says I hardly ever use more than a tiny fraction of the available RAM anyway). I also like gedit, a lot, so I'll have a good nose around to see what plugins there are. Thanks

---

### Post by Land Rover Series 3 on 2009-11-26
> **chillicampari said:**
> [http://computerprogramming.suite101.com/article.cfm/creating_linux_man_pages](http://computerprogramming.suite101.com/article.cfm/creating_linux_man_pages)
Excellent. That would be a really neat solution - writing my own customized man pages. Thanks for the link.

---

### Post by Land Rover Series 3 on 2009-11-26
> **3rdalbum said:**
> Man pages use their own sort of markup (in other words, they are not Rich Text or HTML).

You can create man pages in Gmanedit.
Yes, a quick Dogpile search found it straight away. I'll have a good look at this. Many thanks for the info.

---

### Post by Land Rover Series 3 on 2009-11-26
My thanks to everyone who took the trouble to respond. I think I have all the information I need now, thank you, so I'll crack on with it. I think that writing a few of my own customized man pages would be a good way to go, so will be trying out a few to see if I can get the hang of it.
Meanwhile, my LRS3 clutch awaits me ....

---

### Post by l-x-l on 2009-12-01
> **diesch said:**
> Use
```
 man -Hfirefox 
```
to see the man page in Firefox.

This didn't work for me in gnome-terminal. I get this message when I type it in:

```

What manual page do you want?

```

---

### Post by Land Rover Series 3 on 2009-12-01
> **l-x-l said:**
> This didn't work for me in gnome-terminal. I get this message when I type it in:

```

What manual page do you want?

```
No, it doesn't work for me either, whatever I try (-H, --html, -Hfirefox, and so on). Still, there's other ways of doing things so it's no big deal.

---

### Post by Cheesemill on 2009-12-01
> **falconindy said:**
> Man pages use a markup language that pre-dates HTML called roff. The GNU implementation is, of course, called groff. Raw files are fed through nroff or troff (I forget which) to produce the formatting you see.

Semi-related: If you think man pages are pretty, you should see them in color. Try this: Install the package 'most', and then open up /etc/manpath.config with your favorite text editor (and sudo). Find your way down to around line 78 where you see a commented out line:
```
#DEFINE    pager    pager -s
```Uncomment it and change it to:
```
DEFINE     pager    most -s
```Man pages will now be in color! OOOoooOOOoooohhhh...

Nice one falconindy,

I'm a sucker for colourising my .bashrc and other things, this is a great one to add to my 'must do on a new install' stuff.

Cheers.

---

### Post by diesch on 2009-12-02
You still have to provide the man pahe you want to see, e.g.

```
man -Hfirefox ls
```

---

### Post by Land Rover Series 3 on 2009-12-02
> **diesch said:**
> You still have to provide the man pahe you want to see, e.g.

```
man -Hfirefox ls
```
Yes, I understood that, but it still doesn't work for me. But no problem, because I doubt that I'll want to view manpages in Firefox anyway (the standard system is fine for what I want). Thanks anyway

---

### Post by l-x-l on 2009-12-03
> **diesch said:**
> You still have to provide the man pahe you want to see, e.g.

```
man -Hfirefox ls
```

When I type the above in a terminal, I get the following:

```

$ man -Hfirefox ls
man: command exited with status 3: /usr/bin/zsoelim | /usr/lib/man-db/manconv -f UTF-8:ISO-8859-1 -t UTF-8//IGNORE | preconv -e UTF-8 | tbl | groff -mandoc -Thtml
```

---

### Post by diesch on 2009-12-05
Do you have *groff* installed? Maybe it's not installed by default.

---

### Post by l-x-l on 2009-12-06
> **diesch said:**
> Do you have *groff* installed? Maybe it's not installed by default.

Works now. Thx.

---

