---
title: "Can't delete pix from trash..?"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by DonaldJ on 2009-02-03
1300 pix in trash...

Permissions can't be changed to Read & Write..?
Something's "back-end" won't permit permissions changes..?  Butt I wants to change it... How is it that it's butt is boss..?  I guess if democracy can do it, then why not Linux...

How do I force-empty the trash in Ubuntu-804?..

In changing the desktop to taste, I deleted the trash icon in the bottom toolbar, and set a trash icon on the desktop...  does this mean that the OS now has 2-trashes..?   

Me thinks it's gonna take years to learn this Linux thingawhozits...

What is the most crucial insight in understanding how to work the insides of  Ubuntu..?
What one thing gives the user that sudden "light-bulb" "over the hump" flash, that finally now they see the light of Linux's fog..?

---

### Post by drs305 on 2009-02-03
Your trash may belong to another user, probably *root*. You can open nautilus with admin privileges and navigate to your trash bins to delete trash.
```

gksudo nautilus $HOME/.local/share/Trash

```
Use SHFT=DEL to delete so it's not moved to "Trash"! Also use caution since you can delete any file, including system files, when operating as 'root'.

User's trash in recent ubuntu versions is stored in ~/.local/share/Trash, while root's trash is in /root/.local/share/Trash.

Here is a guide that will tell you what you need to know to find all the trash on your system (there can be multiple bins) and how to delete it:
[http://ubuntuforums.org/showthread.php?t=898573]("http://ubuntuforums.org/showthread.php?t=898573")

---

### Post by Neural oD on 2009-02-03
in 8.10 your trash files are found in /home/your-user-name/.local/Trash/files
there is also an info folder under Trash - that stores info about the files.
one way to do it would be to type this: sudo rm -f "~/.local/share/Trash/files/*"
and: sudo rm -f "~/.local/share/Trash/info/*"

on your second question - no you don't have two trashes

to your last question - it requires time to learn a new system - no shortcuts - spend time tinkering away (on a non essential system - preferably in a vm) and spend time in the forums. Also google is your friend :)

---

### Post by DonaldJ on 2009-02-03
[QUOTE=drs305;6668375]Your trash may belong to another user, probably *root*. You can open nautilus with admin privileges and navigate to your trash bins to delete trash.
```

gksudo nautilus $HOME/.local/share/Trash

```


__________________________




I tried that..  I got, "Sorry, couldn't display all the contents of "trash": Operation not supported"...

I'm getting "operation not supported" for half the things I try to open..?

Do I need to re-install Ubuntu?..  

The 1300-pix were downloaded in SeaMonkey on W2000, and edited with Irfanview in W2000, then transferred to Ubuntu with a flash drive...  They edit easily in  Gimp, and they do what they're supposed to do in Ubuntu.. buy just won't delete from Trash...  Umm..?  "sandpaper the hd"..?  
I'm stuck...

---

### Post by XanTrax on 2009-02-03
Type this in at a terminal

```

sudo rm -rfv ~/.local/share/Trash/files
sudo rm -rfv ~/.local/share/Trash/info

```

and post any errors that are encountered (shouldnt be any)

---

### Post by DonaldJ on 2009-02-03
"to your last question - it requires time to learn a new system - no shortcuts - spend time tinkering away (on a non essential system - preferably in a vm) and spend time in the forums."

_____________________


Has anyone found a better tinkering format than just bumping into problems and striving to solve them..?   

Is there a formula for productive-tinkering..?

---

