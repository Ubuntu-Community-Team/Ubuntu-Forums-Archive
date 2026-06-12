---
title: "Google Earth &amp; Gourmet"
date: 2010-07-20
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2010-07-20
Both Google Earth & Gourmet Recipe Manager seem to break today. I've done nothing unusual. Earth stalls at the first screen and has to be stopped with the Kill command. Gourmet gives an error about no plugin to import URL. Screenshot of that, attached.

---

### Post by tgalati4 on 2010-07-20
For googleearth, try turning off Compiz.  Open a terminal:

metacity --replace
googleearth --debug

Post any errors.  Can't help with gourmet since I haven't used it.

---

### Post by Mark_in_Hollywood on 2010-07-21
I turned off compiz. 

In a terminal I tried:

metacity --replace
googleearth --debug

see attached screenshots.

metacity hung, and locked the desktop

and 

googleearth --debug


returned command not found

---

### Post by tgalati4 on 2010-07-27
When I run googleearth, I have to turn off compiz.  Running:

metacity --replace

is supposed to run the metacity (a 2D desktop manager that is standard with Gnome).  The fact that metacity doesn't run properly means you might have other issues.  You shouldn't turn off compiz first--that will lock up the desktop quickly.  metacity --replace with turn off compiz and then replace it with metacity.  Then you should be able to run googleearth.

I'm running it under Jaunty and I get the following in a terminal:

tgalati4@tpad-Gloria7 ~ $ googleearth --debug
Warning: Unable to create prefs directory '/home/tgalati4/.googleearth'. File exists.

(And it comes up and runs normally with no errors.)

If you can't find googleearth then:

whereis googleearth

For me:

tgalati4@tpad-Gloria7 ~ $ whereis googleearth
googleearth: /usr/bin/googleearth /usr/lib/googleearth /usr/share/googleearth /usr/share/man/man1/googleearth.1.gz


When you are finished with googleearth, shut it down then:

compiz --replace

Normally one writes a script to turn replace compiz with metacity, run googleearth, then rerun compiz.  You can modify the script /usr/bin/googleearth to accomplish this.

Since you are running Lucid, it's possible there is some other graphics issue.

---

