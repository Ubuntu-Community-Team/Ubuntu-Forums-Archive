---
title: "dpkg error... HELP!"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by ltipto1 on 2009-04-08
I have a red error indication at the top of my desktop.  It says,"An error occurred, please run Package Manager from the right-click menu or apt-get in a termainal to see what is wrong.  The error message was: 'Error: BrokenCount > 0'This usually means that your installed packages have unmet dependencies"

I'm a real Linux newbie, and I don't have a clue how to proceed.  Anyone want to give me a hand?

When I try and run Synaptic Package Manager it tells me to run "apt-get dpkg --configure-1" to fix the problem.  Huh?  The last thing I did before I shut down last night was to do an apt-get on Java.  Maybe I should undo that.  How?

---

### Post by taurus on 2009-04-08
Close synaptic or update manager if you have either of them open.  Then, open a terminal and run

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

