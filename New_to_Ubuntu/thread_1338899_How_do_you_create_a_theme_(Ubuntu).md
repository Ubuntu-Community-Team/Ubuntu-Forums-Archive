---
title: "How do you create a theme (Ubuntu)?"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by momrocker on 2009-11-26
The title pretty much says it all. I want a way to modify everything about a theme, from the font to the icons and colors of the windows. Any programs you could point me to or advice would be nice. I've fiddled with the [customize] option with the themes and it doesn't seem to get the job done unless you already have themes created by others, and I don't want that, I want to build a theme from scratch. Thanks in advance ;)

---

### Post by MelDJ on 2009-11-26
hi there
just go to system-preferences-appearance. then under the theme tab, customize a theme.

---

### Post by momrocker on 2009-11-26
> **momrocker said:**
> I've fiddled with the [customize] option with the themes and it doesn't seem to get the job done unless you already have themes created by others, and I don't want that, I want to build a theme from scratch.

You were saying?

---

### Post by MelDJ on 2009-11-26
oh i am sorry. :oops:

i dont really know what you mean by making a theme from scratch but i believe emerald can help you. you can use it to customize windows. to get it just install from synaptic.


sorry again

---

### Post by momrocker on 2009-11-26
Well, I just assumed that since [customize] uses themes to make themes, there must have been a completely original theme to begin with, right? Like the god of themes? Or theres something else to make themes. And could you post a guide for Emerald? Ive tried it but I have _no_ clue how it works **lol** :D

---

### Post by Virtual Liberty on 2009-11-26
Have you checked [Gnome Art tutorial page]("http://live.gnome.org/GnomeArt/Tutorials") ?

---

### Post by kansasnoob on 2009-11-26
Look:

[ATTACH]137725[/ATTACH]

To do that I first install a couple of packages:

```
sudo apt-get install gnome-themes-more gnome-themes-extras shiki-colors-metacity-theme gnome-backgrounds
```

Then I right click the desktop and choose change background. Wow more wallpaper! I like Aqua, then I click on the Theme tab.

I happen to like starting with Nuvola, but then I customize by selecting Unity controls, I go super dark on selected items color, and Shikki-colors-metacity borders, and Nuvoal icons.

There are literally hundreds of options!

Oh, and search gnome-colors in synaptic. I don't even use those.

---

### Post by momrocker on 2009-11-26
thanks for the link to the tutorial, and to the other person, the whole point is that i _dont_ want to install more themes and backgrounds, i want to create** my own**!!!!! :neutral:

---

### Post by MelDJ on 2009-11-27
> **momrocker said:**
> other person, the whole point is that i _dont_ want to install more themes and backgrounds, i want to create** my own**!!!!! :neutral:

the link given by virtual liberty pretty much gives the answer to the question.

---

### Post by ankspo71 on 2009-11-27
Hi,
This link might have some info about themes that you can use. [http://library.gnome.org/admin/system-admin-guide/stable/](http://library.gnome.org/admin/system-admin-guide/stable/)

Since you prefer not to modify any downloaded themes, you can look at and experiment with Ubuntu's themes. Ubuntu's themes are stored in /usr/share/themes. As far as I know, there is no program out there to create themes from scratch yet. From what I have heard, theme designers use other peoples themes as examples and start creating from there.

More on gnome: [http://library.gnome.org/](http://library.gnome.org/)

Hope this helps.
James

---

### Post by momrocker on 2009-11-27
Ok, so I'm pretty much stuck with the [customize] feature? ](*,) Well, I was hoping for something more complicated, but unless i program my own (which isnt gonna happen cuz i have no clue about programing), then im screwed. And I'm still waiting on the Emerald tutorial, also, if anyone knows of one...

---

### Post by almufadado on 2009-11-27
Themes are store here 

/usr/share/themes

From there you can be pick one and start modifying it !

Not to mess your system, you probably better of installing virtualbox from sun, install your ubuntu version there and mess all you want with them.

Rememeber to create a share folder outside to save your work !

Hint : to save time and trouble after installing everything on the virtual machine simply copy the file of the guest system in /home/ <your user name> /.VirtualBox/Machines.

---

### Post by ankspo71 on 2009-11-27
> **momrocker said:**
> Ok, so I'm pretty much stuck with the [customize] feature? ](*,) Well, I was hoping for something more complicated, but unless i program my own (which isnt gonna happen cuz i have no clue about programing), then im screwed. And I'm still waiting on the Emerald tutorial, also, if anyone knows of one...

Actually, what we mean is that you can edit any theme you like with Gedit (for the text files) and Gimp (for the images). As the previous poster suggested, it's best to make sure you don't actually edit the themes directly, in case things don't turn out as well as you like.

You can use these codes in your terminal to make a backup of Ubuntu's themes.
To backup the themes
```
sudo cp -r /usr/share/themes /usr/share/themesbackup
```

To restore them later you can: 
```
sudo cp -r /usr/share/themesbackup /usr/share/themes
```

Hope this helps.
James

---

