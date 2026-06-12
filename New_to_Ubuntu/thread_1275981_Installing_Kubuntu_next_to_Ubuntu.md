---
title: "Installing Kubuntu next to Ubuntu"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by Prince Valiant on 2009-09-26
Hello,

I'm thinking of installing Kubuntu next to the pre-existing Ubuntu OS.  I've backed up my files, but is there anything I should beware of when I change the partitions during installation?  I want to make sure that when I resize the larger partition I don't mess anything up...lost files, broken OS, that sort of thing.  Thanks in advance!

-Val

---

### Post by sandyd on 2009-09-26
why not just do
```

sudo apt-get install kubuntu-desktop

```
that will install all the stuff that comes with kubuntu.

---

### Post by Prince Valiant on 2009-09-26
Thanks-

I'll try it.  What would the difference between this and installing kubuntu?

-Val

---

### Post by theozzlives on 2009-09-26
> **Prince Valiant said:**
> Thanks-

I'll try it.  What would the difference between this and installing kubuntu?

-Val

None really, the only difference is Ubuntu uses GNOME and Kubuntu uses KDE desktops. You also have a choice between KDM or GDM (if it says Kubuntu or Ubuntu at startup).

---

### Post by Prince Valiant on 2009-09-26
Okay, oops.

I assumed a) that installing the KDE desktop would be effective for only one user account, and 2) that the Kubuntu desktop would be included in the installation.  

Is there any way for these two hopes to be brought about?  As it is, the user switcher of GDE fails on startup.  Thanks for your suggestions!

-Val

P.S. All this was caused because I'd like to run a KDE program, namely Kompozer, which did not work properly on Gnome.

---

### Post by kansasnoob on 2009-09-26
Look at this section:

> Playing Around
KDE/Gnome Comparison
Install KDE
Install XFCE
Install IceWM
Pure Gnome
Pure KDE
Pure XFCE
Make your own Ubuntu remix 

of this guide:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

### Post by laidback on 2009-09-27
I installed Kubuntu-desktop via synaptic last week, both on 8.10 and 9.04 systems. Both worked perfectly and now you can choose which you want. If you have an auto user-login for Gnome then simply logout, then bottom left of the screen select Options (I think it's that) and then Session. You get a list of login options, one will be Gnome, another KDE, amongst others, you can also make either Gnome of KDE the default, choose as you wish. 

Enjoy

PS If you don't have the auto-login I guess you end up at the login/choose session screen as it boots.

---

