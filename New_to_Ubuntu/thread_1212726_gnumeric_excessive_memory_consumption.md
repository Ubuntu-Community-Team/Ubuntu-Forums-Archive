---
title: "gnumeric excessive memory consumption"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by Javhar_ on 2009-07-14
Gnumeric is my favourite spreadsheet, but I do have one issue with it...

I have lots of CSV files, each with a filesize of around 5Mb - 10Mb and containing on the order of 10k - 50k rows and up to 10 or 20 columns. Reading one into Gnumeric works fine. But when I try to sort, or copy or add a column, memory consumption balloons. Sometimes it sails way past 1Gb, at which point everything becomes entirely unresponsive. Mouse pointer moves only very slowly and does not respond to clicks anymore. Some keyboard commands still work, with massive delay. If I happen to have a terminal window in focus I can kill Gnumeric which revives everything else. Otherwise I'm forced to log out. This even happens when I start up Gnumeric with nice -10 by default.

I haven't been able to find anything about this in any forums. Is it just me, or does anyone else have this Gnumeric problem?

Is there any way I can limit the memory consumption of a given application?

---

### Post by Sef on 2009-07-14
Have you checked [gnumerics]("http://projects.gnome.org/gnumeric/") website?

---

### Post by jbrefort on 2009-07-14
It might be a gnumeric bug. Please file a bug report at bugzilla.gnome.org, attach a sample file and details about how to reproduce.

---

