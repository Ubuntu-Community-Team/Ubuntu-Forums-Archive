---
title: "[SOLVED] mdf/mds to iso"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by Tpolich on 2008-12-17
How do I turn a disk that has the big mdf file and the small mds file into an ISO image that I can burn to a CD or is there a way just to burn the mdf/mds.

Thank you in advance

---

### Post by Hospadar on 2008-12-17
System->Administration->Synaptic

Search for and install "mdf2iso"

Then from the command line, navigate to where your mdf/mds file is, let's say it was on the desktop```
cd ~/Desktop
```then ```
mdf2iso <filename>.mdf <outputname>.iso
``` where <filename> is the name of your mdf file, and outputname is the name you want the output .iso to be

Then you can just right-click the iso and burn it to a disk, or Applications->Sound and Video->Brasero and burn the image that way.

---

### Post by Tpolich on 2008-12-17
> **Hospadar said:**
> System->Administration->Synaptic

Search for and install "mdf2iso"

Then from the command line, navigate to where your mdf/mds file is, let's say it was on the desktop```
cd ~/Desktop
```then ```
mdf2iso <filename>.mdf <outputname>.iso
``` where <filename> is the name of your mdf file, and outputname is the name you want the output .iso to be

Then you can just right-click the iso and burn it to a disk, or Applications->Sound and Video->Brasero and burn the image that way.

Thank you for the fast reply.

---

