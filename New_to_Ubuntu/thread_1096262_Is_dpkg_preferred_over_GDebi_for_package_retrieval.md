---
title: "Is dpkg preferred over GDebi for package retrieval\installation?"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by ozark_hillbilly on 2009-03-14
I need to install W32 codecs from medibuntu.org to try and get Totem movie player to run .wmv files.

Is there a preferred retrieval/install method?

Terminal using TP & dpkg OR 

 go to site, download i386 codec binaries and then run GDebi Package Installer

Does it matter?

Ed

---

### Post by jakupl on 2009-03-14
Well I just add medibuntu to the sources list and use apt-get

---

### Post by ozark_hillbilly on 2009-03-14
> **jakupl said:**
> Well I just add medibuntu to the sources list and use apt-get

Haven't done that before.
Is this something you add in Synaptic?

Can you point me to a information spot on doing such a thing?

Ed

---

### Post by Gramps on 2009-03-14
Go here and follow the directions [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by ozark_hillbilly on 2009-03-14
> **Gramps said:**
> Go here and follow the directions [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Thanks for link!!

---

### Post by billgoldberg on 2009-03-14
Or run this command:

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list && wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y w32codecs


This will add the medibuntu repo to your sources list and install the codecs for you.

Just copy/paste it into the terminal.

---

