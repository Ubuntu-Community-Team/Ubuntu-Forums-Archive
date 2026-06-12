---
title: "Update manager problem"
date: 2011-06-06
forum: New to Ubuntu
---

### Post by Septuagenarian on 2011-06-06
I have started getting this error message when I run update manager ,
Could not initialise the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'

Can anyone help please ?

---

### Post by Septuagenarian on 2011-06-06
P.S. I don't know where the " smiley " came from , it's not on the original .

---

### Post by raja.genupula on 2011-06-06
run this 

sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update

---

### Post by wolfen69 on 2011-06-06
See the second last post on this thread. [http://ubuntuforums.org/archive/index.php/t-1727056.html](http://ubuntuforums.org/archive/index.php/t-1727056.html)

---

### Post by raja.genupula on 2011-06-06
please mark the thread as solved, if you done with this problem

---

### Post by Septuagenarian on 2011-06-06
That did the trick ! Brilliant ! Many thanks , I think ( hope ) I have clicked on the correct key to mark this solved .

---

