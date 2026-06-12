---
title: "Hardware Profile"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by Phil Binner on 2009-03-06
I'm having some conceptual problems transferring from Windows to Ubuntu. The current one regards viewing the hardware profile, which would have been easy. I've just installed a couple of new cards for receiving satellite and broadcast TV, and I want to check out their names and drivers, etx, before going on a software hunt. How do I do this in Ubuntu Intrepid.

---

### Post by kanikilu on 2009-03-06
I think "lspci" will give you some information on add-on cards like that. You can also do "sudo lshw -html > ~/Desktop/lshw.html" and open that in Firefox.

As for a GUI equivalent to Windows' Device Manager, I don't know of any off-hand.

// Edit - I haven't used it, but a quick search of synaptic shows a package called "gnome-device-manager", perhaps that's closer to what you're looking for?

---

### Post by Paqman on 2009-03-06
There's a couple of packages that will give you a rundown of your specs: [hardinfo](apt:hardinfo) and [sysinfo](apt:sysinfo)

---

### Post by egalvan on 2009-03-06
> **kanikilu said:**
> 
As for a GUI equivalent to Windows' Device Manager, I don't know of any off-hand.

// Edit - I haven't used it, but a quick search of synaptic shows a package called "gnome-device-manager", perhaps that's closer to what you're looking for?

Yep, that is the one that looks the most like MS Device Manager.
Installs easily with Synaptic.
Found under
*Applications -> System Tools*
on my machine.

---

### Post by Phil Binner on 2009-03-07
I set up the Gnome Device Manager. As was indicated above this was easy. It doesn't appear to do anything, however. You can look at things which may comprise your computer, but there is very little indication of which is what, and nothing about whether a device has a driver or if it is working. The manual has two sections. The first, the introduction, is a picture of the window, and the second, the advanced section, has the words " GNOME Device Manager is a complex program, with many advanced features. ", and nothing more. Everything displayed seems only to be text, i.e. there is no active element. Does anyone know if there should be anything more. Could it be that teh full device manager is not available for Intrepid yet.

---

