---
title: "entertainer 0.1 installation"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by epicmono on 2008-12-17
i did sudo apt-get upgrade as well as sudo apt-get update as told in one of the post in this forum... but still entertainer doesn't run properly..

here's what happens.. i hope i was giving the commands properly..

michel@pee-see:~/Desktop/entertainer-0.1/src$ ./entertainer-content-management.py 

(./entertainer-content-management.py:5340): ClutterGLX-WARNING **: failed to bind GLXGetProcAddress or GLXGetProcAddressARB
michel@pee-see:~/Desktop/entertainer-0.1/src$ ./entertainer-backend.py 
Entertainer backend starting...
michel@pee-see:~/Desktop/entertainer-0.1/src$ ./entertainer-frontend.py 

(./entertainer-frontend.py:5539): ClutterGLX-WARNING **: failed to bind GLXGetProcAddress or GLXGetProcAddressARB

It seems that your Clutter version is too old. Entertainer
                     requires Clutter 0.5 or later. Execution Aborted!
michel@pee-see:~/Desktop/entertainer-0.1/src$ 



any suggestions??

[ the content manager opens up after i give ./entertainer-content-management.py ]

---

### Post by Shhnap on 2008-12-17
I have no idea what is going wrong but since nobody has suggested anything yet maybe you would like a suggestion.

1) Does glxgears work perfectly for you?

2) What graphics settings and cards are you using?

3) Have you tried using mesa opengl instead? Because this seems like an opengl problem.

Hope sombody can help with this.

---

### Post by Layman's terms on 2009-03-24
epicmono,

Entertainer 0.1 is a really old version of Entertainer now. The website at entertainer-project.com hasn't been updated recently due to hosting issues, but the project's wiki page and Launchpad pages are up to date.

[http://wiki.entertainer-project.com/wiki/StartUpGuide](http://wiki.entertainer-project.com/wiki/StartUpGuide) is a good place to start for installation instructions.

You can also ask any question directly to the developers on Launchpad ([https://launchpad.net/entertainer](https://launchpad.net/entertainer)) or on the IRC channel (more info that can be found on the wiki).

Good luck.

---

