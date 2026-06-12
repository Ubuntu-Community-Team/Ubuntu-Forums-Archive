---
title: "uninstall demo of jets and guns"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by grewolf on 2009-12-31
Ubuntu Karmic 9.10.  Jets and guns demo.  I am trying to uninstall this demo and get this error message 

[COLOR="Red"]libgtk-1.2.so.0: cannot open shared object file: No such file or directory[/COLOR]

I was then scouring the net for this error message and found this in the bug pages( see below).  I've been using Ubuntu for a while but still struggle with the command line.  Some help in how to remove would be great.  The uninstall tool doesn't work (error message) It's not listed in synaptic and have failed using the command line to try and uninstall.  


[COLOR="Red"]Maia Kozheva  wrote 12 hours ago:  	  #10

The package was removed for good reason - GTK1 is an obsolete version, has been deprecated for 8 years, and a significant amount of effort was spent to remove dependent applications or port them to GTK2.

It is not the responsibility of Ubuntu developers to guarantee workable conditions for "commercial linux applications and games" outside the repository; the best solution for such software would be to bundle the required libraries.
Benjamin Thyreau wrote 7 hours ago: 	#11

Hi Maia,
This is interesting:
"It is not the responsibility of Ubuntu developers to guarantee workable conditions for "commercial linux applications and games" outside the repository;"
Is it an Ubuntu policy ? Do you have a quotable source for that ? This is a major info for both ISV and users imho.
nodemaster wrote 4 hours ago: 	#12

Hi Maia,

is this an official statement? Just asking, because we are looking forward to upgrade our servers to 10.04 LTS next year at our company. And we definitely have GTK1 dependencies. Of course we have extended support, but if I read your information, I doubt it might be possible to do an upgrade.... :-O[/COLOR]

---

