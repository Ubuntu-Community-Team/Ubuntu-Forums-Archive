---
title: "Problem with reading package lists in Ubuntu 11.04"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by axi.torvalds on 2011-04-30
Hello I am not new to Ubuntu yet I am still a beginner and I recently upgraded to Ubuntu 11.04 and every time I try to install something from the command line using sudo apt-get command I get this and the searching the software center takes ages with no results at the end P.S. It is not my connection speed problem I have fast internet! 

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/eg.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by axi.torvalds on 2011-04-30
> **axi.torvalds said:**
> Hello I am not new to Ubuntu yet I am still a beginner and I recently upgraded to Ubuntu 11.04 and every time I try to install something from the command line using sudo apt-get command I get this and the searching the software center takes ages with no results at the end P.S. It is not my connection speed problem I have fast internet! 

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/eg.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
I solved this 
sudo cd /var/lib/apt/lists/
sudo rm archive.ubuntu.com_ubuntu_dists_jaunty_universe_binary-i386_Packages

also the same for all packages filled with HTLM from the modem
when finished with it, just update.......:D

---

### Post by axi.torvalds on 2011-04-30
> **axi.torvalds said:**
> Hello I am not new to Ubuntu yet I am still a beginner and I recently upgraded to Ubuntu 11.04 and every time I try to install something from the command line using sudo apt-get command I get this and the searching the software center takes ages with no results at the end P.S. It is not my connection speed problem I have fast internet! 

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/eg.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
For someone not used to command line operations here is another solution, from the terminal just do:

gksu nautilus (it will ask for your pwd)

Then navigate to /var/lib/apt/lists

Choose: "View" --> "List"
(can also be done via CTRL+2)

....and then click on "Type" in the Nautilus interface in order to get all files of the same kind to line up with each other.

Mark/highlight all the files of the type HTML and delete them. (I actually copied them to another folder just in case they were needed, but they once they are gone all is fine (for me)).

---

