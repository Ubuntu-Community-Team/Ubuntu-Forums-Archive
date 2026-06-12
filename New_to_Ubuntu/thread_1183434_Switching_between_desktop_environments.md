---
title: "Switching between desktop environments?"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by Vunutus on 2009-06-10
I've used GNOME for a good while now and it's really starting to frustrate me now for a number of reasons (the primary one being that restarting/logging off nukes appearance settings at random).

I know I can install the Kubuntu desktop and boot into it easily enough, but I have a few questions regarding what to do after that. Say I decide that I want to permanently switch to Kubuntu. Is there an easy way to completely remove all the main GNOME related packages so my system looks like I had just installed from a Kubuntu disc in the first place? I'd like to avoid playing package whack-a-mole.

---

### Post by nothingspecial on 2009-06-10
[[COLOR="Red"]This is what you need[/COLOR]]("http://www.psychocats.net/ubuntu/purekde")

---

### Post by john.nicholls on 2009-06-10
The package gnome-desktop-environment should contain dependencies for most of Gnome's packages, so removing it should be effective. Just check first that doing this doesn't remove anything essential. Alternatively, or as a further step, you could go into Synaptic and remove any package starting with gnome. Again, check first that this doesn't try to remove something essential.

---

