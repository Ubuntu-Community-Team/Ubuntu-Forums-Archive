---
title: "Installing themes"
date: 2010-08-25
forum: New to Ubuntu
---

### Post by spillage2 on 2010-08-25
Hi all,

trying to install some nicer themes but every time i download a theme i get "Insufficient permissions to install the theme in:
/home/mark/.themes"

my laptop also has ubutnu 10.04 and has no problems installing new themes.

anyone got any ideas?

cheers

spill.

---

### Post by LiquidMeson on 2010-08-25
Have you tried installing themes by dragging the file to "Appearance Preferences/Theme"

---

### Post by spillage2 on 2010-08-25
Hi,

yes tried that and exactly the same..

---

### Post by LiquidMeson on 2010-08-25
You can see hidden folders like ".themes" by pressing ctrl+h on the keyboard. Once you can see it open the properties by right clicking and see if you have write permissions.

---

### Post by spillage2 on 2010-08-25
ok for some reason its showing as locked and root. any ideas on how to change this to all?

---

### Post by LiquidMeson on 2010-08-25
alt+f2
gksu nautilus

See if it works now.

---

### Post by spillage2 on 2010-08-25
Thanks allot thats going into my own help folder..never knew you do that..

Cheers,

Spill.

---

### Post by inameiname on 2010-08-25
You could manually install them. I typically just extract the compressed file, and copy and paste the folder to /usr/share/themes. Then when changing themes, it'll either be directly in the Appearance Preferences/Theme or you just select Customize it and they will be there.

---

### Post by coffeecat on 2010-08-25
> **spillage2 said:**
> ok for some reason its showing as locked and root. any ideas on how to change this to all?

Nothing in your home folder should be owned by root. Using a root-owned nautilus to copy the files certainly works but it doesn't solve whatever went wrong to get wrong ownerships in your home folder.

Any ideas how that might have happened?

You might want to think of 'sudo chown....' your whole home folder to get the ownership right. If you want the whole syntax post back and I'm sure someone will help you. I'll be logging off in a minute. Late here.

---

### Post by spillage2 on 2010-08-26
I have no idea how this happened and it was the only file with root ownership. This is a fairly new installation and not much has been done to it.

I would like to know more about sudo chown as not that clued up on using commands but starting to learn.

---

### Post by coffeecat on 2010-08-27
From what you say in your first post, it looks as though your /home/mark/.themes folder (and possibly all its contents) is owned by root - which is odd. Clearly something unusual must have happened. It should be owned by "mark" and be in the mark group - if you haven't changed your default group.

The chown command stands for change ownership, and has to be run as administrator if it involves any ownership apart from your own - hence the sudo. To restore your .themes folder to your ownership (+contents), open a terminal (Applications > Accessories) and:

```
sudo chown -R mark: /home/mark/.themes
```The -R option ensures a recursive chown - that is, all files and folders within .themes are chown'ed. Be sure not to miss the trailing colon after 'mark' - that ensures the default group is applied. If you've not used the terminal before for sudo commands, the password prompt may confuse you. It doesn't look as though anything is being typed in, but it is. This is not a bug, but a feature.

Once you've chown'ed your .themes folder, try installing another theme to make sure it works. Rather than simply chown your whole home folder, I suggest you do just the .themes one as above and then check the ownership of all the others to see if anything else is amiss. Open your home folder from the Places menu and show the hidden folders with View > Show Hidden (or ctrl-H). Check each folder in turn with Right-click > Properties > Permissions. In fact there is a folder owned by root -  the Examples one. I don't know why this should be, but it only matters if you want to delete it.

---

