---
title: "How do I remove Accessibility Features?"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by franklin_m on 2009-09-08
Running netbook remix on Dell mini10V.  How do I remove features I don't use, like accessibility stuff? I've tried add/remove, but it won't let me. I'm not familiar enough with linux to venture into Synaptic w/o some advice/help.

Thanks

---

### Post by alejaaandro on 2009-09-08
Administration->Synaptic Package Manager

search what you want to uninstall and it will then tell you what other things have to be uninstalled (if any) because they depend on whatever you want to delete.. if you don't mind losing any of those, go ahead and click aply..

---

### Post by winotree on 2009-09-08
It's as simple as **alejaaandro** says: in fact there are any number of applications that can be safely  removed, including many **ttf**  files, *effectively saving you many MB!*  Just remember not to delete anything that takes more than a few dependencies with it -- Google them first if you don't know what they're for.  You can always add them back into your system later, if you change your mind.  ;)

---

### Post by alejaaandro on 2009-09-08
as you are in a netbook, winotrees' tip is very good.. me being on a dell mini 9, i have deleted a bunch of things to gain valuable space.. currently i'm using 2.1GB..

things i remove: ttf fonts for unwanted laguages, evolution (though might take away some useful things, so be careful), gimp (why need it on a netbook?), nvidia drivers, unwanted icon themes, support for things i don't have like bluetooth..

after that, to save even more space, in synaptic go to "status" (lower left), then "Installed (autoremovable)" and delete those (check if you need any, but usually it's stuff that are no longer needed because you uninstalled other things that made use of them)..

then, go to "status" again , and delete all in "installed (residual config)".. these are things u deleted, but not with "mark for complete removal", so they have some config files left..

finally, on my netbook i always set in synaptic under settings->preferences->files
"delete downloaded packages after installation", and press :delete cached package files" or else after some time of installing new stuff you'll be left with a huge folder with all the installation files  (.deb just like the .exe you use to install in windows)

---

### Post by franklin_m on 2009-09-08
Thanks so much. I removed a bunch of stuff tonight. Never thought font files would take up so much space, but they sure do.

Frank

---

