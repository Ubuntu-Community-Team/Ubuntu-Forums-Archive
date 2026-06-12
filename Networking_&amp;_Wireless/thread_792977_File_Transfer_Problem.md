---
title: "File Transfer Problem"
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by xxrealmsxx on 2008-05-13
Hello all,
         I am using pyNeighborhood to mount a network share inside of my Home folder. Unfortunately i am having some file permission issues. First, I can only use pyNeighborhood as SUDO to mount the folder, secondly I cannot copy files to the mounted network folder. I am able to make folders, and read the directory, but for some reason I am unable to write to it.

Does anyone have any suggestions?

I also get an error on boot saying that $Home/.dmrc is unreadable but I have no idea whether or not that is related. :confused:

---

### Post by xxrealmsxx on 2008-05-13
I believe I fixed the problem by running: 

sudo chmod U+S /usr/bin/smbmount

and

sudo chmod U+S /usr/bin/smbumount

---

