---
title: "GDM Theme isn't on the list!"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by abbott_j on 2009-04-29
I've installed a GDM login theme and it says that it is installed but it doesn't show up on the list of GDM themes. When I try to install it again it says that it is already installed and if I would like to install it again anyway. No matter how many times I install it, it never shows up.

---

### Post by Therion on 2009-04-29
Reboot.

---

### Post by abbott_j on 2009-04-29
i have, many times

---

### Post by abbott_j on 2009-04-29
seriously! i need to know how to fix this!

---

### Post by Mortus Pryde on 2009-04-29
I am sure some one can help you through your problem. I to found bobo's post disrespectful and have reported it as such. I hope he/she has not detured you from resolving yoru issue.

Though I do not know the solution for you as I to am still new and have not had this issue, I am sure there is one. If you could perhaps describe exactly how you installed the GDM theme. It was a GDM theme for the login screen, not for your desktop which is actually a GTK theme?

I may be able to help you a little there if the latter is your case.

---

### Post by abbott_j on 2009-04-29
i installed it from [www.**gnome](www.**gnome)**-**look**.org/* i didn't extract it because i have looked at other ubuntu posts that say to and they're right, i have installed other GDM themes for my login screen in the past. once i've done that i click on add and find it and i add it but it doesn't appear therefor i can't select it for my login screen.*

---

### Post by ikisham on 2009-04-29
You say you **didn't** extraxt or **did** extract? 'cos I think you must extract them and drag the directory (folder) to the 'Themes' folder in System>Preferences>Appearance.

---

### Post by abbott_j on 2009-04-29
you don't extract it or it won't show up when you are searching for it but that's not my case, i can find it but when i click to install it installs but fails to appear on the list of GDM's. And you can't drag it into the themes because it's not one of those themes, it's a different type of theme

---

### Post by Elfy on 2009-04-29
Perhaps there is something wrong with the file you downloaded - could you link to it please.

---

### Post by abbott_j on 2009-04-29
[http://www.gnome-look.org/content/show.php/SystemAccess?content=52145](http://www.gnome-look.org/content/show.php/SystemAccess?content=52145)

i downloaded the (SystemAccess ALL DISTRO 1024x768) one then i later tried the (SystemAccess 1024x768) and it still didn't work

---

### Post by abbott_j on 2009-04-29
sorry bout the smilies, it just did that

---

### Post by ikisham on 2009-04-29
If you see the last posts in that link you gave you'll find a 'fixed' version another guy made. You can try that or wait a bit for a more knowledgeble advice from someone here.
Here's the link: [http://draeath.freeshell.org/systemaccess_1024x768-fixed.tar.gz](http://draeath.freeshell.org/systemaccess_1024x768-fixed.tar.gz)

---

### Post by abbott_j on 2009-04-29
kthxbai

---

### Post by Elfy on 2009-04-29
It appears to show in the login window selection menu as A Glance Is Enough - or at least it did here.


> It does not show in the gdm menu, but if you select the AGlancelsEnough theme, it works. It worked for me that way. from the comments on page 2

---

### Post by fballem on 2009-04-29
> **abbott_j said:**
> [http://www.gnome-look.org/content/show.php/SystemAccess?content=52145](http://www.gnome-look.org/content/show.php/SystemAccess?content=52145)

i downloaded the (SystemAccess ALL DISTRO 1024x768) one then i later tried the (SystemAccess 1024x768) and it still didn't work

I checked the site for you, and it appears that there are technical issues with the theme, which is probably why it isn't working for you. You should uninstall it and select one of the other themes that came with ubuntu. Do a reboot after this to make sure that your system is still working.

I note that the author has provided a different website at [http://draeath.freeshell.org/systemaccess_1024x768-fixed.tar.gz](http://draeath.freeshell.org/systemaccess_1024x768-fixed.tar.gz) but I would use this with caution. Building a GDM Theme is not a simple task.

I am still working my way through the complexities of the GTK themes (the ones that run on your desktop), but when I looked at the contents of the archive, it seemed very light - it appears lots of items that are needed are missing.

Sorry I can't solve this for you, but I would recommend that you remove it. If you're still interested, then go to the site that the author provided and download from there.

Regards,

---

### Post by Mortus Pryde on 2009-04-29
> **fballem said:**
> I checked the site for you, and it appears that there are technical issues with the theme, which is probably why it isn't working for you. You should uninstall it and select one of the other themes that came with ubuntu. Do a reboot after this to make sure that your system is still working.

I note that the author has provided a different website at [http://draeath.freeshell.org/systemaccess_1024x768-fixed.tar.gz](http://draeath.freeshell.org/systemaccess_1024x768-fixed.tar.gz) but I would use this with caution. Building a GDM Theme is not a simple task.

I am still working my way through the complexities of the GTK themes (the ones that run on your desktop), but when I looked at the contents of the archive, it seemed very light - it appears lots of items that are needed are missing.

Sorry I can't solve this for you, but I would recommend that you remove it. If you're still interested, then go to the site that the author provided and download from there.

Regards,

Dispite my limited experiance I was thinking along these lines as well. Similar to when installing a desktop theme it may not just appear as there are several elements that make up a theme and a "Theme" may just carry one component of that, and so not appear as an actual Theme.

---

### Post by Elfy on 2009-04-29
I don't profess to know whether there is anythin gmissing or awry with the package - but I just logged out - A Glance Is Enough will get you the login that you were looking for.

---

### Post by fballem on 2009-04-29
This won't work out of the box, but if you want an idea of what goes into a theme, download this file and extract it to a folder that you set up.

[http://dlc.sun.com/osol/jds/downloads/extras/opensolaris-gdm-themes-0.9.tar.gz](http://dlc.sun.com/osol/jds/downloads/extras/opensolaris-gdm-themes-0.9.tar.gz)

Once you've done that, open the folder to open-solaris-gdm-themes-0.9 > themes > Indiana. You will see quite a list of contents, including a .desktop file. In the past, I have modified earlier versions of this theme, but haven't had a chance to do so recently.

This is fairly complete, when taken with the nimbus GTK theme that includes the nimbus fonts that are needed for this GDM theme to work. As I said earlier, building a complete theme is not a trivial task and it's hard to do correctly.

Regards,

---

