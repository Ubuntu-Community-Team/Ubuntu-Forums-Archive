---
title: "Problems upgrading to Lucid from Karmik"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by darkrapsody on 2010-05-24
Hi!

Having some n00b problems over here.

I'm trying to install Lucid Lynx from Karmik Koala, from the Update Manager, with the default procedure. So, everything good 'til the second marker of the dialogue window of progress. 

I got this message:



An unresolvable problem occurred while calculating the upgrade:
The «ubuntu-desktop» package it's marked to be uninstalled, but it's in the black list of desinstallation.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu


I'm sorry if this is so obvious, but I honestly, don't understand the problem. Can someone help me by explaining me or telling me what else can I do?

TIA.

Darkrapsody.

---

### Post by wojox on 2010-05-24
Did you try upgrading everything first? Open a terminal and run this:

```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```

---

### Post by darkrapsody on 2010-05-24
Yep, sorry I didn't told in the thread, but that's done.
Thanks for asking...^^

---

### Post by wojox on 2010-05-24
How about fixing any broken packages:

```
sudo dpkg --configure -a
```

```
sudo apt-get install -f
```

You could also try Synaptic Package Manager, go to the Edit menu and hit Fix Broken Packages

---

### Post by darkrapsody on 2010-05-24
Just done. Still got the problem, man... :S

---

### Post by darkrapsody on 2010-05-24
I've tried too much in that fixing/updating packages stuff, and still got nothing. I'd googled for same problem documentation... And nothing...
Please, help me! :@

---

