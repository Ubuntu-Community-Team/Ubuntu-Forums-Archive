---
title: "Using a PCI card? Making Ndiswrapper work?"
date: 2006-08-30
forum: Networking &amp; Wireless
---

### Post by jcrnan on 2006-08-30
Okey, so I need to get a Wireless card working. I have a Jensen Scandinavia Air:Link 6011. Now, I have to get this thing working with ubuntu on a pc with no net. 

So far I have gathered that there isnt any easy way of doing this so that I will have to use Ndiswrapper. And since its a only sourcecode thing I have to compile it wich I have to do on this pc since I cant compile thing on the other since it doesnt have net so I cant download build-essential. ](*,) 

Oh and I dont understand how to even compile it on this pc. It says I need a source code for my kernel installed and I apparently dont have that.

Any help here?

---

### Post by windquest on 2006-09-01
While I am the first to admit I am also a nubie, and I can't get my wireless card working, I can help you a bit since no one else has replied. If you have another computer that is connected to the internet, download the needed files and transfer them to a memory stick (USB). Ubuntu or anyother distro should recognize it and you can transfer the files to your user directory. The GUI worked fine for drag and drop. Ndiswrapper works but you need to take you time. Read the install guide at Ndiswrapper for help. Good luck.

---

### Post by jcrnan on 2006-09-03
well, main problems is that I cant find a deb file for the make command thingy and I dont understand how to link to the kernel like ndiswrapper needs.

---

### Post by spd106 on 2006-09-03
Start by installing the ndiswrapper-utils package, it should be on the CD. You could also try finding the ndisgtk package, but that will be in the universe repo. There are many guides around for this.
If you need to build ndiswrapper from source then open synaptic, in the properties dialog of build-essential it will tell you the dependancies. Write these down. I think you will also need gcc-3.4 + it´s dependants.

---

### Post by jcrnan on 2006-09-04
what does ndiswrapper-utils and ndisgtk do? Do they replace ndiswrapper?

I will try to do the dependancies thing but Im not quite sure I understand it..

---

