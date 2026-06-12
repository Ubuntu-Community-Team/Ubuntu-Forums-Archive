---
title: "ubuntu 11.04 change greeter theme using lightdm?"
date: 2011-08-15
forum: New to Ubuntu
---

### Post by blue-phoenix on 2011-08-15
im using ubuntu 11.04 after extensive goggling i found that changing the greeter(login) theme was near imposable with gdm so 3 more hrs of goggling and lightdm seems to be the answer now how on earth do i change the theme from its default to one i downloaded off of gnome-look.org? ive read that i need to modify the lightdm.conf file but it looks like thats only for pre-configured themes

---

### Post by snip3r8 on 2011-08-15
it is very possible with gdm

[http://ubuntuforums.org/showthread.php?p=7576112#post7576112](http://ubuntuforums.org/showthread.php?p=7576112#post7576112)

---

### Post by blue-phoenix on 2011-08-15
im not wanting to change the desktop theme i want to change the [COLOR=Red]login screen[COLOR=Black] theme[/COLOR][/COLOR] from the default to this [http://gnome-look.org/content/show.php/SystemAccess?content=52145&PHPSESSID=bf592876c88cb1bafca08fc02da8a6d0](http://gnome-look.org/content/show.php/SystemAccess?content=52145&PHPSESSID=bf592876c88cb1bafca08fc02da8a6d0)

---

### Post by snip3r8 on 2011-08-15
The commands on my link do change the [COLOR=Red]login screen[/COLOR] theme to a gtk theme in the folder /usr/share/themes
the downloadable login themes are out of date,if you want a theme for your gdm,download a gtk theme and put it in /usr/share/themes and use the commands to set it.

---

### Post by blue-phoenix on 2011-08-15
my apologies i mis read that post you linked 
is there a way i can convert the gdm theme to a gdk theme? or how do i make my own?

---

### Post by snip3r8 on 2011-08-15
I dont know if you can convert ,and when i tried going into theme making i got nowhere. 

if you can just get a gtk theme that looks similar and then use the wallpaper from inside the theme file from the old theme it might just get the look you are looking for.

there is a tool called ubuntu tweak that can help you change the login screen wallpaper

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by blue-phoenix on 2011-08-15
yeah thas what i have been running into also there not alot of info on how to make them 
waht i realy want is for the login dialogue box to look like the one in the link i posted and none of the gtk themes offer that i guess um just going to give it up for now

---

