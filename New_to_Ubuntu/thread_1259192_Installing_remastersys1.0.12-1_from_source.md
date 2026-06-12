---
title: "Installing remastersys1.0.12-1 from source"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by praveesh on 2009-09-06
Please help me in installing remastersys1.0.12 -1(the tool used to create custom versions of Ubuntu ). There is no make or make install in the tar.gz. More over , there is no instruction for installation in the tar.gz , in their wiki and in their forum. Googling also didn't show any instruction for installation. Since remastersys is just a shell script, it may not need any installation (I DON'T KNOW MORE). The source is attached, please help . 



The reason why Iam trying to install from the source is because the .deb file is unavailable. After adding their repositry , when I clicked on reload, synaptic failed to get the package list of remastersys. No problem with updating other package list. My network is ok. After googling , I have got another repository(of klikit-linux) with remastersys. But that contains only the version 1.0.11 . That version of remastersys is for the Ubuntu versions prior to hardy. For newer versions version 1.0.12-1 is required. I installed v1.0.11 but there are some issues.

---

### Post by marshmallow1304 on 2009-09-06
What repository did you use?
```

deb http://www.geekconnection.org/remastersys/repository ubuntu/
```
Works for me.

---

### Post by marshmallow1304 on 2009-09-06
No compilation/installation required.

Extract the archive.  Open up a terminal and navigate to the directory.  Assuming you extracted on your desktop, it'd be
```
cd ~/Desktop/remastersys-2.0.12
```
Then
```
gksudo remastersys-gui
```

---

### Post by praveesh on 2009-09-06
> **marshmallow1304 said:**
> No compilation/installation required.

Extract the archive.  Open up a terminal and navigate to the directory.  Assuming you extracted on your desktop, it'd be
```
cd ~/Desktop/remastersys-2.0.12
```
Then
```
gksudo remastersys-gui
```

Thank you

---

### Post by praveesh on 2009-09-06
> **marshmallow1304 said:**
> What repository did you use?
```

deb http://www.geekconnection.org/remastersys/repository ubuntu/
```
Works for me.

 I have used the same repository as you did. Do you have the .deb ? . If yes, can you please attach it?.

---

### Post by praveesh on 2009-09-06
> **marshmallow1304 said:**
> No compilation/installation required.

Extract the archive.  Open up a terminal and navigate to the directory.  Assuming you extracted on your desktop, it'd be
```
cd ~/Desktop/remastersys-2.0.12
```
Then
```
gksudo remastersys-gui
```

that doesn't work. When I used the code, a kdialog with a number of options was shown  .When I clicked on the 1st option (restore including user data) . The remastersys replied that the iso image is created in the directory /home/remastersys/remastersys . But nothing was created. (I had the remastersys v 1.0.11 . I uninstalled it before using the v1.0.12. )  Thank you

---

### Post by praveesh on 2009-09-06
I have finally found it out my self. Copy the shell scripts remastersys, remastersys-grubconfig, remastersys-grub-restore, remastersys-gui to the directory /usr/bin . Copy the contents of the directory etcdata to /etc . Copy contents of the desktopdata to the desktop. Done. I DON'T KNOW WHAT TO DO WITH THE CONTENTS OF THE FOLDER DEBIAN.  Any how, thanks to all.

---

