---
title: "[SOLVED] Gnome - Web Development Editor"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by suncoolsu on 2008-12-13
I want a good Web Development Editor only for GNOME (no KDE)
One I am aware of is Blue Fish

Any other suggestions??

Also if anyone can suggest me a good LaTeX editor for gnome (similar to KILE on KDE) 
I have used WINEFISH - didnt like it that much. Kile doesnt work very well for me on Gnome.

Thx

---

### Post by epitaph on 2008-12-13
For LaTeX, I use gedit with the LaTeX plugin:

[http://live.gnome.org/Gedit/LaTeXPlugin](http://live.gnome.org/Gedit/LaTeXPlugin)

You could also try TeXmaker, which will more closely resemble kile:

```
sudo apt-get install texmaker
```

You could just install kile in gnome too.

For web development everyone is going to have different preferences. I don't do anything intense and am quite happy with gedit myself. Might want someone with more web development experience to answer on that one.

---

### Post by tinny on 2008-12-13
For static web development (HTML, CSS) I like KompoZer (available in the Ubuntu repositories)

[http://kompozer.sourceforge.net/](http://kompozer.sourceforge.net/)

---

### Post by Primefalcon on 2008-12-13
try Quanta plus if your after a graphical editor

cssed is a great css editor as well

personaly I like just gedit or vi but hey that's me

---

### Post by theApokalypsis on 2008-12-13
Aptana Studio is by far the most advanced give the Web 2.0 age and such. Its based of Eclipse. It can be a plugin or a standalone download. JS, PHP, Rails editors with intellisense. CSS/XHTML editors, FTP support and more.

[http://www.aptana.com/](http://www.aptana.com/)

---

### Post by suncoolsu on 2008-12-14
Thanks to all of u guys... I have installed Kompozer and I liked it a lot..Cuz I am not just need HTML and CSS

Regarding the LaTeX editor. How to install the LaTeX plugin from tarbell? Please tell?

Kile on Gnome always gives me some compiling problem. I tried installing Kile on gnome but the Tex files which were alright on my KDE Desktop start to show errors when compile with Kile (pdflatex in kile) on Gnome. Do you guys know a solution to this?

Thx 
B

---

### Post by epitaph on 2008-12-14
Have you installed the texlive package?

```
sudo apt-get install texlive
```

---

