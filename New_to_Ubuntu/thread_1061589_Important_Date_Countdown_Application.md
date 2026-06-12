---
title: "Important Date Countdown Application"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by styyle14 on 2009-02-05
I know that there is a countdown tool for the gnome panel, yet it only allows for a maximum of several hours to be selected.  I am looking for a way to countdown the time until graduation which is several months away, that way I can log onto my computer and see how many days I have left.  Is there a way to make the panel applet do this, or is there another program out there to do this for me?  I tried several google searches, but the word "countdown" brought up largely irrelevant articles.

Any Help Would Be Greatly Appreciated,
Styyle14

P.S. I also run KDE, so any app that would work for that may be useful as well.

---

### Post by SteveDee on 2009-02-06
> **styyle14 said:**
> I know that there is a countdown tool for the gnome panel, yet it only allows for a maximum of several hours to be selected.  I am looking for a way to countdown the time until graduation which is several months away, that way I can log onto my computer and see how many days I have left.  Is there a way to make the panel applet do this, or is there another program out there to do this for me?  I tried several google searches, but the word "countdown" brought up largely irrelevant articles.

Any Help Would Be Greatly Appreciated,
Styyle14

P.S. I also run KDE, so any app that would work for that may be useful as well.

Its really easy to write a very short program to do this. Why not download Gambas, start a new project, and in the FMain class add this code:-

PUBLIC SUB Form_Open()
   ME.Caption = "Only " & DateDiff(Date, "02/27/2009", gb.day) & " days left to go!"
END


When your program runs there will be a blank window with the caption:-
"Only 21 days left to go!"

Replace "02/27/2009" with your [graduation] end date.

---

### Post by clapper65 on 2010-04-04
Thanks Steve.  I was looking for an applet to do this, but I like the Gambas program better.

---

### Post by bumeshrai on 2012-10-15
Its a really simple solution. Great Work!!

---

### Post by oldos2er on 2012-10-15
Old thread closed, please don't bump old threads.

---

