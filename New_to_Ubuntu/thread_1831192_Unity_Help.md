---
title: "Unity Help"
date: 2011-08-23
forum: New to Ubuntu
---

### Post by mintpenguin20 on 2011-08-23
When I click on aplications it brings up that search thing , one problem I have with it is that it comes up FULL SCREEN is there anyway to stop it from being full screen ? I have seen pictures and videos of other peoples desktops and when they search for stuff it does not come up full screen like mine , any advice ?

---

### Post by PhantmKllr on 2011-08-23
Kindly post a little info on your current configuration/computer specs.

---

### Post by beew on 2011-08-23
First install dconf-tools 

```
sudo apt-get install dconf-tools
```Then in the terminal (or you can use ALT+F2 to bring up the run dialogue box) type
```
dconf-editor
```When the dconf-editor appears, navigate to Desktop > Unity and fix the form factor to "Desktop", that way the dash will not take up the whole screen. If the form factor is fixed at netbook the dash will always open fullscreen, if it is automatic then the system would decide for you.

---

### Post by raja.genupula on 2011-08-23
thanks you very much , now my dash also looking as some part of desktop , not entire desktop .

---

