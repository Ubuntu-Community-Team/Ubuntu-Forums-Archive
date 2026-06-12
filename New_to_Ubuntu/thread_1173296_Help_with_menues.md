---
title: "Help with menues"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by tiggsy on 2009-05-29
Ubuntu is great, and I am generally pleased I switched 

But

there is one thing that really pisses me off 

When i install something in synaptic, i expect to be able to use it. So I look in the menus, and I try looking in the hidden stuff in the menus (in edit menus). Sometimes it's there. Often it's not.

Then I look in a couple of folders, ~Home and so on. After a while i give up. I've tried using search, this just wastes more time, and rarely finds anything - which is sad. Bad as the Windows search function is, it usually finds things eventually.

You can't use it if you can't find it, so in the end i just uninstall the stuff again, no point cluttering up the system with stuff i can't use

THIS IS REALLY ANNOYING, not to say a big time waster

---

### Post by Bölvaður on 2009-05-29
> **tiggsy said:**
> Ubuntu is great, and I am generally pleased I switched 

But

there is one thing that really pisses me off 

When i install something in synaptic, i expect to be able to use it. So I look in the menus, and I try looking in the hidden stuff in the menus (in edit menus). Sometimes it's there. Often it's not.

Then I look in a couple of folders, ~Home and so on. After a while i give up. I've tried using search, this just wastes more time, and rarely finds anything - which is sad. Bad as the Windows search function is, it usually finds things eventually.

You can't use it if you can't find it, so in the end i just uninstall the stuff again, no point cluttering up the system with stuff i can't use

THIS IS REALLY ANNOYING, not to say a big time waster


press Alt+F2 and the name of the program or the package you installed. It often works.
Sometimes menu items are not added, sometimes because of a reason and sometimes it seems to have been forgotten. Then you'll have to check the name of the package and make your own launcher with the package name as the command.

---

### Post by ranch hand on 2009-05-29
This thread is for suggestions for and information about Ubuntu education.  This is a bunch of oppertunities to join others in learning about and running Ubuntu.

Your post seems to be a general gripe.  I suggest that this is not the place for it.

That said, have you tried opening the terminal and simply typing the name of the app you are trying to use.  this should open it.

---

### Post by bodhi.zazen on 2009-05-29
> **tiggsy said:**
> Ubuntu is great, and I am generally pleased I switched 

Edit: Moved to ABT ;)

But

there is one thing that really pisses me off 

When i install something in synaptic, i expect to be able to use it. So I look in the menus, and I try looking in the hidden stuff in the menus (in edit menus). Sometimes it's there. Often it's not.

Then I look in a couple of folders, ~Home and so on. After a while i give up. I've tried using search, this just wastes more time, and rarely finds anything - which is sad. Bad as the Windows search function is, it usually finds things eventually.

You can't use it if you can't find it, so in the end i just uninstall the stuff again, no point cluttering up the system with stuff i can't use

THIS IS REALLY ANNOYING, not to say a big time waster

A few observations.

Although uncommon, sometimes you need to log off and back on for newly installed applications to appear in your menu.

Another potential problem, not all applications are graphical, ie some are command line only, and thus will not appear in your menu.

There are a number of search functions in Ubuntu and I will list the ones I use to find applications (I use the terminal).

1. Which - say your application is called "foo" -

```
which foo
```2. locate -

```
locate foo
```locate uses a data base which is updated automatically every 24 hours , so with a newly installed application you will need to automatically update it yourself first ...

```
sudo updatedb
```
=== 

With that said, if needed, you can always add a "launcher" to your menu. When adding a launcher click the menu button and navigate to your application.

---

