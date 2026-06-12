---
title: "Remove Nvida updates from showing up in the update manager"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by captincrash on 2010-05-13
I am running a gateway laptop and anytime I run the update manager (either gui or from terminal) I keep seeing "nvidia-185-modaliases & nvidia-current-modaliases"  both these updates are auto selected to be installed.  What I want to know is how can I prevent these from showing up everytime I go to update my system.  Or am I just being a complete noob here and should I just run these updates.

Sorry if this has already been answered but I didn't seem to have any luck finding this using google.

EDIT: Using Ubuntu 10.04, 64bit, ATI graphics

---

### Post by -humanaut- on 2010-05-13
What version of Ubuntu are you running? and Do you have a Nvidia card?

---

### Post by captincrash on 2010-05-13
10.04 64bit, and ATI Card, with the Intel Centrino package which i believe means that intel is in charge of the chipset and wireless card along with the processor.

---

### Post by -humanaut- on 2010-05-13
You should be able to remove the Nvidia options with sudo apt-get remove but if there not causing a problem and the system is working right I would probably just leave them.

---

### Post by 2hot6ft2 on 2010-05-13
Find them in Synaptic and remove them, then there wont be anything to get updates.
System > Administration > Synaptic Package Manager
If you're sure your card is ATI then you don't need them anyway. Makes me wonder how you got them installed in the first place.
:popcorn:

---

