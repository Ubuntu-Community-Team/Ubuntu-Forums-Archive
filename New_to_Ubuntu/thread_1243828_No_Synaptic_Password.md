---
title: "No Synaptic Password"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by cat2005 on 2009-08-18
I logged into synaptic to check something a moment ago.  I had to use my password.  I then exited.  A few minutes later, I need to re-enter synaptic.  I did so, but was not asked for a password.  

Why is that?  More importantly, how can I fix the system such that it asks for a password every time I want to do an admin task, even if I just did that same task 2 or 3 minutes ago?

---

### Post by LewRockwell on 2009-08-18
> **cat2005 said:**
> I logged into synaptic to check something a moment ago.  I had to use my password.  I then exited.  A few minutes later, I need to re-enter synaptic.  I did so, but was not asked for a password.  

Why is that?  More importantly, how can I fix the system such that it asks for a password every time I want to do an admin task, even if I just did that same task 2 or 3 minutes ago?

[http://ubuntuforums.org/showthread.php?t=82456](http://ubuntuforums.org/showthread.php?t=82456)

.

---

### Post by cat2005 on 2009-08-18
> **LewRockwell said:**
> [http://ubuntuforums.org/showthread.php?t=82456](http://ubuntuforums.org/showthread.php?t=82456)

.


Hi,

Yes, I have been to that website but am still lost.  I used to run Mepis and it had a "superuser file manager".  I could click on it and enter my root password.  From there, I could find any critical document (fstab, etc) and edit it if needed.  No other window would have root, just the one I opened.

I am trying to find / do something like that for Ubuntu-Gnome.  I am using Ubuntu 9.04 at the moment.  

I tried "gksudo gedit", but that was very confusing.  Neverthless, looking here:  

[http://ubuntuforums.org/showthread.php?t=24008](http://ubuntuforums.org/showthread.php?t=24008)  (post #5)

seems to give some guidance on how to create a "launcher".  A launcher could work but to be honest, I do not understand the instructions given.  Am I supposed to put those lines into terminal or somewhere else?  Once completed, would this launcher still prompt me for a root password?  

Sorry, but I grew up Windows.  I hope Ubuntu proves to be a good de-tox program.  :-) 

Thanks.

---

### Post by drs305 on 2009-08-18
> **cat2005 said:**
> 
seems to give some guidance on how to create a "launcher".  A launcher could work but to be honest, I do not understand the instructions given.  Am I supposed to put those lines into terminal or somewhere else?  Once completed, would this launcher still prompt me for a root password?  

Sorry, but I grew up Windows.  I hope Ubuntu proves to be a good de-tox program.  :-) 

Thanks.

To create a launcher, right click on the panel, Add to Panel, Custom Application Launcher. Name it what you want. In the command line, in the example you referenced, add: **gksudo "gnome-open %u"**
Click OK to save the shortcut.

You can drag any file to that panel icon and the file will open with the default gui app run as root.

You would still be prompted for a password in this example.

---

### Post by stoogiebuncho on 2009-08-18
If you want a "superuser file manager", you should try this:

```
gksudo nautilus
```

(Nautilus is the file manager in Ubuntu (assuming you're running gnome).  Putting the "gksudo" in front of it opens it as root and will ask you for a password)

You can create a launcher by putting that code in the "command" line of a launcher, as described above.

---

### Post by cat2005 on 2009-08-18
> **drs305 said:**
> To create a launcher, right click on the panel, Add to Panel, Custom Application Launcher. Name it what you want. In the command line, in the example you referenced, add: **gksudo "gnome-open %u"**
Click OK to save the shortcut.

You can drag any file to that panel icon and the file will open with the default gui app run as root.

You would still be prompted for a password in this example.


Oh....I see now....I should type 

[B]gksudo "gnome-open %u"
[/B]
in the application launcher "command line" not terminal "command line".    Thanks.

---

### Post by cat2005 on 2009-08-18
> **stoogiebuncho said:**
> If you want a "superuser file manager", you should try this:

```
gksudo nautilus
```(Nautilus is the file manager in Ubuntu (assuming you're running gnome).  Putting the "gksudo" in front of it opens it as root and will ask you for a password)

You can create a launcher by putting that code in the "command" line of a launcher, as described above.


Question:  When creating a launcher, what is the difference between putting:

[B]gksudo "gnome-open %u"
[/B]
and

[B]gksudo nautilus
[/B]
Thank you again!

---

### Post by stoogiebuncho on 2009-08-18
gksudo "gnome-open %u" creates a launcher that you can drag other files onto and it will open them with administrative rights.

gksudo nautilus opens the file manager with administrative rights

Does that make sense?

---

### Post by cat2005 on 2009-08-18
> **stoogiebuncho said:**
> gksudo "gnome-open %u" creates a launcher that you can drag other files onto and it will open them with administrative rights.

gksudo nautilus opens the file manager with administrative rights

Does that make sense?



Yes, now I get it....thank you again.

---

