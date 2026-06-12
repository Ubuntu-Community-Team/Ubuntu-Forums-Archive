---
title: "Can you use 11.04 without Unity?"
date: 2011-04-28
forum: New to Ubuntu
---

### Post by garl on 2011-04-28
I want to try Ubuntu 11.04. If I don't like Unity, can I uninstall it and install the version of Gnome that's on 10.10? And if so, how?

---

### Post by leviathan8 on 2011-04-28
Unity is built on the top of Gnome2, so, yes, you can choose the desktop session at the login screen.

---

### Post by garl on 2011-04-28
Do you have that option every time you log in?

---

### Post by elliotn on 2011-04-28
yep

---

### Post by leviathan8 on 2011-04-28
[IMG]http://farm6.static.flickr.com/5207/5222344209_e4aa8e895f.jpg[/IMG]

This is the login screen. Clicking on the sessions menu will bring you up the available desktop environments. You want to choose Ubuntu Classic Desktop from here. Once set, it will remain the same. Have a nice day.

---

### Post by garl on 2011-04-28
Ok, thanks. I'm still curious though, how do you uninstall a desktop environment and install a new one (like KDE for example)? Or would you keep the default and install a new one?

---

### Post by leviathan8 on 2011-04-28
IMO, I would keep the old desktop environment if I don't like the new one.

For KDE, use:

```
sudo apt-get install kubuntu-desktop
```

For Xfce, use:

```
sudo apt-get install xubuntu-desktop
```

For Lxde, use:

```
sudo apt-get install lxde
```

For Openbox, use:

```
sudo apt-get install openbox obconf openbox-themes
```

There are many, many more window managers to choose from, but these are the most common. Once installed, they will be in your login screen at sessions menu. Have fun.

---

### Post by garl on 2011-04-28
Thanks again! (:

---

### Post by dash10 on 2011-04-28
Glad to see this, cheers all

---

### Post by beew on 2011-04-28
> **leviathan8 said:**
> IMO, I would keep the old desktop environment if I don't like the new one.

For KDE, use:

```
sudo apt-get install kubuntu-desktop
```For Xfce, use:

```
sudo apt-get install xubuntu-desktop
```For Lxde, use:

```
sudo apt-get install lxde
```For Openbox, use:

```
sudo apt-get install openbox obconf openbox-themes
```There are many, many more window managers to choose from, but these are the most common. Once installed, they will be in your login screen at sessions menu. Have fun.

Problem with that is say, you try KDE and don't like it, when you uninstall the KDE desktop it will uninstall other (all?) KDE applications you may want to keep, even though you can install these applications separately under gnome (or any non kde desktop)

---

### Post by GrouchyGaijin on 2011-04-28
Hi Everyone,

What is the advantage to moving to 11.04 if you don't plan on using Unity?
I've got 10.10 set up really nicely and would hate to have to retweak (is that a word?) everything.

---

### Post by Paqman on 2011-04-28
> **GrouchyGaijin said:**
> Hi Everyone,
What is the advantage to moving to 11.04 if you don't plan on using Unity?
I've got 10.10 set up really nicely and would hate to have to retweak (is that a word?) everything.

There's nothing stopping you from staying with Maverick if you like it. Maverick is supported until April next year, so you can keep using it till then.

Generally, the advantage of new versions is that they contain bugfixes and newer versions of the software.

---

### Post by GrouchyGaijin on 2011-04-28
> **Paqman said:**
> There's nothing stopping you from staying with Maverick if you like it. Maverick is supported until April next year, so you can keep using it till then.

Generally, the advantage of new versions is that they contain bugfixes and newer versions of the software.

Thanks,

I realize that there is nothing stopping me from staying with 10.10.  I was wondering what the advantage is to moving to 11.04 if you don't plan on using Unity.

---

### Post by Hippytaff on 2011-04-28
> **beew said:**
> Problem with that is say, you try KDE and don't like it, when you uninstall the KDE desktop it will uninstall other (all?) KDE applications you may want to keep, even though you can install these applications separately under gnome (or any non kde desktop)

not in my experience - usually the apps stay, but maybe I did it wrong :?

---

### Post by el_koraco on 2011-04-28
> **GrouchyGaijin said:**
> Thanks,

I realize that there is nothing stopping me from staying with 10.10.  I was wondering what the advantage is to moving to 11.04 if you don't plan on using Unity.

Most people swear by the Natty Classic mode. It also has the "wonder patch" in the kernel that might or might not give you a performance boost. Plus, there's *some* new software available.

---

### Post by Paqman on 2011-04-28
> **el_koraco said:**
> It also has the "wonder patch" in the kernel that might or might not give you a performance boost.

You're highly unlikely to see any extra performance at all from this patch unless you do a lot of uberintensive work in a terminal while multitasking. It's been hugely overhyped.

---

### Post by Hippytaff on 2011-04-28
> **el_koraco said:**
> Most people swear by the Natty Classic mode. It also has the "wonder patch" in the kernel that might or might not give you a performance boost. Plus, there's *some* new software available.

hype on a grand scale

---

### Post by GrouchyGaijin on 2011-04-28
> **Hippytaff said:**
> hype on a grand scale

That is what I thought as well.

---

### Post by leviathan8 on 2011-04-29
> **beew said:**
> Problem with that is say, you try KDE and don't like it, when you uninstall the KDE desktop it will uninstall other (all?) KDE applications you may want to keep, even though you can install these applications separately under gnome (or any non kde desktop)

Taking the case of KDE, if you remove the kubuntu-desktop, only the kdm and some other core KDE programs will be removed. All the applications will be kept, and yes, you can remove them from Gnome. 
Deleting the package [FONT="System"]kdebase-runtime[/FONT] will remove EVERY application installed belonging to kde. So if you plan to remove kde applications, but if there are some of them you actually like and want to use under Gnome, first make a list of them, then delete the runtime package and install again separately your favorite programs. 
Have a nice day.

---

