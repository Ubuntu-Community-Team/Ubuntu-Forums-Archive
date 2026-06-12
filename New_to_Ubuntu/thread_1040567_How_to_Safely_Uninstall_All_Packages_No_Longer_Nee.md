---
title: "How to Safely Uninstall All Packages No Longer Needed?"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by Gias Kay on 2009-01-15
Hello,

I am currently having this problem and will describe it in details.

I was trying to install a program which I downloaded as a .deb since it's not included in the standard Ubuntu repository. For this program to work I have installed three dependencies:

```
sudo apt-get install libqt4-core python-qt4 pyqt4-dev-tools
```

Then proceeded with [FONT="Courier New"]sudo dpkg -i[/FONT] to install the said .deb. Everything went fine to this place.

Now I've tried out the said program, and decided to remove it with [FONT="Courier New"]sudo dpkg -P[/FONT].

Now the problem comes - I'd like to remove those three no-longer-in-use dependencies as well, but I believe that while I was installing those three dependencies, they did in turn draw in other depended packages, yet it's not every package that's listed on their dependencies list, since some of them were already installed in my system prior to me installing the three dependencies... got what I mean?
```

&#9746;  &#9484; &#9733;
&#9746; &#9472;&#9508; &#9733;
&#9746;  &#9492; &#9734;

&#9746;: Three dependencies I'd like to remove
&#9733;: Packages installed as the dependencies of those three packages which I'd also like to remove
&#9734;: Packages listed as the dependencies of those three packages but were already in my system priorly which I do not want to see them affected

```

I am currently looking for a safe way to do what I am describing, but the only way so far I've founded seems to be Aptitude (which functions exactly the same way as my logic above), however it only works for packages that were installed through [FONT="Courier New"]sudo aptitude install[/FONT] which means it sadly is not an option available for me. So I am here seeking for helps and wondering why ain't they integrate Aptitude with apt-get or even better, Synaptic?

Any helps would be appreciated.

---

### Post by kingmonkey on 2009-01-15
What version of ubuntu are you using?

This usally does it:

```
sudo apt-get autoremove 
```

---

### Post by Gias Kay on 2009-01-15
I am using Intrepid.

My primary concern with [FONT="Courier New"]sudo apt-get autoremove[/FONT] is if it would misbehave and do something like:

```

&#9746;  &#9484; &#9733;
&#9746; &#9472;&#9508; &#9733;
&#9746;  &#9492; &#9733;

```

Deleting dependencies my system actually still need? The first Google result of "apt-get autoremove" is disturbing.

---

### Post by mrboojive on 2009-01-15
You can try typing in ```
sudo apt-get autoremove libqt4-core python-qt4 pyqt4-dev-tools
``` and see what it says it's going to remove. It will ask you for confirmation and if it looks like it's going to remove something important, you can just tell it not to do anything.

---

### Post by jakupl on 2009-01-15
> **Gias Kay said:**
> 
Deleting dependencies my system actually still need? The first Google result of "apt-get autoremove" is disturbing.

That's not disturbing at all. You just boot into recovery mode and do 
```
apt-get ubuntu-desktop
```

---

### Post by Gias Kay on 2009-01-15
> **mrboojive said:**
> You can try typing in ```
sudo apt-get autoremove libqt4-core python-qt4 pyqt4-dev-tools
``` and see what it says it's going to remove. It will ask you for confirmation and if it looks like it's going to remove something important, you can just tell it not to do anything.

I don't want to resolve into manual judging/guessing. How do I see on which date a package is installed? By knowing the time they are installed I can filter out the packages I am looking to rid/keep.

---

### Post by mrboojive on 2009-01-15
Apt-get keeps a log of everything it does in the file /var/log/apt/term.log so if you look at that, it should show you every package that was installed when you installed those dependencies.

---

### Post by Gias Kay on 2009-01-18
Thanks, the log provides exactly what I was looking for. This should be integrated into the Synaptic GUI by all means.

---

### Post by shacristo on 2009-01-18
In synaptic there is a filter that shows all packages that can be autoremoved.  It only shows packages that were installed as dependencies that are no longer needed for any currently installed packages.  apt-get autoremove does the same thing.  It's perfectly safe.

---

### Post by mrboojive on 2009-01-18
> **Gias Kay said:**
> Thanks, the log provides exactly what I was looking for. This should be integrated into the Synaptic GUI by all means.

Synaptic does have a history of things you've installed/uninstalled using Synaptic if you go to File>History, but it doesn't include things installed/uninstalled from the command line.

---

