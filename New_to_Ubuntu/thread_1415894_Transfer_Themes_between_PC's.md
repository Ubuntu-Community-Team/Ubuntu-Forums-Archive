---
title: "Transfer Themes between PC's"
date: 2010-02-25
forum: New to Ubuntu
---

### Post by NagWolf on 2010-02-25
Hi, how do I copy my GDM themes from my PC to a Friend's?

I copied /usr/share/gdm/themes over to his PC, but can't convince "Appearance" to list the themes

Thanx so long

---

### Post by ubunterooster on 2010-02-25
1 make sure he has the gnome art theme installer installed.
2 in Appearance, add new themes, select the theme files

---

### Post by NagWolf on 2010-02-26
Thanx for the reply, in theory that should work, but there isn't any .theme files, only Folders with art and xml files in...

:(

Thanx again

---

### Post by ubunterooster on 2010-02-26
so these are customized themes. I am not sure what to do in this case. Otherwise, if they can be, redownload from the site.

---

### Post by mechro on 2010-02-26
On your computer, navigate to /usr/share/gdm/themes

For each theme folder right-click and select **Create Archive**. This will create a tar.gz file which will be recognised as a GDM theme file.

Transfer these tar.gz's to your friend's computer. To install a GDM theme file(.tar.gz) go to **System > Administration > Login Window > Local** and click the Add button.

You might be able to make a tar.gz of your whole /usr/share/gdm/themes folder and do a multi theme installation... I'm not sure but try it and see.

---

