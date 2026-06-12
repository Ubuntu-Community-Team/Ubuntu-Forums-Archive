---
title: "Sane Backend help for HP Scanjet 8250"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by js@lloyd on 2009-04-02
Sane-project.org shows that my scanner is supported:

[IMG]http://i728.photobucket.com/albums/ww284/jsinlloyd/sane.png[/IMG]

However, I don't know what to do with it.  I'm a brand new user, so this is all new to me.  Xsane recognizes my scanner when it boots up, but Xsane crashes after scan initiates.  Thanks for the help.

JS

---

### Post by schmidtbag on 2009-04-03
run it in terminal and copy the info it says when it crashes

---

### Post by js@lloyd on 2009-04-03
> **schmidtbag said:**
> run it in terminal and copy the info it says when it crashes

One of the problems that I have is that I'm new, and I don't know exactly what I'm suppposed to run in the terminal.  I do know what a terminal is, but just dont know what i need to copy/paste.

---

### Post by schmidtbag on 2009-04-03
terminal can run programs, its extremely imporant you understand what it does if you want to use linux or a unix based OS (mac barely counts as unix based).  i don't use xsane but i'm pretty sure you can just open up terminal and type "xsane"

if that doesn't work, right click on the applications menu, select "edit menus", find xsane, edit it, and type the command given in terminal

---

### Post by lexe-cc on 2009-04-03
Run a terminal
run this command (paste it into the terminal, shift+ctrl+v)
```
xsane
```
then copy the output from the terminal (shift+ctrl+c)
paste it here :)

cheerio

---

### Post by js@lloyd on 2009-04-03
> **lexe-cc said:**
> Run a terminal
run this command (paste it into the terminal, shift+ctrl+v)
```
xsane
```
then copy the output from the terminal (shift+ctrl+c)
paste it here :)

cheerio

Got it.  Here you go.  Actually, I've been told to run two in the past XSANE and sudo xsane.  Here are both:

jsinlloyd@JS-Desktop:~$ sudo xsane
[sudo] password for jsinlloyd: 
/usr/share/themes/Clearlooks/gtk-2.0/gtkrc:241: Invalid symbolic color 'selected_fg_color'
/usr/share/themes/Clearlooks/gtk-2.0/gtkrc:241: error: invalid identifier `selected_fg_color', expected valid identifier

(xsane:6485): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6485): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6485): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6485): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6485): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6485): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6485): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6485): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6485): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6485): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6485): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6485): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6485): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6485): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6485): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6485): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6485): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6485): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6485): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6485): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6485): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6485): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6485): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6485): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6485): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6485): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6485): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6485): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6485): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6485): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6485): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6485): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

---

### Post by schmidtbag on 2009-04-03
lol I have no idea what that means but luckily that seems to be a very specific error.  Try googling it or check the xsane website, it might tell you what this means.  I don't do scanning so some of that terminology means nothing to me, try checking your settings if theres weird values set to them.

---

### Post by js@lloyd on 2009-04-03
results from xsane

[IMG]http://i728.photobucket.com/albums/ww284/jsinlloyd/xsane.png[/IMG]

---

### Post by schmidtbag on 2009-04-03
as you can see, the results aren't really any different.  sudo just means you are running the program as super-user, and a program like that isn't going to change because of it.

---

### Post by lexe-cc on 2009-04-03
seems like the error comes from the program's gui? :???:
i have absolutely no clue ..

however i have encountered this gtk spinbutton before when designing a gui .. 

maybe this sounds silly, but try to open it with another theme? (check appearances)

---

