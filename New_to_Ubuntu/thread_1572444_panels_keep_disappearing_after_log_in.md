---
title: "panels keep disappearing after log in"
date: 2010-09-11
forum: New to Ubuntu
---

### Post by rs87424 on 2010-09-11
I have lucid and after I log in my desktop will pop up with the icons but the panels are gone.  Eventually after much effort and rebooting several times I get the panels to come back again.  I just need to figure out why the panels come and go without warning.  Feedback would be much appreciated

---

### Post by rolnics on 2010-09-11
Are you running compiz or anything like that?

---

### Post by rs87424 on 2010-09-11
I am actually

---

### Post by BJones007 on 2010-09-11
> **rs87424 said:**
> I have lucid and after I log in my desktop will pop up with the icons but the panels are gone.  Eventually after much effort and rebooting several times I get the panels to come back again.  I just need to figure out why the panels come and go without warning.  Feedback would be much appreciated
Right click on the panel and select properties and un - tick autohide. That should work

---

### Post by rs87424 on 2010-09-11
well I wish it was that simple.  its not on autohide and I never use autohide the panels are simply completely gone for the whole session I am logged in

---

### Post by ssdt on 2010-09-11
Maybe try to go back to metacity. metacity --replace might be good for that.

---

### Post by BJones007 on 2010-09-12
Ok try this in the terminal (alt+f2 search for gnome-terminal) then type this command: sudo apt-get install gnome-panel
lemme know if that works

---

### Post by rs87424 on 2010-09-13
it just says that I already have the newest panel version

---

### Post by rs87424 on 2010-09-13
and now its really bad... like they are showing and nothing is on them anymore.. no volume no preferences nothing... and it happens randomly and my speakers start crackling its horrible... I am so tired of this happening just about every time I get an update

---

### Post by rs87424 on 2010-09-13
OK OK.... I have the solution.  I saw that you posted the install for the panels.  Well I thought if I just remove them and install them again that would fix the problem... 

[PHP]sudo apt-get remove gnome-panel[/PHP]

then:

[PHP]sudo apt-get install gnome-panel[/PHP]

that did the trick... anyone else with this problem should feel free to use this as a fix.. and thanks for the code because I couldn't remember exactly what I needed to type in the terminal

---

