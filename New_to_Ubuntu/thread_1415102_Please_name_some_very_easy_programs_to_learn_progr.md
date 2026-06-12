---
title: "Please name some very easy programs to learn programming"
date: 2010-02-24
forum: New to Ubuntu
---

### Post by oingk on 2010-02-24
Hi

A long time ago (about 12 years ago), when I was younger, my geek friend got me into "programming" (if it can be called that). Basically we were making a program on the computer (that was usable on Microsoft systems of the time, I would guess one of the first types of commercial Windows avaiable) where a user could talk to a virtual talker. The program thus would give you a text, like "Hi" and await your responce. Depending on your responce, the program would answer back. For example if program sais "how are you", and you type in "not good", the progam would ask, "why what's the problem?". 

A thing I remember was that we used to "program" it by saying something like "IF blah blah, THEN blah blah", which would go to say "If user sais this, then answer this".

The program was really fun and we used to let our classmates who were still computer-clueless to play with it so that we would compete for who has made the most human mind-like program.

For a long time I gave up with using computers and now I'm starting to play with them again. Now I really want to remember what this program was, so that I can start to slowly learn to program. But I can't ask my friend (he is "dead").

Can you guys help me reminding me of what this program is probably called?
I would really appreciate this.

I know this program is probably really low level for most of you, but not for me as I am in the beginning steps of "programming".

Also, another request I have from you, is to give me a name of a  (maybe similar) easy to use program that I can use on Linux as a first step to learn some computer programming.

Thanks.

---

### Post by mvalviar on 2010-02-24
Is that a code in BASIC? If you want to learn programming I suggest you learn python. No better way to learn it than to learn it from [MIT]("http://ocw.mit.edu/OcwWeb/Electrical-Engineering-and-Computer-Science/6-00Fall-2008/CourseHome/index.htm").

---

### Post by oingk on 2010-02-24
Yes I believe it was called something like "BASIC". OK I will give Python a try.

---

### Post by raydeen on 2010-02-24
It sounds like you guys were working on a variant of Eliza

[http://en.wikipedia.org/wiki/ELIZA]("http://en.wikipedia.org/wiki/ELIZA")

I would think Python might be a good candidate for doing a version of the program as it can do some pretty good text parsing. Eliza pretty much just looked at what the user typed in, picked out some key words and then spit out a sentence or question based on those words. There's some web based programs that do this now. They go the extra mile by remembering what other users have typed and applying that to similar sentences that new users type.

---

### Post by oingk on 2010-02-24
raydeen, I'm not sure if it was a variant of ELIZA, but I don't think it was called "ELIZA", I think the name of it sounded something like BASIC. However, thanks for telling me about ELIZA and the other info, I find it interesting.

---

### Post by sukamusiru on 2010-02-24
> **mvalviar said:**
> Is that a code in BASIC? If you want to learn programming I suggest you learn python. No better way to learn it than to learn it from [MIT]("http://ocw.mit.edu/OcwWeb/Electrical-Engineering-and-Computer-Science/6-00Fall-2008/CourseHome/index.htm").

It's not the most pythonic code (one of the professors is learning as he goes) but it is a good launchpad.

---

### Post by Miljet on 2010-02-24
Here is another vote for Python. There is an excellent 7 part introduction to programming in Python in the free Full Circle on-line magazines.

[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

### Post by J V on 2010-02-24
That would be QBASIC (now replaced with visual basic cause no-one uses command prompt in windows world)

Python: Highest level client-side language available
C#4: finally has dynamic typing, making it best... no compiler available yet though so no good
PHP: Much better than Python IMO but it just doesn't feel right for a client-side program

Quick package that should get you started:

```
sudo apt-get install glade gedit-plugins
cd /tmp
wget -r "http://live.gnome.org/Gedit/Plugins?action=AttachFile&do=get&target=python_indentation.tar.gz"
sudo tar -xzf "Plugins?action=AttachFile&do=get&target=python_indentation.tar.gz" --overwrite --directory "/usr/lib/gedit-2/plugins"
rm -f "Plugins?action=AttachFile&do=get&target=python_indentation.tar.gz"
cd
gconftool-2 --type list --list-type string --set /apps/gedit-2/plugins/active-plugins [filebrowser,spell,docinfo,time,codecomment,externaltools,joinlines,sessionsaver,terminal,devhelp,indent,modelines,python_indentation]
gconftool-2 --type bool --set /apps/gedit-2/preferences/ui/bottom_panel/bottom_panel_visible true
gconftool-2 --type int --set /apps/gedit-2/preferences/ui/recents/max_recents 20
gconftool-2 --type bool --set /apps/gedit-2/preferences/ui/side_pane/side_pane_visible true
gconftool-2 --type bool --set /apps/gedit-2/preferences/syntax_highlighting/enable true
gconftool-2 --type bool --set /apps/gedit-2/preferences/editor/auto_indent/auto_indent true
gconftool-2 --type bool --set /apps/gedit-2/preferences/editor/bracket_matching/bracket_matching true
gconftool-2 --type bool --set /apps/gedit-2/preferences/editor/current_line/highlight_current_line true
gconftool-2 --type bool --set /apps/gedit-2/preferences/editor/line_numbers/display_line_numbers true
gconftool-2 --type bool --set /apps/gedit-2/preferences/editor/right_margin/display_right_margin true
gconftool-2 --type bool --set /apps/gedit-2/preferences/editor/save/auto_save true
gconftool-2 --type bool --set /apps/gedit-2/preferences/editor/search_highlighting/enable true
gconftool-2 --type bool --set /apps/gedit-2/preferences/editor/tabs/insert_spaces true
gconftool-2 --type int --set /apps/gedit-2/preferences/editor/tabs/tabs_size 4
gconftool-2 --type string --set /apps/gedit-2/preferences/editor/wrap_mode/wrap_mode "GTK_WRAP_WORD"
```

---

### Post by oingk on 2010-02-24
You're right, it was QBASIC.

I will definetely try Python.

Regarding PHP, wouldn't that also be valuable for website building? I am also building a website and so far its only HTML and CSS based. Many functions I want to give it I find that they require PHP language. Wouldn't that be the same PHP as the one you are talking about here?

---

### Post by Mark Phelps on 2010-02-25
My own background involves several decades of computer systems engineering with nearly half of that spent in software engineering of some form or other -- ranging from 1st generation languages (yes, machine code), to 5th general languages.  Along the way, I got involved with writing microcode (not code for microcomputers), device drivers, kernel routines, web pages (HTML and JavaScript), and even messing around with Cold Fusion and FrontPage.

Which is a roundabout way of saying that there are a LOT of choices regarding which kind of programming you want to do, why you want to do it -- and the unfortunate realization that there is not enough time to learn them all.

For example, if your interest is personal (as in, curiosity), it doesn't really matter which programming type and language you pick as long as you find the result satisfying.

But, if your purpose is in turning your knowledge into a job, you would do better asking folks who are already employed as programmers what they would recommend. I mention this because I read a blog article recently claiming that some high percentage of open source programmers were paid for their work, in other words, professionally employed.  So, if employment as a programmer is your end state goal, you need to check out where the programmers work and what tools/languages they use.

---

### Post by oingk on 2010-03-12
Hi

OK. Basically, for the moment, the reason that I mostly want to learn programming is for using this knowledge into website development.

For now, I am making a website "from scratch" that is based on HTML and CSS codes. I want to go some steps further to make my website more interactive to visitors. There are also manyother things I have in mind for my website that I can't do using only HTML and CSS.

Please refer me to some programming language or whatever it's called, that will help me improve my website.

---

