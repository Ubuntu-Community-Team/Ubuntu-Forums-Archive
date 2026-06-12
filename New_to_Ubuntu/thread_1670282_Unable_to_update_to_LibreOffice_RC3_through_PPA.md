---
title: "Unable to update to LibreOffice RC3 through PPA"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by lbarnes on 2011-01-18
Hey guys, I had LibreOffice RC2 installed through the libreoffice ppa on my 10.10 64 Ubuntu system and was waiting for the ppa to update before installing RC3. Well, today RC3 was released and I am unable to update through Update Manager or Terminal:
```
lennon@lennon-HP-HDX-16-Notebook-PC~ $ sudo apt-get upgrade
[sudo] password for lennon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libreoffice libreoffice-base libreoffice-base-core libreoffice-calc libreoffice-core libreoffice-draw libreoffice-filter-binfilter libreoffice-gnome libreoffice-gtk libreoffice-impress
  libreoffice-math libreoffice-writer python-uno
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
lennon@lennon-HP-HDX-16-Notebook-PC~ $

```

```
lennon@lennon-HP-HDX-16-Notebook-PC~ $ sudo apt-get install libreoffice
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libreoffice : Depends: libreoffice-core (= 1:3.3.0~rc3-2maverick1) but 1:3.3.0~rc2-3maverick1 is to be installed
               Depends: libreoffice-java-common (>= 1:3.3.0~rc3~) but 1:3.3.0~rc2-3maverick1 is to be installed
E: Broken packages
lennon@lennon-HP-HDX-16-Notebook-PC~ $ 

```
I was wondering if anyone was waiting like I was and was able to update through the ppa today. I'm thinking that the likely reason is that RC2 should be completely removed for RC3 to be installed. If that's the case what is the ideal way to remove RC2 properly? Thanks for any suggestions.

---

### Post by lbarnes on 2011-01-18
```
sudo ppa-purge libreoffice
```
allowed me to remove RC2 and I was able to install RC3 without problems through the ppa.

---

### Post by TGBaker on 2011-01-18
> **lbarnes said:**
> ```
sudo ppa-purge libreoffice
```
allowed me to remove RC2 and I was able to install RC3 without problems through the ppa.

My problem was my settings for my repositories. I did not have the pre-released updates checked. I checked it then unchecked it. LibreOffice still showed up in update manager and it updated CR-2 to CR-3. I had originally installed through Ubuntu Tweaks, Thanks for letting me know it had been released.

---

### Post by lbarnes on 2011-01-18
Yeah, I have every box checked, I definitely had some kinda conflict going on as I haven't seen any similar issues yet. Glad you got yours up to date, peace.

---

