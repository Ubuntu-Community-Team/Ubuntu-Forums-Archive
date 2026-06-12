---
title: "how to use Recoll in gnome"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by gkraju on 2009-06-29
hi i have installed Recoll 1.12 to search files in my system 
it indexes the files properly but when i try open files or folder 
it shows some error dialog saying
[B][I]
The viewer specified in mimeconf for application/pdf :pdf is not found[/I][/B]

i am having Ubuntu 8.04 Gnome 2.22

please help thanks in advance

---

### Post by aharown07 on 2009-09-10
If you do some more reading at the Recoll site you'll find more info there, but in general, what that error means is that you need some helper libraries to give Recoll the ability to index various file types. In fact, if you run Recoll, let it index, then select Help->Show missing helpers, it'll list which ones you need.

But it's good to compare that list to the helpers page at the Recoll site because the files/packages (whatever the right term is) listed in "missing helpers" are often parts of larger packages that go by another name in Synaptic.

Once you identify the packages you need, to go synaptic, look them up and install them. Works great.

---

