---
title: "it won't let me add new repositories"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by abunchanumbers on 2009-01-28
I'm trying to add some new repositories through the software sources panel, but when i add the line the add source button doesn't light up.
if you need an example, one of the repositories I'm trying to add is medibuntu.

---

### Post by Coreigh on 2009-01-28
You can edit the sources.list directly with gedit.

Press Alt+F2 to get the run dialog and type > gksudo gedit /etc/apt/sources.list
You will be prompted for a password and then Gedit will open the sources.list

---

### Post by RomeReactor on 2009-01-28
Hi. Can you post the line you're trying to add in Software Sources? Are you following [these instructions]("https://help.ubuntu.com/community/Medibuntu")?

---

### Post by abunchanumbers on 2009-01-28
sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list
and yes i've been following the instructions

---

### Post by RomeReactor on 2009-01-28
That line must be run from the terminal (Applications->Accessories->Terminal).

---

### Post by abunchanumbers on 2009-01-28
that worked, thanks.

---

