---
title: "Efax-Gtk Can't find ps viewer"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by LearningPerson on 2008-12-12
Hello,

My fax was working last week and I could view one fax sent to me.  Today the message was: "Can't find the ps view program - please check your installation and the path environmental variable"

I can use the terminal if each command is spelled out.  Don't seem to be intuitive otherwise.

Thanks (and I did check but nothing was exactly what I need).

Sharon

---

### Post by LearningPerson on 2008-12-13
> **LearningPerson said:**
> Hello,

My fax was working last week and I could view one fax sent to me.  Today the message was: "Can't find the ps view program - please check your installation and the path environmental variable"

I can use the terminal if each command is spelled out.  Don't seem to be intuitive otherwise.

Thanks (and I did check but nothing was exactly what I need).

Sharon

Solved by going into Efax-Gtk, File, Settings, Print and changed the "lpr" setting to "Use GTK +  print system".  

Works fine now.  Hope this helps someone else.

---

### Post by bob12564 on 2009-12-01
Your post just help me!  Thanks!  I chose Evince as my viewer and that works well.

---

