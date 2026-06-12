---
title: "flowchart generator"
date: 2010-08-04
forum: New to Ubuntu
---

### Post by gaurish108 on 2010-08-04
Hi, I am using Ubuntu 10.04. I am currently learning C, and was wondering if there was any open source software which could create a flowchart for a C program. Can anyone suggest the best one if there are any?

I know that using Data Display Debugger we can run through the program flow, but a flowchart maker would also be invaluable.

---

### Post by 23dornot23d on 2010-08-04
[DIA is pretty good]("http://www.linux.com/learn/tutorials/289802:creating-flowcharts-with-dia") and is in synaptic ......

[More examples]("http://techblissonline.com/create-flow-chart-uml-diagram-network-diagram/")

---

### Post by tgalati4 on 2010-08-04
What you want is an automated code parser that creates a flowchart from somebody's code.  I don't know of any offhand, but there are some UML tools (Unified Modeling Language) that will read C code and create Class connection diagrams.  It's not exactly a flowchart, but it will help parse a complex software project.

This is one that I have used:

[http://argouml.tigris.org/](http://argouml.tigris.org/)

---

### Post by mbsullivan on 2010-08-04
DDD's going to operate on the program dynamically (i.e. with real program inputs).

If you're more interested in the dynamic behavior of a program, rather than the static properties of the code, then you'll want to generate the callgraphs of the application.

Kcachegrind is an intuitive profiler which can also visualize the callgraphs for a program run. This is useful because it not only shows you the connections in a program, but it also tells you where most of the time is spent in the program.

Kcachegrind will generate an output that looks like [this]("http://sandroandrade.files.wordpress.com/2009/04/kcgshot3large.gif"). It is available in the repos via:

```
sudo aptitude install kcachegrind
```

Mike

---

