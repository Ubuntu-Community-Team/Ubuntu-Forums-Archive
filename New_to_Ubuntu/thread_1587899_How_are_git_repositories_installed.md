---
title: "How are git repositories installed?"
date: 2010-10-04
forum: New to Ubuntu
---

### Post by mr_luksom on 2010-10-04
At the risk of asking a dumb question, how do I install something from a git repository? Do I add it into aptitude? Is there another system?

---

### Post by Perfect Storm on 2010-10-04
usually
git clone <link> <folder>
but in most cases <folder> are not needed as it will create one for you (in most cases). Make sure to install git tool first.

try 
man git 
for more info and flags.

Then you need to get into its directory and compile the stuff.


Edit: if you want to learn more about git: [http://git-scm.com/](http://git-scm.com/)

---

### Post by mr_luksom on 2010-10-04
Okay, so git is really a about managing the files in a project, and 'git clone' copies them to your machine to use (compile etc).

---

### Post by Perfect Storm on 2010-10-04
Aye, it's like cvs, Mercury to get a look at a development point in a project or for multiply developers working on the same project, but they are sitting in diffrent location on the globe.

---

