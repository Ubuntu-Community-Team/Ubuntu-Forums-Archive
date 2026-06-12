---
title: "Requires installation of untrusted packages"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by spiritofelric on 2010-01-21
Hoping someone can lead me to documentation or explain how to handle the situation where:

Ubuntu software Center produces the warning, "Requires installation of untrusted packages".  The guides I've read don't explain the preferred way of importing a key or what to do in the Ubuntu register to ensure I'm downloading trusted packages.  Instead of just going to Synaptic PM and adding the package (if that isn't the way)?

Sorry for the naive question.

The specific download in question is: 
=====================================
Qt 4 Designer

The message is:
==============
Requires installation of untrusted packages
The action would require the installation of packages from not authenticated sources.
Details:
fontconfig-config libfontconfig1 libfontconfig1-dev

---

### Post by cariboo on 2010-01-21
Where are you downloading the packages from? I just installed QT$ Designer yesterday using Synaptic, and never got any messages about untrusted packages. I'm running Karmic and I use the main US servers.

---

### Post by nothingspecial on 2010-01-21
```
apt-cache showpkg qt4-designer
Package: qt4-designer
Versions: 
4.5.3really4.5.2-0ubuntu1 (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_karmic_main_binary-i386_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_karmic_main_binary-i386_Packages
                  MD5: cdfd30f0ec154b8bdc30b8b14be6b2d4


Reverse Depends: 
  kuiviewer,qt4-designer
  qdevelop,qt4-designer
  qt-sdk,qt4-designer
  qdevelop,qt4-designer
  libqtjambi-dev,qt4-designer
  eric,qt4-designer
  qt4-dev-tools,qt4-designer
  libqtgui4,qt4-designer 4.1.4
  libqt4-qt3support,qt4-designer 4.4.0~beta1-1
  libqscintilla2-designer,qt4-designer
  kuiviewer,qt4-designer
Dependencies: 
4.5.3really4.5.2-0ubuntu1 - libc6 (2 2.3.4) libgcc1 (2 1:4.1.1) libqt4-designer (5 4.5.3really4.5.2-0ubuntu1) libqt4-network (5 4.5.3really4.5.2-0ubuntu1) libqt4-xml (5 4.5.3really4.5.2-0ubuntu1) libqtcore4 (5 4.5.3really4.5.2-0ubuntu1) libqtgui4 (5 4.5.3really4.5.2-0ubuntu1) libstdc++6 (2 4.1.1) libqt4-dev (0 (null)) libqt4-designer (3 4.4.0~beta1-1) libqt4-core (3 4.4.0~beta1-1) libqt4-designer (3 4.4.0~beta1-1) qt4-dev-tools (1 4.0.1-2) 
Provides: 
4.5.3really4.5.2-0ubuntu1 - 
Reverse Provides:
```

Doesn`t look problamatic.

---

### Post by spiritofelric on 2010-01-21
> **cariboo907 said:**
> Where are you downloading the packages from? I just installed QT$ Designer yesterday using Synaptic, and never got any messages about untrusted packages. I'm running Karmic and I use the main US servers.

I was using the Ubuntu Software Center... i suppose i could just try obtaining it through Synaptic Package Manager.  

Just wondering what the consequence of marking not authenticated software is and if there is a proper process i should follow when installing non-authenticated files?

---

### Post by spiritofelric on 2010-01-21
GAH!

Well... i installed it through Synaptic and now my fonts are totally messed up.  I further compounded the issue by trying to uninstall qt4-designer and all its dependencies, and now most fonts are barely legible.

I'm really stuck for how to fix this... any suggestions would be appreciated.


Additional:
It seems to be specifically linked to KDE apps.  And more specifically apps that use QT as the design model.  
Font Sizes 9-12 seem to be the only ones impacted.  At this point, though, most of my KDE apps are unusable.  Still searching for a solution.

---

### Post by DannStarr on 2010-01-22
Im in the same situation as you. Any software I want to download and install using ubuntu software centre gives me that same error message. I click OK, hoping it will continue to just download, but nothing... I've checked my repositories and all seem to be active

---

### Post by JiuJitsu500 on 2010-01-22
I have the same issues no matter what I do, but it gets past that through the terminal...

In the software center, look at the app you wish to install. Instead of clicking install, scroll down to the bottom where the title is, and after it will be something in parenthesis... i.e. Movie Player has (totem) following it.

open a terminal and type:

sudo apt-get install WHATEVER-WAS-IN-PARENTHESIS

Obviousl replacing the caps there with whatever was in the parenthesis... so movie player would be "sudo apt-get install totem"

It'll ask you for your password, so give it... then to verify, so hit y, then y gaain to install.... But this only works from the software center outside of it you have you change the servers you have. But try this :)

---

### Post by DannStarr on 2010-01-22
I managed to fix my Ubuntu Software Centre with the following commands:

```
sudo apt-get clean
```

```
cd /var/lib/apt
```

```
sudo mv lists lists.old
```

```
sudo mkdir -p lists/partial
```

```
sudo apt-get clean
```

```
sudo apt-get update
```

---

### Post by spiritofelric on 2010-01-23
> **DannStarr said:**
> I managed to fix my Ubuntu Software Centre

Thank you... that was all very helpful.  I did a 'man' on 'app-get' and learned quite a bit.

Sometimes the app doesn't have a relation in brackets.  It's kind-of frustrating because synaptic shows all the dependencies at once, where as, USC only shows them one at a time.  Wish there was a comprehensive guide on how to safely manage installs.

Really appreciate you taking the time to respond.  Do you know any commands for completely removing an app?

---

### Post by lian1238 on 2010-01-23
**Dannstarr**, could you explain what the fix does and why it works? Thanks a bunch!

I've experienced this bug since I first installed Karmic. I'm surprised it hasn't been fixed yet!

---

### Post by LouieGeetoo on 2011-03-10
> **DannStarr said:**
> I managed to fix my Ubuntu Software Centre with the following commands:

```
sudo apt-get clean
``````
cd /var/lib/apt
``````
sudo mv lists lists.old
``````
sudo mkdir -p lists/partial
``````
sudo apt-get clean
``````
sudo apt-get update
```
I was having trouble installing Skype on Ubuntu 10.10, and this fixed it for me. Thank you!

---

