---
title: "Got FVWM but want to change!"
date: 2010-03-08
forum: New to Ubuntu
---

### Post by Revo99 on 2010-03-08
Hello All,

I have FVWM currently as my window manager but want to change it to something more user friendly. As I am about a week into Ubuntu. I am starting to learn some of the basic commands. So will definitely continue to use command line.

I really dont know what I would like yet. But I think I want to move to something like KDE. I dont want something too graphical. So would below install be best? Then install KDE programs as needed.

Is it possible or do I even need to remove FVWM to Install the below?

```
"sudo apt-get install kdebase kdm x-window-system-core"
```

Thank you in advance for your help. Also any other base GUI suggestions and why would be greatly appreciated.

Regards,

Revo99

Now a keen Ubuntu learner

---

### Post by r-senior on 2010-03-08
Ah, fvwm, that brings back some memories!

How did you install Ubuntu to get fvwm as your window manager?

How old is the machine you will be running the desktop on? In other words, what do you have in terms of processor, memory and graphics card? That might influence your choice of window manager.

---

### Post by Revo99 on 2010-03-08
> **r-senior said:**
> Ah, fvwm, that brings back some memories!

How did you install Ubuntu to get fvwm as your window manager?

How old is the machine you will be running the desktop on? In other words, what do you have in terms of processor, memory and graphics card? That might influence your choice of window manager.

Its definitely will be able to run any interface. See below my signature. I have Ubuntu Server 9.10 installed. I then installed xorg and fvwm.

I think KDE would be a good. The reason I want a light version of it is because I want to learn from the bottom up.

Main question is if the above code is right and do I need to remove fvwm. If so how?

Thanks r-senior

Revo99

---

### Post by patchwork on 2010-03-08
You can have multiple window managers, so you don't need to remove your current one.  I've never heard anyone complain that kde is lightweight, however.  

Although I'm not sure about only installing kdebase, if you want the entire kde setup you can install ```
sudo apt-get install kubuntu-desktop
```

If you're having trouble with your current window manager, maybe we can help you through that without adding the bloat of kde?  Did you ever install a file manager after the window manager, for instance?

---

### Post by r-senior on 2010-03-08
The easiest way to get yourself a KDE desktop would be:

$ sudo apt-get install kubuntu-desktop

But that will install the whole shebang: Konqueror, Kopete, Amarok, etc, etc. That doesn't sound like what you want.

Maybe have a read of this though:

[http://www.psychocats.net/ubuntu/whichbuntu]("http://www.psychocats.net/ubuntu/whichbuntu")

The Xubuntu desktop/XFCE might appeal to you?

As to your question, you don't need to remove fvwm, although you can. Will those packages give you a usable KDE environment? I honestly don't know.

This page shows you how to get back to Ubuntu from Kubuntu:

[http://www.psychocats.net/ubuntu/puregnome]("http://www.psychocats.net/ubuntu/puregnome")

It could be of use in that it shows you the packages that would be installed in a full Kubuntu installation. (If you wanted to install Kubuntu and get back to your server environment for example, you'd just omit the "apt-get install ubuntu desktop" from the end).

I think what you are effectively trying to do is build your own "Revobuntu" distribution. If you want to do that, the question is not really for the absolute beginners' forum and you might be better off in General Support -> Desktop Environments?

---

### Post by Revo99 on 2010-03-08
> **patchwork said:**
> You can have multiple window managers, so you don't need to remove your current one.  I've never heard anyone complain that kde is lightweight, however.  

Although I'm not sure about only installing kdebase, if you want the entire kde setup you can install ```
sudo apt-get install kubuntu-desktop
```

If you're having trouble with your current window manager, maybe we can help you through that without adding the bloat of kde?  Did you ever install a file manager after the window manager, for instance?

Hey Patchwork,

I did indeed install a file manager which was nautilus. I can't figure out the window management of FVWM once I have opened Nautilus. When I click on the desktop it wont bring up my menu anymore. 

When you say your not sure about installing kdebase is this because you are not familiar with it or you would be hesitant.

thanks again,

Revo99

---

### Post by r-senior on 2010-03-08
> **Revo99 said:**
> I did indeed install a file manager which was nautilus. I can't figure out the window management of FVWM once I have opened Nautilus. When I click on the desktop it wont bring up my menu anymore.
Nautilus may be taking over the desktop. There is an option you can pass:

```
nautilus --no-desktop
```

---

### Post by patchwork on 2010-03-08
Rev - 
I have no experience with kde beyond loading it, realizing I hated the interface, and removing it.  


~ good luck to you no matter which direction you go

---

### Post by Revo99 on 2010-03-08
> **patchwork said:**
> Rev - 
I have no experience with kde beyond loading it, realizing I hated the interface, and removing it.  


~ good luck to you no matter which direction you go

How would I remove FVWM if I wanted something like Kwin.

Cheers,

Revo

---

### Post by Revo99 on 2010-03-08
I have installed Kwin. How do I change my diplay manager to kwin?

---

### Post by patchwork on 2010-03-08
Here you go:

```
sudo apt-get install kwin && sudo apt-get remove fvwm
```

---

### Post by teward on 2010-03-08
i believe at login you can choose the interface you want to load... not sure, because I still use 9.04 :P

---

### Post by patchwork on 2010-03-08
Trek, he doesn't use gdm or xdm....uses startx through console

---

### Post by Revo99 on 2010-03-09
Thanks again to everyone especially Patchwork.

I managed to uninstall a few WM I accidentally installed.

Then installed the base of IceWM. its working well.

Now to create new threads. But Internet researching is the way. Gotta dig it out.

Cheers,

Revo99

next..... antivirus & wireless card.

---

