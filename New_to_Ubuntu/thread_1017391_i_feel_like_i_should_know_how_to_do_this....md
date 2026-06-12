---
title: "i feel like i should know how to do this..."
date: 2008-12-21
forum: New to Ubuntu
---

### Post by shogunmidas on 2008-12-21
im trying to get the flurry screensaver to to work on ibex. i have downloaded the flurry file to my desktop. now im trying to move it to the screensavers file and it wont let me ... saying that i dont have that permission to do that. i need to be root... how can i become root? 

lol... i need to be root,and cant figure out out how to do that...

plz helpe save me from madlolz attackaz.

---

### Post by FAJALOU on 2008-12-21
gksu nautilus

---

### Post by eagle416 on 2008-12-21
In shell console

sudo su

---

### Post by taurus on 2008-12-21
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by shogunmidas on 2008-12-21
i did

sudo su (for superuser?)

then i went to my desktop where i have the flurry and i tried to move it to the screensavers file it tells me "there was an error launching the application." anything?

---

### Post by taurus on 2008-12-21
What was the exact command that you ran to get that error message?

---

### Post by jamesrl on 2008-12-21
'sudo su' makes you root in the terminal (until you close it, or type exit).  So you can mv things by typing text.
gksudo nautilus 
launches the graphical file browser (nautilus) with root permissions, so you can move things around graphically, until you close the nautilus you just launched.  [You only have root permissions in the window that you just opened.]

---

### Post by kixome on 2008-12-21
#in terminal

sudo su
 

"(dont include this)#then type"

nautilus
 
"#try from there"

---

### Post by jamesrl on 2008-12-21
You can also install nautilus-gksu package to grant root [super-user] privileges within an already opened nautilus session.  

I should add that, its usually best not to mess around with changing files in the /usr or /lib directories too much, so the package manager can do everything automatically (and trust all the proper files are there).  That's why you have to manually stipulate you want permission to change something there (so you don't do something bad accidentally like overwrite necessary files).  I'm not entirely familiar with gnome-screensaver configuration (I haven't used a screensaver since i had an old CRT monitor, as they don't make sense with proper power-management and LCD technology), but it seems like there should be a way to add screensavers stored in your home directory.

---

### Post by kixome on 2008-12-21
otherwise, "though this is not wise" you can edit you panel menu by right clicking the application button, and selecting edit menus. When it opens, scroll to system tools and check the root terminal. Then you can access root terminal from Applications>system tools> root terminal.

When root terminal opens, type nautilus and try to copy files once it opens.

!!!!Be very careful what you do as the root user, I have messed up many of my installations by using root!!!!!

---

### Post by shogunmidas on 2008-12-21
what i tried to do and im not even sure if this is the right way to do this... i downloaded the flurry.tar.tg to my desktop, i extracted it and then i didnt know where it should go to make it work so i did a search for "screensaver" one of the files that came up inside of it was every screensaver i currently can use, so i thought i should just moove my new flurry into that file and i could be done with it. but it wouldnt let me.

there was no command i just tried dragging and dropping it in its place.

---

### Post by taurus on 2008-12-21
If you just like drag n drop, don't run "sudo su" from a terminal.  Instead, just run

```
gksudo nautilus
```

---

### Post by shogunmidas on 2008-12-21
i tried that

gksudo nautilus

and this is what i got...

** (nautilus:29073): WARNING **: Unable to add monitor: Operation not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSNautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

---

### Post by kixome on 2008-12-21
obviously the file/directory doesn't exist, not to be a smarty pants, but you should read the output of the command you entered.

---

### Post by kixome on 2008-12-21
bad mojo, but i think i have got it

---

### Post by kixome on 2008-12-21
I think I know what you need to do.

in terminal type: sudo nautilus

when nautilus opens, navigate to /home/yourusername/

then create a new folder/directory named shares, right click this folder and click properties. Click on the share tab. click the box to share the folder. Next click allow other people to write in this folder, then click create share, when prompted click automatically create permissions!. After that try the other steps like gksudo nautilus!

The steps mentioned above should enable sharing and automatically create said folder.

---

