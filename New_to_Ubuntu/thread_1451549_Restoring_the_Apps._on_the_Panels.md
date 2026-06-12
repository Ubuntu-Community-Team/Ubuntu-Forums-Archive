---
title: "Restoring the Apps. on the Panels"
date: 2010-04-10
forum: New to Ubuntu
---

### Post by Otis Spunkmiyer on 2010-04-10
Hello out there, Otis Spunkmiyer here.

I removed some applications from the various panels that I want back.  But don't know how to restore them.
And can't even remember what half of them where, but I would like it to look like it did when I first installed the OS.

Any advice would be appreciated, thank you.

---

### Post by |Mitch| on 2010-04-10
right click + edit menus

or 

right click + add to panel

---

### Post by Otis Spunkmiyer on 2010-04-10
That did not help.  I'm talking about the main panels.
All that did was put items in my task bar.
I want the original applications back on the main panels that fall under the subtitle to the left.

For instance under System-Preference I would like the Accessibility App back.

---

### Post by NCLI on 2010-04-10
If you want it to look exactly like it did when you first installed Ubuntu, go to your Home folder, press ctrl+h, then navigate to .gconf->apps. Then delete the folder called panel.

Finally, press alt+F2, and run "gnome-panel --replace"

---

### Post by Otis Spunkmiyer on 2010-04-10
Nope, still the same.

What happen originally was I deleted the apps. from the 'main menu' under preferences-system.  Where you can check the box's if you want it to show.  I deleted .  But that should have not removed the app from the system, I would think  anyway.

---

### Post by immoweichert on 2010-04-10
If you click System -> Preferences -> Main Menu, you should be able to add all applications that you've taken off again. Are you sure the  apps have been deleted from the sytem ? If then you reinstall the different packages via the synaptic package manager - I think - only been using Ubuntu for 6 days :)

---

### Post by Otis Spunkmiyer on 2010-04-10
I can't add them back from there, because like I said I deleted them.  Not just un-checked the box.

---

### Post by NCLI on 2010-04-10
No offense, but that wasn't a very smart thing to do. You'll have to add all of them, and their icons, back manually. I don't think there's an easy way to do this, other than creating a new user. Programs are stored in /usr/bin. Have fun :(

---

### Post by Otis Spunkmiyer on 2010-04-10
The one I'm most concern about was the Accessibility app. on the 'System'  The panel under Preferences.  The app that helps if you have handicaps.  The Icon was blue and I believe it showed a figure.
I don't know the name to look under in Synaptic Manager.

---

### Post by NCLI on 2010-04-10
Never mind, I found out how to restore your menu. From your home folder, go to ".config", then delete the folder "menus". Lastly, run the command, "gnome-panel --replace" from ALT+F2 again.

---

### Post by NCLI on 2010-04-10
The name of the application you're looking for is "gnome-at-properties".

---

### Post by Otis Spunkmiyer on 2010-04-10
Still no go.
All that did was restore what I had un-checked, but not the ones I deleted.  Any other ideas ? Thanks for all your help.

---

### Post by gulyas on 2010-04-10
so I'm running Karmic, any help on the same issue would be great. I can't find ".config" anywhere, even when I search in "file system" I also accidentally deleted my totem movie player. Help?

---

### Post by NCLI on 2010-04-10
Well, I'm afraid that's all I've got for now, you'll have to restore the ones you need manually. And like I mentioned above, the accessibility settings application can be run with the command "gnome-at-properties".

---

### Post by Otis Spunkmiyer on 2010-04-10
There is no gnome-at-properties listen in synaptic manager.

OK, thank you, I'll run it from terminal.

---

### Post by Otis Spunkmiyer on 2010-04-10
That's the one.  
I wish I knew how to get it back on the panel.

---

### Post by lidex on 2010-04-10
Try this:
```
sudo apt-get install ubuntu-desktop
```

You want accessibility:
```
sudo apt-get install at-spi gnome-accessibility
```
Now edit your menus="System -> Preferences -> Main Menu"

---

### Post by pj_kare on 2010-04-11
I tried this below before posting a reply and it seemed to work fine:

Open: System/Preferences/Main Menu
On the left menu select System then Preferences (which is where the icon belonged).

On the right of the Main Menu window select **+New Item**, leave as Type: Application, and fill in as per below (copy and paste if easier):

```
Name: Assistive Technologies

Command: gnome-at-properties

Comment: Choose which accessibility features to enable when you log in
```To restore the default icon click on the Launcher (spring) icon in the top left corner and in the Browse address clear any text and paste in the following:
```
/usr/share/icons/Humanity/apps/48/preferences-desktop-accessibility.svg
```Click OK.

Note: To replace any others that are missing, try booting into a live cd if you have one, right click on any icon/launcher missing from your menu and select **Add this launcher to desktop**, and actually add it to your desktop (so you can view its properties). Right click on it and select properties, you will then be able to write down or copy and paste the info to a text document and save it to somewhere you can access after you reboot, a flash drive maybe, and use to create new menu launchers when you boot back into your system. (If you click on the icon to try and find where it is it won't work it just expects you to search for it). If you have to **Browse** for icons I think most of the ones you will need are in File System  /usr/share/icons/Humanity/apps/48/ just copy and paste this code: ```
/usr/share/icons/Humanity/apps/48/
``` over anything in Browse, it will load the icons for you.

I trust this helps you without being too confusing, I've gone over it a few times myself to make sure even I can understand it :confused:.

EDIT: ooops....just noticed the [Ubuntu Netbook Remix] in thread title, I don't know if you even have a CD/DVD drive, no matter, I'm sure we can help you with the rest of the launchers you deleted.

---

### Post by Otis Spunkmiyer on 2010-04-11
Thank You !  I had gotten the app. back on the panel before I read your post.  But I could not get the right icon.  But thanks to your post it's right now.

What I had done was navigated to File System-usr/share/applications, saw that indeed the program was still there, then right click on it, went down to properties and click that, and copy the command line to launch.
Having remember about being able to add, (since I had deleted from the same spot) in the 'Main List' I then added it back into the Preference area under Systems.

Once again thank you.

---

### Post by pj_kare on 2010-04-11
Being new(ish) to Ubuntu/Linux myself I'm thrilled to be able to help even if only partly.
And you are most welcome \\:D/

---

