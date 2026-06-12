---
title: "problem when trying to remove KDE and returning to pure Gnome"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by sweedtwail on 2010-10-25
When I try to uninstall kubuntu from the instructions listed here: [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome) I get the following in the terminal:
```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libaccess-bridge-java : Depends: default-jre but it is not going to be installed or
                                  openjdk-6-jre but it is not going to be installed or
                                  sun-java6-jre but it is not installable
E: Broken packages

```
I'm using ubuntu 10.10

---

### Post by cstudent on 2010-10-25
You can try going to Synaptic (System menu-Administration) and running Fix Broken Packages under the Edit menu.

---

### Post by sweedtwail on 2010-10-25
Nope, that didn't seem to do anything.
I tried again and I got the same message

---

### Post by cstudent on 2010-10-25
I would try to install one of the packages the message suggest like default-jre and see if it can fix the unmet dependency.

---

### Post by sweedtwail on 2010-10-25
That did it, Thanks!

---

