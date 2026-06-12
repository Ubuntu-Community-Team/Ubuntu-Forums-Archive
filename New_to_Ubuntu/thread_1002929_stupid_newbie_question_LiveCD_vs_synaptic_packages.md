---
title: "stupid newbie question: LiveCD vs synaptic packages"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by Thriell on 2008-12-05
Another question from the clueless newbie:

What's the difference between downloading and installing the kubuntu LiveCD and just using the synaptic package manager to download and install the kubuntu packages?

I'm guessing that using the package manager would give one the choice between gnome and kde, but is that the only difference?

I've discovered I *REALLY* like KDE much better than gnome.

---

### Post by snowpine on 2008-12-05
Hi Thriell,

No need to re-install, the following terminal command (or you can use synaptic, but why bother?) will install Kubuntu on top of your existing Ubuntu install, preserving all of your documents and settings:

```
sudo apt-get install kubuntu-desktop
```

You can then switch between KDE and Gnome at the login screen by choosing Options->Settings.

Alternately, you can completely remove Gnome and install KDE with this handy tutorial (just copy and paste the line of code into the terminal):

[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

Good luck!

---

### Post by Michael.Godawski on 2008-12-05
When you start the Live CD session nothing is installed yet. The whole Ubuntu/Kubuntu OS is run within your RAM. When you choose to install it, then the system files are transferred to the hard drive.

Once installed you can use the Synaptic Package Manager to download and install applications. These come in form of packages.

You cannot put a versus between the Live CD and Synaptic. These are two different stories.

Edit : I somehow misunderstood you ... do what snowpine suggested. Am I getting older :) ?

---

### Post by Paqman on 2008-12-05
> **Thriell said:**
> 
What's the difference between downloading and installing the kubuntu LiveCD and just using the synaptic package manager to download and install the kubuntu packages?


The Kubuntu packages (ie: kubuntu-desktop) will obviously be a much smaller download than a whole LiveCD. But otherwise they're exactly the same packages.

Psychocats has a good guide to [removing Gnome and installing KDE](http://www.psychocats.net/ubuntu/purekde).

---

### Post by Thriell on 2008-12-07
Thanks for your answers. You've all been very helpful.

---

