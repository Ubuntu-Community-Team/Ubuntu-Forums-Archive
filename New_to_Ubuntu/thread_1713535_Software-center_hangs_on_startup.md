---
title: "Software-center hangs on startup"
date: 2011-03-24
forum: New to Ubuntu
---

### Post by gidra on 2011-03-24
Software-centre just hangs on startup, I invoke it from terminal and it doesn't report anything back. I just get a blank window and just hang there, nothing is loaded. Any ideas please?

---

### Post by ubudog on 2011-03-24
Hi there!  May I ask, what are your specs?  

Also, try Synaptic, to see if it does the same thing.  (System>Administration>Synaptic Package Manager)

---

### Post by gidra on 2011-03-24
Hi ubudog, thanks for getting back to me. Synaptics is working fine when invoked both from the terminal or nautilus. I'm on an x64 intel machine. I also removed ~/.cache/software-center so to rebuild itself, after reading here [https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/671054](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/671054) Still no go, thanks for your ideas

---

### Post by ubudog on 2011-03-24
Hmm, so it's not an apt problem.  Maybe try this command to see if it works:

```
rm $HOME/.config/software-center/softwarecenter.cfg
```

Hope that helps.  Are you sure there are no errors when you try to start it from Terminal?  Weird.

```
software-center
```

To see any possible errors.  Post them in a code block here.  :)

---

### Post by gidra on 2011-03-24
Still no go :(

---

### Post by ubudog on 2011-03-24
Looks like in the remove command, I see a permission denied.  Maybe try running it with sudo?

---

