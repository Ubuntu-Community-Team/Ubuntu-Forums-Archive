---
title: "Help unlocking a locked down Edubuntu desktop?"
date: 2010-06-25
forum: New to Ubuntu
---

### Post by DJASH on 2010-06-25
Hi,

I'm experimenting with the lockdown features in Edubuntu 10.04 LTS.

Have created a couple of users and used System | Preferences | Main Menu from these accounts to remove unwanted menu items including the Terminal and Main Menu item itself.  Also used the System | Administration | Lockdown Editor to lockdown accounts...

Now realise I want to add a couple of desktop links to network shares and wishing the system wasn't so locked down!  Can I get the Main Menu (editor) or Terminal back for these users from the main admin account or do I have to delete the locked down users and start again?

DJASH

---

### Post by -humanaut- on 2010-06-25
try hitting alt+f2 and using gksu gnome-terminal

---

### Post by cariboo on 2010-06-25
I'm not sure about Edubuntu, but you should be able to edit the menus, by pressing Alt-F2 and typing:

```
alacarte
```

---

### Post by Jakiejake on 2010-06-25
> **cariboo907 said:**
> I'm not sure about Edubuntu, but you should be able to edit the menus, by pressing Alt-F2 and typing:

```
alacarte
```

LOL how do they make up these names
It poped up with the menu editor

---

### Post by Jakiejake on 2010-06-25
If you are using a Gnome desktop
Then you can right click and remove the menu(s)
Then Just add in quick launch (or whatever they are) icons to launch the internet a few games office etc

---

### Post by DJASH on 2010-06-25
Hi,

thanks for all the prompt replies.

Unfortunately from the locked down accounts ALT-F2 does nothing.
This is because I have used the "Lockdown Editor" pessulus to disable the command line...

Havn't tried the create new panel route yet.  But suspect that if I can create a new panel and add the Main Menu it will just be the edited version duplicated with all the useful programs edited off (by me!).

Think I'm looking for some procedure to do from the admin account (which has no restrictions) to release the lockdown so I can run alacarte or pessulus or terminal...

any more suggestions.

DJASH

---

