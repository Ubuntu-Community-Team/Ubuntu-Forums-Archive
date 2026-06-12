---
title: "Where is System-&gt;Administration-&gt;Software sources gone to?"
date: 2010-06-14
forum: New to Ubuntu
---

### Post by daimaru on 2010-06-14
hi was wondering if this is a bug or if it was changed during last update or so. I just noticed that the menu point System->Administration->"Software Souces" is missing on my ubuntu installation. It was there before, but today its just gone. Was this taken out on purpose or is this a but? 

Does anyone know the terminal command to launch software sources ? Please post so I can try running it from terminal and recreate the menu link. 

thx

---

### Post by garvinrick4 on 2010-06-14
> **daimaru said:**
> hi was wondering if this is a bug or if it was changed during last update or so. I just noticed that the menu point System->Administration->"Software Souces" is missing on my ubuntu installation. It was there before, but today its just gone. Was this taken out on purpose or is this a but? 

Does anyone know the terminal command to launch software sources ? Please post so I can try running it from terminal and recreate the menu link. 

thx
Go to Synaptics and see if it is still there? Under settings repository. If not try this

Go to computer to file system to /etc to /apt to /sources.list and click on it. Does that go 
to Software Sources. If you right click on it, and choose gedit it will open your sources.list

---

### Post by daimaru on 2010-06-14
i can still reach repos through synaptic, and edit the sources.list file, but "Software Sources" is not in the menu anymore.

could you right click your applications menu select "edit menu" got to system admin and check the properties for the "Software Sources". What does it say under command ? 

You can also open it from terminal using 
```
alacarte
```

---

### Post by garvinrick4 on 2010-06-14
> **daimaru said:**
> hi was wondering if this is a bug or if it was changed during last update or so. I just noticed that the menu point System->Administration->"Software Souces" is missing on my ubuntu installation. It was there before, but today its just gone. Was this taken out on purpose or is this a but? 

Does anyone know the terminal command to launch software sources ? Please post so I can try running it from terminal and recreate the menu link. 

thx```

gksudo software-properties-gtk
```

---

### Post by londonkeith on 2010-06-14
If you're using Ubuntu 10.04 try the following. System->Preferences->Main menu->Administration and click on Software Sources.

---

### Post by daimaru on 2010-06-15
> **garvinrick4 said:**
> ```

gksudo software-properties-gtk
```
thx software-properties-gtk was not installed anymore.. no idea why, but reinstalled it and got the menu link back. 

thx for the help

---

### Post by garvinrick4 on 2010-06-15
> **daimaru said:**
> thx software-properties-gtk was not installed anymore.. no idea why, but reinstalled it and got the menu link back. 

thx for the help You are welcome: Run this and in home folder wiil have text file with all your
packages in alphabetical order for easy locating in true name.
                                  
sudo dpkg --get-selections > installedsoftware

---

