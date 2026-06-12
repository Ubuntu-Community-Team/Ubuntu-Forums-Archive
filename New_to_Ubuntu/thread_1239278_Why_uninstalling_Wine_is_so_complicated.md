---
title: "Why uninstalling Wine is so complicated?"
date: 2009-08-13
forum: New to Ubuntu
---

### Post by Ric_NYC on 2009-08-13
First I had to type this:

sudo apt-get purge wine


It didn't remove It... Then I typed this:

sudo apt-get autoremove wine


No sucess...

Then I had to type this

rm -f $HOME/.config/menus/applications-merged/wine
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine


I _**think**_ I removed it...




Is it my fault?

---

### Post by qamelian on 2009-08-13
> **Ric_NYC said:**
> First I had to type this:

sudo apt-get purge wine


It didn't remove It... Then I typed this:

sudo apt-get autoremove wine


No sucess...

Then I had to type this

rm -f $HOME/.config/menus/applications-merged/wine
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine


I _**think**_ I removed it...




Is it my fault?
I think the problem is that those folders don't get created during the install, but during the first run of wine. Because of that, there is no way for the package manager to know to delete them. This is actually normal. The same thing happens for any app that creates .files & folders for settings during the first run. If you browse the .'s in you home folder after uninstalling an app, you'll usually still find the files and folders containing your personal settings for the app have been left behind.

---

### Post by wojox on 2009-08-13
Try:
```
sudo apt-get --purge remove wine
```

You deleted all the conf files from you HOME directory with the other options.

---

### Post by asmoore82 on 2009-08-13
It's one of those "Feature not a Bug" scenarios ...

The package manager will never destroy user data of any application,
Wine just happens to be one of those apps that create a lot of highly visible user data.

For most Apps it can be a life-saver:
1. you install the App and configure how you want it;
2. you think you no longer need it and remove it;
3. you end up needing it again and re-install it;
4. you happily find that your configuration from step 1 is still intact.

---

### Post by Ric_NYC on 2009-08-13
I started by trying to remove one application from the entries in the Wine menu.... I had that application uninstalled  but it wouldn't disappear from the menu...

I decided to remove everything... That showed me that it wasn't as easy as "sudo apt-get remove wine".

---

### Post by ronaldprettyman on 2009-08-13
> **Ric_NYC said:**
> First I had to type this:

sudo apt-get purge wine


It didn't remove It... Then I typed this:

sudo apt-get autoremove wine


No sucess...

Then I had to type this

rm -f $HOME/.config/menus/applications-merged/wine
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine


I _**think**_ I removed it...




Is it my fault?

rm -rf ~/.wine

---

### Post by qamelian on 2009-08-13
> **ronaldprettyman said:**
> rm -rf ~/.wine
That still won't remove the menu entries for any apps installed via wine.

---

### Post by CatKiller on 2009-08-13
> **Ric_NYC said:**
> I started by trying to remove one application from the entries in the Wine menu.... I had that application uninstalled  but it wouldn't disappear from the menu...

That's actually the fault of the installer that you used to install whatever Windows application it was. The uninstall scripts should remember everything that they added, including Desktop icons and Start menu entries. But they don't. They don't in Windows, either. Whenever I uninstalled something in Windows I would have to manually remove the menu entries that they'd put all over the menu. The same is true here.

It's just that the location of these entries is different (since Wine tries to integrate the Windows applications into your user environment for you). So instead of C:\Documents and Settings\UserName\Start Menu, it's ~/.local/share/applications.

Your actions seem a bit drastic. Would you uninstall Windows just because there was still a Start menu entry for an application that you'd uninstalled?

---

### Post by Ric_NYC on 2009-08-13
> **CatKiller said:**
> That's actually the fault of the installer that you used to install whatever Windows application it was. The uninstall scripts should remember everything that they added, including Desktop icons and Start menu entries. But they don't. They don't in Windows, either. Whenever I uninstalled something in Windows I would have to manually remove the menu entries that they'd put all over the menu. The same is true here.

It's just that the location of these entries is different (since Wine tries to integrate the Windows applications into your user environment for you). So instead of C:\Documents and Settings\UserName\Start Menu, it's ~/.local/share/applications.

Your actions seem a bit drastic. Would you uninstall Windows just because there was still a Start menu entry for an application that you'd uninstalled?

 
No. But that bothered me.
Having an entry for an application that has been uninstalled looks really bad.

I wanted it to be that simple: when an application is uninstalled its entry in the Wine menu should disappear... Don't you agree?

---

### Post by CatKiller on 2009-08-13
> **Ric_NYC said:**
>  I wanted it to be that simple: when an application is uninstalled its entry in the Wine menu should disappear... Don't you agree?

Of course. The same is just as true in Windows; when an application is uninstalled its entry in the Start menu should disappear.

Don't blame Wine, blame software developers that can't be bothered to write proper install/uninstall scripts for Windows software. That's pretty much all of them. If you install Windows software, you have to put up with the fact that most Windows software is crap.

---

### Post by harry2006 on 2009-08-13
i don't think we can expect that uninstalling the software should also remove those folders created by otherwasy...we've to do that manually...

---

### Post by Ric_NYC on 2009-08-13
> **harry2006 said:**
> i don't think we can expect that uninstalling the software should also remove those folders created by otherwasy...we've to do that manually...

I didn't expect that. I don't care if the folders stay somewhere in the system... I'm talking about entries in the menu.
 Do you think that "orphan entries" look good in the "Applications" Menu? They pollute the menu and are good for nothing since they don't start anything when you click on them.

---

### Post by NightwishFan on 2009-08-13
Wine programs stick in GNOME menus. It is a pretty big annoyance. If I remove Morrowind (example). The morrowind menu entry will still be there. Fine, I will just remove it in Alacarte. (Gnome menu editor). Here is the problem. If I reinstall Morrowind, the menu entries will not come back. :(

Solution? Hide them in Alacarte rather than delete them. Then 'unhide' them if you reinstall.

Alacarte is called menu editor in Ubuntu, and it is under the preferences menu.

---

### Post by CatKiller on 2009-08-13
> **Ric_NYC said:**
> Do you think that "orphan entries" look good in the "Applications" Menu? They pollute the menu and are good for nothing since they don't start anything when you click on them.

If you have a mechanism for automatically removing them, I'm sure the Wine people would love to hear from you. Especially since the thing that put them there refuses to remove them itself.

---

