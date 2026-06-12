---
title: "problems with 'kde' and 'gnome'  - default browser settings"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by peterpan7191 on 2010-05-01
currently using lucid lynx - 10.04 (but had this problem since 9.10)

i use both kde and gnome sessions 

when i change my default browser settings in kde using system settings -> default  applications -> file manager, and say make it dolphin; the default browser in gnome is also changing to dolphin instead of nautilus ( when i access desktop folders or places->pictures/videos/music etc)  

this really is annoying as clearly for a kde application to run in gnome takes longer time...

ny work arounds ??

help is appreciated to the max ... :)

---

### Post by peterpan7191 on 2010-05-06
still stuck ..... :cry:


hoping some replies [-o<

---

### Post by peterpan7191 on 2010-07-03
bump,
Isn't any one familiar with this problem

---

### Post by lkjoel on 2010-07-03
First of all, every time you bump, you push others down, so then their problems will have less chances of being answered.

Since I am not yet at my Ubuntu computer, I can't help you completely.

Try this:
```
sudo apt-get update
sudo apt-get upgrade
```
Then check in System->Preferences->Preferred Applications.

---

### Post by KdotJ on 2010-07-03
> **lkjoel said:**
> First of all, every time you bump, you push others down, so then their problems will have less chances of being answered.


To be fair, peterpan7191 did bump this thread from 2 months a go. Not many people look 2 months back in the thread lists

---

### Post by lkjoel on 2010-07-03
> **KdotJ said:**
> To be fair, peterpan7191 did bump this thread from 2 months a go. Not many people look 2 months back in the thread lists
Oops sorry peterpan7191!
I did not see the dates.

---

### Post by peterpan7191 on 2010-07-30
> **lkjoel said:**
> 
Try this:
```
sudo apt-get update
sudo apt-get upgrade
```Then check in System->Preferences->Preferred Applications.

Ya I tried dat after updating as you suggested.
But I could not find any tab or option to change file browser in 'Preferred Applications'

---

### Post by lkjoel on 2010-08-08
Is KDE and GNOME installed correctly?
Because KDE configuration should not affect GNOME configuration.

---

### Post by teh603 on 2010-08-08
Is it possible they both share a common configuration file or metafile?

---

### Post by peterpan7191 on 2010-08-10
Till date I've had no problems with kde n gnome.
I frequently switch between them and kde also has least crashes (almost none unless I do crappy stuff :D )
Im sure they both are properly installed.

bdw another frend of mine also has the same problem.

---

### Post by lkjoel on 2010-08-10
Can you get a GTK browser (such as nautilus or thunar), because KDE loads a GTK app faster than GNOME loads a KDE app.

---

### Post by peterpan7191 on 2010-08-20
> **lkjoel said:**
> Can you get a GTK browser (such as nautilus or thunar), because KDE loads a GTK app faster than GNOME loads a KDE app.


That is what is the current status in the ubuntu. Anyway Thanx :)

Hope a fix comes to this problem :)

---

### Post by PPPilot on 2010-08-20
I installed the KDE Desktop into my existing Gnome Lucid install. I can now choose between the two at login and nothing has changed in how my Gnome desktop runs but I was surprised to see all the KDE applications appear in my Gnome menu. I figured that I would not see those except when I logged into the KDE Desktop and visa-versa but all the applications for both desktops are present in both. This does not seem to cause any problems but I would not have thought it would work this way....

---

### Post by peterpan7191 on 2010-08-23
> **PPPilot said:**
>   I figured that I would not see those except when I logged into the KDE Desktop and visa-versa but all the applications for both desktops are present in both. 


Exactly even I prefer using kde applications in kde and gnome ones in gnome though both are available. This browser problem still troubles me

---

