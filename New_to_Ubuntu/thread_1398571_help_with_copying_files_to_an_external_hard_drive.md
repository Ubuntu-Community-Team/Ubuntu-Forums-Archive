---
title: "help with copying files to an external hard drive"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by newinstlou on 2010-02-04
So my windows xp desktop crashed (yes i'm done with windows). I can not even log in.  Having not made a back up of the hard drive in a few months, there are some recent documents and photos that I want to try and save. 
 
So a friend of mine suggested that I try ubuntu and boot from the cd.  That works!  Once it's loaded, I can see the files on the desktop's hard drive.  Then I hook up an external hard drive via usb (verbatim), and I can see those files as well.
 
The problem is that when I try to "copy" a document from the desktop's hard drive and "paste" it to the external hard drive, ubuntu is telling that that I don't have write permissions to the external hard drive?
 
I am hoping that there is a basic easy fix for this, and that someone here can help me.
 
Thanks!

---

### Post by nhasian on 2010-02-04
something is amiss.  you should be able to write to the external drive just fine.  perhaps the external drive was not shut down properly?  you should hook it up to a windows pc and run scandisk on it to fix any errors.

if that doesnt help then press Alt-F2 and type

```
gksu nautilus
```

then you can copy/paste files in this window with super user privileges.

[COLOR="Blue"]tip[/COLOR] while in the file browser, hit Control-T for a new tab so you can have both source and destination folders in the same window.

---

### Post by newinstlou on 2010-02-07
Thanks - 
 
But when i type int he code to use nautilus, it asks me to "please enter root password to run nautilus" ?  I don't know the root password.
 
I cannot get the Control-T to work, maybe I'm doing it from the wrong place?

---

### Post by Girya on 2010-02-07
the control T is a typo try control-t

---

### Post by 3177 on 2010-02-07
use ```
sudo nautilus
```root password is the password you use to log on
if you use auto login, its the password you made during installation

---

### Post by chaanakya_chiraag on 2010-02-07
There's something wrong here...I don't think he's installed, and the LiveCD shouldn't ask for the root password...

---

### Post by Girya on 2010-02-07
try this link: [http://http://googlethem.com/ubuntu-live-cd-root-password-and-live-session-password-for-user-ubuntu/]("http://http://googlethem.com/ubuntu-live-cd-root-password-and-live-session-password-for-user-ubuntu/")

---

### Post by halitech on 2010-02-07
> **3177 said:**
> use ```
sudo nautilus
```root password is the password you use to log on
if you use auto login, its the password you made during installation

as nhasian already said, it should be
```
gksu nautilus
```
not sudo nautilus

I know the OP is running from a Livecd but getting into good habits early is better then breaking old bad habits later

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by 3177 on 2010-02-11
any luck yet?

i tried myself from a live cd and it worked fine
i didnt type in a password(just pressed enter when it asked for the password)
i did use sudo (though i will try to break the habit) but gksu worked as well

---

