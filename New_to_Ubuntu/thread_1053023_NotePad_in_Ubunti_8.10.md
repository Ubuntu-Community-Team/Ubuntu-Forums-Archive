---
title: "NotePad in Ubunti 8.10"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by enrico68 on 2009-01-28
Sorry if I asked this before, but it is still not clear to me: what is the program in Ubuntu that replicates Notepad for Windows? I am studying the C language, I have the compiler, but need the notepad to write the source code. From reading other threads I understand that either of the following should do: Gedit, Leafpad, Kate. Is that correct? If so, how do I access anyone of them, once I start Ubuntu up? Thanks 

ENRICO

---

### Post by happycodemonkey on 2009-01-28
If you're running Gnome, gEdit is the way to go. I think you'll be much more pleased with it than Notepad, the syntax highlighting is very nice. 

After you install it using either apt-get or Synaptic, it should just show up in your applications menu under Accessories...I believe it's called "Text Editor" for whatever reason, rather than gEdit in the menu.

---

### Post by ptn107 on 2009-01-28
gedit, Applications -> Accessories -> Text Editor

---

### Post by rrashkin on 2009-01-28
It should be available under Applications>Accessories

---

### Post by enrico68 on 2009-01-28
Thanks everyone, I'll give it a try tonite, I am really curious to see what it looks like...

---

### Post by Therion on 2009-01-28
It looks something like this:

[http://ubuntu-ku.org/sorani/a/wp-content/uploads/2008/05/gedit2.png](http://ubuntu-ku.org/sorani/a/wp-content/uploads/2008/05/gedit2.png)

---

### Post by resander on 2009-01-28
You can also install the code::blocks IDE (Integrated Development Environment) that contains an editor and lots more for program development. Info at [www.codeblocks.org](www.codeblocks.org).

You can download from synaptic using codeblocks as searchkey. 

To get latest codeblocks version (usually best choice):

i)  enter 'sudo gedit /etc/apt/sources.list' (without the quotes) and when in editor
    add lines

     deb [http://apt.jenslody.de/](http://apt.jenslody.de/) any main
     deb-src [http://apt.jenslody.de/](http://apt.jenslody.de/) any main
     deb [http://apt.wxwidgets.org/](http://apt.wxwidgets.org/) etch-wx main

    at the end of /etc/apt/sources.list

    OR

    select Software Sources from the GUI Administration menu,
    select Third Party Software and add the three lines above
 
 ii)  enter 'apt-get install jens-lody-debian-keyring' from terminal

 iii) enter 'wget -q [http://apt.wxwidgets.org/key.asc](http://apt.wxwidgets.org/key.asc) -O-  | sudo apt-key add -' from terminal

 iv)  use apt-get update and apt-get install codeblocks OR use 
      update and install via Synaptic manager

---

### Post by jimmy the saint on 2009-01-28
Once you have tried it out, read these articles on great plugins to make it it an even better editor for programmers.

[http://lifehacker.com/software/linux-tip/give-gedit-the-power-of-textmate-321945.php](http://lifehacker.com/software/linux-tip/give-gedit-the-power-of-textmate-321945.php)
[http://tombuntu.com/index.php/2008/05/15/extending-the-gedit-text-editor-with-plugins/](http://tombuntu.com/index.php/2008/05/15/extending-the-gedit-text-editor-with-plugins/)

---

### Post by Hospadar on 2009-01-28
I really like kate, the kde text editor, you can install it with synaptic.
the newest version even has a built-in terminal (you might need konsole installed for it to work) for compiling and whatnot

if you want a more complete development environment, try kdevelop or eclipse with cdt.
for a beginner though i woud stick to a text editor and terminal

---

