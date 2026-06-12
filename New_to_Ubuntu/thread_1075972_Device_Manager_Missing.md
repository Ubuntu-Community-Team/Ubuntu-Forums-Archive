---
title: "Device Manager Missing"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by audine on 2009-02-20
Hello,

I'm totally new to Ubuntu.  I bought The Official Ubuntu Book which came with Hardy Heron on a CD.  After finally getting it to work in safe graphics mode, I found that I could not get a wireless connection.  I decided to download 8.10 from the internet.  This version is working on my computer, graphics and wireless no problem.  One of the problems I was having with HH was I could not find the Device Manager.  It wasn't under system>administration, and gnome-device-manager was not in the Synaptic Package Manager.  Although I haven't needed to use it with 8.10, it isn't there either.  I tried to open a terminal and install from there, but I get this message:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnome-device-manager is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gnome-device-manager has no installation candidate


Now what?

Thanks,
Audine

---

### Post by BDNiner on 2009-02-20
If you search for gnome-device-manager in synaptic you can download it and install it from there. You will find the application in Applications -> System Tools -> Device Manager.

---

### Post by sydbat on 2009-02-20
You may have to enable the correct repositories.

In Hardy (sorry, don't have Intrepid) you can go to Applications > Add/Remove and choose All Available Applications.

Alternately, go into System > Administration > Software Sources and choose Main, Universe, Restricted and Mulitverse.

---

### Post by trlkly on 2009-02-20
Well, if you aren't using it, there's not much reason to install it. But if you still want to:

Enable the universe repositories:
[LIST=1]
[*]Go to System > Administration > Software Sources
[*]Type in your password if necessary.
[*]Make sure the line with the word "universe" is checked.
[*]Close Software Sources
[/LIST]

Also, I think you'll probably want to install both gnome-device-manager and libgnome-device-manager0.

Finally let me repeat my advice not to install this unless you need it. But you still may want to enable universe so you'll have more packages to choose from.

ETA: Aw, man beat me to it. Oh well. My directions are a bit more thorough, so I'll leave them up.

---

