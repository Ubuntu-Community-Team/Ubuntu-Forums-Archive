---
title: "Meaning of a command"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by Souptik on 2011-02-20
Hi, What does "apt-get autoremove" do ???? Yes I understand it removes some unneeded packages, but how does it select what to remove and what not to remove ????

---

### Post by yeats on 2011-02-20
When you install a package with apt-get (or aptitude or synaptic or the Ubuntu Software Center), it automatically installs all the programs that the selected program depends on.  If you later remove that program, it does not remove the dependencies unless you tell it to.  The autoremove program keeps you from having to manually track down each dependency that's no longer needed.

---

### Post by Souptik on 2011-02-20
> **yeats said:**
> When you install a package with apt-get (or aptitude or synaptic or the Ubuntu Software Center), it automatically installs all the programs that the selected program depends on.  If you later remove that program, it does not remove the dependencies unless you tell it to.  The autoremove program keeps you from having to manually track down each dependency that's no longer needed.

Firstly, thanks for your response.
Does this mean simply that App A depends on App B... and if I uninstall App B and then give the command then App A will be uninstalled ??? Forgive me, I am a complete noob, and some serious advice on "simple" things...:lolflag:

---

### Post by yeats on 2011-02-20
> Does this mean simply that App A depends on App B... and if I uninstall App B and then give the command then App A will be uninstalled ???

Yes - if you ```
sudo apt-get install app-a
``` you will see something like "this following packages are required and will also be installed", and that list of packages will include App B.  The APT system is smart enough that if you (for whatever reason) did ```
sudo apt-get remove app-b
```, it would say "the following packages will also be removed" and list App A among them.

You might also try using aptitude rather than apt-get if dependencies are a big deal - it's got a more complex way of resolving dependency problems.  Experiment and see (you might try all that in a VM rather than on your main system ;-) ).

---

### Post by Souptik on 2011-02-20
> **yeats said:**
> Yes - if you ```
sudo apt-get install app-a
``` you will see something like "this following packages are required and will also be installed", and that list of packages will include App B.  The APT system is smart enough that if you (for whatever reason) did ```
sudo apt-get remove app-b
```, it would say "the following packages will also be removed" and list App A among them.

You might also try using aptitude rather than apt-get if dependencies are a big deal - it's got a more complex way of resolving dependency problems.  Experiment and see (you might try all that in a VM rather than on your main system ;-) ).


Thank you very much. This has solved my confusion quite nicely. I will mark the thread solved.

---

