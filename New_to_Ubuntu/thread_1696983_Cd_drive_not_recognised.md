---
title: "Cd drive not recognised"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by nutsypig on 2011-02-28
:( Installed Ubuntu 10.10 to my Travelmate 2410 laptop ( somehow removed windows! oops!) very impressed and enjoying the experience so far except thet I cannot play cd's or dvd's. When placing a disc in the drive, it fires up with the green light, whirrs for a second or two and then dies?? I have  installed RealPlayer 11, gnome, totem etc etc but cannot recognise the cd drive.  Where can I find a driver or how do I configure the drive ?

---

### Post by vivek.pandey on 2011-02-28
can you see your cd in the pkaces menu?

---

### Post by BbUiDgZ on 2011-02-28
> **neo_aryan said:**
> can you see your cd in the pkaces menu?

he means the places menu

---

### Post by nutsypig on 2011-03-01
No, it does not appear in the "places" drop down. There is a folder in the "computer" > "file system" but does not show any content when inserting a cd. when opening with "movieplayer " does not show any content in the sidepane. When trying Realplayer says that a component is missing, does not have the capabilities to play back this content, Unknown file format, URL: file: ///cdrom ?

Thankyou for your attention so far
Regards

---

### Post by vivek.pandey on 2011-03-01
Insert the cd, in terminal type:
sudo mount
post your output

---

### Post by omnom on 2011-03-01
Basically it depends on your _***"GROUPS"....***_    :KS

Go to: [COLOR=Red]
>System[/COLOR]  **(On the Bar ABOVE YOUR SCREEN)**[COLOR=Red]
         >Administration
         >Users & Groups[/COLOR]

Then:[COLOR=Red]
 >Manage Groups 
         >cdrom[/COLOR]   **          (Or something Similar)**
[COLOR=Red][U]
It will ask an administration Password[/U] [/COLOR][I](Except you have loged in as a SuperUser or Admin)
[/I] 

Click on it..... See if you (the user) are selected.... If not, click on the small box....
:D:D:D

_*Otherwise ...........  **I DON'T KNOW***_  (!!!)


I hope I helped!!!! ENJOY:popcorn:


:lolflag::lolflag::lolflag:

---

### Post by nutsypig on 2011-03-02
Having looked in "users and groups" cdrom did appear there briefly but due to some inappropriate keyboard action it disappeared but did reappear in the "places" drop down???
I think I was hoping for a Windows style "detecting new hardware"  I think that the situation is terminal!!!!! Everything else works a treat so I suppose I will just have to use my I-Pod whilst surfing etc. 

Thanks or your attention.

Regards

:P:(:confused::P):P

---

