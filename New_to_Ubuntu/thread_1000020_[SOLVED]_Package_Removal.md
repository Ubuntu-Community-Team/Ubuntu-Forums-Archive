---
title: "[SOLVED] Package Removal"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by majestic12 on 2008-12-02
Hello all, 
I am new to Ubuntu, but a longtime user of Linux, specifically .rpm
based distros.  Is there a way to use Synaptic or KPackage to remove
a single application?  For instance if I want to remove kmahjongg or kmines?
When I select a single app, it does an upstream dependency check and wants to remove the whole of KDE...not necessary...or wanted. Also is there no way to remove categories of software such as kde-toys only?

---

### Post by Dedoimedo on 2008-12-02
Hello,
Why would you want to leave dependecies that no other app needs?
It's leaving leftovers that are unneeded and clutter space.
Dedoimedo

---

### Post by majestic12 on 2008-12-02
> **Dedoimedo said:**
> Hello,
Why would you want to leave dependecies that no other app needs?
It's leaving leftovers that are unneeded and clutter space.
Dedoimedo

The problem is I want to remove simply 1 game from the system and it wants to remove the whole of KDE.  I don't want to do that, so no, KDE does not depend on kmines....kmines depends on KDE.

---

### Post by SunnyRabbiera on 2008-12-02
it is strange that its doing this, usually when you just mark a game package or something it will just remove the game.
What version of KDE is this app based on?
you can get information with the help option in the menu

---

### Post by anotherdisciple on 2008-12-02
Before 8.10 *buntu has had a meta-package called *buntu-desktop... it used to depend on a lot of unnecessary programs. If you remove the dependency... it removes the whole dependency list in the meta-package.

However. in 8.10 it seemed to fix this... most of the packages are in "Recommends" instead. This makes for less headaches when you are removing unwanted software.

---

### Post by anotherdisciple on 2008-12-02
Also... if you remove with aptitude... it gives you the option to leave dependencies unresolved... you could try that.

---

### Post by Dedoimedo on 2008-12-02
I do not think Synaptic is trying to uninstall the whole of KDE, simply the dependencies specific for that application.
Did you try from the command line: sudo apt-get remove <application>?

Dedoimedo

---

### Post by majestic12 on 2008-12-02
> **SunnyRabbiera said:**
> it is strange that its doing this, usually when you just mark a game package or something it will just remove the game.
What version of KDE is this app based on?
you can get information with the help option in the menu

This is Ubuntu 8.04 LTS Server with KDE 3.5.10 installed and synaptic.  I am in Synaptic, select Games and Amusement.  In the package list the top 3 are amor, atlantik and atlantikdesigner. If I select any of these and set to 'Mark for Removal' I get a popup window that says 'Mark additional required changes?' There is an area that says
'To be removed' with selections of kde and kdeaddons.  It asks/wants me to mark some of them.  Even if I mark none of them and click the Mark button, 

Using 'amor' as an example, when I mark it for removal and click Apply I get a dialog that says 35 packages will be held back and 4 will be removed. 2294KB of space will be freed and in the To be removed section I see:

amor
kde
kdeamusements
kdetoys

I think it's just a display problem.  I gambled and told it to go ahead and it looks like it just removed amor.

Is there no higher level granularity that I can remove entire packages like kdetoys?

---

