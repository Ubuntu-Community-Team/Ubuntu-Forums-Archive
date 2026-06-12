---
title: "Initializing wireless on boot."
date: 2007-04-19
forum: Networking &amp; Wireless
---

### Post by ocho on 2007-04-19
In order to enable wireless networking after a reboot, I have to use the commands sudo depmod -a and sudo modprobe ndiswrapper. 

I am looking to automatically run these commands from possibly a startup script or automatically initiate my wireless card using some other method. I have tried sudo ndiswrapper -m to no avail. 

Any help? Thanks in advance.

---

### Post by ocho on 2007-04-20
Anyone?

---

### Post by Mb0742 on 2007-04-20
I am a complete newb but you can try nsidwrapper -m in terminal... (Presuming you use it)

EDIT: it could be ndiswrapper, sorry 'bout that.

---

### Post by ocho on 2007-04-20
Yep, I've already tried that as mentioned in my first post :) . Thanks anyway.

Any other suggestions?

---

### Post by Kent84 on 2007-04-22
Try putting those commands "sudo depmod" and "sudo modprobe" in startup list... accessible in Gnome via. System->Sessions

---

