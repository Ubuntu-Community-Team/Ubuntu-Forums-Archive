---
title: "java runtime installation problem!"
date: 2011-02-13
forum: New to Ubuntu
---

### Post by kaparthy on 2011-02-13
hi, i have installed ubuntu 10.10 on my PC today n i'm a complete noob. i started using ubuntu for the first time and the problem is:

I AM NOT ABLE TO INSTALL JAVA RUNTIME ENVIRONMENT (NEITHER OPENJDK NOR SUN JAVA) ON MY LAPTOP.

i made a quick search in the forum but i couldnt find a solution. the error i get is:

"Package dependencies cannot be resolved"

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

i get this error not only when i try to install java runtime but also when i install a few other office software, games, browsers etc.

i also tried to install it using the terminal as per the many solutions given in the forum for the same error but i could not complete installation , it says :


"The following packages have unmet dependencies:
 wine1.2 : Depends: libaudio2 but it is not installable
           Depends: libesd0 (>= 0.2.35) but it is not installable
           Recommends: gnome-exe-thumbnailer but it is not going to be installed or
                       kdebase-runtime but it is not going to be installed
E: Broken packages"

when i try to install "wine" and the same error when i try to install open jdk or sun java. 

plz help! i want this java runtime for using my java apps.!
PLZ HELP!!

---

### Post by yeats on 2011-02-13
Okay, the first thing to try when you hit this sort of thing is (in a terminal):

```
sudo apt-get -f install
```

which tells APT (the underlying packaging system) to try to automatically fix the problem.  In any case, it will produce more output that will probably be useful.  Can you type that command and copy/paste the output here within CODE tags (click the # symbol in the menu when composing)?

If that doesn't work, do the same thing with the following:

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install libaudio2
sudo apt-get install libesd0
```

the output will probably lead us to the actual conflict.

---

### Post by kaparthy on 2011-02-13
hi yeats!, this is the output i get :

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 261 not upgraded.
```

---

### Post by xtremethegreat1 on 2011-02-13
Go to synaptic package manager. Then open the repositories window from the menu at the top. Then check all repositories except for the ones on the update page. Add canonical partners and source repositories as well. And make sure the download server is the main server (because there's apt-key problems with other servers, at least the one I had). Then close it and the click reload in synaptic package manager. That should solve the dependency problems. And lemme know if it works.

---

### Post by yeats on 2011-02-13
> **kaparthy said:**
> hi yeats!, this is the output i get :

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 261 not upgraded.
```

That indicates to me that the problem is probably wider than just java & wine...  Try what xtremethegreat1 suggests and try the

```
sudo apt-get update && sudo apt-get upgrade
```

command again.

---

### Post by kaparthy on 2011-02-13
Guyz! Thank you very much!!! Both xtremethegreat1 and yeats! I tried what xtremethegreat1 said, it worked like magic! So i went to this synpatic manager and set the server to main server. Thats it! 

It automatically downloaded some packages and i reloaded n was able to install sun java! I'm sure other softwares will also work!

Once again, thank you very much, i love this forum!!:d

---

### Post by Souptik on 2011-02-13
> **kaparthy said:**
> Guyz! Thank you very much!!! Both xtremethegreat1 and yeats! I tried what xtremethegreat1 said, it worked like magic! So i went to this synpatic manager and set the server to main server. Thats it! 

It automatically downloaded some packages and i reloaded n was able to install sun java! I'm sure other softwares will also work!

Once again, thank you very much, i love this forum!!:d


Please mark the thread solved.:D

---

### Post by kaparthy on 2011-02-13
done.

---

### Post by xtremethegreat1 on 2011-02-13
:)

---

