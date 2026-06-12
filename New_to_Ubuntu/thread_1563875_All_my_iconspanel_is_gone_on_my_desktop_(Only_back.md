---
title: "All my icons/panel is gone on my desktop (Only background shows)!"
date: 2010-08-29
forum: New to Ubuntu
---

### Post by Swami_Sez on 2010-08-29
Hi, when I started up my computer after trying to install Ubuntu 10.04 I'm 100% sure I royally screwed up and accidentally deleted something very important to make free space. Because when I start up my laptop, when it gets to the desktop screen there is nothing on it except for the background and the mouse pointer which doesn't work when I click it. And a message pops up saying "Cannot create the directory "home/antione/.gnome2/share/fonts". This is needed to allow changing the mouse pointer theme. "
 
I'm pretty bummed out as I can't seem to find any threads directly relating to the same problem I have right now... However I'm confident you Ubuntu Wonder Kids will be able to help me find a solution! Thanks!:P

---

### Post by Perfect Storm on 2010-08-29
Seems you may have messed up the permissions in your home folder. The easiest solution would be deleting your Desktop settings and allowed ubuntu to create a new default one.

<alt>+<F2>
```
gnome-terminal
```

Then;
```
cd
sudo rm -rf .gnome2
```

---

### Post by Swami_Sez on 2010-08-30
> **Artificial Intelligence said:**
> Seems you may have messed up the permissions in your home folder. The easiest solution would be deleting your Desktop settings and allowed ubuntu to create a new default one.
 
<alt>+<F2>
```
gnome-terminal
```
 
Then;
```
cd
sudo rm -rf .gnome2
```
 
I entered it and when it brought me to the login screen I logged in then it just has a blank screen now with the mouse pointer.

---

### Post by Swami_Sez on 2010-08-30
> **Artificial Intelligence said:**
> Seems you may have messed up the permissions in your home folder. The easiest solution would be deleting your Desktop settings and allowed ubuntu to create a new default one.
 
<alt>+<F2>
```
gnome-terminal
```
 
Then;
```
cd
sudo rm -rf .gnome2
```
 
 
Ok, I restored my Ubuntu 8.04, and the "Entertainment, Games, Learn, Productivity, Web" Icon Panel is showing up along with the mouse cursor, but there is no top panel? We're getting closer!:D

---

### Post by Perfect Storm on 2010-08-30
```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

if it doesn't help - it may be something completely different.

---

### Post by Swami_Sez on 2010-08-30
> **Artificial Intelligence said:**
> ```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```
 
if it doesn't help - it may be something completely different.
 
 
All I need to do now it seems is to get my top panel to show.

---

### Post by Perfect Storm on 2010-08-30
<alt>+<F2>
```
gnome-panel
```

Then you need to add the different stuff to the panel. You can do that by right cleick on the panel.

---

### Post by Swami_Sez on 2010-08-30
> **Artificial Intelligence said:**
> <alt>+<F2>
```
gnome-panel
```
 
Then you need to add the different stuff to the panel. You can do that by right cleick on the panel.
 
 
Entered "gnome-panel". It gave me a "command not found"

---

### Post by Perfect Storm on 2010-08-30
Are you sure you spelled it correctly? (Note that linux is case sensitive)

---

### Post by Swami_Sez on 2010-08-30
> **Artificial Intelligence said:**
> Are you sure you spelled it correctly? (Note that linux is case sensitive)
 
 
Yep, entered "gnome-panel"
 
Terminal Respone: "-bash: gnome-panel: command not found  *I didn't insert a ":", I'm just restating the message.

---

### Post by Perfect Storm on 2010-08-30
Have you removed any packages when you cleaned up?
```
sudo apt-get install gnome-panel
```

---

