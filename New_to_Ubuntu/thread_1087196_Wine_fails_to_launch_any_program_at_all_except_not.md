---
title: "Wine fails to launch any program at all except notepad"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-03-04
Hi everyone

after re-installing wine with sudo apt-get remove wine and sudo apt-get install wine,
 AND after deleting the folder ".wine" in nautilus (with root privileges) 
and then typing "winecfg" in terminal, wine no longer launches anything. 

I click on "applications" "Wine" "Programs" and then select a program but none launch at all. 
in terminal, i type: 

wine (directory of .EXE file goes here)
ENTER 

And i get this crap: 
wine: could not load L"Z:\\home\\jake\\.local\\share\\applications\\wine\\Programs\\Ship Simulator 2008\\Ship Simulator 2008.desktop": Bad EXE format for 

what does this mean???

---

### Post by asuastrophysics on 2009-03-04
oh wait i think i got it. 

wine no longer recognises programs that were in its folder before the uninstall 

but why then are they still visible in the applications menu?
shouldn't they disappear if the file to which they refer to is gone?

---

