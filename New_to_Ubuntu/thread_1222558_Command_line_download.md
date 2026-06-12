---
title: "Command line download"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by Pres B on 2009-07-25
Hi.. I'm one of those guys who is dual booting...and Windows is acting kind of crazy right now on my laptop.  I think these next couple weeks might be the ones where I start making moves towards using Linux full time.  (Linux Mint 7 right now.)  

Anyway, I was trying to download the MonoDevelop IDE.  When I clicked on the links to download nothing happened.  So I tried to be a smart guy and typed: 

aptitude install monodevelop 

in the terminal.  There were definitely packages download..but now I am not really sure what to do.  My impression is that there should be a tarball somewhere to be extracted... ?  

Any help on my next step(s)? 

Thanks:confused:

---

### Post by Elfy on 2009-07-25
Aptitude downloaded and installed it for you - it will be downloaded as a deb and stored in the apt cache folder.

IT should be installed for you - if there's no menu item it will need to be run from the command line. No idea what the command for it is - try monodevelop

Edit - it should be in the menu under Programming

---

### Post by Pres B on 2009-07-25
Hi Forest.  I realized that the program was in the menu already.  I guess I assumed I had to extract a file.  Thanks for your help.

---

### Post by Elfy on 2009-07-25
You're welcome - aptitude or apt-get will always download the deb and install it unless you tell it to only download the file.

---

