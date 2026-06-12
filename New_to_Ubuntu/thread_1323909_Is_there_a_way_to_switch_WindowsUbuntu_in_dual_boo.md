---
title: "Is there a way to switch Windows/Ubuntu in dual boot quicker?"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by Weapondrift on 2009-11-12
Im not trying to make Ubuntu my primary OS. What I would like to do is quickly switch between Ubuntu and Windows if this is possible. Heck If I could make it where SHIFT+down switched over to Windows and Ubuntu (similar to Alt+Tab switches prgrams) id be happy. Is this possible?

---

### Post by mbzn on 2009-11-12
not sure why you want to do this, but in most cases VirtualBox should do the trick.

---

### Post by 3rdalbum on 2009-11-12
Usually, having one OS in a virtual machine is the best solution. But you could try hibernating both operating systrms. Reboot and choose the other OS from the grub menu and it will resume.

---

### Post by footprint on 2009-11-12
Perhaps a little explanation would help. The suggestion from MBZN about virtual box is to run one of the operating systems as a virtual machine inside the other one. If you do this the main OS is referred to as the host and the other one running within it as the guest.

If the host was Ubuntu and the guest was Windows then you could have the Windows virtual machine running full screen on one Ubuntu desktop, then switching desktops would effectively switch operating systems.

The open source edition of VirtualBox is in the Ubuntu repositories but this does not support USB. The non-free version available from the Sun VirtualBox website does.

I hope this helps.

---

### Post by alienclone on 2009-11-12
with only one machine, the previous suggestions of virtualizing would be the best solution. what i do is i have two seperate boxes networked together and use a KVM switch so they share the same keyboard, monitor, and mouse, i just switch the controls from one box to the other with a keyboard shortcut.

---

