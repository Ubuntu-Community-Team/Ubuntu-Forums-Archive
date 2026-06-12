---
title: "performance concerns of having multiple desktop env"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by li(fe)sp on 2010-07-22
I would like to know about performance implications of having multiple Desktop environments...how serious is this
say I install ubuntu and then KDE on top of it...vs direct installation of kubuntu (without gnome of course)...
I am new to ubuntu and like the fact that we can have multiple desktop environment in a plug and play manner..I would like to install all of them and experiment...KDE,Xfce etc etc ..but I dont wanna destroy my system.

---

### Post by Paqman on 2010-07-22
The immediate problem is that you'll have to download a ton of stuff, and that you menus will get very crowded with apps from both environments (many of which will duplicate each other's functions)

You'll be able to choose which environment to log into, and the system will load all the required libs for that environment. When you try and launch an app from the other environment, it will have to go load up all the required libs, meaning that it will launch quite slowly.

So for example, if you log into a Gnome session then it's business as usual until you launch a KDE app. The system will then have to load lots of KDE stuff into memory before it launches that app. This will use up quite a lot of RAM for just one app. However, if you launch a second KDE app, then all the required stuff is probably already running, and it will launch as fast as it would if you were logged into a KDE session.

---

### Post by bodhi.zazen on 2010-07-22
With anything close to modern hardware you are extremely unlikely to notice much, if any, of a performance hit. Your menues will be a little crowded and your system will use a little more RAM.

I would give it a try, most people settle on a single DE/WM and "mix and match" applications.

For example, personally I tend to use Fluxbox/Openbox/XFCE but I prefer K3b (which is a kde app).

I do not notice any performance hit with k3b vs any other (gui) burning application.

---

### Post by li(fe)sp on 2010-07-22
Thanks very much guys..both of ur responses make perfect sense...and wow..I posted a question in ubuntu forum for the first time...went to lunch and back..wah la...answers..I already started loving ubuntu and the community..
I am gonna try the usual gnome & KDE for now..I may later tryout openbox wm

Thanks again

---

